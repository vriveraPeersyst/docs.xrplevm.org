# Using IBC

The Inter-Blockchain Communication Protocol (IBC) is an open-source protocol designed to handle authentication and the transport of data between blockchains. IBC enables heterogeneous blockchains to communicate trustlessly, facilitating the exchange of data, messages, and tokens.

As a Cosmos-based blockchain, the XRPL EVM implements IBC, allowing it to connect seamlessly with other Cosmos chains or any blockchain that supports the IBC protocol. This interoperability enables the native bridging of tokens, messages, and accounts between chains.

For more detailed information on IBC, refer to the [IBC documentation](https://ibc.cosmos.network/).

## Available IBC Channels

The XRPL EVM has established IBC channels with various Cosmos-based chains, enabling cross-chain token transfers and communication.

### Mainnet Channels

| Destination     | From XRPL EVM (Source → Dest) | To XRPL EVM (Dest → Source) |
|-----------------|-------------------------------|-----------------------------|
| Cosmos Hub      | `channel-2`                   | `channel-1377`             |
| Elys Network    | `channel-1`                   | `channel-27`               |
| Injective       | `channel-0`                   | `channel-436`              |
| Osmosis         | `channel-3`                   | `channel-104325`           |
| Noble           | `channel-4`                   | `channel-152`              |

### Testnet Channels

| Destination                | From XRPL EVM (Source → Dest) | To XRPL EVM (Dest → Source) |
|----------------------------|-------------------------------|-----------------------------|
| CosmosHub Provider Testnet | `channel-1`                   | `channel-374`               |
| Osmosis Testnet            | `channel-2`                   | `channel-10361`             |
| Elys Network Testnet       | `channel-3`                   | `channel-10`                |
| Injective Testnet          | `channel-4`                   | `channel-77038`             |

These channels enable seamless token transfers and message passing between XRPL EVM and the connected Cosmos chains.
