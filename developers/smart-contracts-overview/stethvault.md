# STETHVault

A Vault that uses variable weekly yields to buy strangles. It uses Lido as a yield source.

src: [https://github.com/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol](https://github.com/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol)

## Public State Variables

### INVESTOR\_RATIO <a href="#denominator" id="denominator"></a>

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L27](https://github.com/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L27)

```solidity
function INVESTOR_RATIO() external view returns (uint256)
```

_INVESTOR\_RATIO is the proportion that the weekly yield will be split The precision of this number is set by the variable DENOMINATOR. 5000 is equivalent to 50%._

**Returns**

| Name | Type    | Description          |
| ---- | ------- | -------------------- |
| \_0  | uint256 | investor ratio value |

### investor <a href="#investor" id="investor"></a>

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L28](https://github.com/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L28)

```solidity
function investor() external view returns (address)
```

Returns the investor's wallet. [Investor](../../stethvv/system-actors.md) is the role responsible for buying weekly options.

**Returns**

| Name | Type    | Description      |
| ---- | ------- | ---------------- |
| \_0  | address | investor address |

### sharePriceDecimals <a href="#sharepricedecimals" id="sharepricedecimals"></a>

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L29](https://github.com/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L29)

```solidity
function sharePriceDecimals() external view returns (uint8)
```

**Returns**

| Name | Type  | Description          |
| ---- | ----- | -------------------- |
| \_0  | uint8 | share price decimals |

### lastRoundAssets <a href="#lastroundassets" id="lastroundassets"></a>

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L30](https://github.com/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L30)

```solidity
function lastRoundAssets() external view returns (uint256)
```

**Returns**

| Name | Type    | Description                               |
| ---- | ------- | ----------------------------------------- |
| \_0  | uint256 | Total assets in the end of the last round |

### lastSharePrice <a href="#lastshareprice" id="lastshareprice"></a>

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L31](https://github.com/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L31)

```solidity
function lastSharePrice() external view returns (uint256 numerator, uint256 denominator)
```

**Returns**

| Name        | Type    | Description                              |
| ----------- | ------- | ---------------------------------------- |
| numerator   | uint256 | Share Price in the end of the last round |
| denominator | uint256 | undefined                                |

## View Methods <a href="#maxdeposit" id="maxdeposit"></a>

### assetsOf <a href="#max_withdraw_fee" id="max_withdraw_fee"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L63](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L63)

```solidity
function assetsOf(address owner) external view returns (uint256)
```

Outputs the amount of asset tokens of an `owner` are either waiting for the next round, deposited or committed.

**Parameters**

| Name  | Type    | Description   |
| ----- | ------- | ------------- |
| owner | address | owner address |

**Returns**

| Name | Type    | Description      |
| ---- | ------- | ---------------- |
| \_0  | uint256 | amount of assets |

### sharePrice <a href="#shareprice" id="shareprice"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L75](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L75)

```solidity
function sharePrice() external view returns (uint256)
```

Return the stETH price per share

_Each share is considered to be 10^(assets.decimals()) The share price represents the amount of stETH needed to mint one vault share. When the number of vault shares that has been minted thus far is zero, the share price should simply be the ratio of the underlying asset's decimals to the vault's decimals._

**Returns**

| Name | Type    | Description         |
| ---- | ------- | ------------------- |
| \_0  | uint256 | Current Share Price |

## Write Methods

### depositWithPermit

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L82](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L82)

```solidity
function depositWithPermit(uint256 assets, address receiver, uint256 deadline, uint8 v, bytes32 r, bytes32 s) external nonpayable returns (uint256)
```

Deposit ERC20 tokens with permit, a gasless token approval.

_Mints shares to receiver by depositing exactly amount of underlying tokens. For more information on the signature format, see the EIP2612 specification:_ [_https://eips.ethereum.org/EIPS/eip-2612#specification_](https://eips.ethereum.org/EIPS/eip-2612#specification)

**Parameters**

| Name     | Type    | Description             |
| -------- | ------- | ----------------------- |
| assets   | uint256 | Amount of assets        |
| receiver | address | Receiver address        |
| deadline | uint256 | timestamp deadline      |
| v        | uint8   | transaction signature v |
| r        | bytes32 | transaction signature r |
| s        | bytes32 | transaction signature s |

**Returns**

| Name | Type    | Description  |
| ---- | ------- | ------------ |
| \_0  | uint256 | share amount |

### mintWithPermit

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L96](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/STETHVault.sol#L96)

```solidity
function mintWithPermit(uint256 shares, address receiver, uint256 deadline, uint8 v, bytes32 r, bytes32 s) external nonpayable returns (uint256)
```

Mint shares with permit, a gasless token approval.

_Mints exactly shares to receiver by depositing amount of underlying tokens. For more information on the signature format, see the EIP2612 specification:_ [_https://eips.ethereum.org/EIPS/eip-2612#specification_](https://eips.ethereum.org/EIPS/eip-2612#specification)

**Parameters**

| Name     | Type    | Description             |
| -------- | ------- | ----------------------- |
| assets   | uint256 | Amount of assets        |
| receiver | address | Receiver address        |
| deadline | uint256 | timestamp deadline      |
| v        | uint8   | transaction signature v |
| r        | bytes32 | transaction signature r |
| s        | bytes32 | transaction signature s |

**Returns**

| Name | Type    | Description              |
| ---- | ------- | ------------------------ |
| \_0  | uint256 | underlying tokens amount |
