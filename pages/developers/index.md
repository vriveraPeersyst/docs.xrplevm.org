# Developers 💻

Welcome! These pages will guide you through building on the **XRPL EVM**

## Advanced Guides

1. **[Using XRP as a Wrapped ERC-20](./interacting-with-evm/advanced-guides/using-xrp-as-wrapped-erc20.md)**
   Discover why you *don't* need to wrap XRP on XRPL EVM, how to work with the 18-decimal native ERC-20 at  
   `0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE`, and how to migrate from wXRP to the canonical token.troduction to Goldsky](./interacting-with-evm/use-goldsky-indexer/goldsky-overview.md)**
   Goldsky offers real-time data indexing for XRPL EVM, helping you track contract events, logs, and state changes.

2. **[Set Up Your Indexer](./interacting-with-evm/use-goldsky-indexer/setup-indexer.md)**
   Learn how to create and deploy an indexer for your XRPL EVM smart contracts using [Goldsky](https://goldsky.com).

3. **[Query Indexed Events](./interacting-with-evm/use-goldsky-indexer/query-events.md)**
   Use GraphQL to query your data and integrate insights into your frontend.

4. **[Best Practices](./interacting-with-evm/use-goldsky-indexer/best-practices.md)**
   Learn how to design indexers that are efficient, reliable, and compatible with frequent contracts updates.of Oracles](./interacting-with-evm/use-oracle-data/band-protocol.md)**
   Learn how oracles provide external data feeds to smart contracts.

2. **[Integrate Band Protocol Oracle](./interacting-with-evm/use-oracle-data/band-protocol.md)**
   Use Band's oracle contracts to fetch real-time price data on-chain.

3. **[Query Available Price Feeds](./interacting-with-evm/use-oracle-data/band-protocol.md)**
   Explore available assets (XRP, BTC, ETH, etc.) with secure on-chain access.ain**, from writing your first smart contract to creating advanced applications. Whether you're coming from Ethereum development or new to blockchain development entirely, you'll find everything you need to build high-performance decentralized applications.

The XRPL EVM Sidechain offers a complete development environment with Ethereum compatibility, fast finality, and low transaction costs. You can build native dApps that take full advantage of the blockchain's performance, and optionally integrate cross-chain functionality when needed.

Below is a quick overview of all the available guides and resources in the developer section. Feel free to explore in whichever order suits you best!

---

## Coming from Ethereum?

If you're an Ethereum developer looking for better performance and lower costs, start here:

**Migration Guide for Ethereum Developers** - Learn how to migrate your existing Ethereum projects to the XRPL EVM Sidechain with minimal changes, while gaining significant benefits in speed and cost-efficiency. (Guide available in our developer resources)

---

## Smart Contract Development

Start building on the XRPL EVM Sidechain with these comprehensive guides:

1. **[Develop a Smart Contract](./interacting-with-evm/develop-a-smart-contract.md)**
   Learn the fundamentals of smart contract development on the XRPL EVM Sidechain, including the benefits of native development with fast finality and low costs.

2. **[Deploy the Smart Contract](./interacting-with-evm/deploy-the-smart-contract.md)**
   Step-by-step deployment guide using Remix or Hardhat on the XRPL EVM Sidechain.

3. **[Interact with the Smart Contract](./interacting-with-evm/interact-with-the-smart-contract.md)**
   Call contract functions and integrate using `web3.js` or `ethers.js` in your native dApps.

4. **[Verify the Smart Contract](./interacting-with-evm/verify-the-smart-contract.md)**
   Learn how to verify code on the XRPL EVM Explorer for transparency and trust.

5. **[Next Steps](./interacting-with-evm/next-steps.md)**
   Explore advanced topics like token standards, DeFi protocols, and full-stack dApp architecture.

---

## Axelar Cross-Chain Integration

For dApps that need multi-chain functionality, the XRPL EVM Sidechain offers flexible cross-chain options:

### Bridge Integrations

1. **[Introduction to Cross-Chain Bridges](./interacting-with-evm/advanced-guides/cross-chain-transactions/introduction.md)**
   Learn about available bridge options for connecting with other blockchain ecosystems when cross-chain functionality is needed.

2. **[Cross-Chain Token Transfers](./interacting-with-evm/advanced-guides/cross-chain-transactions/send-tokens.md)**
   Use bridge services to move tokens between XRPL EVM Sidechain and other networks.

