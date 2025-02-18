# Send and receive tokens from XRPL

Transferring tokens across chains is a critical aspect of cross-chain dApps. This process involves secure and efficient movement of assets between ecosystems, enabling interoperability. The XRP Ledger (XRPL) is no exception, but its inability to execute native smart contracts makes cross-chain communication even more crucial.

To facilitate token transfers, XRPL integrates with the Axelar cross-chain communication protocol. Axelar offers two primary solutions for this purpose: [Gateway Tokens](https://docs.axelar.dev/dev/general-message-passing/gmp-tokens-with-messages/) and the [Interchain Token Service (ITS)](https://docs.axelar.dev/dev/send-tokens/interchain-tokens/intro/).

For XRPL and XRPL EVM, the Interchain Token Service is the preferred choice. ITS is a modern solution that preserves native token qualities while providing advanced features for managing token properties and supply across chains. In a few words, each connected chain has its own ITS address that will be used as the entry point for token transfers. This address is a smart contract in the XRPL EVM and an account in the XRPL Ledger. For a comprehensive understanding of ITS, check the [official documentation](https://docs.axelar.dev/dev/send-tokens/interchain-tokens/intro/). Additionally, Axelar's [step-by-step guide](https://docs.axelar.dev/dev/send-tokens/interchain-tokens/developer-guides/programmatically-create-a-token/) provides detailed guidance on how to create an interchain token with its corresponding properties.

For practical guidance on using ITS to send and receive tokens, refer to the guides below. These cover how to transfer XRP and [IOU](https://xrpl.org/docs/concepts/tokens/fungible-tokens)/[ERC20](https://docs.openzeppelin.com/contracts/4.x/erc20) tokens between the XRP Ledger and XRPL EVM. The examples are written in TypeScript and leverage the [xrpl.js](https://js.xrpl.org/index.html) and [ethers](https://docs.ethers.org/v6/) libraries to interact with the XRP Ledger and XRPL EVM, respectively.

---

## Sending assets from XRP Ledger to XRPL EVM

Sending assets from the XRP Ledger to the XRPL EVM or other chains is straightforward. The process involves executing a standard payment transaction, specifying the following key parameters:

- [`Amount`](https://js.xrpl.org/interfaces/Payment.html#Amount): Specifies the quantity of the asset to be transferred. The format and value depend on the type of asset being sent (e.g., XRP or IOUs).
- [`Destination`](https://js.xrpl.org/interfaces/Payment.html#Destination): Refers to the **Interchain Token Service** address on the XRP Ledger.  
- [`Memos`](https://js.xrpl.org/interfaces/Payment.html#Memos): Contains additional data required for the transfer, including:
  - The **destination chain ID** on the Axelar network.
  - The **recipient's address** on the destination chain.
  - A **payload hash**, which is only relevant for [GMP messages](https://docs.axelar.dev/dev/general-message-passing/overview/) and ignored in token transfers.

**Important**: All fields within [`Memos`](https://js.xrpl.org/interfaces/Payment.html#Memos) must be encoded in hexadecimal format before submission.

### Sending XRP from XRP Ledger to XRPL EVM

To send **XRP** (the native token) from the XRPL to the XRPL EVM, you simply specify the number of XRP in drops in the [`Amount`](https://js.xrpl.org/interfaces/Payment.html#Amount).

{% tabs %}
{% tab label="Devnet" %}
```ts
import { Wallet, Client, Payment, convertStringToHex } from "xrpl";

// wallet variable corresponds to xrpl.js Wallet instance
// client variable corresponds to xrpl.js Client instance

// Create the payment transaction object
const payment: Payment = {
  TransactionType: "Payment",
  Account: wallet.address, // Sender's address
  Amount: "100000000", // 100 XRP in drops
  // ITS address on the XRPL Devnet
  Destination: "rGAbJZEzU6WaYv5y1LfyN7LBBcQJ3TxsKC",
  Memos: [
    {
      Memo: {
        // hex(destination_address)
        MemoType: Buffer.from("destination_address").toString("hex").toUpperCase(),
        // Destination contract address (hexadecimal, without 0x prefix)
        MemoData: "ECFA31764C91805B6C8E1D488941E41A86531880",
      },
    },
    {
      Memo: {
        // hex(destination_chain)
        MemoType: Buffer.from("destination_chain").toString("hex").toUpperCase(),
        // The destination chain ID on the Axelar network (hexadecimal)
        // for Devnet
        MemoData: Buffer.from("xrpl-evm-devnet").toString("hex").toUpperCase(),
      },
    },
  ],
};

// Autofill transaction
const transaction = await client.autofill(payment);

// Sign transaction
const signedTransaction = wallet.sign(transaction).tx_blob;

// Submit transaction
const result = await client.submit(signedTransaction);
```
{% /tab %}

{% tab label="Testnet" %}
<!-- Placeholder for Testnet configuration; coming soon -->
**Testnet details coming soon.**
{% /tab %}
{% /tabs %}

### Sending IOU tokens from XRP Ledger to XRPL EVM

Sending IOU tokens (fungible tokens on XRPL) is similar, except the `Amount` field is an [`IssuedCurrencyAmount`](https://js.xrpl.org/interfaces/IssuedCurrencyAmount.html). Below is an example for **100 RLUSD**.

{% tabs %}
{% tab label="Devnet" %}
```ts
import { Wallet, Client, Payment, convertStringToHex } from "xrpl";

// wallet variable corresponds to xrpl.js Wallet instance
// client variable corresponds to xrpl.js Client instance

// Create the payment transaction object
const payment: Payment = {
  TransactionType: "Payment",
  Account: wallet.address, // Sender's address
  Amount: {
    currency: "524C555344000000000000000000000000000000", // RLUSD (non-standard code)
    issuer: "rMxCKbEDwqr76QuheSUMdEGf4B9xJ8m5De", // RLUSD issuer address
    value: "100", // Amount to transfer
  },
  // ITS address on the XRPL Devnet
  Destination: "rGAbJZEzU6WaYv5y1LfyN7LBBcQJ3TxsKC",
  Memos: [
    {
      Memo: {
        // hex(destination_address)
        MemoType: Buffer.from("destination_address").toString("hex").toUpperCase(),
        // Destination contract address (hexadecimal, without 0x prefix)
        MemoData: "ECFA31764C91805B6C8E1D488941E41A86531880",
      },
    },
    {
      Memo: {
        // hex(destination_chain)
        MemoType: Buffer.from("destination_chain").toString("hex").toUpperCase(),
        // The destination chain ID on the Axelar network (hexadecimal)
        // for Devnet
        MemoData: Buffer.from("xrpl-evm-devnet").toString("hex").toUpperCase(),
      },
    },
  ],
};

// Autofill transaction
const transaction = await client.autofill(payment);

// Sign transaction
const signedTransaction = wallet.sign(transaction).tx_blob;

// Submit transaction
const result = await client.submit(signedTransaction);
```
{% /tab %}

{% tab label="Testnet" %}
<!-- Placeholder for Testnet configuration; coming soon -->
**Testnet details coming soon.**
{% /tab %}
{% /tabs %}

---

## Sending assets from XRPL EVM to XRP Ledger

To send assets from the XRPL EVM back to the XRPL, you’ll call the [`interchainTransfer`](https://github.com/axelarnetwork/interchain-token-service/blob/9edc4318ac1c17231e65886eea72c0f55469d7e5/contracts/interfaces/IInterchainTokenStandard.sol#L19) method of the **ITS contract** on the XRPL EVM. You must provide:

- `tokenId`: The token’s Axelar ID.
- `destinationChain`: The Axelar chain ID of the target chain (e.g., `"xrpl"` or `"xrpl-dev"`).
- `destinationAddress`: The address on the XRPL where the assets will be received (an R-address).
- `amount`: The amount to transfer, as an integer without decimals.

### ITS Contract Instantiation

Below is an example of instantiating the ITS contract in the **XRPL EVM Devnet**:

{% tabs %}
{% tab label="Devnet" %}
```ts
import { Contract } from "ethers";

// The signer initialization is omitted for brevity

// Instantiate the ITS contract
const its = new Contract(
  "0x1a7580C2ef5D485E069B7cf1DF9f6478603024d3", // ITS address in XRPL EVM Devnet
  ITS_ABI, // ABI for the ITS contract
  signer
);
```
{% /tab %}

{% tab label="Testnet" %}
<!-- Placeholder for Testnet configuration; coming soon -->
**Testnet details coming soon.**
{% /tab %}
{% /tabs %}

### Sending XRP from XRPL EVM to XRP Ledger

To transfer **XRP** back to the XRPL, call `interchainTransfer` on the ITS contract. Use the **XRP token ID** for Devnet:

{% tabs %}
{% tab label="Devnet" %}
```ts
import { ethers } from "ethers";

await its.interchainTransfer(
  "0xbfb47d376947093b7858c1c59a4154dd291d5b2251cb56a6f7159a070f0bd518", // XRP token ID (Devnet)
  "xrpl-dev", // Destination chain ID
  "rAddressFromRecipientInXRPL", // Recipient address on XRP Ledger
  "100000000000000000000", // 100 XRP in wei
  "0x", // Metadata (unused)
  ethers.BigNumber.from("0") // Gas (unused)
);
```
{% /tab %}

{% tab label="Testnet" %}
<!-- Placeholder for Testnet configuration; coming soon -->
**Testnet details coming soon.**
{% /tab %}
{% /tabs %}

### Sending ERC20 tokens from XRPL EVM to XRP Ledger

When sending ERC20 tokens:

1. **Trust Line**: The recipient must have a trust line for that token on the XRP Ledger.
2. **Approve**: The sender must `approve` the ITS contract to transfer tokens on their behalf.

#### 1. Establish a Trust Line on the XRPL

```ts
import { Wallet, Client, TrustSet } from "xrpl";

// wallet variable corresponds to xrpl.js Wallet instance
// client variable corresponds to xrpl.js Client instance

// Create the trust set transaction object
const trustSet: TrustSet = {
  TransactionType: "TrustSet",
  Account: wallet.address,
  LimitAmount: {
    currency: "524C555344000000000000000000000000000000", // RLUSD
    issuer: "rMxCKbEDwqr76QuheSUMdEGf4B9xJ8m5De", // RLUSD issuer
    value: "100", // >= the amount to be transferred
  },
};

// Autofill transaction
const transaction = await client.autofill(trustSet);

// Sign transaction
const signedTransaction = wallet.sign(transaction).tx_blob;

// Submit transaction
const result = await client.submit(signedTransaction);
```

#### 2. Approve the ITS Contract on the XRPL EVM

```ts
import { Contract } from "ethers";

// The signer initialization is omitted for brevity

// Instantiate the ERC20 contract
const erc20 = new Contract(
  "0x20937978F265DC0C947AA8e136472CFA994FE1eD", // RLUSD ERC20 token address (example)
  ERC20_ABI,
  signer
);

// Call the approve method
await erc20.approve(
  "0x1a7580C2ef5D485E069B7cf1DF9f6478603024d3", // ITS address in XRPL EVM Devnet
  "100000000000000000000" // >= the amount to be transferred
);
```

#### 3. Call `interchainTransfer` on the ITS Contract

{% tabs %}
{% tab label="Devnet" %}
```ts
import { ethers } from "ethers";

// Call the interchainTransfer method
await its.interchainTransfer(
  "0x85f75bb7fd0753565c1d2cb59bd881970b52c6f06f3472769ba7b48621cd9d23", // RLUSD token ID (example)
  "xrpl-dev", // Destination chain ID
  "rAddressFromRecipientInXRPL", // Recipient address on XRP Ledger
  "100000000000000000000", // 100 RLUSD in integer form
  "0x", // Metadata (unused)
  ethers.BigNumber.from("0") // Gas (unused)
);
```
{% /tab %}

{% tab label="Testnet" %}
<!-- Placeholder for Testnet configuration; coming soon -->
**Testnet details coming soon.**
{% /tab %}
{% /tabs %}

---

With these examples, you can send and receive both **XRP** and **IOU/ERC20** tokens across the XRPL and the XRPL EVM using Axelar’s **Interchain Token Service (ITS)**. As Testnet details become available, you can place the correct addresses, chain IDs, and token IDs in the **Testnet** tabs to support that environment as well.