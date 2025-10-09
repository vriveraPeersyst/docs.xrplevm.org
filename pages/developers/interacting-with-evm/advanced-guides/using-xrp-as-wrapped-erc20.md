# Using **XRP as an ERC‑20** on XRPL EVM

> **Audience:** First‑time XRPL EVM builders who need an ERC‑20 representation of XRP for AMMs, vaults, and DeFi flows.
>
> **Key fact:** Native XRP is automatically exposed **as an ERC‑20** at the sentinel address `0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE` – no custom wXRP contract required.
>
> **Limitation:** There is a hard limit of 7 for calling `0xEee..` contract on the same block. This causes long/complex routes to fail on the aggregator. In this case we recommend using a WXRP forked from ethereum WETH9 contract, deployed and verified by [MOAI Finance](https://xrplevm.moai-finance.xyz/swap) `0x7C21a90E3eCD3215d16c3BBe76a491f8f792d4Bf` as the standard to avoid liquidity fragmentation.

---

## 1 / Why this matters

| Typical Ethereum flow    | XRPL EVM flow                |
| ------------------------ | ---------------------------- |
| ETH → wrap → WETH → pool | **XRP ERC-20 → pool**        |

Because XRPL EVM embeds the wrapping logic in the node, you skip the `wrap/unwrap` calls, saving gas and preventing fragmented liquidity.

---

## 2 / Sentinel address & decimals

* **ERC‑20 address (hard‑coded):** `0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE`
* **Decimals:** `18` (mirrors the common ERC‑20 standard)
* **Total supply:** Mirrors the XRPL ledger in real‑time.

> 📝 **Tip:** Hard‑code the address; there’s no bytecode to query and no proxy to upgrade.

---

## 3 / Quick‑start code (TypeScript + ethers v6)

```ts
import { ethers } from "ethers";

// 1) Connect to Testnet or Mainnet
const provider = new ethers.JsonRpcProvider("https://rpc.testnet.xrpl.org");
const signer   = provider.getSigner();

// 2) Declare the XRP-ERC20 contract
export const XRP_ERC20 = "0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE";
export const erc20Abi = [
  "function transfer(address to, uint256 amount) external",
  "function mint(address to, uint256 amount) external",
  "function burn(uint256 amount) external",
  "function burnFrom(address account, uint256 amount) external",
  "function approve(address spender, uint256 amount) external returns (bool)",
  "function balanceOf(address account) external view returns (uint256)",
  "function increaseAllowance(address spender, uint256 addedValue) external returns (bool)",
  "function allowance(address owner, address spender) external view returns (uint256)"
];
const xrp = new ethers.Contract(XRP_ERC20, erc20Abi, signer);

// 3) Send 5 XRP
await xrp.transfer("0xRecipient...", ethers.parseUnits("5", 18));

// 4) Deposit into an AMM (example)
await xrp.approve(ammAddress, ethers.parseUnits("250", 18));
await amm.addLiquidity(XRP_ERC20, otherToken, ethers.parseUnits("250", 18), minLp);
```

> **Remember:** Users still need a small XRP balance in their account to pay for gas, even though your contract interactions use the XRP ERC‑20.

---

## 4 / Integration checklist

* [ ] Replace any custom **wXRP** addresses with `XRP_ERC20`.
* [ ] Delete `wrap()` / `unwrap()` helper functions.
* [ ] Update subgraphs & indexers to track the sentinel address.
* [ ] Re‑deploy pools or vaults that expected 6‑decimal tokens.
* [ ] Smoke‑test on **Devnet** → then ship to **Mainnet**.

---

## 5 / FAQ

**Q:** *Can I deploy my own wXRP contract?*
**A:** You can, but you’ll split liquidity and confuse wallets. Stick to the built‑in ERC‑20.

**Q:** *Is **`decimals()`** 18?*
**A:** Yes — XRPL EVM represents XRP with 18 decimals so math libraries and UIs designed for ETH‐style tokens work seamlessly.

**Q:** *What happens if I accidentally send XRP to another address?*
**A:** Standard ERC‑20 rules apply; there is no unwrap contract to rescue funds, so double‑check addresses.

---

## 6 / Need help?

**Discord:** [https://discord.gg/xrplevm](https://discord.gg/xrplevm)

Happy building! 🚀
