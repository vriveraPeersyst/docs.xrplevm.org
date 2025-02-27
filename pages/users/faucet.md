# Faucet

To explore and interact with the **XRPL EVM Sidechain**, you need test XRP (`XRP`) to cover transaction fees and execute smart contracts. There are two primary ways to obtain test `XRP`:

- **Faucet** [Chains.tools](https://chains.tools/faucet/xrplevm) — **for Devnet**  
- **[XRPL EVM Bridge](../users/using-the-bridge.md)** — for transferring XRP from XRPL Devnet or Testnet

{% tabs %}
{% tab label="Devnet" %}

## Using the Faucet (Devnet)

To acquire test `XRP` on the **XRPL EVM Devnet**, you can use the [Chains.tools Faucet](https://chains.tools/faucet/xrplevm) or transfer from the XRPL Devnet via the [XRPL EVM Bridge](../users/using-the-bridge.md).

### Steps to Use the Faucet (Devnet)

1. **Visit the Faucet Website**

   - Go to the **XRPL EVM Devnet** Chains.tools [Faucet](https://chains.tools/faucet/xrplevm).

2. **Enter Your Wallet Address**

   - Copy your wallet address from an EVM-compatible wallet (e.g., MetaMask) configured for the XRPL EVM Devnet.
   - Paste the wallet address into the faucet’s input field.

3. **Complete the CAPTCHA**

   - Prove you’re not a robot.

4. **Request Test XRP**

   - Click the button to request `XRP`.
   - Each wallet can request up to **10 XRP every 60 minutes** (subject to change).

5. **Check Your Wallet**
   - Open your wallet (e.g., MetaMask) on the **XRPL EVM Devnet**.
   - Confirm your new test `XRP` balance.

If you run out of faucet requests or need additional test tokens, consider bridging from the **XRPL Devnet** using the [XRPL EVM Bridge](../users/using-the-bridge.md).

{% /tab %}

{% tab label="Testnet" %}

## No Dedicated Faucet (Testnet)

Currently, there is **no dedicated faucet** available on the **XRPL EVM Testnet**.  
Instead, you can obtain XRP for the Testnet via the **XRPL EVM Bridge** once it’s ready at [bridge.testnet.xrplevm.org](https://bridge.testnet.xrplevm.org).

### Steps

1. **Wait for the Bridge Availability**  
   - A dedicated Testnet bridge at [bridge.testnet.xrplevm.org](https://bridge.testnet.xrplevm.org) is planned.  
   - Once operational, you can transfer XRP from the XRPL Testnet to the XRPL EVM Testnet.

2. **Configure Your Wallet**  
   - Make sure your EVM-compatible wallet (e.g., MetaMask) is configured for the **XRPL EVM Testnet**.

3. **Use the Bridge**  
   - Follow the instructions provided on the bridge site to lock or transfer test XRP from the XRPL Testnet to your XRPL EVM Testnet address.

Check the [XRPL EVM Bridge guide](../users/using-the-bridge.md) for general bridge usage details. 

{% /tab %}
{% /tabs %}

## Next Steps

- **Bridge Assets**: If you want to move tokens from the XRPL (Testnet or Devnet) to the XRPL EVM sidechain, check out the [XRPL EVM Bridge guide](../users/using-the-bridge.md).
- **Deploy Smart Contracts**: Learn how to [deploy a contract](../../developers/developing-smart-contracts/deploy-the-smart-contract.md) on the XRPL EVM Testnet or Devnet.

By leveraging the bridge (or the Devnet faucet), you can quickly begin developing and experimenting on the XRPL EVM sidechains without spending real XRP.