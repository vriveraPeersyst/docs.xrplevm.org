# Using the Bridge

The **XRPL EVM Bridge** is a user-friendly solution for moving tokens—such as **XRP**, IOUs, and ERC20 assets-between the **XRP Ledger (XRPL)** and the **XRPL EVM** sidechain. This bridge operates **bidirectionally**:  

With the Axelar Bridge, developers and users can:

- **Obtain test XRP** on XRPL without a dedicated XRPL wallet.  
  \- You can see the XRPL account’s seed in the browser’s Local Storage (Right-click → Inspect → Application → Local Storage).  
- **Bridge tokens** between XRPL and XRPL EVM (Testnet or Devnet) for dApp development and experimentation.  
- **Seamlessly move assets** across chains, enabling advanced cross-chain functionality and interoperable applications.

{% tabs %}
{% tab label="Testnet" %}
## Axelar Bridge (Testnet)

The Axelar-powered bridge enables secure, **bidirectional** transfers of **XRP**, IOUs, and ERC20 tokens between the **XRPL Testnet** and the **XRPL EVM Testnet**. By leveraging XRPL’s self-funded test accounts, you don’t need a separate XRPL wallet to initiate transactions from XRPL to XRPL EVM. However, when sending tokens **from** XRPL EVM **to** XRPL, you’ll sign the transaction in MetaMask.

### Steps to Use the Axelar Bridge (Testnet)

1. **Open the Axelar Bridge**  
   Go to [https://bridge.testnet.xrplevm.org/](https://bridge.testnet.xrplevm.org/)

2. **Set XRPL Testnet as the Source Chain**  
   - Select **"XRPL Testnet"** as the source chain.
   - Select **"XRPL EVM Testnet"** as the destination chain.  
   ![Set XRPL as source chain](./images/usingTheBridgeAxelar1.png)

3. **Select the Testnet Account (Faucet)**  
   - If you need test XRP on the XRPL Testnet this acts as a faucet by generating new funded accounts with 100 XRP.
   ![Select the faucet](./images/usingTheBridgeAxelar2.png)

4. **Connect Your Wallets**  
   - **XRPL Testnet**: No additional signature is required here; the test account is self-funded.
   - **XRPL EVM Wallet**: Connect MetaMask with network set to **XRPL EVM Testnet**.  
   ![Connect Wallets](./images/usingTheBridgeAxelar3.png)

5. **Choose a Token and Amount**  
   - Select **XRP**, IOUs, or an ERC20 token you wish to bridge.
   - Enter the amount to transfer.  
   ![Choose token and amount](./images/usingTheBridgeAxelar4.png)

6. **Transfer and Confirm**  
   - If transferring **from** XRPL **to** XRPL EVM, no XRPL signature is required. If **from** XRPL EVM **to** XRPL, you’ll sign the transaction in MetaMask.
   - Track progress in the [Axelar Testnet Explorer](https://testnet.axelarscan.io/).  
   ![Process bridge transaction](./images/usingTheBridgeAxelar5.png)

7. **Verify the Transaction**  
   - Once complete, you’ll see a confirmation message.
   - Use the [XRPL EVM Testnet Explorer](https://explorer.testnet.xrplevm.org) to verify the transaction.  
   ![Transaction executed successfully](./images/usingTheBridgeAxelar6.png)

By using the Axelar Bridge on Testnet, you can safely experiment with cross-chain transfers and test your dApps without risking real XRP.

{% /tab %}

{% tab label="Devnet" %}
## Axelar Bridge (Devnet)

The Axelar-powered bridge also supports **bidirectional** transfers between the **XRPL Devnet** and the **XRPL EVM Devnet**. Similar to Testnet, XRPL Devnet accounts are self-funded for outgoing transactions, while transfers **from** XRPL EVM **to** XRPL require signing via MetaMask.

### Steps to Use the Axelar Bridge (Devnet)

1. **Open the Axelar Bridge**  
   Visit [https://bridge.devnet.xrplevm.org/](https://bridge.devnet.xrplevm.org/)

2. **Set XRPL Devnet as the Source Chain**  
   - Select **"XRPL Devnet"** as the source chain.
   - Select **"XRPL EVM Devnet"** as the destination chain.  
   ![Set XRPL as source chain](./images/usingTheBridgeAxelar1.png)

3. **Select or Fund a Devnet Account**  
   - If you need test XRP on the XRPL Devnet this acts as a faucet by generating new funded accounts with 100 XRP.
   ![Select the faucet](./images/usingTheBridgeAxelar2.png)

4. **Connect Your Wallets**  
   - **XRPL Devnet**: No separate XRPL signature is required for outgoing transactions.
   - **XRPL EVM Wallet**: Connect MetaMask with network set to **XRPL EVM Devnet**.  
   ![Connect Wallets](./images/usingTheBridgeAxelar3.png)

5. **Choose a Token and Amount**  
   - Select **XRP**, IOUs, or an ERC20 token supported on Devnet.
   - Enter the desired amount to bridge.  
   ![Choose token and amount](./images/usingTheBridgeAxelar4.png)

6. **Transfer and Confirm**  
   - Outgoing from XRPL? No XRPL signature needed. Outgoing from EVM to XRPL? Sign with MetaMask.
   - Monitor status in the [Axelar Devnet Amplifier Explorer](https://devnet-amplifier.axelarscan.io/).  
   ![Process bridge transaction](./images/usingTheBridgeAxelar5.png)

7. **Verify the Transaction**  
   - After completion, a success message appears.
   - Check the [XRPL EVM Devnet Explorer](https://explorer.devnet.xrplevm.org) for transaction details.  
   ![Transaction executed successfully](./images/usingTheBridgeAxelar6.png)

{% /tab %}
{% /tabs %}

## Why Use the Axelar Bridge?

- **Bidirectional Transfers**: Easily move assets **from** XRPL **to** XRPL EVM (no XRPL signature required) or **from** XRPL EVM **to** XRPL (sign with MetaMask).
- **Self-Funded XRPL Accounts**: Automatically obtain test XRP on XRPL without a dedicated wallet plugin.
- **Cross-Chain dApps**: Build decentralized apps that interact with both XRPL and EVM-compatible smart contracts.
- **Security and Decentralization**: Axelar’s cross-chain infrastructure ensures trustless interoperability.