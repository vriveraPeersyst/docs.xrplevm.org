# Using the Bridge

The [**XRPL EVM Bridge**](https://bridge.xrplevm.org/) plays a critical role in facilitating asset and data transfers between the XRP Ledger (XRPL) and the XRPL Ethereum Virtual Machine (EVM) sidechains.

{% tabs %}
  {% tab label="Testnet" %}
## Axelar Bridge (Testnet)

The Axelar-powered bridge enables secure and decentralized asset transfers between the **XRPL Testnet** and the **XRPL EVM Testnet**. With its advanced interoperability capabilities, Axelar provides a smooth user experience while supporting cross-chain functionality for developers and users alike.

### Steps to Use the Axelar Bridge (Testnet)

1. **Open the Axelar Bridge**  
   Go to [https://bridge.testnet.xrplevm.org/](https://bridge.testnet.xrplevm.org/) (or the designated Testnet URL, if different).

2. **Set XRPL Testnet as the Source Chain**  
   - In the bridge UI, select **"XRPL Testnet"** as the source chain.
   - Select **"XRPL EVM Testnet"** as the destination chain.  
   ![Set XRPL as source chain](./images/usingTheBridgeAxelar1.png)

3. **Select a Testnet Account (Faucet)**  
   - If you need test XRP on the XRPL Testnet, use the [faucet](../faucet.md) to fund your account.
   - Make sure you have enough test XRP for transaction fees.  
   ![Select the faucet](./images/usingTheBridgeAxelar2.png)

4. **Connect Your Wallets**  
   - **XRPL Testnet Wallet**: Connect your XRPL Testnet wallet in the bridge UI.  
   - **EVM Wallet**: Connect your MetaMask or another EVM-compatible wallet, set to **XRPL EVM Testnet**.  
   ![Connect Wallets](./images/usingTheBridgeAxelar3.png)

5. **Choose a Token and Amount**  
   - Select the token you want to bridge (e.g., **XRP**).
   - Enter the amount to transfer.  
   ![Choose token and amount](./images/usingTheBridgeAxelar4.png)

6. **Transfer and Confirm**  
   - Click **Transfer** and confirm the transaction in your wallet.
   - Track progress in the [Axelar Portal](https://axelarscan.io/) (selecting the appropriate Testnet network, if needed).  
   ![Process bridge transaction](./images/usingTheBridgeAxelar5.png)

7. **Verify the Transaction**  
   - Once complete, you’ll see a confirmation.  
   - Use the [XRPL EVM Testnet Explorer](`https://explorer.xrplevtest.net` or similar) to verify the transaction.  
   ![Transaction executed successfully](./images/usingTheBridgeAxelar6.png)

By using the Axelar bridge on Testnet, you can safely experiment with cross-chain transfers and develop/test dApps without using real XRP.

  {% /tab %}

  {% tab label="Devnet" %}
## Axelar Bridge (Devnet)

The Axelar-powered bridge also supports transfers between the **XRPL Devnet** and the **XRPL EVM Devnet**, enabling developers to build and test cutting-edge functionality in a sandbox environment.

### Steps to Use the Axelar Bridge (Devnet)

1. **Open the Axelar Bridge**  
   Visit [https://bridge.devnet.xrplevm.org/](https://bridge.devnet.xrplevm.org/) (the same or a dedicated Devnet URL).

2. **Set XRPL Devnet as the Source Chain**  
   - Choose **"XRPL Devnet"** as the source chain.
   - Choose **"XRPL EVM Devnet"** as the destination chain.  
   ![Set XRPL as source chain](./images/usingTheBridgeAxelar1.png)

3. **Select or Fund a Devnet Account**  
   - If you need XRP on the XRPL Devnet, use the [faucet](../faucet.md) to fund your account.
   - Ensure you have enough XRP to cover Devnet transaction fees.  
   ![Select the faucet](./images/usingTheBridgeAxelar2.png)

4. **Connect Your Wallets**  
   - **XRPL Devnet Wallet**: Connect your XRPL Devnet wallet in the bridge UI.  
   - **EVM Wallet**: Connect your MetaMask (or another EVM-compatible wallet) that is set to **XRPL EVM Devnet**.  
   ![Connect Wallets](./images/usingTheBridgeAxelar3.png)

5. **Choose a Token and Amount**  
   - Select **XRP** or another token supported on the Devnet.
   - Enter the desired amount to bridge.  
   ![Choose token and amount](./images/usingTheBridgeAxelar4.png)

6. **Transfer and Confirm**  
   - Click **Transfer** and confirm the transaction in your wallet.
   - Monitor the transfer status via the [Axelar Portal](https://axelarscan.io/) if Devnet is supported there.  
   ![Process bridge transaction](./images/usingTheBridgeAxelar5.png)

7. **Verify the Transaction**  
   - After the bridge transaction completes, you’ll see a success message.
   - Check the [XRPL EVM Devnet Explorer](https://explorer.xrplevm.org) to confirm the transaction details.  
   ![Transaction executed successfully](./images/usingTheBridgeAxelar6.png)

Using the Devnet bridge is ideal for early-stage testing of interoperability features and cutting-edge dApps.

  {% /tab %}
{% /tabs %}

## Why Use the Axelar Bridge?

- **Seamless Asset Transfers**: Move XRP or other tokens between XRPL and XRPL EVM with minimal friction.  
- **Cross-Chain dApps**: Build decentralized applications that can interact with both XRPL and EVM-compatible contracts.  
- **Security and Decentralization**: Axelar’s cross-chain infrastructure ensures trustless interoperability.

By leveraging the Axelar bridge, you can take full advantage of XRPL EVM’s capabilities—whether you’re on **Testnet** for preliminary development or **Devnet** for deeper experimentation.
