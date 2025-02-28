# Using the Bridge

The **XRPL EVM Bridge** is a user-friendly solution for moving tokens—such as **XRP**, IOUs, and ERC20 assets-between the **XRP Ledger (XRPL)** and the **XRPL EVM** sidechain. This bridge operates **bidirectionally**:  

With the Axelar Bridge, developers and users can:

- **Obtain test XRP** on XRPL without a dedicated XRPL wallet.  
  \- You can see the XRPL account’s seed in the browser’s Local Storage (Right-click → Inspect → Application → Local Storage).  
- **Bridge tokens** between XRPL and XRPL EVM (Testnet or Devnet) for dApp development and experimentation.  
- **Seamlessly move assets** across chains, enabling advanced cross-chain functionality and interoperable applications.

## Axelar Bridge (Devnet)

The Axelar-powered bridge also supports **bidirectional** transfers between the **XRPL Devnet** and the **XRPL EVM Devnet**. Similar to Testnet, XRPL Devnet accounts are self-funded for outgoing transactions, while transfers **from** XRPL EVM **to** XRPL require signing via MetaMask.

### Steps to Use the Axelar Bridge (Devnet)

1. **Open the Axelar Bridge**  
   Visit [https://bridge.xrplevm.org/](https://bridge.xrplevm.org/)

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
   - Check the [XRPL EVM Devnet Explorer](https://explorer.xrplevm.org) for transaction details.  
   ![Transaction executed successfully](./images/usingTheBridgeAxelar6.png)


## Why Use the Axelar Bridge?

- **Bidirectional Transfers**: Easily move assets **from** XRPL **to** XRPL EVM (no XRPL signature required) or **from** XRPL EVM **to** XRPL (sign with MetaMask).
- **Self-Funded XRPL Accounts**: Automatically obtain test XRP on XRPL without a dedicated wallet plugin.
- **Cross-Chain dApps**: Build decentralized apps that interact with both XRPL and EVM-compatible smart contracts.
- **Security and Decentralization**: Axelar’s cross-chain infrastructure ensures trustless interoperability.