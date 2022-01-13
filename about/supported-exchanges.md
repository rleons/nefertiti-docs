# Supported Exchanges

| Exchange     | Code | [Default](../strategies/built-in-strategies.md#default-strategy) | [Stop-Loss](../strategies/built-in-strategies.md#stop-loss-strategy) |   |
| ------------ | ---- | :--------------------------------------------------------------: | :------------------------------------------------------------------: | - |
| Binance      | BINA |                       :white\_check\_mark:                       |                         :white\_check\_mark:                         |   |
| Binance.US   | BIUS |                       :white\_check\_mark:                       |                         :white\_check\_mark:                         |   |
| Bitstamp     | BITS |                       :white\_check\_mark:                       |                                  :x:                                 |   |
| Bittrex      | BTRX |                       :white\_check\_mark:                       |                         :white\_check\_mark:                         |   |
| CEX.IO       | CXIO |                       :white\_check\_mark:                       |                                  :x:                                 |   |
| Coinbase Pro | GDAX |                       :white\_check\_mark:                       |                                  :x:                                 |   |
| Crypto.com   | CRO  |                       :white\_check\_mark:                       |                                  :x:                                 |   |
| HitBTC       | HITB |                       :white\_check\_mark:                       |                                  :x:                                 |   |
| KuCoin       | KUCN |                       :white\_check\_mark:                       |                      :ballot\_box\_with\_check:                      |   |
| Wootrade     | WOO  |                       :white\_check\_mark:                       |                                  :x:                                 |   |

{% hint style="info" %}
:ballot\_box\_with\_check:Partially Supported

Stop-Loss strategy works best with exchanges that support OCO (one-cancells-the-other) orders. However, do to high community demand, we have partial support on KuCoin with some minor limitations.\
\
Since we cannot place the limit TP (take-profit) and SL (stop-loss) orders together, once Nefertiti detects a filled [buy](../quick-start/commands.md#buy) order, the [sell](../quick-start/commands.md#sell) instance will;

1. Place a stop-loss limit order BELOW your entry.
2. Monitor ticker price until take-profit level is reached, once this price level is reached, Nefertiti will cancel the stop-loss order and place a market sell. IF this stop-loss price level is reached, Nefertiti will exit your position at a loss and nothing else will happen. **\[\*]**

**\[\*]** IF you combine the `--stoploss` strategy with `--dca` on the sell instance, another buy order will be placed. (see `--dca` option on the [sell](../quick-start/commands.md#sell) command for deails).
{% endhint %}
