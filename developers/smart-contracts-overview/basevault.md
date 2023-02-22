# BaseVault

Base contract responsible for the main logic of our vault. It inherits ERC4626 and ERC20 contracts, so, some functions are not shown below. We only document the functions that we did any modification or overridden on it. You can check [ERC4626](https://eips.ethereum.org/EIPS/eip-4626) specification here, and [ERC20](https://eips.ethereum.org/EIPS/eip-20) here.

## Public State Variables

### DENOMINATOR <a href="#denominator" id="denominator"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L35](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L35)

```solidity
function DENOMINATOR() external view returns (uint256)
```

_DENOMINATOR represents the precision for the following system variables: - MAX\_WITHDRAW\_FEE - INVESTOR\_RATIO_

**Returns**

| Name | Type    | Description                                    |
| ---- | ------- | ---------------------------------------------- |
| \_0  | uint256 | Precision number used when calculating the fee |

### MAX\_WITHDRAW\_FEE <a href="#domain_separator" id="domain_separator"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L41](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L41)

```solidity
function MAX_WITHDRAW_FEE() external view returns (uint256)
```

_MAX\_WITHDRAW\_FEE is a safe check in case the ConfigurationManager sets a fee high enough that can be used as a way to drain funds. The precision of this number is set by constant DENOMINATOR._

**Returns**

| Name | Type    | Description      |
| ---- | ------- | ---------------- |
| \_0  | uint256 | Max Fee boundary |

### MIN\_INITIAL\_ASSETS <a href="#min_initial_assets" id="min_initial_assets"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L47](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L47)

```solidity
function MIN_INITIAL_ASSETS() external view returns (uint256)
```

Minimum asset amount for the first deposit

_This amount prevents the first depositor to steal funds from subsequent depositors. See_ [_https://code4rena.com/reports/2022-01-sherlock/#h-01-first-user-can-steal-everyone-elses-tokens_](https://code4rena.com/reports/2022-01-sherlock/#h-01-first-user-can-steal-everyone-elses-tokens)

**Returns**

| Name | Type    | Description            |
| ---- | ------- | ---------------------- |
| \_0  | uint256 | Initial deposit amount |

### configuration <a href="#configuration" id="configuration"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L49](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L49)

```solidity
function configuration() external view returns (contract IConfigurationManager)
```

**Returns**

| Name | Type    | Description                  |
| ---- | ------- | ---------------------------- |
| \_0  | address | ConfigurationManager address |

## View Methods

### currentRoundId

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L97](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L97)

```solidity
function currentRoundId() external view returns (uint32)
```

Returns the current round ID.

**Returns**

| Name | Type   | Description      |
| ---- | ------ | ---------------- |
| \_0  | uint32 | current round Id |

### isProcessingDeposits

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L104](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L104)

```solidity
function isProcessingDeposits() external view returns (bool)
```

Determines whether the Vault is in the processing deposits state.

_While it's processing deposits, `processDeposits` can be called and new shares can be created. During this period deposits, mints, withdraws and redeems are blocked._

**Returns**

| Name | Type | Description                    |
| ---- | ---- | ------------------------------ |
| \_0  | bool | Is processing deposits boolean |

### processedDeposits

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L111](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L111)

```solidity
function processedDeposits() external view returns (uint256)
```

Returns the amount of processed deposits entering the next round.

**Returns**

| Name | Type    | Description                                           |
| ---- | ------- | ----------------------------------------------------- |
| \_0  | uint256 | Amount of processed deposits entering the next round. |

### queuedDeposits <a href="#queueddeposits" id="queueddeposits"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L313](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L313)

```solidity
function queuedDeposits() external view returns (address[])
```

Outputs addresses in the deposit queue

**Returns**

| Name | Type       | Description                |
| ---- | ---------- | -------------------------- |
| \_0  | address\[] | addresses in deposit queue |

### controller

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L325](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L325)

```solidity
function controller() external view returns (address)
```

Returns the vault controller

**Returns**

| Name | Type    | Description        |
| ---- | ------- | ------------------ |
| \_0  | address | Controller address |

### idleAssetsOf <a href="#idleassetsof" id="idleassetsof"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L284](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L284)

```solidity
function idleAssetsOf(address owner) external view returns (uint256)
```

Outputs the amount of asset tokens of an `owner` is idle, waiting for the next round.

**Parameters**

| Name  | Type    | Description   |
| ----- | ------- | ------------- |
| owner | address | Owner address |

**Returns**

| Name | Type    | Description           |
| ---- | ------- | --------------------- |
| \_0  | uint256 | Amount of Idle Assets |

