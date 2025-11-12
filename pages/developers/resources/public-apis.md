# Public APIs

Public APIs offer ready-to-use endpoints for accessing and interacting with the XRPL EVM network without needing to run your own node. They enable developers, wallets, and services to read blockchain data, send transactions, and query network status in real time.

{% tabs %}

{% tab label="Mainnet" %}

## Mainnet Official Public APIs

| Type              | URL                                                                       |
| ----------------- | ------------------------------------------------------------------------- |
| Ethereum JSON RPC | [https://rpc.xrplevm.org](https://rpc.xrplevm.org)                        |
| Ethereum JSON WS  | [https://ws.xrplevm.org](https://ws.xrplevm.org)                          |
| Tendermint RPC    | [https://cosmos-rpc.xrplevm.org](https://cosmos-rpc.xrplevm.org)          |
| Cosmos gRPC       | [https://cosmos-grpc.xrplevm.org](https://cosmos-grpc.xrplevm.org)        |
| Cosmos API        | [https://cosmos-api.xrplevm.org](https://cosmos-api.xrplevm.org)          |

## Grove as Main Service Provider

[Grove](https://grove.city) is the **main service provider** for XRPL EVM via its [Build In The Shade](https://buildintheshade.com/docs) portal.  
They offer enterprise-grade infrastructure with guaranteed uptime, global edge network, and developer-first tooling for both Mainnet and Testnet.

With Grove, you can access:

- **Ethereum JSON-RPC** over HTTPS and WebSockets  
- **CometBFT (Tendermint) RPC** via REST endpoints  
- **Cosmos SDK REST APIs** for modules like `bank`, `staking`, etc.  
- **Batching support** and enhanced error handling for JSON-RPC calls  

Grove provides public endpoints for quick integration and testing, with support for authenticated requests for production use.

👉 Check the full Grove documentation and endpoints here:  
[https://buildintheshade.com/docs](https://buildintheshade.com/docs)

### Mainnet Endpoints

| Interface                      | Endpoint                                                         | Notes                                                                                                                      |
| ------------------------------ | ---------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Ethereum JSON RPC (HTTPS)      | `https://xrplevm.buildintheshade.com`                            | Send JSON-RPC 2.0 requests. Standard Ethereum JSON-RPC API for EVM interactions.                                          |
| Ethereum JSON WS (WSS)         | `wss://xrplevm.buildintheshade.com`                              | Use for `eth_subscribe` (e.g., `newHeads`). Real-time event subscriptions and monitoring.                                  |
| Cosmos Chain ID                | `xrplevm_1440000-1`                                              | Cosmos Chain ID for XRPL EVM Sidechain Mainnet.                                                                            |
| Block Explorer                 | [XRPL EVM Explorer](https://explorer.xrplevm.org/)              | Official block explorer for XRPL EVM Mainnet.                                                                              |

### Testnet Endpoints

| Interface                      | Endpoint                                                         | Notes                                                                                                                      |
| ------------------------------ | ---------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Ethereum JSON RPC (HTTPS)      | `https://xrplevm-testnet.buildintheshade.com`                    | Send JSON-RPC 2.0 requests. Standard Ethereum JSON-RPC API for EVM interactions.                                          |
| Ethereum JSON WS (WSS)         | `wss://xrplevm-testnet.buildintheshade.com`                      | Use for `eth_subscribe` (e.g., `newHeads`). Real-time event subscriptions and monitoring.                                  |
| Cosmos Chain ID                | `xrplevm_1449000-1`                                              | Cosmos Chain ID for XRPL EVM Sidechain Testnet.                                                                            |
| Block Explorer                 | [XRPL EVM Testnet Explorer](https://explorer.testnet.xrplevm.org/) | Official block explorer for XRPL EVM Testnet.                                                                              |

## Pocket Network

[Pocket Network](https://api.pocket.network) provides **enterprise-grade infrastructure** for XRPL EVM with guaranteed uptime, global edge network, and developer-first tooling.

With Pocket Network, you can access:

- **JSON-RPC** for standard Ethereum JSON-RPC API interactions
- **CometBFT API** for Tendermint consensus layer access
- **Cosmos SDK API** for Cosmos SDK REST and gRPC endpoints
- **WebSockets** for real-time event subscriptions and monitoring

Pocket Network offers a free public RPC endpoint with fair use limits. No API key required for basic usage.

👉 Check the full Pocket Network API documentation:  
- **Mainnet**: [https://api.pocket.network/docs/xrplevm](https://api.pocket.network/docs/xrplevm)  
- **Testnet**: [https://api.pocket.network/docs/xrplevm-testnet](https://api.pocket.network/docs/xrplevm-testnet)

### Mainnet Network Information

| Property              | Value                                              |
| --------------------- | -------------------------------------------------- |
| **Network Name**      | XRPL EVM Sidechain                                 |
| **Native Token**      | XRP                                                |
| **Cosmos Chain ID**   | `xrplevm_1440000-1`                                |
| **Pocket Service ID** | `xrplevm`                                          |
| **Block Explorer**    | [XRPL EVM Explorer](https://explorer.xrplevm.org/) |

### Testnet Network Information

| Property              | Value                                                              |
| --------------------- | ------------------------------------------------------------------ |
| **Network Name**      | XRPL EVM Testnet                                                   |
| **Native Token**      | XRP                                                                |
| **Cosmos Chain ID**   | `xrplevm_1449000-1`                                                |
| **Pocket Service ID** | `xrplevm-testnet`                                                  |
| **Block Explorer**    | [XRPL EVM Testnet Explorer](https://explorer.testnet.xrplevm.org/) |

### Supported APIs

| API                | Documentation                                                           |
| ------------------ | ----------------------------------------------------------------------- |
| **JSON-RPC**       | [JSON-RPC Supported Methods](https://api.pocket.network/docs/api-definition/definition#json-rpc-supported-methods) |
| **CometBFT API**   | [Cosmos & CometBFT](https://api.pocket.network/docs/api-definition/definition#cosmos--cometbft)           |
| **Cosmos SDK API** | [Cosmos & CometBFT](https://api.pocket.network/docs/api-definition/definition#cosmos--cometbft)           |
| **WebSockets**     | [WebSockets](https://api.pocket.network/docs/api-definition/definition#websockets)                 |

### Public Endpoint

Pocket Network provides a free public RPC endpoint with fair use limits. No API key required for basic usage. For production applications, consider using authenticated endpoints with higher rate limits.

{% tabs %}

        {% tab label="Ethereum JSON RPC" %}
        | Provider/Validator              | RPC Endpoint URL                                                                              |
        | ------------------------------- | --------------------------------------------------------------------------------------------- |
        | **Peersyst**                    | [https://rpc.xrplevm.org](https://rpc.xrplevm.org)                                            |
        | **Grove**                       | [https://xrplevm.buildintheshade.com](https://xrplevm.buildintheshade.com)                   |
        | **Cumulo**                      | [https://json-rpc.xrpl.cumulo.org.es](https://json-rpc.xrpl.cumulo.org.es)                    |
        | **Imperator**                   | [https://rpc_evm-xrp.imperator.co/](https://rpc_evm-xrp.imperator.co/)                        |
        | **Enigma**                      | [https://xrp-evm-rpc.enigma-validator.com/](https://xrp-evm-rpc.enigma-validator.com/)        |
        | **Stakeme**                     | [https://xrpl-evm-rpc.stakeme.pro/](https://xrpl-evm-rpc.stakeme.pro/)                        |


        {% /tab %}
        {% tab label="Ethereum JSON WS" %}
        | Provider/Validator  | WSS Endpoint URL                                                                                 |
        | ------------------- | ------------------------------------------------------------------------------------------------ |
        | **Peersyst**        | [https://ws.xrplevm.org]( https://ws.xrplevm.org)                                                |
        | **Grove**           | [wss://xrplevm.buildintheshade.com](wss://xrplevm.buildintheshade.com)                           |
        | **Cumulo**          | [https://ws.xrpl.cumulo.org.es](https://ws.xrpl.cumulo.org.es)                                   |
        | **Imperator**       | [ws://ws_evm-xrp.imperator.co](ws://ws_evm-xrp.imperator.co)                                     |
        

        {% /tab %}
        {% tab label="Tendermint RPC" %}
        | Provider/Validator   | EVM RPC Endpoint URL                                                                               |
        | ------------------------- | ----------------------------------------------------------------------------------------------|
        | **Peersyst**              | [https://cosmos-rpc.xrplevm.org](https://cosmos-rpc.xrplevm.org)                              |
        | **Polkachu**              | [https://xrp-rpc.polkachu.com/](https://xrp-rpc.polkachu.com/)                                |
        | **Cumulo**                | [https://rpc.xrpl.cumulo.org.es/](https://rpc.xrpl.cumulo.org.es/)                            |
        | **Imperator**             | [https://rpc-xrp.imperator.co/](https://rpc-xrp.imperator.co/)                                |
        | **Enigma**                | [https://xrp-rpc.enigma-validator.com/](https://xrp-rpc.enigma-validator.com/)                |
        | **Stakeme**               | [https://xrpl-rpc.stakeme.pro/](https://xrpl-rpc.stakeme.pro/)                                |

        {% /tab %}
        {% tab label="Cosmos gRPC" %}
        | Provider/Validator        | gRPC Endpoint URL                                                                             |
        | ------------------------- | ----------------------------------------------------------------------------------------------|
        | **Peersyst**              | [https://cosmos-grpc.xrplevm.org](https://cosmos-grpc.xrplevm.org)                            |
        | **Polkachu**              | [https://xrp-grpc.polkachu.com:30090/](https://xrp-grpc.polkachu.com:30090/)                  |
        | **Cumulo**                | [http://grpc.xrpl.cumulo.org.es](http://grpc.xrpl.cumulo.org.es)                              |
        | **Imperator**             | [http://grpc-xrp.imperator.co:443](http://grpc-xrp.imperator.co:443)                          |

        {% /tab %}
        {% tab label="Cosmos API" %}
        | Provider/Validator        | API Endpoint URL                                                                 |
        | ------------------------- | -------------------------------------------------------------------------------- |
        | **Peersyst**              | [https://cosmos-api.xrplevm.org](https://cosmos-api.xrplevm.org)                 |
        | **Polkachu**              | [https://xrp-api.polkachu.com/](https://xrp-api.polkachu.com/)                   |
        | **Cumulo**                | [https://api.xrpl.cumulo.org.es/](https://api.xrpl.cumulo.org.es/)               |
        | **Imperator**             | [https://lcd-xrp.imperator.co/](https://lcd-xrp.imperator.co/)                   |
        | **Enigma**                | [https://xrp-lcd.enigma-validator.com/](https://xrp-lcd.enigma-validator.com/)   |
        | **Stakeme**               | [https://xrpl-rest.stakeme.pro/](https://xrpl-rest.stakeme.pro/)                 |

        {% /tab %}
    {% /tabs %}

{% /tab %}

{% tab label="Testnet" %}

    {% tabs %}

        {% tab label="Ethereum JSON RPC" %}
        | Provider/Validator              | RPC Endpoint URL                                                                              |
        | ------------------------------- | --------------------------------------------------------------------------------------------- |
        | **Peersyst**                    | [https://rpc.testnet.xrplevm.org](https://rpc.testnet.xrplevm.org)                            |
        | **Grove**                       | [https://xrplevm-testnet.buildintheshade.com](https://xrplevm-testnet.buildintheshade.com)    |
        | **Cumulo**                      | [https://json-rpc.xrpl.cumulo.com.es](https://json-rpc.xrpl.cumulo.com.es)                    |
        | **ITRocket**                    | [https://xrplevm-testnet-evm.itrocket.net](https://xrplevm-testnet-evm.itrocket.net)          |
        | **Mekong Labs**                 | [https://exrpd-testnet-json-rpc.mekonglabs.tech](https://exrpd-testnet-json-rpc.mekonglabs.tech)|
        | **MictoNode**                   | [https://xrpl-testnet-evmrpc.mictonode.com](https://xrpl-testnet-evmrpc.mictonode.com)        |
        | **lesnik UTSA**                 | [https://t-xrpl.evm.utsa.tech](https://t-xrpl.evm.utsa.tech)                                  |
        | **STAVR**                       | [https://xrpl.evm.t.stavr.tech](https://xrpl.evm.t.stavr.tech)                                |
        | **Cosmonaut Stakes**            | [https://xrpl-testnet-evm.cosmonautstakes.com](https://xrpl-testnet-evm.cosmonautstakes.com)  |
        | **Brightlystake**               | [https://xrpl-t-evm.brightlystake.com/evm](https://xrpl-t-evm.brightlystake.com/evm)          |
        | **kgnodes Services**            | [https://xrpl-testnet-jsonrpc.kgnodes.xyz](https://xrpl-testnet-jsonrpc.kgnodes.xyz)          |
        | **Đông QN**                     | [https://evm.testnet.xrplevm.dongqn.com](https://evm.testnet.xrplevm.dongqn.com)              |
        | **Endorphine Stake**            | [https://xrpl-evm.endorphinestake.com](https://xrpl-evm.endorphinestake.com)                  |
        | **High Tower**                  | [https://rpc-evm.xrpl-t.htw.tech](https://rpc-evm.xrpl-t.htw.tech)                            |
        | **Inter Blockchain Services**   | [https://xrpl-evm-testnet-evm-rpc.ibs.team/](https://xrpl-evm-testnet-evm-rpc.ibs.team/)      |


        {% /tab %}

        {% tab label="Ethereum JSON WS" %}
        | Provider/Validator  | WSS Endpoint URL                                                                                 |
        | ------------------- | ------------------------------------------------------------------------------------------------ |
        | **Peersyst**        | [https://ws.testnet.xrplevm.org]( https://ws.testnet.xrplevm.org)                               |
        | **Grove**           | [wss://xrplevm-testnet.buildintheshade.com](wss://xrplevm-testnet.buildintheshade.com)           |
        | **MictoNode**       | [wss://xrpl-testnet-evmrpc-wss.mictonode.com](wss://xrpl-testnet-evmrpc-wss.mictonode.com) |
        | **Cumulo**          | [https://ws.xrpl.cumulo.com.es](https://ws.xrpl.cumulo.com.es)                                 |
        {% /tab %}

        {% tab label="Tendermint RPC" %}
        | Provider/Validator   | EVM RPC Endpoint URL                                                                                       |
        | ------------------------- | -----------------------------------------------------------------------------------------------------------|
        | **Peersyst**              | [http://cosmos.testnet.xrplevm.org:26657](http://cosmos.testnet.xrplevm.org:26657)                         |
        | **Polkachu**              | [https://xrp-testnet-rpc.polkachu.com/](https://xrp-testnet-rpc.polkachu.com/)                |
        | **Cumulo**                | [https://rpc.xrpl.cumulo.com.es](https://rpc.xrpl.cumulo.com.es)                              |
        | **Enigma**                | [https://xrp-rpc.enigma-validator.com/](https://xrp-rpc.enigma-validator.com/)                |
        | **ITRocket**              | [https://xrplevm-testnet-rpc.itrocket.net](https://xrplevm-testnet-rpc.itrocket.net)          |
        | **LuckyStar**             | [http://xrpl-testnet-rpc.luckystar.asia/](http://xrpl-testnet-rpc.luckystar.asia/)            |
        | **Mekong Labs**           | [https://exrpd-testnet-rpc.mekonglabs.tech/](https://exrpd-testnet-rpc.mekonglabs.tech/)      |
        | **MictoNode**             | [https://xrpl-testnet-rpc.mictonode.com](https://xrpl-testnet-rpc.mictonode.com)              |
        | **NodeStake**             | [https://rpc-t.xrp.nodestake.org](https://rpc-t.xrp.nodestake.org)                            |
        | **Cosmonaut Stakes**      | [https://xrpl-testnet-rpc.cosmonautstakes.com](https://xrpl-testnet-rpc.cosmonautstakes.com)  |
        | **lesnik UTSA**           | [https://t-xrpl.rpc.utsa.tech/](https://t-xrpl.rpc.utsa.tech/)                                |
        | **Đông QN**               | [https://rpc.testnet.xrplevm.dongqn.com/](https://rpc.testnet.xrplevm.dongqn.com/)            |
        | **STAVR**                 | [https://xrpl.rpc.t.stavr.tech/](https://xrpl.rpc.t.stavr.tech/)                              |
        | **Cosmonaut Stakes**      | [https://xrpl-testnet-rpc.cosmonautstakes.com/](https://xrpl-testnet-rpc.cosmonautstakes.com/)|
        | **BonyNode**              | [https://xrpl-testnet-rpc.bonynode.online/](https://xrpl-testnet-rpc.bonynode.online/)        |
        | **Brightlystake**         | [https://xrpl-t-evm.brightlystake.com/](https://xrpl-t-evm.brightlystake.com/)                |
        | **NodeStake**             | [https://rpc-t.archive.xrp.nodestake.org/](https://rpc-t.archive.xrp.nodestake.org/)          |
        | **OwlStake**              | [https://xrplevm_1449000-1-rpc.owlstake.com/](https://xrplevm_1449000-1-rpc.owlstake.com/)    |
        | **Endorphine Stake**      | [https://xrpl-rpc.endorphinestake.com/](https://xrpl-rpc.endorphinestake.com/)                |
        | **Validator247.com**      | [https://xrplevm-testnet-rpc.validator247.com/](https://xrplevm-testnet-rpc.validator247.com/)|
        | **High Tower**            | [https://rpc.xrpl-t.htw.tech/](https://rpc.xrpl-t.htw.tech/)                                  |
        | **Nodes Hub**             | [https://xrpl.test.rpc.nodeshub.online/](https://xrpl.test.rpc.nodeshub.online/)              |
        | **Inter Blockchain Services** | [https://xrpl-evm-testnet-rpc.ibs.team/](https://xrpl-evm-testnet-rpc.ibs.team/)          |
        | **Unity Nodes**           | [https://rpc.unitynodes.app/xrplevm-testnet/](https://rpc.unitynodes.app/xrplevm-testnet/)    |

        {% /tab %}

        {% tab label="Cosmos gRPC" %}
        | Provider/Validator        | gRPC Endpoint URL                                                                          |
        | ------------------------- | ----------------------------------------------------------------------------------------   |
        | **Peersyst**              | [http://cosmos.testnet.xrplevm.org:9090](http://cosmos.testnet.xrplevm.org:9090)           |
        | **Kintsugi Nodes**        | `grpc-xrp.kintsugi-nodes.com`                                                              |
        | **Polkachu**              | [https://polkachu.com/testnet_public_grpc](https://polkachu.com/testnet_public_grpc)       |
        | **Cumulo**                | `grpc.xrpl.cumulo.com.es`                                                                  |
        | **ITRocket**              | `xrplevm-testnet-grpc.itrocket.net:443`                                                    |
        | **LuckyStar**             | [https://xrpl-testnet-grpc.luckystar.asia/](https://xrpl-testnet-grpc.luckystar.asia/)     |
        | **Mekong Labs**           | `exrpd-testnet-grpc.mekonglabs.tech:47090`                                                 |
        | **MictoNode**             | `xrpl-testnet-grpc.mictonode.com:22090`                                                    |
        | **NodeStake**             | [https://grpc-t.xrp.nodestake.org:443](https://grpc-t.xrp.nodestake.org:443)               |
        | **UTSA (lesnik)**         | `t-xrpl.grpc.utsa.tech:433`                                                                |
        | **blockitize**            | [http://xrplevm-testnet-grpc.blockitize.com/](http://xrplevm-testnet-grpc.blockitize.com/) |
        | **p10node**               | `grpc.testnet.xrplevm.p10node.com`<br>`grpc-web.testnet.xrplevm.p10node.com`               |
        | **Đông QN**               | `grpc.testnet.xrplevm.dongqn.com`                                                          |
        {% /tab %}

        {% tab label="Cosmos API" %}
        | Provider/Validator        | API Endpoint URL                                                                 |
        | ------------------------- | ------------------------------------------------------------------------------- |
        | **Peersyst**              | [http://cosmos.testnet.xrplevm.org:1317](http://cosmos.testnet.xrplevm.org:1317)   |
        | **Kintsugi Nodes**        | [https://api-xrp.kintsugi-nodes.com](https://api-xrp.kintsugi-nodes.com)         |
        | **Polkachu**              | [https://xrp-testnet-api.polkachu.com/](https://xrp-testnet-api.polkachu.com/)   |
        | **Cumulo**                | [https://api.xrpl.cumulo.com.es](https://api.xrpl.cumulo.com.es)                |
        | **ITRocket**              | [https://xrplevm-testnet-api.itrocket.net](https://xrplevm-testnet-api.itrocket.net) |
        | **LuckyStar**             | [https://xrpl-testnet-api.luckystar.asia/](https://xrpl-testnet-api.luckystar.asia/) |
        | **Mekong Labs**           | [https://exrpd-testnet-api.mekonglabs.tech/](https://exrpd-testnet-api.mekonglabs.tech/) |
        | **MictoNode**             | [https://xrpl-testnet-api.mictonode.com](https://xrpl-testnet-api.mictonode.com)   |
        | **NodeStake**             | [https://api-t.xrp.nodestake.org](https://api-t.xrp.nodestake.org)               |
        | **UTSA (lesnik)**         | [https://t-xrpl.api.utsa.tech](https://t-xrpl.api.utsa.tech)                     |
        | **Đông QN**               | [https://api.testnet.xrplevm.dongqn.com](https://api.testnet.xrplevm.dongqn.com)   |
        | **STAVR**                 | [https://xrpl.api.t.stavr.tech](https://xrpl.api.t.stavr.tech)   |
        | **Cosmonaut Stakes**      | [https://xrpl-testnet-rest.cosmonautstakes.com](https://xrpl-testnet-rest.cosmonautstakes.com)   |
        | **BonyNode**               | [https://xrpl-testnet-api.bonynode.online/](https://xrpl-testnet-api.bonynode.online/)   |
        | **Brightlystake**               | [https://xrpl-t-evm.brightlystake.com/api](https://xrpl-testnet-api.bonynode.online/)   |
        | **kgnodes Services**               | [https://xrpl-testnet-api.kgnodes.xyz](https://xrpl-testnet-api.kgnodes.xyz)   |
        | **BonyNode**               | [https://xrpl-testnet-api.bonynode.online/](https://xrpl-testnet-api.bonynode.online/)   |
        | **BonyNode**               | [https://xrpl-testnet-api.bonynode.online/](https://xrpl-testnet-api.bonynode.online/)   |
        | **BonyNode**               | [https://xrpl-testnet-api.bonynode.online/](https://xrpl-testnet-api.bonynode.online/)   |
        {% /tab %}

        {% tab label="Snapshot / Genesis" %}
        | Provider/Validator        | Snapshot / Genesis URL                                                                                         |
        | ------------------------- | ---------------------------------------------------------------------------------------------------------------- |
        | **Peersyst**              | [Snapshot](https://evm-sidechain-snapshots-testnet.s3.us-east-1.amazonaws.com/exrpd.tar.lz4)                      |
        | **Kintsugi Nodes**        | [http://kintsugi-nodes.com/ripple/snapshot](http://kintsugi-nodes.com/ripple/snapshot)                          |
        | **Polkachu**              | [https://polkachu.com/testnets/xrp/snapshots](https://polkachu.com/testnets/xrp/snapshots)                       |
        | **blockitize**            | [Genesis](https://raw.githubusercontent.com/xrplevm/networks/refs/heads/main/testnet/genesis.json) |
        | **Cumulo**                | [https://cumulo.pro/services/xrplevm/](https://cumulo.pro/services/xrplevm/)                                    |
        | **DeFatRat (TechHubs)**   | [https://xrpl-testnet-snapshots.techhubs.asia/](https://xrpl-testnet-snapshots.techhubs.asia/)                  |
        | **Enigma**                | [Snapshot](https://services.enigma-validator.com/xrp/xrp_365040.tar.lz4) [Genesis](https://xrp-rpc.enigma-validator.com/genesis?)                                      |
        | **ITRocket**              | [https://itrocket.net/services/testnet/xrplevm/](https://itrocket.net/services/testnet/xrplevm/)                |
        | **LuckyStar**             | [Snapshot](https://luckystar-1.gitbook.io/luckystar.asia/testnet/cosmos-eco/xrpl/snapshot)<br>[Genesis](https://xrpl-testnet-services.luckystar.asia/xrpl/genesis.json) |
        | **Mekong Labs**           | [http://exrpd-testnet-snapshots.mekonglabs.tech/](http://exrpd-testnet-snapshots.mekonglabs.tech/)              |
        | **MictoNode**             | [https://services.mictonode.com/xrpl-evm/snapshot](https://services.mictonode.com/xrpl-evm/snapshot)            |
        | **UTSA (lesnik)**         | [https://utsa.gitbook.io/services/testnet/xrpl-evm/snapshots](https://utsa.gitbook.io/services/testnet/xrpl-evm/snapshots) |
        | **Node9x**                | [https://service.node9x.com/testnet/xrpl-evm/service-and-snapshot](https://service.node9x.com/testnet/xrpl-evm/service-and-snapshot) |
        | **NodeStake**             | [https://nodestake.org/xrp](https://nodestake.org/xrp) |
        {% /tab %}

        {% tab label="Documentation / Guide" %}
        | Provider/Validator        | Docs / Guide URL                                                                 |
        | ------------------------- | ------------------------------------------------------------------------------- |
        | **Grove**                 | [XRPL-EVM Documentation](https://buildintheshade.com/docs)                       |
        | **Polkachu**              | [Installation Guide](https://polkachu.com/testnets/xrp/installation)              |
        | **Cumulo**                | [Node Guide](https://cumulo.pro/services/xrplevm/)                              |
        | **Enigma**                | [Main site](https://enigma-validator.com/stake-with-us/xrp-testnet#services) |
        | **ITRocket**              | [ITRocket XRPL Docs](https://itrocket.net/services/testnet/xrplevm/installation/#installation)            |
        | **LuckyStar**             | [Node Guide](https://luckystar-1.gitbook.io/luckystar.asia/testnet/cosmos-eco/xrpl/node-setup)   |
        | **Mekong Labs**           | [Node Guide](https://github.com/Mekong-labs/NodeGuide/tree/main/XRPL)            |
        | **MictoNode**             | [Basic Guide](https://services.mictonode.com/xrpl-evm/installation)                           |
        | **Trace**                 | [Russian docs](https://trace-team.gitbook.io/xrpl)            |
        | **UTSA (lesnik)**         | [Node Installation](https://utsa.gitbook.io/services/testnet/xrpl-evm/installation)            |
        | **XSS**                   | [Installation](https://services.xsslabs.tech/xrpl-evm/installation)               |
        | **blockitize**            | [Node documentation](https://services.blockitize.com/?project=xrpl-evm) |
        | **node9x**                | [https://service.node9x.com/testnet/xrpl-evm](https://service.node9x.com/testnet/xrpl-evm) |
        | **Imperator.co**          | [https://www.imperator.co/services/chain-services/testnets/xrp](https://www.imperator.co/services/chain-services/testnets/xrp) |
        | **NodeStake**             | [https://nodestake.org/xrp](https://nodestake.org/xrp)                           |
        {% /tab %}

        {% tab label="Other / Monitoring & Tools" %}
        | Provider/Validator        | Additional Info / Tools                                                                                                                           |
        | ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
        | **Cumulo**                | [RPC & API Scan](https://cumulo.pro/services/xrplevm/)                                                                        |
        | **ITRocket**              | [Validator Analytics](https://itrocket.net/services/testnet/xrplevm/analytics/validators-performance), [Consensus Analytics](https://itrocket.net/services/testnet/xrplevm/analytics/consensus/), [Peer scanner](https://itrocket.net/services/testnet/xrplevm/public-rpc/), [Decentralization Analytics](https://itrocket.net/services/testnet/xrplevm/decentralization/) |
        | **node9x**                | [exrpd commands](https://service.node9x.com/testnet/xrpl-evm/command)                                                                                           |
        | **NodesHub**              | [Useful commands](https://services.nodeshub.online/testnet/xrpl/useful-commands)                                                                                        |
        {% /tab %}
    {% /tabs %}

    ---
{% /tab %}
{% /tabs %}
