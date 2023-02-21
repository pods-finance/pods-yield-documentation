# 🔐 Access Control

### TLDR

In our smart contracts, we made some architectural decisions to reduce our smart contract risks and access control risks:

* The Admin/Multisig does not have access to the principal
* The Admin/Multisig can not permanently freeze funds.
* The contracts are not upgradeable (No malicious upgradability can happen)
* You can leave the position at any point in time
* The Multisig/Admin only has access to the **weekly yield.** This represents less than 1% of the TVL
* The withdrawal fee can change up to a 10% cap (No malicious attack on fees)&#x20;

Below we will dive deep into the privileges of each role:&#x20;

### VaultController

Multisig 2/3: [https://etherscan.io/address/0xe24E8beEBa6219CD2F6FA25D5b04a0e78f19Aa0A](https://etherscan.io/address/0xe24E8beEBa6219CD2F6FA25D5b04a0e78f19Aa0A)

This role is responsible for the functions `endRound` and `startRound.`During the `endRound` phase, other addresses can not perform deposit or withdrawal actions until the `startRound` function is called. In order to avoid the risk of principal funds getting stuck, after a week (\~604800 blocks) any address can call the startRound function, enabling withdrawals again.

### ConfigurationManager Owner

Multisig 2/3: [https://etherscan.io/address/0xe24E8beEBa6219CD2F6FA25D5b04a0e78f19Aa0A](https://etherscan.io/address/0xe24E8beEBa6219CD2F6FA25D5b04a0e78f19Aa0A)

This role is responsible for setting the:

* VaultController of a certain vault
* Withdraw fee ratio of a certain vault (cap at 10% by the code)
* Migration contract of a certain vault (in case of migration)
* Cap of a certain vault

### Investor

Multisig 2/3: [https://etherscan.io/address/0x448C7875633EA285996870BF56bcE7C64Ee94A70](https://etherscan.io/address/0x448C7875633EA285996870BF56bcE7C64Ee94A70)

This role is the one responsible for using 50& of the weekly yield to buy options at the best price. This could be an off-chain exchange, L2 trade, or OTC.