### getWithdrawFeeRatio <a href="#getwithdrawfeeratio" id="getwithdrawfeeratio"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L275](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L275)

```solidity
function getWithdrawFeeRatio() external view returns (uint256)
```

Returns the fee charged on withdraws.

**Returns**

| Name | Type    | Description        |
| ---- | ------- | ------------------ |
| \_0  | uint256 | Withdraw Fee Ratio |

### depositQueueSize <a href="#depositqueuesize" id="depositqueuesize"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L306](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L306)

```solidity
function depositQueueSize() external view returns (uint256)
```

Outputs current size of the deposit queue.

**Returns**

| Name | Type    | Description |
| ---- | ------- | ----------- |
| \_0  | uint256 | Queue Size  |

### maxDeposit <a href="#maxdeposit" id="maxdeposit"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L226](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L226)

```solidity
function maxDeposit(address) external view returns (uint256)
```

_Returns the maximum amount of the underlying asset that can be deposited into the Vault for the receiver, through a deposit call. - MUST return a limited value if receiver is subject to some deposit limit. - MUST return 2 \*\* 256 - 1 if there is no limit on the maximum amount of assets that may be deposited. - MUST NOT revert._

**Parameters**

| Name | Type    | Description   |
| ---- | ------- | ------------- |
| \_0  | address | Owner address |

**Returns**

| Name | Type    | Description                         |
| ---- | ------- | ----------------------------------- |
| \_0  | uint256 | Max amount of underlying to deposit |

### maxMint <a href="#maxmint" id="maxmint"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L242](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L242)

```solidity
function maxMint(address) external view returns (uint256)
```

_Returns the maximum amount of the Vault shares that can be minted for the receiver, through a mint call. - MUST return a limited value if receiver is subject to some mint limit. - MUST return 2 \*\* 256 - 1 if there is no limit on the maximum amount of shares that may be minted. - MUST NOT revert._

**Parameters**

| Name | Type    | Description   |
| ---- | ------- | ------------- |
| \_0  | address | Owner Address |

**Returns**

| Name | Type    | Description                             |
| ---- | ------- | --------------------------------------- |
| \_0  | uint256 | Max amount of shares that can be minted |

### maxRedeem <a href="#maxredeem" id="maxredeem"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L264](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L264)

```solidity
function maxRedeem(address owner) external view returns (uint256)
```

_Returns the maximum amount of Vault shares that can be redeemed from the owner balance in the Vault, through a redeem call. - MUST return a limited value if owner is subject to some withdrawal limit or timelock. - MUST return balanceOf(owner) if owner is not subject to any withdrawal limit or timelock. - MUST NOT revert._

**Parameters**

| Name  | Type    | Description   |
| ----- | ------- | ------------- |
| owner | address | Owner Address |

**Returns**

| Name | Type    | Description                               |
| ---- | ------- | ----------------------------------------- |
| \_0  | uint256 | Max amount of shares that can be redeemed |

### maxWithdraw <a href="#maxwithdraw" id="maxwithdraw"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L253](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L253)

```solidity
function maxWithdraw(address owner) external view returns (uint256)
```

_Returns the maximum amount of the underlying asset that can be withdrawn from the owner balance in the Vault, through a withdraw call. - MUST return a limited value if owner is subject to some withdrawal limit or timelock. - MUST NOT revert._

**Parameters**

| Name  | Type    | Description   |
| ----- | ------- | ------------- |
| owner | address | Owner Address |

**Returns**

| Name | Type    | Description                                          |
| ---- | ------- | ---------------------------------------------------- |
| \_0  | uint256 | Max amount of underlying asset that can be withdrawn |

### totalAssets <a href="#spentcap" id="spentcap"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L292](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L292)

```solidity
function totalAssets() external view returns (uint256)
```

_Returns the total amount of the underlying asset that is “managed” by Vault. - SHOULD include any compounding that occurs from yield. - MUST be inclusive of any fees that are charged against assets in the Vault. - MUST NOT revert._

**Returns**

| Name | Type    | Description |
| ---- | ------- | ----------- |
| \_0  | uint256 | undefined   |

### totalIdleAssets

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L299](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L299)

```solidity
function totalIdleAssets() external view returns (uint256)
```

Outputs the amount of asset tokens is idle, waiting for the next round.

**Returns**

| Name | Type    | Description |
| ---- | ------- | ----------- |
| \_0  | uint256 | undefined   |

### previewRedeem <a href="#previewdeposit" id="previewdeposit"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L218](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L218)

```solidity
function previewRedeem(uint256 shares) external view returns (uint256)
```

