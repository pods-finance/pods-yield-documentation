# How to withdraw

In this guide, we will cover an example of how to deposit into the stETHvv Vault.&#x20;

### 1) If you are withdrawing ETH

If you want to withdraw ETH, it will be a 2-step process. You will need to first Permit (gasless transaction) the Adapter contract to withdraw on your behalf. Then the Adapter contract will convert stETH to ETH under the hood using Curve.

{% tabs %}
{% tab title="Javascript" %}
<pre class="language-javascript"><code class="lang-javascript">import BigNumber from 'bignumber.js'
import { ethers } from 'ethers'

<strong>// Parameters example
</strong>const podsAdapterAddress = '0x4aad0755efd63f4e9b7fac19bd426db4a0d9b5e8'
const podsStethvvAddress = '0x463f9ed5e11764eb9029762011a03643603ad879'
const podsAdapterABI = '' // You can find this information on the Contract Addresses page
const PodsVaultABI = '' // Get this in our Contract Addresses section
const userAddress = '0x123..'

// Instantiate contracts
const PodsAdapter = await ethers.getContractAt(PodsAdapterAddress, PodsAdapterABI)
const PodsVault = await ethers.getContractAt(podsStethvvAddress, PodsVaultABI)

// Check User balance
const userSharesBalance = await PodsVault.balanceOf(userAddress)

// Calculate Slippage tolerance
const slippageTolerance = 2/100; // (Eg: 2%)
const sharesWithSlippageTolerance = userSharesBalance * (1-slippageTolerance)

/////////////
// Ethers.js

const permit = await PodsVault.doPermitFor({
  signer, //This is the only parameter that we are omitting in this tutorial. This is the signer Ethers.js object
  address: PodsVault.address,
  sender: userAddress,
  spender: podsAdapterAddress,
  amount: userSharesBalance,
})

const args = [
  PodsVault.address,
  shares.toString(),
  userAddress,
  sharesWithSlippageTolerance.toString(),
  permit.deadline,
  permit.v,
  permit.r.toString(),
  permit.s.toString(),
]

const transaction = await PodsAdapter.redeemWithPermit(...args)
</code></pre>
{% endtab %}

{% tab title="Solidity" %}
Coming soon...
{% endtab %}
{% endtabs %}

### 2) If you are withdrawing stETH directly

Withdrawing `stETH` is a 1-step process

{% tabs %}
{% tab title="Javascript" %}
<pre class="language-javascript"><code class="lang-javascript">import BigNumber from 'bignumber.js'
import { ethers } from 'ethers'

// Ethers.js
<strong>// Parameters example
</strong>const podsStethvvAddress = '0x463f9ed5e11764eb9029762011a03643603ad879' // Change here for stETHvv or ETHphoria
<strong>const PodsVaultABI = '' // Get this in our Contract Addresses section
</strong>const userAddress = '0x123..' // Address that will receive the shares

// 1) Check address balance
const PodsVault = await ethers.getContractAt(podsStethvvAddress, PodsVaultABI)
const userShareBalance = await PodsVault.balanceOf(userAddress)
const amount = userShareBalance * (1- 0.5) // Withdraw 50% of the shares

/**
  * @param amount Amount to be deposited into the vault
  * @param receiver Address that will receive the token after the withdraw
  * @param receiver Address that will be the owner of the Vault's shares
  * @return uint256 Amount of shares returned by vault ERC4626 contract
 */
await PodsVault.redeem(
  amount, 
  userAddress,
  userAddress
)
</code></pre>
{% endtab %}

{% tab title="Solidity" %}
Coming soon...
{% endtab %}
{% endtabs %}

