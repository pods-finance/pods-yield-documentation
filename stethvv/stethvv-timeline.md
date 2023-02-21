# stETHvv Timeline

### Timeline

* End Round: Friday 15:00 UTC
* Start Round: Friday 15:30 UTC
* Deposits Processing Window: between the end of the current round and the start of the following round&#x20;
* Options Buying: Friday after the End Round

### Observations&#x20;

1. Deposits can **only** happen between the `startRound` and the `endRound`.
2. Withdrawals can **only** happen between the `startRound` and the `endRound`.
3. All funds deposited between `startRound` and `endRound` are processed **together** at the same time.&#x20;

Considering how the current system is designed, we advise our users to deposit funds into the vault _**closer to the start of the next round**_.&#x20;

This happens because:

* Any yield generated in the vault by the yield strategy (in this case, Lido) before the deposit has been processed will NOT be considered.&#x20;

{% hint style="info" %}
<mark style="color:blue;">This means that the best moment to deposit is on Thursday night, ET time. And the best moment to withdraw is after the current week's round is finished, Friday night, ET time.</mark>&#x20;
{% endhint %}