_Allows an on-chain or off-chain user to simulate the effects of their redeemption at the current block, given current on-chain conditions. - MUST return as close to and no more than the exact amount of assets that would be withdrawn in a redeem call in the same transaction. I.e. redeem should return the same or more assets as previewRedeem if called in the same transaction. - MUST NOT account for redemption limits like those returned from maxRedeem and should always act as though the redemption would be accepted, regardless if the user has enough shares, etc. - MUST be inclusive of withdrawal fees. Integrators should be aware of the existence of withdrawal fees. - MUST NOT revert. NOTE: any unfavorable discrepancy between convertToAssets and previewRedeem SHOULD be considered slippage in share price or some other type of condition, meaning the depositor will lose assets by redeeming._

**Parameters**

| Name   | Type    | Description   |
| ------ | ------- | ------------- |
| shares | uint256 | Shares amount |

**Returns**

| Name | Type    | Description   |
| ---- | ------- | ------------- |
| \_0  | uint256 | Assets amount |

### previewWithdraw <a href="#previewwithdraw" id="previewwithdraw"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L211](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L211)

```solidity
function previewWithdraw(uint256 assets) external view returns (uint256)
```

_Because of rounding issues, we did not find a way to return exact shares when including the fees. This is not 100% compliant to ERC4626 specification. You can follow the discussion here:_ [_https://ethereum-magicians.org/t/eip-4626-yield-bearing-vault-standard/7900/104_](https://ethereum-magicians.org/t/eip-4626-yield-bearing-vault-standard/7900/104) _This function will return the number of shares necessary to withdraw assets not including fees. This means that you will need to redeem MORE shares to achieve the net assets._

**Parameters**

| Name   | Type    | Description   |
| ------ | ------- | ------------- |
| assets | uint256 | Assets amount |

**Returns**

| Name | Type    | Description   |
| ---- | ------- | ------------- |
| \_0  | uint256 | Shares Amount |

### Write Methods

### deposit

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L118](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L118)

```solidity
function deposit(uint256 assets, address receiver) external nonpayable returns (uint256)
```

_Mints shares Vault shares to receiver by depositing exactly amount of underlying tokens. - MUST emit the Deposit event. - MAY support an additional flow in which the underlying tokens are owned by the Vault contract before the deposit execution, and are accounted for during deposit. - MUST revert if all of assets cannot be deposited (due to deposit limit being reached, slippage, the user not approving enough underlying tokens to the Vault contract, etc). NOTE: most implementations will require pre-approval of the Vault with the Vault’s underlying asset token._

**Parameters**

| Name     | Type    | Description |
| -------- | ------- | ----------- |
| assets   | uint256 | assets      |
| receiver | address | receiver    |

**Returns**

| Name | Type    | Description |
| ---- | ------- | ----------- |
| \_0  | uint256 | shares      |

### depositWithPermit

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L131](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L131)

```solidity
function depositWithPermit(uint256 assets, address receiver, uint256 deadline, uint8 v, bytes32 r, bytes32 s) external nonpayable returns (uint256)
```

Deposit ERC20 tokens with permit, a gasless token approval.

_Mints shares to receiver by depositing exactly amount of underlying tokens. For more information on the signature format, see the EIP2612 specification: https://eips.ethereum.org/EIPS/eip-2612#specification_

**Parameters**

| Name     | Type    | Description           |
| -------- | ------- | --------------------- |
| assets   | uint256 | assets                |
| receiver | address | receiver address      |
| deadline | uint256 | timestamp deadline    |
| v        | uint8   | signature parameter v |
| r        | bytes32 | signature parameter r |
| s        | bytes32 | signature parameter s |

**Returns**

| Name | Type    | Description   |
| ---- | ------- | ------------- |
| \_0  | uint256 | shares amount |

### endRound

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L347](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L347)

```solidity
function endRound() external nonpayable
```

Closes the round, allowing deposits to the next round be processed. and opens the window for withdraws.

### handleMigration

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L399](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L399)

```solidity
function handleMigration(uint256 assets, address receiver) external nonpayable returns (uint256)
```

Handle migrated assets.

**Parameters**

| Name     | Type    | Description |
| -------- | ------- | ----------- |
| assets   | uint256 | undefined   |
| receiver | address | undefined   |

**Returns**

| Name | Type    | Description                   |
| ---- | ------- | ----------------------------- |
| \_0  | uint256 | Estimation of shares created. |

### migrate

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L378](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L378)

```solidity
function migrate() external nonpayable
```

Migrate assets from this vault to the next vault.

_The `newVault` will be assigned by the ConfigurationManager_

### processQueuedDeposits

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L412](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L412)

```solidity
function processQueuedDeposits(address[] depositors) external nonpayable
```

Distribute shares to depositors queued in the deposit queue, effectively including their assets in the next round.

