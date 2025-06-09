# Developers 💻

Welcome! These pages will guide you through building on the **XRPL EVM**, from writing your first smart contract to creating cross-chain applications that tap into the broader Cosmos and Axelar ecosystems. Whether you’re a newcomer to blockchain development or an experienced Solidity engineer, you’ll find everything you need right here.

Below is a quick overview of all the available guides and resources in the developer section. Feel free to explore in whichever order suits you best!

---

## Developing Smart Contracts

1. **[Develop a Smart Contract](./developing-smart-contracts/develop-a-smart-contract.md)**  
   Start with the basics: learn about smart contracts, the benefits of building on XRPL EVM, and how to write Solidity contracts that leverage the XRPL’s speed and low fees.

2. **[Deploy the Smart Contract](./developing-smart-contracts/deploy-the-smart-contract.md)**  
   Walk through step-by-step instructions for deploying your contract on the XRPL EVM network. Covers both Remix IDE for quick deployment and Hardhat for more advanced workflows.

3. **[Interact with the Smart Contract](./developing-smart-contracts/interact-with-the-smart-contract.md)**  
   Once your contract is deployed, discover how to call contract functions, query data, and integrate with libraries like `web3.js` or `ethers.js`.

4. **[Verify the Smart Contract](./developing-smart-contracts/verify-the-smart-contract.md)**  
   Learn how to verify your contract’s source code on the XRPL EVM Explorer, enabling transparency and trust for users who interact with your smart contract.

5. **[Next Steps](./developing-smart-contracts/next-steps.md)**  
   Wrap up your initial learning by reviewing key concepts. Then dive deeper into advanced topics like cross-chain messaging, token standards, and building full-stack dApps.

---

## Making a Cross-Chain DApp

1. **[Introduction to Cross-Chain DApps](./making-a-cross-chain-dapp/introduction.md)**  
   Understand how Axelar’s interoperability layer and the XRPL’s low-cost, high-speed environment open the door for cross-chain applications spanning the EVM and XRPL ecosystems.

2. **[Send Tokens Across Chains](./making-a-cross-chain-dapp/send-tokens.md)**  
   Leverage Axelar’s Interchain Token Service (ITS) for bridging tokens between the XRPL Ledger and XRPL EVM. Learn how to send and receive both XRP and IOU/ERC-20 tokens.

3. **[Send Messages Across Chains](./making-a-cross-chain-dapp/send-messages.md)**  
   Go beyond token transfers. Explore how to call any function on another chain using Axelar’s General Message Passing (GMP)—ideal for advanced cross-chain logic and workflows.

4. **[Cross-Chain DApps FAQ](./making-a-cross-chain-dapp/faqs.md)**  
   Get answers to common questions about architecture, latency, liquidity considerations, and the best practices for building reliable multi-chain solutions.

---

## Interacting with Cosmos

1. **[Introduction](./interacting-with-cosmos/introduction.md)**  
   The XRPL EVM is built on the Cosmos SDK, benefiting from its modular structure and native interoperability features. Learn how the Cosmos SDK and EVM work together under the hood.

2. **[Using IBC](./interacting-with-cosmos/using-ibc.md)**  
   Explore IBC (Inter-Blockchain Communication), a protocol that securely connects Cosmos-based networks. Discover how the XRPL EVM can connect and transfer assets to other IBC-enabled chains.

3. **[Using the API](./interacting-with-cosmos/using-the-api.md)**  
   Query network data via Cosmos endpoints (gRPC, REST, and CometBFT RPC). Interact with governance, staking, and more through straightforward HTTP or gRPC calls.

4. **[Address Translation](./interacting-with-cosmos/address-translation.md)**  
   Understand how the XRPL EVM represents addresses in two formats (Bech32 for Cosmos and `0x` for EVM). Learn to easily translate between them in your apps.

---

## Use Oracle Data

1. **[Overview of Oracles](./use-oracle-data/band-protocol.md)**  
   Learn what blockchain oracles are, why they’re essential for smart contracts, and the role they play in fetching off-chain data securely.

2. **[Integrate Band Protocol Oracle](./use-oracle-data/band-protocol.md)**  
   Step-by-step guide to deploying and interacting with Band Protocol’s StdReferenceProxy contract on the XRPL EVM sidechain.

3. **[Query Available Price Feeds](./use-oracle-data/band-protocol.md)**  
   Discover which asset price feeds (XRP, BTC, ETH, and more) are supported and how to fetch real-time data within your Solidity contracts.

---

## Indexing On-Chain Data

1. **[Indexing XRPL EVM with Goldsky](./indexing-xrpl-evm-with-goldsky.md)**
   Learn how to build high-performance subgraphs to index smart contract events, token data, and custom app logic using Goldsky's hosted GraphQL infrastructure. Merge off-chain and on-chain data into the same endpoint using goldsky's Mirror.

---

## Developer Resources

1. **[Block Explorers](./resources/block-explorers.md)**  
   Locate and analyze on-chain data. Compare Devnet and Testnet explorers, and discover how to inspect blocks, transactions, and contracts in real time.

2. **[Public APIs](./resources/public-apis.md)**  
   Access the XRPL EVM networks (Devnet or Testnet) through various RPC endpoints, REST APIs, and gRPC interfaces—no need to run your own node.

---

## Getting Started & Next Steps

- If you’re new to XRPL EVM, you might want to start by writing a simple Solidity contract, deploying it, and then verifying it. You can then expand your skillset by exploring cross-chain features or diving into the Cosmos SDK.
- For more advanced developers, check out the **Advanced Guides** and **Interacting with Cosmos** sections for extended interoperability and on-chain logic.

The XRPL EVM community is always growing. Join us on [Discord](https://discord.gg/xrplevm) or [GitHub](https://github.com/xrplevm) to share what you build, ask questions, and stay up to date on new features and improvements.

We’re excited to see what you’ll create on the XRPL EVM. Happy building!

