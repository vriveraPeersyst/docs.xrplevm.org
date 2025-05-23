# Band Protocol

[Band Protocol](https://www.bandprotocol.com/) is a decentralized, cross-chain data oracle that connects real-world data and APIs to smart contracts. It runs on BandChain, a high-performance blockchain built with the Cosmos SDK, and is designed to support a wide range of blockchain development frameworks.

### Band Oracle Deployment on XRPL EVM Sidechain

| Network | StdReferenceProxy Contract Address                                                                                                                 |
| ------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Testnet | [0x8c064bCf7C0DA3B3b090BAbFE8f3323534D84d68](https://explorer.testnet.xrplevm.org/address/0x8c064bCf7C0DA3B3b090BAbFE8f3323534D84d68?tab=contract) |

{% admonition type="info" name="Note" %}
Mainnet address will be listed when available.
{% /admonition %}

### How to Use Band Oracle in Your Smart Contracts

You can fetch real-time price data from Band’s oracle using the StdReferenceProxy contract. Follow the integration steps provided in the repository below:

[https://github.com/bandprotocol/band-std-reference-contracts-solidity](https://github.com/bandprotocol/band-std-reference-contracts-solidity)

### Available Oracle Price Feeds

The following price feeds are currently supported on XRPL EVM Sidechain:

- XRP
- BTC
- ETH