**Parameters**

| Name       | Type       | Description                         |
| ---------- | ---------- | ----------------------------------- |
| depositors | address\[] | Array of owner addresses to process |

### redeem

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L175](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L175)

```solidity
function redeem(uint256 shares, address receiver, address owner) external nonpayable returns (uint256 assets)
```

_Burns exactly shares from owner and sends assets of underlying tokens to receiver. - MUST emit the Withdraw event. - MAY support an additional flow in which the underlying tokens are owned by the Vault contract before the redeem execution, and are accounted for during redeem. - MUST revert if all of shares cannot be redeemed (due to withdrawal limit being reached, slippage, the owner not having enough shares, etc). NOTE: some implementations will require pre-requesting to the Vault before a withdrawal may be performed. Those methods should be performed separately._

**Parameters**

| Name     | Type    | Description      |
| -------- | ------- | ---------------- |
| shares   | uint256 | shares amount    |
| receiver | address | receiver address |
| owner    | address | owner address    |

**Returns**

| Name   | Type    | Description   |
| ------ | ------- | ------------- |
| assets | uint256 | assets amount |

### refund

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L362](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L362)

```solidity
function refund() external nonpayable returns (uint256 assets)
```

Withdraw all user assets in unprocessed deposits.

**Returns**

| Name   | Type    | Description   |
| ------ | ------- | ------------- |
| assets | uint256 | assets amount |

### startRound

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L332](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L332)

```solidity
function startRound() external nonpayable returns (uint32)
```

Starts the next round, sending the idle funds to the strategy where it should start accruing yield.

**Returns**

| Name | Type   | Description      |
| ---- | ------ | ---------------- |
| \_0  | uint32 | The new round id |

### withdraw

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L194](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L194)

```solidity
function withdraw(uint256 assets, address receiver, address owner) external nonpayable returns (uint256 shares)
```

_Because of rounding issues, we did not find a way to return assets including the fees. This is not 100% compliant to ERC4626 specification. You can follow the discussion here: https://ethereum-magicians.org/t/eip-4626-yield-bearing-vault-standard/7900/104 This function will withdraw the number of assets asked, minus the fee. Example: If the fee is 10% and 100 assets was the input, this function will withdraw 90 assets._

**Parameters**

| Name     | Type    | Description      |
| -------- | ------- | ---------------- |
| assets   | uint256 | assets amount    |
| receiver | address | receiver address |
| owner    | address | owner address    |

**Returns**

| Name   | Type    | Description   |
| ------ | ------- | ------------- |
| shares | uint256 | shares amount |

### mint <a href="#mint" id="mint"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L146](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L146)

```solidity
function mint(uint256 shares, address receiver) external nonpayable returns (uint256)
```

_Mints exactly shares Vault shares to receiver by depositing amount of underlying tokens. - MUST emit the Deposit event. - MAY support an additional flow in which the underlying tokens are owned by the Vault contract before the mint execution, and are accounted for during mint. - MUST revert if all of shares cannot be minted (due to deposit limit being reached, slippage, the user not approving enough underlying tokens to the Vault contract, etc). NOTE: most implementations will require pre-approval of the Vault with the Vault’s underlying asset token._

**Parameters**

| Name     | Type    | Description |
| -------- | ------- | ----------- |
| shares   | uint256 | undefined   |
| receiver | address | undefined   |

**Returns**

| Name | Type    | Description |
| ---- | ------- | ----------- |
| \_0  | uint256 | undefined   |

### mintWithPermit <a href="#mintwithpermit" id="mintwithpermit"></a>

[https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L159](https://github.dev/pods-finance/yield-contracts/blob/main/contracts/vaults/BaseVault.sol#L159)

```solidity
function mintWithPermit(uint256 shares, address receiver, uint256 deadline, uint8 v, bytes32 r, bytes32 s) external nonpayable returns (uint256)
```

Mint shares with permit, a gasless token approval.

_Mints exactly shares to receiver by depositing amount of underlying tokens. For more information on the signature format, see the EIP2612 specification:_ [_https://eips.ethereum.org/EIPS/eip-2612#specification_](https://eips.ethereum.org/EIPS/eip-2612#specification)

**Parameters**

| Name     | Type    | Description |
| -------- | ------- | ----------- |
| shares   | uint256 | undefined   |
| receiver | address | undefined   |
| deadline | uint256 | undefined   |
| v        | uint8   | undefined   |
| r        | bytes32 | undefined   |
| s        | bytes32 | undefined   |

**Returns**

| Name | Type    | Description |
| ---- | ------- | ----------- |
| \_0  | uint256 | undefined   |
