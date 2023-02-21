# EthAdapter

The **EthAdapter** is responsible for accepting deposits and withdrawals in ETH, instead of accepting the staked ETH directly. It uses Curve as a trading venue under the hood.

## Public State Variables

### pool

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L23](https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L23)

```solidity
function pool() external view returns (address
```

Curve's pool for the ETH <> stETH token pair.

### ETH\_INDEX

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L28](https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L28)

```solidity
function ETH_INDEX() external view returns (int128)
```

ETH token index in the Curve pool. It is constant `0`.

### STETH\_INDEX

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L33](https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L33)

```solidity
function ETH_INDEX() external view returns (int128)
```

StETH token index in the Curve pool. It is constant `1`.

### ETH\_ADDRESS

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L38](https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L38)

```solidity
function ETH_ADDRESS() external view returns (address)
```

ETH token address representation. It is constant `0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE`

### STETH\_ADDRESS

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L43](https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L43)

```solidity
function STETH_ADDRESS() external view returns (address)
```

StETH token address representation. It is constant 0xae7ab96520DE3A18E5e111B5EaAb095312D7fE84

## View Methods

### convertToSTETH

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L61](https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L61)

```solidity
function convertToSTETH(uint256 ethAmount) external view returns (uint256)
```

Convert `ethAmount` ETH to stETH using Curve pool and returns the resulting amount of stETH.

**Parameters**

| Name      | Type    | Description              |
| --------- | ------- | ------------------------ |
| ethAmount | uint256 | Amount of ETH to convert |

**Returns**

| Name | Type    | Description                           |
| ---- | ------- | ------------------------------------- |
| \_0  | uint256 | Amount of stETH receiveid in exchange |

### convertToETH

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L70](https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L70)

```solidity
function convertToETH(uint256 stETHAmount) external view returns (uint256)
```

Convert `stethAmount` stETH to ETH using Curve pool and returns the resulting amount of ETH.

**Parameters**

| Name        | Type    | Description              |
| ----------- | ------- | ------------------------ |
| stETHAmount | uint256 | Amount of ETH to convert |

**Returns**

| Name | Type    | Description                         |
| ---- | ------- | ----------------------------------- |
| \_0  | uint256 | Amount of ETH receiveid in exchange |

## Write Methods <a href="#deposit" id="deposit"></a>

### deposit <a href="#deposit" id="deposit"></a>

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L81](https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L81)

```solidity
function deposit(contract IVault vault, address receiver, uint256 minOutput) external payable returns (uint256)
```

Deposit `msg.value` of ETH, convert to stETH and deposit into `vault`

**Parameters**

| Name      | Type            | Description                                          |
| --------- | --------------- | ---------------------------------------------------- |
| vault     | contract IVault | Pods' strategy vault that will receive the stETH     |
| receiver  | address         | Address that will be the owner of the Vault's shares |
| minOutput | uint256         | slippage control. Minimum acceptable amount of stETH |

**Returns**

| Name | Type    | Description                                                 |
| ---- | ------- | ----------------------------------------------------------- |
| \_0  | uint256 | uint256 Amount of shares returned by vault ERC4626 contract |

### redeem

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L100](https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L100)

```solidity
function redeem(contract IVault vault, uint256 shares, address receiver, uint256 minOutput) external nonpayable returns (uint256)
```

Redeem `shares` shares, receive stETH, trade stETH for ETH and send to receiver

**Parameters**

| Name      | Type            | Description                                                         |
| --------- | --------------- | ------------------------------------------------------------------- |
| vault     | contract IVault | Pods' strategy vault that will receive the shares and payback stETH |
| shares    | uint256         | Amount of Vault's shares to redeem                                  |
| receiver  | address         | Address that will receive back the ETH withdrawn from the `vault`   |
| minOutput | uint256         | slippage control. Minimum acceptable amount of ETH                  |

**Returns**

| Name | Type    | Description                                          |
| ---- | ------- | ---------------------------------------------------- |
| \_0  | uint256 | uint256 Amount of assets received from Vault ERC4626 |

