# How to deposit

In this guide, we will cover an example of how to deposit into the stETHvv Vault.&#x20;

### 1) If you are depositing using ETH

For this scenario, you can use our Adapter contract. It will convert ETH into stETH using Curve pool under the hood.&#x20;

{% tabs %}
{% tab title="Javascript" %}
<pre class="language-javascript"><code class="lang-javascript">import BigNumber from 'bignumber.js'
import { ethers } from 'ethers'

<strong>// Parameters example
</strong>const podsAdapterAddress = '0x4aad0755efd63f4e9b7fac19bd426db4a0d9b5e8'
const podsStethvvAddress = '0x463f9ed5e11764eb9029762011a03643603ad879'
const podsAdapterABI = '' // You can find this information on the Contract Addresses page

// ETH Amount that will be deposited
const amount = (new BigNumber(1)).multipliedBy(new BigNumber(10).pow(18))
 // 1 ETH
const receiver = '0x123..' // Address that will receive the shares
const slippage = 2/100; // (Eg: 2%)

/////////////
// Ethers.js

// Instantiate contract
const PodsAdapter = await ethers.getContractAt(PodsAdapterAddress, PodsAdapterABI)

const destinationVault = podsStethvvAddress
const minOutput = amount.multipliedBy(1-slippage)

/**
  * @param destinationVault Pods' strategy vault that will receive the stETH
  * @param receiver Address that will be the owner of the Vault's shares
  * @param minOutput slippage control. Minimum acceptable amount of stETH
  * @return uint256 Amount of shares returned by vault ERC4626 contract
 */
await PodsAdapter.deposit(
  destinationVault, 
  receiver, 
  minOutput, 
  { value: amount }
)
</code></pre>
{% endtab %}

{% tab title="Solidity" %}
Coming soon...
{% endtab %}
{% endtabs %}



### 2) If you are depositing using stETH directly
