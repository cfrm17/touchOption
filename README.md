# Touch Option Valuation

Touch FX options include One-Touch Up, One-Touch Down and Double One Touch with rebate paid at expiry, and No Touch Up, No Touch Down, and Double No Touch.

The valuation model is an ad-hoc one that attempt to price Exotics with volatility smile surface. The idea behind Skew Touch is to build a hedging portfolio made of smile contracts (Call/Put or Risk Reversal /Butterfly) which, under volatility flatness assumption (ATM), matches Black-Scholes Vega and its derivatives with respect to FX spot and volatility, Vanna and Volga, of the target Touch Option. 

The difference between the hedge value when priced with volatility smile and the hedge value when priced with ATM volatility, called over-hedge, is then assumed to reflect the difference between the market Touch option price and the Black-Scholes (ATM) Touch option price (also called Theoretical Value). The over-hedge is typically adjusted by scaling it with the probability of FX spot not touching the barrier level (equivalently, probability of needing the hedge).

Let t S be the spot FX rate of a currency pair FOREIGN/DOMESTIC (FOR/DOM, f/d) at time t. In the FOR/DOM notation scheme, when one considers, for example, the EUR/USD-spot Skew Touch Model, say, at 1.26 USD per 1 EUR, the currency USD is used to measure 1 EUR, therefore we say that EUR is the underlying (the asset, the foreign currency) and USD is the numeraire (the domestic currency) used to value the asset 1 EUR. Another example: consider USD/JPY-spot trading, say, at 116 JPY per 1 USD; the currency JPY is used to measure 1 USD, so USD is the underlying (the asset, the foreign currency), and JPY is the numeraire (the domestic currency).

Let T be the time (in years) from current date (valuation date) to expiry date, shortly called time to expiry. Let be the time (in years) from spot date to delivery date, shortly called time to delivery. Let be the domestic interest rate (continuously compounded, ACT/365), the foreign interest rate (same conventions). Note that these rates apply from spot date to delivery date. Let d T d r f r σ be the volatility parameter (we think of it as a specification only in this section). The following continuous geometric Brownian process usually models the spot FX rate (here is the standard Brownian motion):

 

Let be the forward FX rate (forward price of the underlying) for anchor term . FX market quotes the swap points, , for an anchor term, and then Td F d TTd P Td Td F := S + P , were S will denote the known spot FX rate at spot date. By interest rate parity no-arbitrage argument, we must have:

 

This allows us to compute the non-USD interest rate at anchor dates. At non-anchor date, we first compute the USD interest rate (by log-linearly interpolating the anchor USD discount factor curve), then the non-USD interest rate (by log-linearly interpolating the already built anchor non-USD discount factor curve), and then, by applying (2), to obtain the forward rate.

The payoff of a vanilla European call (put) option on the spot FX rate having time to expiry T and strike rate K is

 

where the flag β = 1 for call, and β = −1 for put, and is the notional amount in foreign currency (asset quantity). If a domestic currency notional, is provided, then is set to and the pricing continues as below (or, the Foreign-Domestic Symmetry is enforced, the underlying is reverted and then the pricing continues as below – Delta definition confusions may arise if done this way). The price of this payoff is the present value of its expectation under risk neutral measure (the drift in (1) is made of risk-free interest rates).

We generically denote the price of a Vanilla European by V(K) and the Black-Scholes price by BS(K) (for more readability we dropped the other market data).

We present now the standard family of Single/Double Barrier and Touch (At Expiry)/No-Touch options. The Touch options considered have rebate paid at expiry, that is, they are complementing the No-Touch options. A plethora of relations hold for their payoffs (Knock In/Knock Out, Touch/No Touch, Cash/Asset parities, three and four Barrier replications of Touches). Any pricing model must then induce the same relations at price and Greek levels, otherwise internal arbitrage appears. For Black-Scholes pricing these relations hold easily. But dVega methodology has difficulties (as we will see in the next section).

The following order is assumed: L < H (lower barrier and upper barrier). Spot and all other market data (volatility, interest rates, and expiry) are dropped from notation for clearer presentation. Knowledge of spot, barriers and strike positioning is crucial in Single Barrier classification (especially in regular/reverse taxonomy).

 

An alternative way of classifying Single Barriers is by considering the moneyness of the barrier:

Knock-Out (KO) and Knock-In (KI) Barrier (barrier is out-of-money):

 

Reverse Knock-Out (KO) and Reverse Knock-In (KI) Barrier (barrier is in-the-money):

 

This second market classification is useful and important. The behaviour of RKO/RKI is very different from KO/KI. The owner of a RKO, for example, shows a large intrinsic option value just before the time the barrier is hit. Also, as expiry approaches, reverse barriers start behaving as pure digitals!

References:

https://finpricing.com/lib/EqBarrier.html