### redeemWithPermit <a href="#redeemwithpermit" id="redeemwithpermit"></a>

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L124](https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L124)

```solidity
function redeemWithPermit(contract IVault vault, uint256 shares, address receiver, uint256 minOutput, uint256 deadline, uint8 v, bytes32 r, bytes32 s) external nonpayable returns (uint256 assets)
```

redeemWithPermit `shares` shares, receive stETH, trade stETH for ETH and send to receiver

_Do not need to approve the shares in advance. The vault tokenized shares supports Permit_

**Parameters**

| Name      | Type            | Description                                                         |
| --------- | --------------- | ------------------------------------------------------------------- |
| vault     | contract IVault | Pods' strategy vault that will receive the shares and payback stETH |
| shares    | uint256         | Amount of Vault's shares to redeem                                  |
| receiver  | address         | Address that will receive back the ETH withdrawn from `vault`       |
| minOutput | uint256         | slippage control. Minimum acceptable amount of ETH                  |
| deadline  | uint256         | deadline that this transaction will be valid                        |
| v         | uint8           | recovery id                                                         |
| r         | bytes32         | ECDSA signature output                                              |
| s         | bytes32         | ECDSA signature output                                              |

**Returns**

| Name   | Type    | Description                                  |
| ------ | ------- | -------------------------------------------- |
| assets | uint256 | Amount of assets received from Vault ERC4626 |

### withdraw <a href="#withdraw" id="withdraw"></a>

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L148](https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L148)

```solidity
function withdraw(contract IVault vault, uint256 assets, address receiver, uint256 minOutput) external nonpayable returns (uint256 shares)
```

Withdraw `assets` assets, receive stETH, trade stETH for ETH and send to receiver

_Do not need to approve the shares in advance. The vault tokenized shares supports Permit_

**Parameters**

| Name      | Type            | Description                                                         |
| --------- | --------------- | ------------------------------------------------------------------- |
| vault     | contract IVault | Pods' strategy vault that will receive the shares and payback stETH |
| assets    | uint256         | Amount of assets (stETH) to redeem                                  |
| receiver  | address         | Address that will receive back the ETH withdrawn from the Vault     |
| minOutput | uint256         | slippage control. Minimum acceptable amount of ETH                  |

**Returns**

| Name   | Type    | Description                                        |
| ------ | ------- | -------------------------------------------------- |
| shares | uint256 | Amount of shares burned in order to receive assets |

### withdrawWithPermit <a href="#withdrawwithpermit" id="withdrawwithpermit"></a>

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L171](https://github.com/pods-finance/yield-contracts/blob/main/contracts/proxy/ETHAdapter.sol#L171)

```solidity
function withdrawWithPermit(contract IVault vault, uint256 assets, address receiver, uint256 minOutput, uint256 deadline, uint8 v, bytes32 r, bytes32 s) external nonpayable returns (uint256 shares)
```

withdrawWithPermit `assets` assets, receive stETH, trade stETH for ETH and send to receiver

_Do not need to approve the shares in advance. Vault's tokenized shares supports Permit_

**Parameters**

| Name      | Type            | Description                                                         |
| --------- | --------------- | ------------------------------------------------------------------- |
| vault     | contract IVault | Pods' strategy vault that will receive the shares and payback stETH |
| assets    | uint256         | Amount of assets (stETH) to redeem                                  |
| receiver  | address         | Address that will receive back the ETH withdrawn from the Vault     |
| minOutput | uint256         | slippage control. Minimum acceptable amount of ETH                  |
| deadline  | uint256         | deadline that this transaction will be valid                        |
| v         | uint8           | recovery id                                                         |
| r         | bytes32         | ECDSA signature output                                              |
| s         | bytes32         | ECDSA signature output                                              |

**Returns**

| Name   | Type    | Description                                        |
| ------ | ------- | -------------------------------------------------- |
| shares | uint256 | Amount of shares burned in order to receive assets |

\
\
