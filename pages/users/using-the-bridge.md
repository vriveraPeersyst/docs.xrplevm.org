# Using the Bridge

The Axelar Bridge connects multiple blockchain networks, enabling secure asset transfers across the XRPL ecosystem and beyond. This guide explains how the bridge works and highlights the differences between Testnet and Devnet setups.

**Understanding the Axelar Bridge**

The bridge facilitates cross-chain transfers between XRPL, XRPL EVM, and other chains, ensuring smooth interoperability.

**Testnet vs. Devnet**

- **Testnet Bridge (SquidRouter):**  
  The [Testnet bridge](https://testnet.xrpl.squidrouter.com/) connects all Axelar testnet chains. Use XRPL MetaMask Snap or Crossmark.io, and add the [XRPL EVM Testnet network configuration](./getting-started/connect-to-the-xrpl-evm.md#adding-xrpl-evm-to-metamask) to your wallet.

- **Devnet Bridge:**  
  The simpler [Devnet bridge](https://bridge.xrplevm.org) uses the XRPL wallet as a faucet, with connectivity to XRPL EVM achieved via MetaMask.


---

{% tabs %}
   {% tab label="Testnet" %}

      ## 1. Install MetaMask

      Download and [Install MetaMask wallet](./getting-started/install-metamask.md) for your browser.

      ## 2. Install an XRPL Wallet

      Choose one of the XRPL wallet options below:

      - **XRP Ledger Snap:**  
      Install the [XRPL Snap](https://snap.xrplevm.org) for integration with MetaMask.  
      [Quick Start Guide](https://snap-docs.xrplevm.org/getting-started/quick-start)

      - **Crossmark:**  
      Use the [Crossmark wallet](https://crossmark.io) for a browser-first, non-custodial XRPL experience.

      ## 3. Use the Bridge


      **Which chain do you intend to swap from?**

      {% tabs %}
         {% tab label="XRPL"%}

            ### From XRPL to XRPL EVM:

            #### 1. Connect your XRPL Wallet
            
            Click on **Connect**

            ![UsingTheBridge](./images/ConnectXRPLWallet1.png)

            Choose your XRPL Wallet

            ![UsingTheBridge](./images/ConnectXRPLWallet2.png)

            Sign the request to connect your XRPL Wallet with squidrouter.

            ![UsingTheBridge](./images/ConnectXRPLWallet3.png)
            ![UsingTheBridge](./images/ConnectCrossMarks.png)

            Congratulations, first step completed! As you can see in the image the account `rfLm...bYVY` is now connected.

            ![UsingTheBridge](./images/ConnectXRPLWallet4.png)

            #### 2. Select the amount to swap.

            By hovering the mouse on top of your **Balance** and the **Max** button element you can select all your XRPL available drops. 

            ![UsingTheBridge](./images/AmountXRPLWallet1.png)

            **Type** or **paste** your desired swap amount instead.

            ![UsingTheBridge](./images/AmountXRPLWallet2.png)

            #### 3. Set the receiver:

            Click on **Add recipient** to introduce the XRPL EVM destination address.

            ![UsingTheBridge](./images/SetRecepientXRPLWallet1.png)

            Connect your XRPL EVM account with any Wallet Connect compatible wallet or paste the XRPL EVM receiver address.

            ![UsingTheBridge](./images/SetRecepientXRPLWallet2.png)
            ![UsingTheBridge](./images/SetRecepientXRPLWallet3.png)

            #### 4. Transfer

            Press **SWAP** to start the cross-chain bridge transfer of **XRP**.

            ![UsingTheBridge](./images/SwapXRPLWallet.png)

            **Review** and **Approve** the transaction request sent to your XRPL Wallet.

            ![UsingTheBridge](./images/SwapApproveXRPLWallet.png)
            ![UsingTheBridge](./images/ApproveCrossmark.png)

            #### 5. View your XRP on the XRPL EVM Testnet

            [**Add XRPL EVM Testnet**](./getting-started/connect-to-the-xrpl-evm.md#adding-xrpl-evm-to-metamask) Network to MetaMask if you havn't yet.

         {% /tab %}

         {% tab label="XRPL EVM"%}

            #### 1. Connect your XRPL EVM Wallet
            
            Click on **Connect**

            ![UsingTheBridge](./images/ConnectXRPLEVMWallet.png)

            Choose your XRPL EVM Wallet

            ![UsingTheBridge](./images/ConnectXRPLEVMWallet1.png)

            Sign the request to connect your wallet with squidrouter.

            ![UsingTheBridge](./images/ConnectXRPLEVMWallet2.png)
            ![UsingTheBridge](./images/ConnectXRPLEVMWallet3.png)

            Congratulations, first step completed! As you can see in the image the account `0x8ccb...d13D` is now connected.

            ![UsingTheBridge](./images/ConnectXRPLEVMWallet4.png)

            #### 2. Select the amount to swap.

            By hovering the mouse on top of your **Balance** and the **Max** button element you can select all your available XRP. 

            ![UsingTheBridge](./images/AmountXRPLEVMWallet1.png)

            **Type** or **paste** your desired swap amount instead.

            ![UsingTheBridge](./images/AmountXRPLEVMWallet2.png)

            #### 3. Set the receiver:

            Click on **Add recipient** to introduce the XRPL destination address.

            ![UsingTheBridge](./images/SetRecepientXRPLEVMWallet1.png)

            **Connect** your XRPL account with any compatible wallet or **paste** the XRPL receiver address.

            ![UsingTheBridge](./images/SetRecepientXRPLEVMWallet2.png)
            ![UsingTheBridge](./images/SetRecepientXRPLEVMWallet3.png)

            #### 4. Transfer

            Press **SWAP** to start the cross-chain bridge transfer of **XRP**.

            ![UsingTheBridge](./images/SwapXRPLEVMWallet.png)

            **Review** and **Approve** the transaction request sent to your XRPL Wallet.

            ![UsingTheBridge](./images/SwapApproveXRPLEVMWallet.png)

         
         {% /tab %}
      {% /tabs %}


   {% /tab %}
   {% tab label="Devnet" %}

   ## Axelar Bridge (Devnet)

   With the Axelar Bridge, developers and users can:

   - **Obtain test XRP** on XRPL without a dedicated XRPL wallet.  
   \- You can see the XRPL account’s seed in the browser’s Local Storage (Right-click → Inspect → Application → Local Storage).  
   - **Bridge tokens** between XRPL and XRPL EVM (Testnet or Devnet) for dApp development and experimentation.  
   - **Seamlessly move assets** across chains, enabling advanced cross-chain functionality and interoperable applications.

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

   {% /tab %}
{% /tabs %}