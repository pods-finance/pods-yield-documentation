---
description: 🙋🏽‍♂️No-dumb-questions page.
---

# FAQ

## What are options? <a href="#eef2" id="eef2"></a>

An option is an agreement between two parties: a seller and a buyer. The seller writes the contract terms and sells them to the buyer for a premium. That means the seller now has an obligation, and the buyer has a right (but not an obligation) to exercise the contract terms upon expiration.

## **What types of options are there?** <a href="#ec54" id="ec54"></a>

There are two basic types of options: puts and calls. A put represents the right to **sell** the underlying asset at the strike price. On the other hand, a call conveys the right to **buy** an asset at the strike price.

## What is a strangle? <a href="#e318" id="e318"></a>

A strangle is an options strategy in which the investor holds a position in both a [call](https://www.investopedia.com/terms/c/call.asp) and a [put](https://www.investopedia.com/terms/p/put.asp) option with different [strike prices](https://www.investopedia.com/terms/s/strikeprice.asp), but with the same expiration date and underlying asset. A strangle is a good strategy if you think the underlying security will experience a large price movement in the near future but are unsure of the direction. However, it is profitable mainly if the asset does swing sharply in price.

## What is the strike price? <a href="#2f53" id="2f53"></a>

The strike price is commonly used to designate the price at which the underlying asset will be sold or bought in the future.

## What is Lido?

Lido is a decentralized staking protocol that allows users to stake their ETH and receive ETH 2 rewards.

## What is stETH?

stETH is the token that represents the staked [ETH in Lido](https://help.lido.fi/en/articles/5230610-what-is-steth).&#x20;

## What is the potential PnL ?

$$
Payoff = (Principal Invested+0.8*Profit fromExercise + ...
$$

$$
...+0.5*LidoYield) * 0.999
$$

## What is the token stETHvv I receive in the wallet once deposited into the vault?

The stETHvv token represents your shares of the total vault.&#x20;

## Does the stETHvv token have a price?

Yes. right now the easiest way to calculate its price is by doing the math: TVL / Total Supply

NOTE: We will add a reading function directly in the contract to make that step easier.

## Is the stETHvv token an [ERC-20](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/)?

Yes.&#x20;

## What are the fees?

0.1% management fee at withdrawal and 20% performance fee on exercised options

## Does the vault follow the [ERC 4626 standard](https://ethereum.org/en/developers/docs/standards/tokens/erc-4626/)?

Yes.&#x20;

## Is there a withdrawal window?

**No**. You can withdraw anytime.\
\
Although, It depends on whether or not your deposits have been processed. you can check if the deposit was processed by clicking on the "show breakdown" inside the vault page.

<figure><img src="../.gitbook/assets/Screen Shot 2023-05-24 at 10.33.21 AM.png" alt=""><figcaption><p>Breakdown Position visualization</p></figcaption></figure>

* if your deposit has not been processed yet you can withdraw your deposit from the queue using Etherscan directly using the `refund`  function on each vault address.

<figure><img src="../.gitbook/assets/Screen Shot 2023-05-24 at 10.35.46 AM.png" alt=""><figcaption><p>Refund function on Contract/Write in Etherscan</p></figcaption></figure>

* if your deposit has been processed you can withdraw at any time from the app's front end.

## Have more questions?&#x20;

Reach out to us on our channels:

* [Twitter](https://twitter.com/PodsFinance)
* [Discord](https://discord.com/invite/Qf7utym)



