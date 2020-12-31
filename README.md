# Modeling Vanilla Interest Rate Swaps

The following is an exploration of vanilla interest rate swap. We will model the value of a swap using the `QuantLib` python module.

A swap is an agreement between two parties to exchange a series of cash flows, which can also be viewed as a series of forward contracts. 

![Interest Rate Swap Example](https://kidquant.com/post/images/Modeling-Interest-Rate-Swaps/Swaps.png)

The example above involves two different financial institutions with two different cashflow payments. Bank A is paying a lending institution a fixed rate of 5% while Bank B is another lending institution LIBOR plus 1.25%. Bank A is interested in paying the floating rate, while Bank B would prefer to pay the fixed rate.

Perhaps Bank A believes interest rates will fall in the future, thus, providing the institution the opportunity to take advantage of small cashflow payments. On the other side of the position, since Bank B wants to pay a fixed rate, perhaps the institution believes interest rates will rise in the future, so it can lock in relatively lower interest payments.

The way the swap works is simple. Bank A, wanting a floating rate, pays a swap dealer LIBOR plus 1.1% and then receives the fixed rate of 4.6% from the same dealer. At the same time, Bank B pays the dealer a fixed rate of 4.7% and receives LIBOR plus 1%. The net payment for Bank A is the difference between what it pays to its lender and what it receives from the dealer, plus what it pays to the dealer ((5% - 4.6%) + (L+ 1.1%)). The net payment for Bank B is the difference between the floating rate it pays and the floating rate it receives, plus the fixed rate it pays ((L+1.25%)-(L+1%)+4.7%)). The dealer makes money from what it provides from the fixed and floating rate.

This example involves an intermediary, although two parties can facilitate a contract without one. Whether or not there is an intermediary is irrelevant for the purposes of our model.

The swap's price is determined by the initial terms of the swap at the inception of the swap contract. However, the value of a swap is determined by the market value during the swap contract's life.

Swaps are equivalent to a series of forward contracts, with each created at the spot price. If the present value of the payments in a swap or forward contract is not zero, then the party who will receive the greater stream of payments has to pay the other party the present value of the difference, or in other words, the net value.