3. **[Cross-Chain Messaging](./interacting-with-evm/advanced-guides/cross-chain-transactions/send-messages.md)**
   Execute smart contract logic across chains using cross-chain messaging protocols.

4. **[Integrate the Squid Widget](./interacting-with-evm/advanced-guides/cross-chain-transactions/swap-with-squid-widget.md)**
   Add the [Squid Widget](https://docs.squidrouter.com/widget-integration/add-a-widget/widget/getting-started) to enable token swaps from any chain into XRP on XRPL EVM. Perfect for onboarding users directly from Ethereum, Arbitrum, Polygon, etc.

5. **[Skip Widget](../developers/interacting-with-cosmos/advanced-guides/cross-chain-transactions/swap-with-skip-widget.md)**
   Add cross-chain swaps from Cosmos chains to your app.

### Cosmos Cross-Chain Ecosystem Integration

1. **[Cosmos SDK Foundation](./interacting-with-cosmos/introduction.md)**
   Understand how XRPL EVM Sidechain leverages the Cosmos SDK for performance and modularity.

2. **[Using IBC](./interacting-with-cosmos/using-ibc.md)**
   Transfer assets to and from other Cosmos SDK chains using Inter-Blockchain Communication.

3. **[Using the API](./interacting-with-cosmos/using-the-api.md)**
   Query network data using gRPC, REST, or CometBFT endpoints.

4. **[Address Translation](./interacting-with-cosmos/advanced-guides/address-translation.md)**
   Convert addresses between Cosmos Bech32 and EVM-style `0x` formats.

5. **[Integrate Cosmos Widgets](./interacting-with-cosmos/advanced-guides/cross-chain-transactions/swap-with-skip-widget.md)**
   Add widgets to enable users to swap from Cosmos chains like Osmosis or Injective directly into XRP on XRPL EVM Sidechain.

---

## Use Oracle Data

1. **[Overview of Oracles](./use-oracle-data/band-protocol.md)**
   Learn how oracles provide external data feeds to smart contracts.

2. **[Integrate Band Protocol Oracle](./use-oracle-data/band-protocol.md)**
   Use Band’s oracle contracts to fetch real-time price data on-chain.

3. **[Query Available Price Feeds](./use-oracle-data/band-protocol.md)**
   Explore available assets (XRP, BTC, ETH, etc.) with secure on-chain access.

---

## Use Goldsky Indexers

1. **[Introduction to Goldsky](./interacting-with-evm/use-goldsky-indexer/goldsky-overview.md)**
   Goldsky offers real-time data indexing for XRPL EVM, helping you track contract events, logs, and transactions without running your own infrastructure.

2. **[Set Up Your Indexer](./interacting-with-evm/use-goldsky-indexer/setup-indexer.md)**
   Learn how to create and deploy an indexer for your XRPL EVM smart contracts using [Goldsky Studio](https://goldsky.com/).

3. **[Query Indexed Events](./interacting-with-evm/use-goldsky-indexer/query-events.md)**
   Use GraphQL to query your data and integrate insights into your frontend.

4. **[Best Practices](./interacting-with-evm/use-goldsky-indexer/best-practices.md)**
   Learn how to design indexers that are efficient, reliable, and compatible with frequent contract changes or upgrades.

---

## Advanced Guides

1. **[Using XRP as a Wrapped ERC-20](./advanced-guides/using-xrp-as-wrapped-erc20.md)**
   Discover why you *don’t* need to wrap XRP on XRPL EVM, how to work with the 18-decimal native ERC-20 at  
   `0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE`, and how to migrate from wXRP to the canonical token.

---

## Developer Resources

1. **[Block Explorers](./resources/block-explorers.md)**
   Track and inspect blocks, transactions, and contracts.

2. **[Public APIs](./resources/public-apis.md)**
   Access XRPL EVM via public RPC and REST endpoints.

---

## Getting Started & Next Steps

* Begin with deploying and verifying your first contract.
* Dive into Axelar and Cosmos sections to explore cross-chain logic and liquidity flows.
* Use Goldsky to index and query your contract data efficiently.
* Join the XRPL EVM developer community on [Discord](https://discord.gg/xrplevm) and [GitHub](https://github.com/xrplevm).

We're excited to see what you build next on XRPL EVM. 🚀