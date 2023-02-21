# ConfigurationManager

The **ConfigurationManager** is the management layer of the protocol; it sets global or specific vault's parameters as a cap, withdraws fee, migration destination, and the `vaultController` role for each vault.

## View Methods

### getParameter

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/configuration/ConfigurationManager.sol#L34](https://github.com/pods-finance/yield-contracts/blob/main/contracts/configuration/ConfigurationManager.sol#L34)

```solidity
function getParameter(address target, bytes32 name) external view returns (uint256);
```

Retrieves the value of a parameter set to contract. If the value is not a uint256, you will need to perform encoding/decoding operations

**Parameters**

| Name   | Type    | Description                 |
| ------ | ------- | --------------------------- |
| target | address | The contract target address |
| name   | bytes32 | The parameter name          |

**Returns**

| Name    | Type    | Description          |
| ------- | ------- | -------------------- |
| unnamed | uint256 | The stored parameter |

### getGlobalParameter

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/configuration/ConfigurationManager.sol#L](https://github.com/pods-finance/yield-contracts/blob/main/contracts/configuration/ConfigurationManager.sol#L34)[40](https://github.com/pods-finance/yield-contracts/blob/main/contracts/configuration/ConfigurationManager.sol#L41)

```solidity
function getGlobalParameter(bytes32 name) external view returns (uint256);
```

Retrieves the value of a global parameter. If the value is not a uint256, you will need to perform encoding/decoding operations

**Parameters**

| Name | Type    | Description        |
| ---- | ------- | ------------------ |
| name | bytes32 | The parameter name |

**Returns**

| Name    | Type    | Description          |
| ------- | ------- | -------------------- |
| unnamed | uint256 | The stored parameter |

### getCap

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/configuration/ConfigurationManager.sol#L57](https://github.com/pods-finance/yield-contracts/blob/main/contracts/configuration/ConfigurationManager.sol#L57)

```solidity
function getCap(address target) external view returns (uint256);
```

Retrieves the value of the cap set to a contract. If the value is not a uint256, you will need to perform encoding/decoding operations

**Parameters**

| Name   | Type    | Description                 |
| ------ | ------- | --------------------------- |
| target | address | The contract target address |

**Returns**

| Name    | Type    | Description    |
| ------- | ------- | -------------- |
| unnamed | uint256 | The stored cap |

### getVaultMigration

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/configuration/ConfigurationManager.sol#L73](https://github.com/pods-finance/yield-contracts/blob/main/contracts/configuration/ConfigurationManager.sol#L73)

```solidity
function getVaultMigration(address oldVault) external view returns (address);
```

Retrieves the value of the destination contract of an original vault.

**Parameters**

| Name     | Type    | Description      |
| -------- | ------- | ---------------- |
| oldVault | address | The origin vault |

**Returns**

| Name    | Type    | Description           |
| ------- | ------- | --------------------- |
| unnamed | address | The destination vault |

## Write Methods

### setParameter

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/configuration/ConfigurationManager.sol#L22](https://github.com/pods-finance/yield-contracts/blob/main/contracts/configuration/ConfigurationManager.sol#L22)

```solidity
function setParameter(address target, bytes32 name, uint256 value) external onlyOwner;
```

Set specific parameters to a contract or globally across multiple contracts. Use `address(0)` to set a global parameter.

**Parameters**

| Name   | Type    | Description                 |
| ------ | ------- | --------------------------- |
| target | address | The contract target address |
| name   | bytes32 | The parameter name          |
| value  | uint256 | The parameter value         |

### setCap

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/configuration/ConfigurationManager.sol#L48](https://github.com/pods-finance/yield-contracts/blob/main/contracts/configuration/ConfigurationManager.sol#L48)

```solidity
function setCap(address target, uint256 value) external onlyOwner;
```

Set the cap of a target vault.

**Parameters**

| Name   | Type    | Description                 |
| ------ | ------- | --------------------------- |
| target | address | The contract target address |
| value  | uint256 | The cap value               |

### setVaultMigration

[https://github.com/pods-finance/yield-contracts/blob/main/contracts/configuration/ConfigurationManager.sol#L64](https://github.com/pods-finance/yield-contracts/blob/main/contracts/configuration/ConfigurationManager.sol#L64)

```solidity
function setVaultMigration(address oldVault, address newVault) external onlyOwner;
```

Sets the allowance to migrate to a `vault` address.

**Parameters**

| Name     | Type    | Description                                        |
| -------- | ------- | -------------------------------------------------- |
| oldVault | address | The current vault address                          |
| newVault | address | The vault where assets are going to be migrated to |



a





