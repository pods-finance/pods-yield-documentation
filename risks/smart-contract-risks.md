# Smart Contract Risks

### 1) Compared with having exposure only to Lido or other staking services:

You will add on top of your staking services contracts, the risks of Pods Smart Contracts risk.&#x20;

In our smart contracts we made some architectural decisions to reduce a lot of our smart contract risks:

* The Admin/Multisig does not have access to the principal
* The Admin/Multisig can not stop withdraws
* The contracts are not upgradeable (No malicious upgradability can happen)
* You can leave the position at any point in time
* The Multisig/Admin only has access to the **weekly yield.** This represents less than 1% of the TVL
* The Pods Vault itself **is not** exposed to Oracle Risks
* We spend a lot of energy and money on security. You can check our audits [here](broken-reference)

### 2) Compared with holding ETH

Apart from our contracts, we interact with the Yield Source contract (Lido). Lido has three pillars that you believe bring security to the system: Heavy investment in [audits](https://github.com/lidofinance/audits). [Battled tested TVL](https://defillama.com/protocol/lido) and a good [bug bounty](https://lido.fi/bug-bounty).

An issue in the smart contracts from Lido that affects liquidity in secondary markets could result in an indirect impact on our users. This is because users would be holding stETH and stETH could run low on market liquidity.&#x20;



