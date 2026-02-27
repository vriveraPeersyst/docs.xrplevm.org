# Snapshots

Snapshots provide a quick way to bootstrap your node’s state by downloading a pre-synchronized version of the blockchain data. This reduces the time and resources required to sync from the genesis block. Different networks—mainnet and testnet snapshots for various use cases. Some snapshots are pruned (minimal historical data), others retain default state, and some include full historical archives for comprehensive analysis.

## Snapshots

{% tabs %}

{% tab label="Mainnet" %}
| Provider        | URL                                                                                                                    |
| --------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Peersyst**    | [Download Mainnet](https://evm-sidechain-snapshots-mainnet.s3.us-east-1.amazonaws.com/exrpd.tar.lz4)                   |
| **Polkachu**    | [Download Mainnet](https://polkachu.com/tendermint_snapshots/xrp)                                                      |
| **Cumulo**      | [Download Mainnet](https://cumulo.pro/services/xrplevm_mainnet/snapshot)                                               |
| **ITRocket**    | [Download Mainnet](https://itrocket.net/services/mainnet/xrplevm/)                                                     |
{% /tab %}

{% tab label="Testnet" %}
| Provider        | URL                                                                                                                    |
| --------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Peersyst**    | [Download Testnet](https://evm-sidechain-snapshots-testnet.s3.us-east-1.amazonaws.com/exrpd.tar.lz4)                   |
| **Polkachu**    | [Download Testnet](https://polkachu.com/testnets/xrp/snapshots)                                                        |
| **Cumulo**      | [Download Testnet](https://cumulo.pro/services/xrplevm/)                                                               |
| **ITRocket**    | [Download Testnet](https://itrocket.net/services/testnet/xrplevm/)                                                     |
{% /tab %}
{% /tabs %}

**Note:** Always verify the authenticity and integrity of snapshots before using them. Keep in mind that third-party providers may have different update schedules, data policies, and retention periods. Refer to the provider’s documentation for instructions on how to use these snapshots and any associated terms of service.
