# What is the XRPL EVM?

The **XRPL Ethereum Virtual Machine (EVM) Sidechain** is a **sovereign Layer-1 blockchain** funded by [Ripple](https://ripple.com/) and developed by [Peersyst](https://peersyst.com/). It extends the XRP Ledger ecosystem with **full EVM compatibility** for XRP, enabling developers to deploy Ethereum smart contracts, DeFi protocols, and NFTs while keeping **XRP as the native gas currency**.

Built on the [Cosmos SDK](https://cosmos.network/) and secured by [CometBFT](https://cometbft.com/) (formerly Tendermint Core), the XRPL EVM inherits **deterministic finality, modularity, and high throughput**, while remaining **independent of XRPL consensus**. Interoperability is enabled via the **Axelar Network** and **IBC (Inter-Blockchain Communication)**, ensuring fluid connections across XRPL, Ethereum, and the Cosmos ecosystem.

📂 Repositories:

* [XRPL EVM GitHub](https://github.com/xrplevm)
* [XRPL EVM Node](https://github.com/xrplevm/node)
* [Tendermint / CometBFT](https://github.com/tendermint/tendermint)

---

## Architectural Overview

### ⚙️ Base Layer: Cosmos SDK

The XRPL EVM is built with the [Cosmos SDK](https://docs.cosmos.network/), a modular framework that allows developers to compose blockchains with custom modules (governance, staking, fees, bridges). This sovereignty ensures the XRPL EVM can **define its own economics, governance, and upgrade path** without relying on the XRPL or Ethereum mainnet.

### 🔗 Execution Layer: From evmOS → Cosmos EVM

The chain originally integrated [**evmOS** (legacy Evmos)](https://evm.cosmos.network/) as the EVM execution module. However, it is **migrating to Cosmos EVM** — a next-generation EVM implementation designed specifically for the Cosmos SDK.

* **Legacy State (evmOS):**

  * **EVM Version:** Paris
  * **Solidity Compiler:** `solc` ≤ 0.8.24
* **Upcoming State (Cosmos EVM):**

  * **EVM Version:** Prague
  * **Solidity Compiler:** `solc` 0.8.30

This migration improves **EVM equivalence, performance, and developer tooling compatibility**, ensuring dApps built for Ethereum’s latest forks can be deployed on XRPL EVM with minimal changes.

### 🔒 Consensus Layer: CometBFT

Consensus and networking are powered by [CometBFT](https://cometbft.com/) (Tendermint BFT). This provides:

* **Byzantine Fault Tolerance (BFT):** Security even if up to 1/3 of validators act maliciously.
* **Deterministic Finality:** Blocks are finalized in ~5 seconds with no probabilistic rollbacks.
* **Networking Layer:** Optimized p2p stack decoupled from application logic.

---

## Governance: Proof-of-Authority (PoA)

Unlike the XRP Ledger (which uses a unique node list consensus), the XRPL EVM currently operates under a **Proof-of-Authority (PoA)** model.

* **Validators:** A restricted set of entities authorized to produce blocks and participate in governance.
* **Decentralization Roadmap:** Ripple, Peersyst, and early partners currently operate validators, but governance is designed to **progressively decentralize** as the ecosystem matures.
* **PoA Tradeoff:** This design prioritizes **performance and security** in the early stages, while paving the way toward a broader validator set once mainnet adoption stabilizes.

---

## XRP as the Native Currency

The XRPL EVM introduces **XRP as native gas**:

* XRP is bridged from the XRPL via [Axelar](https://axelar.network/), minted on the EVM sidechain, and circulates natively as the **fee token**.
* This means all dApps, contracts, and users interact using **the same XRP they already know**, without introducing a new utility token.
* Bridges are **provisioning mechanisms** only — once XRP is inside the XRPL EVM, it is native to the chain. Consensus does not depend on external bridges.

This alignment ensures the XRPL ecosystem gains programmability **without fragmenting liquidity** into new, redundant tokens.

---

## Interoperability

### 🌉 Bridges

* **Axelar Bridge:** Moves XRP and other assets into XRPL EVM, with support for **General Message Passing (GMP)**, allowing contract-to-contract calls across chains.

### 🌐 IBC (Inter-Blockchain Communication)

The XRPL EVM supports [IBC](https://ibc.cosmos.network/), unlocking interoperability with the **Cosmos Hub, Osmosis, Evmos, and hundreds of IBC-enabled chains**. This extends XRPL liquidity into the entire Cosmos multichain environment.

### Wormhole Integration

Wormhole, one of the leading cross-chain interoperability protocols, is integrating with the XRPL EVM Sidechain.
[Ripple Expands Multichain Interoperability Infrastructure with Wormhole Integration](https://wormhole.com/blog/ripple-expands-multichain-interoperability-infrastructure-with-wormhole)

---

## Developer Experience

The XRPL EVM is designed to be **Ethereum-equivalent**, meaning Solidity developers can build without learning new tools or languages:

* **Languages:** Solidity (≤0.8.24 now, 0.8.30 after Cosmos EVM upgrade).
* **EVM Compatibility:** Currently Paris fork → upgrading to Prague fork.
* **Tools:** Works with [Remix](https://remix.ethereum.org/), Truffle, Hardhat, Foundry, [MetaMask](https://metamask.io/), and [Keplr](https://www.keplr.app/).
* **RPC & APIs:** Standard Ethereum JSON-RPC endpoints are exposed by nodes ([xrplevm/node](https://github.com/xrplevm/node)).

---

## What This Brings to the XRP Ecosystem

The XRPL EVM extends the **utility of XRP** beyond payments by enabling it to fuel **smart contracts and DeFi applications**:

1. **DeFi for XRP:**

   * Lending, borrowing, and yield farming with XRP as gas and collateral.
   * AMMs, liquidity pools, and synthetic assets.

2. **Cross-Chain Liquidity:**

   * XRP gains direct interoperability with Ethereum and Cosmos assets.
   * Enables multi-chain DEXes, NFT marketplaces, and cross-ecosystem dApps.

3. **Programmable Payments:**

   * Combine XRPL’s payment rails with EVM programmability.
   * Automated settlements, escrow, tokenized cross-border transactions.

4. **Developer Onboarding:**

   * Ethereum developers can join the XRP ecosystem without changing tooling.
   * Expands the XRPL ecosystem with a **new wave of dApps** leveraging XRP liquidity.

---

The **XRPL EVM** is a **sovereign Cosmos SDK blockchain** that:

* Uses **XRP as native gas**.
* Runs **CometBFT** consensus under a **PoA validator set**.
* Is **migrating from evmOS → Cosmos EVM**, moving from Paris → Prague fork with `solc` 0.8.30.
* Connects to XRPL, Ethereum, and Cosmos via **Axelar + IBC**.
* Unlocks programmability, DeFi, and multichain utility for the **XRP ecosystem**.
