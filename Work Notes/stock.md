https://www.investopedia.com/trading/getting-to-know-the-greeks/

# Option Greeks

[Delta] - measure of `change in option's price/premium` from `change in underlying asset`.
[Theta] - measure of `price decay` / `∆time`.
[Gamma] - measure of [delta]'s `rate of change over time` and `rate of change in the underlying asset`.
Gamma helps forecast price moves in underlying asset.
[Vega] - measures the `risk of changes in implied volatility` or `forward-looking expected volatility` of the underlying asset price.
[Thet] - measures `time decay in the value of an option or its premium`.

# Options Contracts

[Call option] - allows option holder to buy underlying asset
[Put option] - allows option holder to sell underlying asset

Options can be exercised at any time before expiration date by being converted into underlying asset at a specified price, the [strike price]. Every option has an [expiration date] and a [premium].

[Strike price] - price at which underlying asset can be bought or sold
[Expiration date] - date at which option expires
[Premium] - price of option contract

## volatility

[Volatility] - measure of the `rate and magnitude of change in the price of an asset`. Aka how much an `option's premium, or market value, fluctuates` leading up to its expiration.
Price fluctuations may be caused by `company-specific events`, `changes in the economy`, `or other events that affect the entire market`.
[Implied volatility] - measure of the `expected future volatility` of the underlying asset price. The market's view of what they think will happen to the asset's price change.
[Historical volatility] - measure of the `actual past volatility` of the underlying asset price.

Essentially, [delta] measures the impact of a change in the price of the underlying asset on the option's price. [Gamma] measures the rate of change of [delta] relative to the underlying asset's price. [Vega] measures the impact of a change in the underlying asset's [implied volatility] on the option's price. [Theta] measures the impact of the passage of time on the option's price.

[Delta]: https://www.investopedia.com/terms/d/delta.asp

Delta is the probability that an option will expire in the money.
Gamma is the rate of change of delta.

GEX is the gamma exposure of all options on a given underlying asset. GEX is calculated by multiplying the number of shares represented by each option contract by the option's gamma and summing the result for all options on the underlying asset. GEX is positive when the market is net long gamma and negative when the market is net short gamma.

GEX is a measure of the market's directional risk. When GEX is positive, the market is net long gamma and the market's exposure to directional risk is positive. When GEX is negative, the market is net short gamma and the market's exposure to directional risk is negative. When GEX is zero, the market is delta neutral and the market's exposure to directional risk is zero
[Market directional risk] - risk that the market will move in a particular direction.

[Options and their impact] - Buying options is a bet that the underlying asset will move in a particular direction. Selling options is a bet that the underlying asset will not move in a particular direction. If there are many options betting a certain way, actual stock might trend in that direction.
[Gamma] - measures how much an option's value changes when the stock price moves a little bit. High gamma means value changes a lot when stock price changes a little.
[GEX Calculation] - GEX = (number of shares represented by each option contract) _ (option's gamma) _ (sum for all options on the underlying asset)

Add gamma of all options for a particular stock or entire market. If gamma is positive, market is net long gamma and exposure to directional risk is positive. If gamma is negative, market is net short gamma and exposure to directional risk is negative. If gamma is zero, market is delta neutral and exposure to directional risk is zero.
