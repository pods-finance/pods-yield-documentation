---
description: Understand the system actors
---

# System Actors

There are six main actors in stETHvv design:&#x20;

* Depositors
* Yield Source
* Investor
* Vault Controller
* Round Processor
* Vault

Each actor has an essential role in stETHvv's functionality, which we will cover in this section.&#x20;

### Depositors&#x20;

The depositors are all the users who **deposit** `stETH` (and soon `ETH`) into `stETHvv`. They can be either an EOA (Externed Owned Account) or a contract. This actor will later be able to withdraw their funds alongside their earnings.&#x20;

### Yield Source

The Yield Source is the source of the base yield for this strategy. In the case of stETHvv, the yield source is [Lido Finance](https://lido.fi/).&#x20;

### Investor&#x20;

The Investor EOA (or Multisig) is responsible for buying the put and call options and setting the strangle strategy weekly. The Investor wallet receives part of the weekly yield from the Yield Source, which we call the Investor Ratio (currently set at 50%), and buys the options manually. In case the options bought end _in-the-money_, the profit from the exercised options stays in this wallet and later is sent back to the vault so that they are redeposited into the Yield Source, respecting users' shares proportionately.&#x20;

{% hint style="danger" %}
NOTE: Currently this part of the process is centralized and could even be held off-chain. We intend to automate the option purchases as we see more liquid options available. As of now holding the options purchases on chain would represent a much worse execution, impacting the strategy's profitability significantly.&#x20;
{% endhint %}

{% hint style="success" %}
Admin keys only have access to the 50% of the weekly yield, usually, this represents less than 1% of the TVL.&#x20;
{% endhint %}

### Vault Controller&#x20;

The VaultController is a Multisig responsible for calling the `startRound` and `endRound` functions round. He can also act as a `Depositor` and as a `RoundProcessor`.&#x20;

### Vault&#x20;

A vault is a smart contract that connects all the players to make the strategy work. The vault:

* Receives funds from depositors.
* Calculates the generated interest in the week.
* Create shares for the depositors.
* Receives the profit from exercised options.
* Send part of the yield to the investor's address.

### Round Processor&#x20;

The role of this actor is to process the queued deposits after the `endRound` the function was called and before the `startRound` was called, meaning, only when the flag `isProcessingDeposits` true.&#x20;

In our internal process, the actor `VaultController` will also be responsible for processing the deposits of the week to create a smoother user experience. It is important to highlight that any address could process its own or other deposits, which means that this step does not rely on the Vault Controller itself.&#x20;
