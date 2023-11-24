## 🛠 Connector Info

- **Exchange Type**: Decentralized Exchange (DEX)
- **Market Type**: Automatic Market Maker (AMM)
- **Maintenance Tier**: ![](https://img.shields.io/static/v1?label=Hummingbot&message=BRONZE&color=green)
- **Maintainer:** [ElephantDex](https://elephant.ac)

Currently, Elephant is a **Bronze** exchange, as voted by HBOT holders in each quarterly [Epoch](/governance/epochs). This means Hummingbot Foundation does not maintain the components below, but community members may submit [Proposals](/governance/proposals) to fund development bounties and approve pull requests to fix bugs and add enhancements to them.

| Component | Status | Notes | 
| --------- | ------ | ----- |
| [2️⃣ AMM Connector](#2-amm-connector) | ✅ |
| [3️⃣ Range AMM Connector](#3-range-amm-connector) | Not built |
| [🕯 AMM Data Feed](#amm-data-feed) | ✅ |

## ℹ️ Exchange Info

- **Website**: <https://elephant.ac>
- **Price/Analytics**: <https://elephantinfo.ac>
- **Fees**: 

## 🔑 How to Connect

Create a wallet on one of the supported networks below:

| Chain | Networks | 
| ----- | -------- |
| `Harmony` 

From inside the Hummingbot client, run `gateway connect elephant` in order to connect your wallet:
 
```
Which chain do you want pangolin to connect to? (harmony) >>>
Which network do you want pangolin to connect to? (mainnet) >>>
Enter your harmony-mainnet private key >>>>
```

If connection is successful:

```
The elephant connector now uses wallet [pubKey] on harmony-mainnet
```


## 2️⃣ AMM Connector
*Integration to this DEX's swap pricing and execution endpoints*

- **ID**: `elephant`
- **Connection Type**: REST via [Gateway](/gateway)
- **API Docs**: <https://github.com/elephantproject>
- **Folder**: <https://github.com/hummingbot/gateway/tree/main/src/connectors/elephant>
- **Default Configs**: <https://github.com/hummingbot/gateway/blob/main/src/templates/elephant.yml>

### Endpoints

- `/amm/price`
- `/amm/trade`


For more info, run Gateway and go to <https:localhost:8080> in your browser to see detailed documentation for each endpoint.

## 🕯 AMM Data Feed
*Data feed of this exchange's real-time prices*

- **ID**: `pangolin_[CHAIN]_[NETWORK]`
- **Connection Type**: REST via [Gateway](/gateway)
- **Folder**: <https://github.com/hummingbot/hummingbot/blob/master/hummingbot/data_feed/amm_gateway_data_feed.py>

### Usage

```python
from hummingbot.data_feed.amm_gateway_data_feed import AmmGatewayDataFeed
prices = AmmGatewayDataFeed(
        connector_chain_network="elephant_harmony_mainnet",
        trading_pairs={"WONE-USDT", "WONE-USDC"},
        order_amount_in_base=Decimal("1"),
    )
```

##### Notes

Use the "Add Liquidity" page at: https://elephant.ac/#/add/ to manually approve tokens.

Make sure to approve WONE and wrapped assets as well!*
