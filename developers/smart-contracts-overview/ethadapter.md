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

| Name    | Type    | Description                           |
| ------- | ------- | ------------------------------------- |
| unnamed | uint256 | Amount of stETH receiveid in exchange |

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

| Name    | Type    | Description                         |
| ------- | ------- | ----------------------------------- |
| unnamed | uint256 | Amount of ETH receiveid in exchange |







