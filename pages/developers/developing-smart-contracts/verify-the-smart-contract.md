# Verify a Smart Contract on the XRPL EVM

After deploying your smart contract on the **XRPL EVM**, it is essential to verify the contract source code on the **XRPL EVM Explorer**. Verification ensures transparency and allows users to interact with your contract directly through the explorer.

This guide provides step-by-step instructions for verifying a smart contract using **Remix IDE** and **Hardhat**, with a recommended approach for using **Standard JSON Input** for seamless verification.

---

## Step 1: Access the XRPL EVM Explorer

{% tabs %}
{% tab label="Devnet" %}
1. Open the **XRPL EVM Devnet Explorer**: [https://explorer.devnet.xrplevm.org](https://explorer.devnet.xrplevm.org).  
2. Locate your deployed contract by searching for its **contract address** in the search bar.  
3. Navigate to the **Contract** tab and click **Verify & Publish**.  
{% /tab %}
{% tab label="Testnet" %}
1. Open the **XRPL EVM Testnet Explorer**: [https://explorer.testnet.xrplevm.org](https://explorer.testnet.xrplevm.org).  
2. Locate your deployed contract by searching for its **contract address** in the search bar.  
3. Navigate to the **Contract** tab and click **Verify & Publish**.  
{% /tab %}
{% /tabs %}

---

## Step 2: Select Verification Method

The **XRPL EVM Explorer** supports multiple verification methods. For detailed and error-free verification, it is highly recommended to use **Standard JSON Input** generated from Remix or Hardhat.

### Why Use Standard JSON Input?

- Ensures all compiler settings (e.g., optimization, Solidity version) match the deployed contract.  
- Reduces the chance of mismatches between your source code and the deployed bytecode.

---

## Step 3: Verification with Remix IDE

### Generate Standard JSON Input in Remix

1. Open your contract in **Remix IDE** ([Remix](https://remix.ethereum.org)).  
2. Compile the contract:  
   - Go to the **Solidity Compiler** plugin.  
   - Select the correct **compiler version** used during deployment.  
   - Enable **Optimizer** if it was used during deployment and configure it to match the deployment settings.  
   - Click **Compile**.  
3. Export the compiler details:  
   - Scroll down to **Compilation Details** and copy **COMPILER INPUT**.  
   - Create a `.json` file on your local machine and paste the **COMPILER INPUT**.  

### Upload JSON Input to XRPL EVM Explorer

1. Return to the **XRPL EVM Explorer**'s **Verify & Publish** page.  
2. Select **Standard JSON Input** as the verification method.  
3. Upload the JSON file you generated from Remix.  
4. Choose the appropriate **License Type** (e.g., MIT, GPL, etc.).  
5. Click **Verify**.  

The explorer will process the JSON file and verify your contract. Once verified, the contract source code will be published on the explorer.

---

## Step 4: Verification with Hardhat

The XRPL EVM Explorer supports multiple verification methods. Below are two recommended approaches using Hardhat—configured separately for **Devnet** and **Testnet**.

---

### A) Standard JSON Input

This method uses the same “compiler input” JSON that Hardhat generates during compilation.

1. **Compile your contracts**  
   ```bash
   npx hardhat compile
   ```
2. **Locate the JSON input**  
   After a successful compile, you’ll find a file named `standard-input.json` in:
   ```
   artifacts/solc-input/
   ```
3. **Upload to XRPL EVM Explorer**  
   1. Go to **Verify & Publish** on the Devnet or Testnet Explorer.  
   2. Select **Standard JSON Input**.  
   3. Upload your `standard-input.json`.  
   4. Pick the matching **License Type** (e.g. MIT).  
   5. Click **Verify**.  

---

### B) Hardhat Verify Plugin

Automate verification from your CLI with `@nomicfoundation/hardhat-verify`.

#### 1. Install the plugin

```bash
npm install --save-dev @nomicfoundation/hardhat-verify
# or
yarn add --dev @nomicfoundation/hardhat-verify
```

#### 2. Update `hardhat.config.ts`

{% tabs %}
{% tab label="Devnet" %}
```ts
// ─── Devnet Configuration ───
import "@nomicfoundation/hardhat-toolbox";
import "@nomicfoundation/hardhat-verify";
import * as dotenv from "dotenv";
import { HardhatUserConfig } from "hardhat/config";

dotenv.config();

const config: HardhatUserConfig = {
  solidity: "0.8.24",
  networks: {
    xrplEVMDevnet: {
      url: process.env.XRPL_EVM_DEVNET_URL!, // e.g. https://rpc.devnet.xrplevm.org
      chainId: 1440002,                       // Devnet chain ID
      accounts: [process.env.PRIVATE_KEY!],
    },
  },
  etherscan: {
    apiKey: {
      xrplEVMDevnet: "devnet-key",           // any non-empty string
    },
    customChains: [
      {
        network: "xrplEVMDevnet",
        chainId: 1440002,
        urls: {
          apiURL:    "https://explorer.devnet.xrplevm.org/api",
          browserURL:"https://explorer.devnet.xrplevm.org"
        }
      }
    ]
  }
};

export default config;
```
{% /tab %}
{% tab label="Testnet" %}
```ts
// ─── Testnet Configuration ───
import "@nomicfoundation/hardhat-toolbox";
import "@nomicfoundation/hardhat-verify";
import * as dotenv from "dotenv";
import { HardhatUserConfig } from "hardhat/config";

dotenv.config();

const config: HardhatUserConfig = {
  solidity: "0.8.24",
  networks: {
    xrplEVMTestnet: {
      url: process.env.XRPL_EVM_URL!,        // e.g. https://rpc.testnet.xrplevm.org
      chainId: 1449000,                       // Testnet chain ID
      accounts: [process.env.PRIVATE_KEY!],
    },
  },
  etherscan: {
    apiKey: {
      xrplEVMTestnet: "testnet-key",         // any non-empty string
    },
    customChains: [
      {
        network: "xrplEVMTestnet",
        chainId: 1449000,
        urls: {
          apiURL:    "https://explorer.testnet.xrplevm.org/api",
          browserURL:"https://explorer.testnet.xrplevm.org"
        }
      }
    ]
  }
};

export default config;
```
{% /tab %}
{% /tabs %}


> **Env vars**  
> ```bash
> XRPL_EVM_URL=           https://rpc.testnet.xrplevm.org
> XRPL_EVM_DEVNET_URL=    https://rpc.devnet.xrplevm.org
> PRIVATE_KEY=            0xYOUR_PRIVATE_KEY
> ```

#### 3. Verify via CLI

Use the appropriate `--network` flag:

- **Devnet**  
  ```bash
  npx hardhat verify \
    --network xrplEVMDevnet \
    <CONTRACT_ADDRESS> \
    [constructorArg1] [constructorArg2] …
  ```
  Explorer: https://explorer.devnet.xrplevm.org

- **Testnet**  
  ```bash
  npx hardhat verify \
    --network xrplEVMTestnet \
    <CONTRACT_ADDRESS> \
    [constructorArg1] [constructorArg2] …
  ```
  Explorer: https://explorer.testnet.xrplevm.org

> If your contract has no constructor parameters, just omit the args.  
> Add `--force` to bypass the “already verified” check if needed.

#### 4. Automating in a Script

You can also embed this into your deploy script:

```ts
// scripts/deploy-and-verify.ts
import { ethers, run } from "hardhat";

async function main() {
  const [deployer] = await ethers.getSigners();
  console.log("Deploying with", deployer.address);

  // 1) Deploy
  const C = await ethers.getContractFactory("MyContract");
  const c = await C.deploy(arg1, arg2);
  await c.waitForDeployment();
  console.log("✅ Deployed at", c.target);

  // 2) Pause so explorer can index (10–15 s)
  await new Promise(r => setTimeout(r, 15_000));

  // 3) Verify on Devnet
  await run("verify:verify", {
    address: c.target,
    constructorArguments: [arg1, arg2],
    network: "xrplEVMDevnet",
    force: true,
  });
  console.log("🔍 Verified on Devnet");

  // — or on Testnet:
  // await run("verify:verify", {
  //   address: c.target,
  //   constructorArguments: [arg1, arg2],
  //   network: "xrplEVMTestnet",
  //   force: true,
  // });
}

main().catch(err => {
  console.error(err);
  process.exitCode = 1;
});
```

---

## Additional Tips

### Matching Compiler Settings

- Ensure the **Solidity compiler version** and **optimizer settings** used during deployment match those used for verification.  
- Mismatched settings may result in verification failure.

### License Selection

- Select a license that matches your contract’s codebase. Common licenses include:
  - MIT License  
  - GNU General Public License (GPL)  
  - Unlicense (No License)

### Explorer Indexing Delays

- BlockScout-based explorers can take a few seconds to index newly deployed bytecode.  
- A brief `setTimeout` (10–15 s) or a retry loop usually resolves “no bytecode” or early-failure errors.

### Future-Proofing

- For upcoming cross-chain features (Cosmos IBC, Axelar GMP), design contracts with interoperability in mind.

---

## Why Verify Your Smart Contract?

1. **Transparency:** Verified contracts allow users to view the source code directly on the explorer.  
2. **Trust:** Builds trust with the community by demonstrating the integrity of your contract.  
3. **Ease of Use:** Enables users to interact with the contract directly through the explorer’s interface.

---

By following these steps, you can verify your smart contract seamlessly on the XRPL EVM Explorer for both Devnet and Testnet environments. For advanced use cases, extend your contracts with cross-chain capabilities using **Axelar GMP** and **Cosmos IBC**.