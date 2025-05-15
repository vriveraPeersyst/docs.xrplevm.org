# Join the XRPL EVM

Now that you have successfully installed the `exrpd` binary, it’s time to take the next steps and fully connect to the XRPL EVM. This page provides separate instructions for **Devnet** and **Testnet**. Pick the environment you want to join and follow the steps in that tab.

## Prerequisites

> **Note**: Make sure the [`exrpd` is installed](./installing-the-node.md) before proceeding.

{% tabs %}
{% tab label="Devnet" %}

## Configure the Node

Once you have the `exrpd` binary installed, you need to initialize and configure the node. This involves generating initial configuration files, downloading the appropriate genesis file, and establishing connections to network peers.

### 1. Initialize the node

Initializing your node creates the required configuration files, including validator keys and a default configuration structure. The `<moniker>` is a human-readable name you assign to your node (often the name of your organization or a recognizable identifier), and `<chain-id>` specifies the target network.

```bash
exrpd init YOUR_MONIKER --chain-id exrp_1440002-1
```

After running this, the necessary configuration and key files will be generated in `~/.exrpd`.

### 2. Download the Genesis File

Obtain the Devnet `genesis.json` file and place it in your node’s config directory. If you are trying to validate genesis with the latest version (v6.0.0) as genesis was created using v1.0.0. You can skip the validate genesis `exrpd validate-genesis`:

```bash
wget https://raw.githubusercontent.com/Peersyst/xrp-evm-archive/main/poa-devnet/genesis.json -O ~/.exrpd/config/genesis.json
exrpd validate-genesis
```

If validation succeeds, the genesis file is correct.

### 3. Add Peers

Your node needs to connect to other nodes to synchronize. Fetch a list of Devnet peers and update `persistent_peers` in `~/.exrpd/config/config.toml`:

```bash
PEERS=`curl -sL https://raw.githubusercontent.com/Peersyst/xrp-evm-archive/main/poa-devnet/peers.txt | sort -R | head -n 10 | awk '{print $1}' | paste -s -d, -`
sed -i.bak -e "s/^persistent_peers *=.*/persistent_peers = \"$PEERS\"/" ~/.exrpd/config/config.toml
cat ~/.exrpd/config/config.toml | grep persistent_peers
```

### 4. Advanced Configuration (Optional)

If you need to adjust pruning, logging, or other advanced settings, see the [Advanced Configuration Options](../advanced/node-configuration-options.md).

### 5. Create or Import a Key (Optional)

If you plan to run a validator or sign transactions, generate a new key or import an existing one:

```bash
exrpd keys add <key_name> --keyring-backend <os|file|test>
```

Effective [key management](../validators/managing-keys.md) is critical for the security and operation of validators in the XRPL EVM sidechain.

### 6. (Optional) Download a Snapshot

If you want to speed up synchronization, you can use a snapshot. See the [Snapshots page](../resources/snapshots.md) for details. For example:

```bash
sudo apt-get install wget lz4 -y
cd $HOME/.exrpd
wget https://evm-sidechain-snapshots-devnet.s3.amazonaws.com/exrpd.tar.lz4
tar -xI lz4 -f exrpd.tar.lz4
```

Watch the logs to ensure your node syncs with the Devnet. If everything is correct, you should see blocks being processed.

{% /tab %}
{% tab label="Testnet" %}

## Testnet Setup

The following guide outlines the steps for any participant to launch or join the **XRPL EVM Testnet**.

### 1. Infrastructure Provision

Provision a new machine with stable connectivity and enough resources to run the node. Refer to the XRPL EVM documentation for [minimum specifications](./system-requirements.md).

### 2. Node Installation

Download and install the XRPL EVM node binary using the official instructions:  
[Installing the Node](./installing-the-node.md)

### 3. Configure the Node

Set up the node configuration with the **Testnet** chain ID:

```bash
exrpd config set client chain-id xrplevm_1449000-1
```

Choose a secure keyring backend:

```bash
exrpd config set client keyring-backend <keyring>
```

Adjust other recommended settings:

- **Pruning**: Default
- **API Access**: Disable all except Tendermint RPC (restrict to localhost)
- **Peer Exchange**: Keep default unless specific network config is required

For more details, refer to the [node configuration documentation](https://docs.xrplevm.org/pages/operators/advanced/node-configuration-options) as well as the [node configuration reference](https://docs.xrplevm.org/pages/operators/resources/configuration-reference).

### 4. Create a New Key

Generate a new validator key:

```bash
exrpd keys add <key_name> --key-type eth_secp256k1
```

**Ensure that you back up the mnemonic securely**. Effective [key management](../validators/managing-keys.md) is critical for the security and operation of validators in the XRPL EVM sidechain.

### 5. Initialize the Node

Initialize your node with a moniker (a unique name for your node/validator) and the **Testnet** chain ID:

```bash
exrpd init <moniker> --chain-id xrplevm_1449000-1
```

**Ensure that you back up the node keys securely**. [Read more](https://docs.xrplevm.org/pages/operators/validators/managing-keys).

```sh
~/.exrpd/config/node_key.json
~/.exrpd/config/priv_validator_key.json
```

### 6. Download the Genesis File

Fetch the **Testnet** genesis file:

```sh
wget -O ~/.exrpd/config/genesis.json https://raw.githubusercontent.com/xrplevm/networks/refs/heads/main/testnet/genesis.json
```

### 7. Add Seeds to the Node Configuration

Add seeds to the node configuration that will allow connecting to the rest of the node. Modify the file `~/.exrpd/config/config.toml` to include the following seed node:

```sh
PEERS=`curl -sL https://raw.githubusercontent.com/xrplevm/networks/main/testnet/peers.txt | sort -R | head -n 10 | awk '{print $1}' | paste -s -d, -`
sed -i.bak -e "s/^seeds *=.*/seeds = \"$PEERS\"/" ~/.exrpd/config/config.toml
cat ~/.exrpd/config/config.toml | grep seeds
```

{% /tab %}
{% /tabs %}

### Start the Node

Once your configuration is complete, start the node using your preferred process manager (e.g., systemd, Docker Compose, or another init system) as outlined in the [Installing the Node](./installing-the-node.md) guide. This ensures the node will run continuously and restart on failure:

```sh
# Example using systemd:
systemctl enable exrpd
systemctl start exrpd

# Or, using Docker Compose:
docker-compose up -d xrplevm-node
````

Monitor the logs to verify syncing:

```sh
journalctl -u exrpd -f      # systemd
# or
docker logs -f xrplevm-node # Docker
```

Once it connects to the majority of validators, blocks will start streaming in and your node will produce data.

### Sync the Node

After your node is configured and started, you need to let it synchronize with the network. There are several methods to bring your node up to the current block height, each balancing speed, resource usage, and historical data retention. Common sync approaches include:

- **Sync from Genesis**: Start from block 0 and replay all transactions (slowest, but fully trustless).
- **Snapshot**: Download a pre-generated snapshot of the chain state for faster setup.
- **State Sync**: Leverage CometBFT’s state sync feature to bootstrap the node from recent application state.

For detailed instructions and best practices on each approach, see the [Sync Options page](../advanced/sync-options.md).

### Validate the Setup

- Run `exrpd status` or check logs to confirm synchronization progress.
- Explore [Interacting With the node CLI](../guides/interacting-with-the-node-cli.md) for more commands.

### Next Steps

Once your node is fully synced, you can:

- [Upgrade your node](../guides/upgrading-your-node.md) when new releases are available.
- Customize your node’s behavior in [Node configuration options](../advanced/node-configuration-options.md).
