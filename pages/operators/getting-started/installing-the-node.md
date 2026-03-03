# Installing the Node

This guide focuses on the fastest and easiest operator path: install the latest `exrpd`, then bootstrap from a snapshot.

It covers **Mainnet**, **Testnet**, and **Devnet**, and includes the following run stacks:

- `systemctl`
- `docker`
- `cosmovisor`
- installation with raw binaries
- installation from source

If you specifically need full historical replay from block 0, use [Sync from Genesis](./sync-from-genesis.md).

## Network reference

| Network | Chain ID | Current Version | Genesis |
| ------- | -------- | --------------- | ------- |
| Mainnet | `xrplevm_1440000-1` | `v10.0.2` | [Genesis](https://raw.githubusercontent.com/xrplevm/networks/refs/heads/main/mainnet/genesis.json) |
| Testnet | `xrplevm_1449000-1` | `v10.0.1` | [Genesis](https://raw.githubusercontent.com/xrplevm/networks/refs/heads/main/testnet/genesis.json) |
| Devnet | `xrplevm_1449900-1` | `v9.0.3` | [Genesis](https://raw.githubusercontent.com/xrplevm/networks/refs/heads/main/devnet/genesis.json) |

## Recommended flow (snapshot-first)

1. Install `exrpd` (raw binary or from source).
2. Initialize and configure your node for the target network.
3. Restore snapshot data (when available).
4. Run the node with `systemctl`, `cosmovisor`, or `docker`.

{% admonition type="info" name="Snapshot availability" %}
Public snapshot providers are currently listed for Mainnet and Testnet in [Snapshots](../resources/snapshots.md). If a Devnet snapshot is not published, use [State Sync](../advanced/sync-options.md#state-sync) or [Sync from Genesis](./sync-from-genesis.md).
{% /admonition %}

## 1) Install `exrpd`

### Method A: Raw binary (recommended for most operators)

```bash
cd /tmp
LATEST_TAG=$(curl -s https://api.github.com/repos/xrplevm/node/releases/latest | grep '"tag_name"' | head -1 | cut -d '"' -f4)
wget "https://github.com/xrplevm/node/releases/download/${LATEST_TAG}/node_${LATEST_TAG#v}_Linux_amd64.tar.gz"
tar -xzf "node_${LATEST_TAG#v}_Linux_amd64.tar.gz"
sudo mv bin/exrpd /usr/local/bin/exrpd
sudo chmod +x /usr/local/bin/exrpd
exrpd version
```

### Method B: Build from source

```bash
sudo apt-get update
sudo apt-get install -y build-essential git jq curl wget

git clone https://github.com/xrplevm/node.git
cd node
make build
sudo mv build/exrpd /usr/local/bin/exrpd
sudo chmod +x /usr/local/bin/exrpd
exrpd version
```

### Check Go version against upstream `go.mod`

If you build from source, ensure your local Go version matches what the node currently requires:

```bash
REQUIRED_GO=$(curl -fsSL https://raw.githubusercontent.com/xrplevm/node/main/go.mod | awk '/^go /{print $2; exit}')
echo "Required Go: ${REQUIRED_GO}"
go version
```

If your installed Go version is older than `REQUIRED_GO`, upgrade Go before compiling.

## 2) Initialize and configure for your network

{% tabs %}

{% tab label="Mainnet" %}
```bash
exrpd config set client chain-id xrplevm_1440000-1
exrpd init <moniker> --chain-id xrplevm_1440000-1
wget -O ~/.exrpd/config/genesis.json https://raw.githubusercontent.com/xrplevm/networks/refs/heads/main/mainnet/genesis.json
PEERS=$(curl -sL https://raw.githubusercontent.com/xrplevm/networks/main/mainnet/peers.txt | sort -R | head -n 10 | paste -sd, -)
sed -i.bak -e "s/^seeds *=.*/seeds = \"${PEERS}\"/" ~/.exrpd/config/config.toml
```
{% /tab %}

{% tab label="Testnet" %}
```bash
exrpd config set client chain-id xrplevm_1449000-1
exrpd init <moniker> --chain-id xrplevm_1449000-1
wget -O ~/.exrpd/config/genesis.json https://raw.githubusercontent.com/xrplevm/networks/refs/heads/main/testnet/genesis.json
PEERS=$(curl -sL https://raw.githubusercontent.com/xrplevm/networks/main/testnet/peers.txt | sort -R | head -n 10 | paste -sd, -)
sed -i.bak -e "s/^seeds *=.*/seeds = \"${PEERS}\"/" ~/.exrpd/config/config.toml
```
{% /tab %}

{% tab label="Devnet" %}
```bash
exrpd config set client chain-id xrplevm_1449900-1
exrpd init <moniker> --chain-id xrplevm_1449900-1
wget -O ~/.exrpd/config/genesis.json https://raw.githubusercontent.com/xrplevm/networks/refs/heads/main/devnet/genesis.json
PEERS=$(curl -sL https://raw.githubusercontent.com/xrplevm/networks/main/devnet/peers.txt | sort -R | head -n 10 | paste -sd, -)
sed -i.bak -e "s/^seeds *=.*/seeds = \"${PEERS}\"/" ~/.exrpd/config/config.toml
```
{% /tab %}

{% /tabs %}

## 3) Restore snapshot data

{% tabs %}

{% tab label="Mainnet" %}
Use any provider from [Snapshots](../resources/snapshots.md) and extract into `~/.exrpd`:

```bash
cd ~/.exrpd
wget -O exrpd.tar.lz4 https://evm-sidechain-snapshots-mainnet.s3.us-east-1.amazonaws.com/exrpd.tar.lz4
tar -xI lz4 -f exrpd.tar.lz4
```
{% /tab %}

{% tab label="Testnet" %}
Use any provider from [Snapshots](../resources/snapshots.md) and extract into `~/.exrpd`:

```bash
cd ~/.exrpd
wget -O exrpd.tar.lz4 https://evm-sidechain-snapshots-testnet.s3.us-east-1.amazonaws.com/exrpd.tar.lz4
tar -xI lz4 -f exrpd.tar.lz4
```
{% /tab %}

{% tab label="Devnet" %}
If no public Devnet snapshot is available, use [State Sync](../advanced/sync-options.md#state-sync) or [Sync from Genesis](./sync-from-genesis.md).
{% /tab %}

{% /tabs %}

## 4) Run the node

### Option A: `systemctl` (recommended)

Create `/etc/systemd/system/exrpd.service`:

```ini
[Unit]
Description=XRPL EVM Node (exrpd)
After=network-online.target

[Service]
User=root
ExecStart=/usr/local/bin/exrpd start
Restart=always
RestartSec=3
LimitNOFILE=65535

[Install]
WantedBy=multi-user.target
```

Start it:

```bash
sudo systemctl daemon-reload
sudo systemctl enable exrpd
sudo systemctl start exrpd
sudo journalctl -u exrpd -f
```

### Option B: `cosmovisor` + `systemctl`

Install and prepare layout:

```bash
go install cosmossdk.io/tools/cosmovisor/cmd/cosmovisor@latest
mkdir -p ~/.exrpd/cosmovisor/genesis/bin
cp /usr/local/bin/exrpd ~/.exrpd/cosmovisor/genesis/bin/exrpd
chmod +x ~/.exrpd/cosmovisor/genesis/bin/exrpd
ln -sfn ~/.exrpd/cosmovisor/genesis ~/.exrpd/cosmovisor/current
```

Create `/etc/systemd/system/cosmovisor-exrpd.service`:

```ini
[Unit]
Description=XRPL EVM Node (Cosmovisor)
After=network-online.target

[Service]
User=root
Environment="DAEMON_NAME=exrpd"
Environment="DAEMON_HOME=/root/.exrpd"
Environment="DAEMON_RESTART_AFTER_UPGRADE=true"
Environment="UNSAFE_SKIP_BACKUP=true"
ExecStart=/root/go/bin/cosmovisor run start
Restart=always
RestartSec=3
LimitNOFILE=65535

[Install]
WantedBy=multi-user.target
```

Start it:

```bash
sudo systemctl daemon-reload
sudo systemctl enable cosmovisor-exrpd
sudo systemctl start cosmovisor-exrpd
sudo journalctl -u cosmovisor-exrpd -f
```

For upgrade operations and safer backup settings, follow [Upgrading your node](../guides/upgrading-your-node.md).

### Option C: `docker`

```bash
docker run -d \
  --name xrplevm-node \
  --restart unless-stopped \
  -v /root/.exrpd:/root/.exrpd \
  --entrypoint exrpd \
  peersyst/exrp:latest \
  start

docker logs -f xrplevm-node
```

## Validation

```bash
exrpd status
curl -s localhost:26657/status | jq .result.sync_info
```

{% admonition type="warning" name="Validator signer safety" %}
If this node is a validator signer, keep a **single active validator signer** only. Never run two active instances with the same `~/.exrpd/config/priv_validator_key.json`, and never roll back `~/.exrpd/data/priv_validator_state.json`.
{% /admonition %}

## Next steps

- [Join the XRPL EVM](./join-the-xrplevm.md)
- [Sync from Genesis](./sync-from-genesis.md)
- [Sync options](../advanced/sync-options.md)

