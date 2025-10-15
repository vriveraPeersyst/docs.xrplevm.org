# Introduction

## Getting Started with XRPL EVM Sidechain

### Create a Wallet

To interact with the XRPL EVM Sidechain, you need a compatible Ethereum wallet such as **MetaMask** or **Keplr**. This wallet will serve as your gateway to manage accounts, sign transactions, and deploy smart contracts on the XRPL EVM Sidechain.

- Learn how to [Install MetaMask](./install-metamask.md).
- Connect your wallet to the XRPL EVM Sidechain by following the [Connect MetaMask to the XRPL EVM](./connect-to-the-xrpl-evm.md) guide.

- Learn how to [Install Keplr](./install-keplr.md) and add the XRPL EVM Sidechain Network to your wallet.

---

### Obtain XRP for Transaction Fees

{% tabs %}
{% tab label="Mainnet" %}
Every action on the XRPL EVM Sidechain, such as deploying smart contracts or transferring tokens, requires a small amount of **XRP** to cover transaction fees. There are several convenient ways to obtain XRP for the XRPL EVM Sidechain:

---

### **Option A: Gas Refuel with Gas.zip**

The easiest way to get started is by using **[Gas.zip](https://www.gas.zip)**, a cross-chain **gas refuel service**.
Gas.zip lets you send small amounts of native tokens (like ETH, BNB, or MATIC) from a supported source chain and receive **XRP directly on the XRPL EVM Sidechain** to cover your transaction fees.

* Supports **300+ destination chains**, including XRPL EVM.
* Built on **LayerZero cross-chain messaging** for secure settlement.
* Optimized for low-friction, small transfers (between ~$0.25 and ~$50 per chain).

This is the fastest way to “top up” your wallet with just enough XRP to start interacting with the XRPL EVM Sidechain.

→ [Try Gas.zip](https://www.gas.zip)


---

### **Option B: Cross-Chain Swap with SquidRouter**

Use Squid to swap tokens from any connected chain to XRP on the XRPL EVM Sidechain directly.
→ [Try Squid](https://app.squidrouter.com)

---

### **Option C: Exchange Transfer**

1. **Buy XRP on a centralized exchange** that supports XRPL EVM Sidechain withdrawals
2. **Withdraw directly** to your XRPL EVM Sidechain wallet address

---

### **Option D: Bridge / On-Ramp From the XRP Ledger (XRPL)**

If you already hold XRP on the **XRPL mainnet**, you can bring it over to the XRPL EVM Sidechain using supported wallets and Squid Router. Many XRPL wallets also integrate **fiat on-ramps**, so you can purchase XRP directly before bridging.

#### 🔗 Supported XRPL Wallets for Squid Router (XRPL → XRPL EVM)

| Wallet                 | Notes / Features                           | On-Ramp / Fiat Integration                                          |
| ---------------------- | ------------------------------------------ | ------------------------------------------------------------------- |
| **[Xaman](https://xaman.app/)**              | Self-custody wallet built for XRPL & Xahau | Integrated **MoonPay** (buy XRP / RLUSD with card, Apple Pay, etc.) |
| **[XRPL MetaMask Snap](https://snap.xrplevm.org)** | MetaMask Snap enabling XRPL connectivity   | Built-in **Transak** on-ramp (buy XRP directly)                     |
| **[Crossmark](https://crossmark.io/)**          | Browser-first, non-custodial XRPL wallet   | No direct fiat on-ramp (signing wallet only)                        |
| **[Joey](https://joeywallet.xyz/)**               | XRPL wallet focused on onboarding          | Integrated **MoonPay** (fiat → XRP)                                 |
| **[Bifrost](https://bifrostwallet.com/)**            | Multi-chain wallet with XRPL support       | XRP on-ramp via **Topper by Uphold**                                |
| **[Girin](https://girin.app/)**              | XRPL wallet in Squid’s supported list      | No on-ramp yet → **OnRamp integration coming soon**                 |

---

#### Steps to Bridge XRP → XRPL EVM

1. **Install / configure your XRPL wallet**

   * Choose one of the supported wallets (Crossmark, Xaman, Joey, Girin, Bifrost, or XRPL MetaMask Snap).
   * Ensure your XRPL account is activated (requires ~1 XRP base reserve).

2. **(Optional) On-Ramp to XRP**

   * Buy XRP directly within supported wallets:

     * **Xaman** → MoonPay
     * **Joey** → MoonPay
     * **Bifrost** → Topper (Uphold)
     * **XRPL MetaMask Snap** → Transak

3. **Bridge with Squid Router**

   * Open [Squid Router](https://app.squidrouter.com) and select **XRPL → XRPL EVM**.
   * Connect your XRPL wallet and authorize.
   * Enter the XRP amount and destination XRPL EVM address.
   * Sign the transaction and confirm the bridge.

4. **Receive XRP on XRPL EVM Sidechain**

   * Once the bridge completes, the XRP will be available in your XRPL EVM wallet (e.g. MetaMask).
   * You can now use it for gas, transfers, or smart contracts.

---

### **Option E: Cosmos Ecosystem Swap with Skip Go**

[Skip Go](https://go.skip.build/) enables swaps from Cosmos-based chains (e.g., Osmosis, Injective, Elys Network, Cosmos Hub, Noble and others.) to XRPL EVM Sidechain using Cosmos IBC
→ [Try Skip](https://go.skip.build/?src_asset=uatom&src_chain=cosmoshub-4&dest_asset=axrp&dest_chain=xrplevm_1440000-1&amount_in=&amount_out=) 


{% /tab %}
{% tab label="Testnet" %}

Every action on the XRPL EVM Sidechain, such as deploying smart contracts or transferring tokens, requires a small amount of **XRP** to cover transaction fees. There are two ways to get XRP for the **XRPL EVM Sidechain Testnet**:

1. **Use the Faucet**:  
   The XRPL EVM Sidechain Faucet allows you to request free test XRP for development purposes.  
   _(Read more: [Faucet](../faucet.md))_

2. **Bridge XRP from the XRP Ledger**:  
    Transfer XRP from the XRP Ledger to the XRPL EVM Sidechain using available **Bridge** services.  
    _(Read more: [Transfer XRP with Bridge Services](../using-the-bridge/transfer-xrp-with-axelar.md))_

{% /tab %}
{% /tabs %}

---

### Start Exploring

- **[Install MetaMask](./install-metamask.md)** – Set up an Ethereum-compatible wallet extension.
- **[Connect MetaMask to the XRPL EVM](./connect-to-the-xrpl-evm.md)** – Add Mainnet or Testnet network details.
- **[Install Keplr](./install-keplr.md)** – Use a Cosmos‑native wallet and add the XRPL EVM network.
- **[Transfer XRP through Axelar](../using-the-bridge/transfer-xrp-with-axelar.md)** – Step by step tutorial for sending XRP using squidrouter.
- **[Transfer XRP through Cosmos IBC ](../sending-through-ibc.md)** – Learn how to use Advanced IBC Transfer and send XRP and other tokens across cosmos connected chains.



---

Explore these resources and start building with the XRPL EVM. Whether you're a developer or a blockchain user, this documentation will help you make the most of XRPL EVM’s features. Let’s get started!
