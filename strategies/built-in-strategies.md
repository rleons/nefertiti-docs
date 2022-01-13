# Built-in Strategies

## How does the bot determine where the dip is?

First of all, the ticker price needs to drop at least 5% over a 24-hour period for the bot to kick into action.

The bot will then look at the public order book, aggregate all the orders in the book so that what literally might be thousands of orders now aggregates to roughly 10-20 orders, and then select the top two(2) orders out of those.

At those two(2) **** support levels, the bot will then open limit buy orders for you for the amount you specify. You don’t specify the price, the bot will calculate those for you. You only tell the bot the quantity/amount you want the bot to buy.

Every hour, the bot will cancel your limit __ buy orders and then repeat the above process.

## Default Strategy

Content here

## Stop-Loss Strategy

Content here
