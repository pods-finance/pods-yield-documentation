# Smart Contracts Overview

<figure><img src="../../.gitbook/assets/Pods Yield - v1 (3).png" alt=""><figcaption><p>Pods Yield Contracts Overview</p></figcaption></figure>

### BaseVault&#x20;

A contract that will handle the overall logic of this vault structure with rounds. It is ERC4626 compliant. We use [OZs 4626](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/ERC4626.sol) implementation.&#x20;

### ConfigurationManager&#x20;

Responsible for storing configuration variables of the vault, for instance, the FEE\_RATIO and the VaultController address.&#x20;

### STETHVault&#x20;

This contract inherit `BaseVault to` implement specifics about `stETH` strategy`.`

### ETHAdapter&#x20;

Responsible for converting `ETH` into `stETH`. It uses Curve as the trading venue.



### GitHub repo

{% embed url="https://github.com/pods-finance/yield-contracts" %}

### Coverage

{% embed url="https://coveralls.io/github/pods-finance/yield-contracts?branch=main" %}

### Addresses

{% embed url="https://docs.pods.finance/developers/contracts-addresses" %}

### Audits

{% embed url="https://github.com/pods-finance/yield-contracts/tree/main/audits" %}

### Bug Bounty Program (BBP)

{% embed url="https://immunefi.com/bounty/pods/" %}

### Ad

### Ad

### Ad

### Ad
