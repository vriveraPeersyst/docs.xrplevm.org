# Upgrading your node

Upgrades are coordinated at a specific block height. Nodes running old binaries halt at that height and must be upgraded before they can continue.

For validators, the primary risk during upgrades is **double-signing**. This happens when more than one active validator signer uses the same validator key at the same time (or with inconsistent signer state), which can lead to slashing/jailing.

This guide is a security-first runbook for all run stacks:

- `systemctl`
- `cosmovisor`
- `docker`
- raw binary upgrades
- source-built upgrades

{% admonition type="info" name="List of upgrades" %}
Upgrade heights and target versions for Mainnet/Testnet/Devnet are listed in [Networks](../resources/networks.md).
{% /admonition %}

## Critical validator safety rules

Follow these rules for every validator upgrade:

1. **One signer only**: keep a single active validator signer for `priv_validator_key.json`.
2. **Stop before replace**: fully stop old process/container/service before changing binaries.
3. **Preserve signer state**: never delete or roll back `priv_validator_state.json`.
4. **Never clone signing state to a second active host**.
5. **Verify single active instance** before restart.

{% admonition type="warning" name="Double-sign risk" %}
Do not start a second node (VM, container, backup host, or old binary) with the same validator key while your primary validator is still running. This is the most common path to double-signing.
{% /admonition %}

## Secure upgrade flow (mandatory order)

Use this exact sequence for validators, regardless of stack.

### 1) Confirm target upgrade

- Read target height/version from [Networks](../resources/networks.md).
- Download the target release artifact from [XRPL EVM node releases](https://github.com/xrplevm/node/releases).

### 2) Pre-upgrade checks

```bash
exrpd status
```

Record current height and ensure your node is healthy before starting.

### 3) Stop signer process completely

Stop your runtime stack and confirm the process is gone.

```bash
pgrep -fa exrpd
```

Expected: no active validator signer `exrpd` process.

### 4) Backup validator-critical files

```bash
mkdir -p ~/exrpd-upgrade-backup
cp ~/.exrpd/config/priv_validator_key.json ~/exrpd-upgrade-backup/
cp ~/.exrpd/data/priv_validator_state.json ~/exrpd-upgrade-backup/
cp ~/.exrpd/config/node_key.json ~/exrpd-upgrade-backup/
```

Do not edit these files manually.

### 5) Upgrade binary (raw or source)

#### Raw binary upgrade

```bash
cd /tmp
wget https://github.com/xrplevm/node/releases/download/<target-tag>/node_<target-version>_Linux_amd64.tar.gz
tar -xzf node_<target-version>_Linux_amd64.tar.gz
sudo mv bin/exrpd /usr/local/bin/exrpd
sudo chmod +x /usr/local/bin/exrpd
exrpd version
```

#### Upgrade from source

```bash
cd /tmp
rm -rf node
git clone https://github.com/xrplevm/node.git
cd node
git checkout <target-tag>
make build
sudo mv build/exrpd /usr/local/bin/exrpd
sudo chmod +x /usr/local/bin/exrpd
exrpd version
```

If you build from source, check required Go version first:

```bash
REQUIRED_GO=$(curl -fsSL https://raw.githubusercontent.com/xrplevm/node/main/go.mod | awk '/^go /{print $2; exit}')
echo "Required Go: ${REQUIRED_GO}"
go version
```

### 6) Start exactly one signer

Start your runtime stack (only one instance) and follow logs.

### 7) Post-upgrade validation

```bash
exrpd status
curl -s localhost:26657/status | jq .result.sync_info
```

Confirm blocks are advancing and no upgrade halt error remains.

## Stack-specific upgrade commands

### `systemctl`

```bash
sudo systemctl stop exrpd
pgrep -fa exrpd

# replace /usr/local/bin/exrpd with target binary

sudo systemctl start exrpd
sudo journalctl -u exrpd -f
```

### `cosmovisor`

Place the new binary in the upgrade folder matching the on-chain upgrade name:

```bash
mkdir -p ~/.exrpd/cosmovisor/upgrades/<upgrade-name>/bin
cp /usr/local/bin/exrpd ~/.exrpd/cosmovisor/upgrades/<upgrade-name>/bin/exrpd
chmod +x ~/.exrpd/cosmovisor/upgrades/<upgrade-name>/bin/exrpd
```

Then run:

```bash
sudo systemctl restart cosmovisor-exrpd
sudo journalctl -u cosmovisor-exrpd -f
```

{% admonition type="warning" name="Cosmovisor path" %}
Use `~/.exrpd/...` (not `~/.exprd/...`).
{% /admonition %}

### `docker`

```bash
docker pull peersyst/exrp:<target-tag>
docker stop xrplevm-node
docker rm xrplevm-node

docker run -d \
  --name xrplevm-node \
  --restart unless-stopped \
  -v /root/.exrpd:/root/.exrpd \
  --entrypoint exrpd \
  peersyst/exrp:<target-tag> \
  start

docker logs -f xrplevm-node
```

Do not keep an old validator container running in parallel.

## Automated upgrades with Cosmovisor

Cosmovisor can reduce manual intervention during upgrades. It can also increase operational risk if misconfigured, so validator operators should test in non-production first.

Install:

```bash
go install cosmossdk.io/tools/cosmovisor/cmd/cosmovisor@latest
cosmovisor version
```

Recommended environment variables:

```bash
export DAEMON_NAME=exrpd
export DAEMON_HOME=$HOME/.exrpd
export DAEMON_RESTART_AFTER_UPGRADE=true
export UNSAFE_SKIP_BACKUP=false
export DAEMON_ALLOW_DOWNLOAD_BINARIES=false
```

{% admonition type="warning" name="Auto-download caution" %}
For validators, prefer `DAEMON_ALLOW_DOWNLOAD_BINARIES=false` and stage binaries manually. Auto-download introduces an external dependency at upgrade time.
{% /admonition %}

## Incident prevention checklist

Before starting after upgrade, confirm:

- old process is fully stopped
- no second host/container is signing with same key
- `priv_validator_state.json` is intact and not rolled back
- target binary version is installed
- logs show normal block progression

## Additional Resources

- [Cosmovisor Docs (Cosmos SDK)](https://docs.cosmos.network/main/build/tooling/cosmovisor)
- [XRPL EVM Sidechain Repository](https://github.com/xrplevm/node)
