# Commands

## What are the bot’s most important commands?

While the bot supports many commands, the two most important ones are [`buy`](commands.md#buy) and [`sell`](commands.md#sell). These commands are designed to be running in tandem. You will need to start one instance of [`sell`](commands.md#sell) per exchange, regardless of how many [`buy`](commands.md#buy) instances you are running, for example:

```
cryptotrader sell --exchange=GDAX
```

The [`sell`](commands.md#sell) command listens for buy orders to get filled, and then automatically opens new limit sell orders for them, for this reason, the [`sell`](commands.md#sell) instance should always be started first. In essence, this command will auto-sell your trades. By default, the bot will try and sell them at a 5% profit.

You will then need to start a [`buy`](commands.md#buy) instance for each strategy you want the bot to be trading in, for example:

```
cryptotrader buy --exchange=GDAX --market=BTC-EUR,ETH-EUR
```

## about

About Nefertiti (cryptotrader)

```
cryptotrader about
```

## agg

Calculates the aggregation level for a given market pair.

```
cryptotrader agg [options]
```

| Option     | Required | Description                                                                                                                                                                                                    |
| ---------- | :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| --exchange |    Yes   | <p>[ name | code ]</p><p>For a list of exchanges run <code>cryptotrader exchanges</code></p><p>Example: <code>--exchange=Binance</code></p>                                                                    |
| --market   |    Yes   | <p>A valid market pair.</p><p>Example: <code>--market=BTC-EUR</code></p>                                                                                                                                       |
| --dip      | Optional | <p>Percentage drop that will kick the bot into action, defaults to five (-5%).</p><p>Example: <code>--dip=7</code> for seven percent drop (-7%).</p>                                                           |
| --pip      | Optional | <p>Range in where the market is suspected to move up or down,<br>the bot will ignore support levels outside of this range. Defaults to 30%.</p><p>Example: <code>--pip=20</code> for 20% up and downrange.</p> |
| --max      | Optional | The maximum price that you will want to pay for the coin/token.                                                                                                                                                |
| --min      | Optional | The minimum price that you will want to pay for the coin/token.                                                                                                                                                |

## base

\[placeholder]

## book

\[placeholder]

## buy \*

Opens new limit buy orders on the specified exchange/markets.

```
cryptotrader buy [options]
```

| Option     | Required | Description                                                                                                                                                                                                    |
| ---------- | :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| --exchange |    Yes   | <p>[ name | code ]</p><p>For a list of exchanges run <code>cryptotrader exchanges</code></p><p>Example: <code>--exchange=Binance</code></p>                                                                    |
| --market   |    Yes   | <p>Comma-separated string of the market(s) you want to trade.</p><p>Example: <code>--market=BTC-EUR,ETH-EUR</code></p>                                                                                         |
| --price    |    Yes   | <p>The amount of quote currency you will want to spend for each order.</p><p>Example: <code>--price=25</code></p>                                                                                              |
| --size     | Optional | The amount of base coin/token to buy per order. **\[1]**                                                                                                                                                       |
| --agg      | Optional | Aggregate public order book to the nearest multiple of `--agg`.                                                                                                                                                |
| --dip      | Optional | <p>Percentage drop that will kick the bot into action, defaults to five (-5%).</p><p>Example: <code>--dip=7</code> for seven percent drop (-7%).</p>                                                           |
| --pip      | Optional | <p>Range in where the market is suspected to move up or down,<br>the bot will ignore support levels outside of this range, defaults to 30%.</p><p>Example: <code>--pip=20</code> for 20% up and downrange.</p> |
| --dist     | Optional | <p>Distance between your orders, defaults to two percent (2%).</p><p>Example: <code>--dist=5</code> will force a 5% distance between orders.</p>                                                               |
| --top      | Optional | Number of orders to place in your book.                                                                                                                                                                        |
| --max      | Optional | The maximum price that you will want to pay for the coin/token.                                                                                                                                                |
| --min      | Optional | The minimum price that you will want to pay for the coin/token.                                                                                                                                                |
| --dca      | Optional | <p>The bot will slowly but surely increase your stack while<br>lowering your average buying price. <strong>[2]</strong></p>                                                                                    |
| --test     | Optional | Merely reports what it would do without actually placing orders.                                                                                                                                               |
| --repeat   | Optional | <p>Repeats the buy bot every X hours.</p><p>Example: <code>--repeat=1</code> will repeat the whole process and look<br>for new support levels every hour.</p>                                                  |

{% hint style="info" %}
**\[1]** Please note that `--size` and `--price` are mutually exclusive, meaning you can only use one or the other.

**\[2]** {{{{{In-deph `--dca` explanation}}}}}
{% endhint %}

## cancel

\[placeholder]

## exchanges

\[placeholder]

## listen

\[placeholder]

## markets

\[placeholder]

## notify

\[placeholder]

## order

\[placeholder]

## quote

\[placeholder]

## sell \*

The sell command listens for buy orders getting filled and then opens new sell orders for them.

```
cryptotrader sell [options]
```

| Option     | Required | Description                                                                                                                                                     |
| ---------- | :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| --exchange |    Yes   | <p>[ name | code ]</p><p>For a list of exchanges run <code>cryptotrader exchanges</code></p><p>Example: <code>--exchange=Binance</code></p>                     |
| --mult     | Optional | <p>Sell order multiplier.</p><p>Defaults to <code>1.05</code>, which means five percent (5%)</p><p>Example: <code>--mult=1.03</code> for three percent (3%)</p> |
| --hold     | Optional | <p>Comma-separated string of markets you do NOT want to sell. <strong>[1]</strong></p><p>Example: <code>--hold=BTC-EUR,ETH-EUR</code></p>                       |
| --stoploss | Optional | <p>[ Y ] Enables <a href="../strategies/built-in-strategies.md#stop-loss-strategy">Stop-Loss trading strategy</a></p><p>Example: <code>--stoploss=Y</code></p>  |
| --stop     | Optional | <p>Stop-Loss multiplier, requires <code>--stoploss=Y</code>, defaults to <code>0.90</code></p><p>Example: <code>--stop=0.95</code> <strong>[2]</strong></p>     |
| --dca      | Optional | **\[NEEDS DESCRIPTION]**                                                                                                                                        |
| --notify   | Optional | <p>[ 0 | 1 | 2 | 3 ] Notifications verbosity. <strong>[3]</strong></p><p>Example: <code>--notify=1</code></p>                                                   |
| --sandbox  | Optional | **\[NEEDS DESCRIPTION]**                                                                                                                                        |

{% hint style="info" %}
**\[1]** Note that the bot will always sell a minimum quantity of your coins, even if you instruct the bot to hodl them. This comes with the trading strategy and is not a bug.

**\[2]** On the `--stop=0.95` example, this would place your stop-loss order at (entry-price \* 0.95), in other words, five percent (5%) below your entry.

**\[3]**\
****0 = no notifications\
1 = errors only\
2 = errors + filled orders (default)\
3 = everything (including opened and cancelled orders)
{% endhint %}

## stoploss

\[placeholder]

## update

```
cryptotrader update
```
