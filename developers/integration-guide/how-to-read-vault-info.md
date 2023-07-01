# How to read Vault info

This page will be braked into 2 sections. One regarding the Vault general information (eg: TVL) and the other regarding the user-specific information (Eg: Balances).&#x20;

### 1) Vault information

Inside the Vault information, the main info that you will have:&#x20;

* TVL
* Accumulated Returns (since creation)
* Estimated APY (Get the last 30 days and project this for the year)
* Monthly returns
* Historical transactions

**The easiest way to fetch this information is through our API**: [https://yield-backend.pods.finance/strategies/](https://yield-backend.pods.finance/strategies/)&#x20;

There you will find the information needed from all our vaults.

In this table, you can find the relation between the information above and the response keys.

| Metric                  | Object Key Name              |
| ----------------------- | ---------------------------- |
| TVL                     | `tvlInTokenDeposited`        |
| Accumulated Returns     | `lastAccReturn`              |
| Estimated APY           | `projectedAPY`               |
| Monthly Returns         | `monthlyReturnsBreakdown`    |
| Historical transactions | not supported yet in the API |

### 2) User information

The basic information that you show about the user are:

* Amount Idle (waiting to be processed)
* Amount invested (already processed, waiting to earn yield)
* Historical transactions

**The easiest way to fetch this information is through our API**: [https://yield-backend.pods.finance/](https://yield-backend.pods.finance/strategies/)user/\<userAddress>

In this table, you can find the relation between the information above and the response keys.

| Metric                  | Object Key Name                  |
| ----------------------- | -------------------------------- |
| Amount idle             | `idleAmountInTokenDeposited`     |
| Amount invested         | `investedAmountInTokenDeposited` |
| Number of shares        | `totalShares`                    |
| Returns                 | `returns`                        |
| Historical transactions | `actions`                        |

This information is what we show in this part of our app:

<figure><img src="../../.gitbook/assets/Screen Shot 2023-07-01 at 11.02.48 AM.png" alt=""><figcaption></figcaption></figure>
