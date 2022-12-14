---
description: Upgradeable BEP20 protocol on the Binance Smart Chain.
---

# Main Contract

![](../../.gitbook/assets/bgn.gif)

### About the Main Contract

The Main Contract is a base contract for managing the token itself and holds all necessary functions from the BEP20 standard. This standard IBEP20 interface is used by other applications: from wallets to decentralized exchanges in a consistent way.

### The Characteristics

* [x] BEP20 standard that implements the interface IBEP20
* [x] Upgradeable contract using initializers​
* [x] Solidity best practices
* [x] Binance verified contracts

### Core: MainContract (MainContract.sol)

<mark style="color:blue;">**Functions:**</mark>

* [constructor(name, symbol, decimals)](overview.md#constructor-string-name-string-symbol-uint8-decimals)
* [name()](overview.md#name-string)
* [symbol()](overview.md#symbol-string)
* [decimals()](overview.md#decimals-uint8)
* [totalSupply()](overview.md#undefined)
* [balanceOf(account)](overview.md#undefined-1)
* [getOwner()](overview.md#undefined-2)
* [transfer(to, amount)](overview.md#transferfrom-address-from-address-to-uint256-amount-bool)
* [transferFrom(from, to, amount)](overview.md#undefined)
* [approve(spender, amount)](overview.md#undefined-1)
* [alllowance(owner, spender)](overview.md#undefined-2)
* [initialize(name, symbol, decimals)](overview.md#undefined)

<mark style="color:blue;">**Events:**</mark>

* [Transfer()](overview.md#transfer-address-from-address-to-uint256-value)
* [Approval()](overview.md#approval-address-owner-address-spender-uint256-value)

<details>

<summary>constructor(string name, string symbol, uint8 decimals)</summary>

Sets the values for `name`, `symbol`, and `decimals`. All three of these values are immutable: they can only be set once during construction.

</details>

<details>

<summary>name () → string</summary>

Returns the name of the token - e.g. "MyToken".

</details>

<details>

<summary>symbol () → string </summary>

Returns the symbol of the token, usually a shorter version of the name.

</details>

<details>

<summary>decimals () → uint8</summary>

Returns the number of decimals used to get its user representation. For example, if `decimals` equals `2`, a balance of `505` tokens should be displayed to a user as `5.05` (`505 / 10 ** 2`).

</details>

<details>

<summary>totalSupply () → uint256</summary>

Returns the total supply of the token.

</details>

<details>

<summary>balanceOf (address account) → uint256</summary>

Returns the balance of an address

</details>

<details>

<summary>getOwner () → uint256</summary>

Returns the bep20 token owner which is necessary for binding with bep2 token.

</details>

<details>

<summary>transfer (address to, uint256 amount) → bool</summary>

Moves `amount` tokens from the caller’s account to `to`.

Returns a boolean value indicating whether the operation succeeded.

</details>

<details>

<summary>transferFrom (address from, address to, uint256 amount) → bool</summary>

Emits an `Approval` event indicating the updated allowance. This is not required by the EIP.

</details>

<details>

<summary>approve (address spender, uint256 amount) → bool</summary>

If `amount` is the maximum `uint256`, the allowance is not updated on `transferFrom`. This is semantically equivalent to an infinite approval.

</details>

<details>

<summary>allowance (address owner, address spender) → uint256</summary>

Returns allowance

</details>

<details>

<summary>Transfer (address from, address to, uint256 value)</summary>

Emitted when `value` tokens are moved from one account (`from`) to another (`to`).

Note that `value` may be zero.

</details>

<details>

<summary>Approval (address owner, address spender, uint256 value)</summary>

Emitted when the allowance of a `spender` for an `owner` is set by a call to `approve`. `value` is the new allowance.

</details>

<details>

<summary>initialize(string name, string symbol, uint8 decimals)</summary>

Updates the contract

</details>

### Interface: IBEP20 (IBEP20.sol)

<mark style="color:blue;">**Functions:**</mark>

* [totalSupply()](overview.md#totalsupply-uint256-1)
* [decimals()](overview.md#decimals-uint8-1)
* [symbol()](overview.md#symbol-string-1)
* [name()](overview.md#name-string-1)
* [getOwner()](overview.md#getowner-address-uint256)
* [balanceOf()](overview.md#balanceof-address-account-uint256-1)
* [transfer()](overview.md#transfer-address-recipient-uint256-amount-bool)
* [allowance()](overview.md#allowance-address-owner-address-spender-uint256-1)
* [approve()](overview.md#approve-address-spender-uint256-amount-bool-1)
* [transferFrom()](overview.md#transferfrom-address-sender-address-recipient-uint256-amount-bool)

<mark style="color:blue;">**Events:**</mark>

* [Transfer()](overview.md#transfer-address-from-address-to-uint256-value-1)
* [Approval()](overview.md#approval-address-owner-address-spender-uint256-value-1)

<details>

<summary>totalSupply() → uint256</summary>

Returns the amount of tokens in existence.

</details>

<details>

<summary>decimals() → uint8</summary>

Returns the decimals

</details>

<details>

<summary>symbol() →string</summary>

Returns the symbol

</details>

<details>

<summary>name() →string</summary>

Returns the name

</details>

<details>

<summary>getOwner(address) → uint256</summary>

Returns the owner

</details>

<details>

<summary>balanceOf(address account) → uint256</summary>

Returns the amount of tokens owned by account.

</details>

<details>

<summary>transfer(address recipient, uint256 amount) → bool</summary>

Moves `amount` tokens from the caller’s account to `recipient`.

Returns a boolean value indicating whether the operation succeeded.

</details>

<details>

<summary>allowance(address owner, address spender) → uint256</summary>

Returns the remaining number of tokens that `spender` will be allowed to spend on behalf of `owner` through `transferFrom`. This is zero by default.

This value changes when `approve` or `transferFrom` are called.

</details>

<details>

<summary>approve(address spender, uint256 amount) → bool</summary>

Sets `amount` as the allowance of `spender` over the caller’s tokens.

Returns a boolean value indicating whether the operation succeeded.

</details>

<details>

<summary>transferFrom(address sender, address recipient, uint256 amount) → bool</summary>

Moves `amount` tokens from `sender` to `recipient` using the allowance mechanism. `amount` is then deducted from the caller’s allowance.

Returns a boolean value indicating whether the operation succeeded.

</details>

<details>

<summary>Transfer(address from, address to, uint256 value)</summary>

Emitted when `value` tokens are moved from one account (`from`) to another (`to`).

Note that `value` may be zero.

</details>

<details>

<summary>Approval(address owner, address spender, uint256 value)</summary>

Emitted when the allowance of a `spender` for an `owner` is set by a call to `approve`. `value` is the new allowance.

</details>

#### Imported & Utils Contracts

```solidity
import "@openzeppelin/contracts/proxy/TransparentUpgradeableProxy.sol";
import "@openzeppelin/contracts/utils/math/SafeMath.sol";
import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/utils/Context.sol";
```
