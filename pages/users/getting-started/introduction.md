# Introduction

To access the full functionality of the **XRPL Ethereum Virtual Machine (EVM)**, you will need an account and a balance of **XRP** to cover transaction fees. This section will guide you through the steps to set up your wallet, obtain XRP, and interact with the XRPL EVM.

---

## Getting Started with XRPL EVM

### Create a Wallet

To interact with the XRPL EVM, you need a compatible Ethereum wallet such as **MetaMask** or **Keplr**. This wallet will serve as your gateway to manage accounts, sign transactions, and deploy smart contracts on the XRPL EVM.

- Learn how to [Install MetaMask](./install-metamask.md).
- Connect your wallet to the XRPL EVM by following the [Connect MetaMask to the XRPL EVM](./connect-to-the-xrpl-evm.md) guide.

- Learn how to [Install Keplr](./install-keplr.md) and add the XRPL EVM Network to your wallet.

---

### Obtain XRP for Transaction Fees

{% tabs %}
{% tab label="Mainnet" %}

Every action on the XRPL EVM, such as deploying smart contracts or transferring tokens, requires a small amount of **XRP** to cover transaction fees. Currently there is no OnRamp directly to the XRPL EVM, so you will have to get XRPL Mainnet XRP, from an exchange or an OnRamp and then bridge to the XRPL EVM.

1. **OnRamp XRP from the XRPL MetaMask Snap**:  
   The XRPL MetaMask Snap has a built in OnRamp with [transak.com](https://transak.com/)
   _(Visit the snap: [XRPL MetaMask Snap](https://snap.xrplevm.org))_

2. **Bridge XRP from the XRP Ledger**:  
    Transfer XRP from the XRP Ledger to the XRPL EVM using the **Bridge**.  
    _(Read more: [Using the Bridge](../using-the-bridge.md))_
{% /tab %}
{% tab label="Testnet" %}

Every action on the XRPL EVM, such as deploying smart contracts or transferring tokens, requires a small amount of **XRP** to cover transaction fees. There are two ways to get XRP for the **XRPL EVM Testnet**:

1. **Use the Faucet**:  
   The XRPL EVM Faucet allows you to request free test XRP for development purposes.  
   _(Read more: [Faucet](../faucet.md))_

2. **Bridge XRP from the XRP Ledger**:  
    Transfer XRP from the XRP Ledger to the XRPL EVM using the **Bridge**.  
    _(Read more: [Using the Bridge](../using-the-bridge.md))_

{% /tab %}
{% tab label="Devnet" %}

Every action on the XRPL EVM, such as deploying smart contracts or transferring tokens, requires a small amount of **XRP** to cover transaction fees. There are two ways to get XRP for the **XRPL EVM Devnet**:

1. **Use the Faucet**:  
   The XRPL EVM Faucet allows you to request free test XRP for development purposes.  
   _(Read more: [Faucet](../faucet.md))_

2. **Bridge XRP from the XRP Ledger**:  
    Transfer XRP from the XRP Ledger to the XRPL EVM using the **Bridge**.  
    _(Read more: [Using the Bridge](../using-the-bridge.md))_
{% /tab %}
{% /tabs %}

---

### Start Building and Exploring

Once your wallet is set up and funded with XRP, you’re ready to explore the XRPL EVM’s functionalities:

- **Deploy Smart Contracts**: Use tools like Remix IDE or Hardhat to deploy Solidity-based smart contracts.  
  _(Read more: [Deploy a Smart Contract](../../developers/developing-smart-contracts/deploy-the-smart-contract.md))_

- **Interact with Smart Contracts**: Use libraries like `ethers.js` or `web3.js` to interact with deployed contracts programmatically.  
  _(Read more: [Interact with a Smart Contract](../../developers/developing-smart-contracts/interact-with-the-smart-contract.md))_

- **Experiment with Cross-Chain Functionality**: Leverage Axelar General Message Passing (GMP) for interoperable applications across multiple chains.

---

Explore these resources and start building with the XRPL EVM. Whether you're a developer or a blockchain user, this documentation will help you make the most of XRPL EVM’s features. Let’s get started!
