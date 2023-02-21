---
description: Rounds and events.
---

# How stETHvv Works

stETHvv is composed of Rounds, and there are 3 main events/periods that should be highlighted:

* Start Round
* End Round
* Deposits Processing Window

Each period triggers specific functions which we will cover in this section.&#x20;

## Quick Overview

<figure><img src="../../.gitbook/assets/Vaut flow.png" alt=""><figcaption><p>Diagram 1 - stETHvv vault flow</p></figcaption></figure>

This image represents the basic flow of the vault's lifetime.&#x20;

Deposits and Withdrawals happen when the flag `isProcessingDeposits` is set to false. If the address wants to withdraw before waiting for your shares to be processed, it is possible to use the function withdrawFromTheQueue which will remove the address from the queue and return his funds to the owner.

## Start Round

The Start Round moment sets:

* The allowance of new deposits into the vault;
* The processing of deposits is no longer allowed;
* The allowance of withdrawals from the vault;
* It also sets the `lastRoundAssets` that will be used to calculate the total yield generated during the round period;

The moment of the creation of the vault is called the moment _zero_ or round zero, which sets the start of the rounds system.&#x20;

## End Round

The End Round defines the moment where: &#x20;

* Deposits and withdrawals are blocked until the start of the next round;
* Any premium won from exercised options is moved from the Investor Wallet to the Vault;
* The weekly yield is calculated based on the `lastRoundAssets` variable and the current balance
* Part of the yield (Investor Ratio) is transferred to the Investor's wallet. That yield will be used by the Investor Wallet to buy the new options;

## Deposits Processing Window

As the name suggests, all the funds deposited from the Start to the End Round are processed during this window between the end of the current round and the start of the next round. During this period:  &#x20;

* Newly deposited funds are moved from the vault to the Yield Source (in this case, Lido Finance);

