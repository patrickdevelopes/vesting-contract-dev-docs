---
description: >-
  Private sale protocol that locks tokens from withdrawal until a period of time
  ends.
---

# Runtime

![](../../.gitbook/assets/privateSale.gif)

### About the Private Sale Contract

The Private Sale contract is a base contract for managing the token private sale, allowing investors to purchase tokens using bnb. This contract implements additional functionality and/or custom behavior. Only `whitelisted` users can contribute. The `processPurchase` function in the PostDelivery contract handles the post payout schedule.

### The Characteristics

* [x] Get funded by the [MainContract.sol](overview.md#about-the-main-contract) contract
* [x] Investors must be `whitelisted`
* [x] Able to set up post delivery schedules
* [x] Solidity best practices
* [x] Binance verified contracts

### Core: PrivateSale (PrivateSale.sol)

<mark style="color:blue;">**Modifiers:**</mark>

* <mark style="color:blue;"></mark>[nonReentrant()](runtime.md#undefined)
* [onlyWhitelisted()](runtime.md#undefined)

<mark style="color:blue;">**Functions:**</mark>

* <mark style="color:blue;"></mark>[fallback()](runtime.md#fallback)
* [token()](runtime.md#undefined)
* [wallet()](runtime.md#undefined-1)
* [rate()](runtime.md#undefined-2)
* [weiRaised()](runtime.md#undefined-3)
* [buyTokens()](runtime.md#undefined)
* [isWhitelisted(account)](runtime.md#iswhitelisted-address-account-bool)
* [addWhitelisted(account)](runtime.md#undefined)
* [removeWhitelisted(account)](runtime.md#removewhitelisted-address-account)
* [renounceWhitelisted()](runtime.md#undefined)
* [preValidatePurchase(beneficiary, weiAmount)](runtime.md#prevalidatepurchase-address-beneficiary-uint256-weiamount)
* [postValidatePurchase()](runtime.md#undefined-2)
* [deliverTokens()](runtime.md#undefined)
* [proccessPurchase()](runtime.md#undefined-1)
* [updatePurchasingState()](runtime.md#undefined-2)
* [getTokenAmount()](runtime.md#undefined-3)
* [forwardFunds()](runtime.md#undefined)

<mark style="color:blue;">**Events:**</mark>

* <mark style="color:blue;"></mark>[TokensPurchased(purchaser, beneficiary, value, amount)](runtime.md#tokenspurchased-address-purchaser-address-beneficiary-uint256-value-uint256-amount)
* [WhitelistedAdded(account)](runtime.md#undefined)
* [WhitelistedRemoved(account)](runtime.md#undefined)

<details>

<summary>nonReentrant()</summary>

Contract module that helps prevent reentrant calls to a function.

Inheriting from `ReentrancyGuard` will make the [`nonReentrant`](https://docs.openzeppelin.com/contracts/2.x/api/utils#ReentrancyGuard-nonReentrant--) modifier available, which can be applied to functions to make sure there are no nested (reentrant) calls to them.

Note that because there is a single `nonReentrant` guard, functions marked as `nonReentrant` may not call one another. This can be worked around by making those functions `private`, and then adding `external` `nonReentrant` entry points to them.

</details>

<details>

<summary>onlyWhitelisted()</summary>



</details>

<details>

<summary>fallback()</summary>

fallback function **DO NOT OVERRIDE** Note that other contracts will transfer funds with a base gas stipend of 2300, which is not enough to call buyTokens. Consider calling buyTokens directly when purchasing tokens from a contract.

</details>

<details>

<summary>token() ??? contract IBEP20</summary>



</details>

<details>

<summary>wallet() ??? address payable</summary>



</details>

<details>

<summary>rate() ??? uint256</summary>



</details>

<details>

<summary>weiRaised() ??? uint256</summary>



</details>

<details>

<summary>buyTokens(address beneficiary)</summary>

low level token purchase **DO NOT OVERRIDE** This function has a non-reentrancy guard, so it shouldn???t be called by another `nonReentrant` function.

</details>

<details>

<summary>isWhitelisted(address account) ??? bool</summary>



</details>

<details>

<summary>addWhitelisted(address account)</summary>



</details>

<details>

<summary>removeWhitelisted(address account)</summary>



</details>

<details>

<summary>renounceWhitelisted()</summary>



</details>

<details>

<summary>preValidatePurchase(address beneficiary, uint256 weiAmount)</summary>

Validation of an incoming purchase. Use require statements to revert state when conditions are not met. Use `super` in contracts that inherit from Crowdsale to extend their validations. Example from CappedCrowdsale.sol???s \_preValidatePurchase method: super.\_preValidatePurchase(beneficiary, weiAmount); require(weiRaised().add(weiAmount) ??? cap);

</details>

<details>

<summary>postValidatePurchase(address beneficiary, uint256 weiAmount)</summary>

Validation of an executed purchase. Observe state and use revert statements to undo rollback when valid conditions are not met.

</details>

<details>

<summary>deliverTokens(address beneficiary, uint256 tokenAmount)</summary>

Source of tokens. Override this method to modify the way in which the crowdsale ultimately gets and sends its tokens.

</details>

<details>

<summary>processPurchase(address beneficiary, uint256 tokenAmount)</summary>

Executed when a purchase has been validated and is ready to be executed. Doesn???t necessarily emit/send tokens.

</details>

<details>

<summary>updatePurchasingState(address beneficiary, uint256 weiAmount)</summary>

Override for extensions that require an internal state to check for validity (current user contributions, etc.)

</details>

<details>

<summary>getTokenAmount(uint256 weiAmount) ??? uint256</summary>

Override to extend the way in which ether is converted to tokens.

</details>

<details>

<summary>forwardFunds()</summary>

Determines how ETH is stored/forwarded on purchases.

</details>

<details>

<summary>TokensPurchased(address purchaser, address beneficiary, uint256 value, uint256 amount)</summary>



</details>

<details>

<summary>WhitelistedAdded(address account)</summary>



</details>

<details>

<summary>WhitelistedRemoved(address account)</summary>



</details>

#### Imported & Utils Contracts

```solidity
import "./MainContract.sol";
import "@openzeppelin/contracts/utils/math/SafeMath.sol";
```

### Validation: TimedPrivateSale (TimedPrivateSale.sol)

<mark style="color:blue;">**Modifiers:**</mark>

* [onlyWhileOpen()](runtime.md#undefined)

<mark style="color:blue;">**Functions:**</mark>

* <mark style="color:blue;"></mark>[openingTime()](runtime.md#undefined)
* [closingTime()](runtime.md#undefined-1)
* [isOpen()](runtime.md#undefined-2)
* [hasClosed()](runtime.md#undefined-3)
* [preValidatePurchase(beneficiary, weiAmount)](runtime.md#postvalidatepurchase-address-beneficiary-uint256-weiamount)
* [extendTime(newClosingTime)](https://docs.openzeppelin.com/contracts/2.x/api/crowdsale#TimedCrowdsale-\_extendTime-uint256-)

<mark style="color:blue;">**Events:**</mark>

* <mark style="color:blue;"></mark>[TimedPrivateSaleExtended(prevClosingTime, newClosingTime)](runtime.md#undefined)

<details>

<summary>onlyWhileOpen()</summary>

Reverts if not in crowdsale time range.

</details>

<details>

<summary>openingTime () ??? uint256</summary>

The private sale opening time.

</details>

<details>

<summary>closingTime () ??? uint256</summary>

The private sale ending time (1 year).

</details>

<details>

<summary>isOpen () ??? bool</summary>

`true` if the private sale is open, `false` otherwise.

</details>

<details>

<summary>hasClosed () ??? bool</summary>

Whether private sale period has elapsed

</details>

<details>

<summary>preValidatePurchase(address beneficiary, uint256 weiAmount)</summary>

Extend parent behavior requiring to be within the contributing period

</details>

<details>

<summary>extendTime(uint256 newClosingTime)</summary>

Extend crowdsale.

</details>

<details>

<summary>TimedPrivateSaleExtended(uint256 prevClosingTime, uint256 newClosingTime)</summary>



</details>

#### Imported & Utils Contracts

```solidity
import "./PrivateSale.sol";
import "@openzeppelin/contracts/utils/math/SafeMath.sol";
```

### Distribution: PostDelivery (PostDelivery.sol)

<mark style="color:blue;">**Functions:**</mark>

* <mark style="color:blue;"></mark>[withdrawTokens(beneficiary)](runtime.md#withdrawtokens-address-beneficiary)
* [balanceOf(account)](runtime.md#balanceof-address-account-uint256)
* [processPurchase(beneficiary, tokenAmount)](runtime.md#processpurchase-address-beneficiary-uint256-tokenamount-1)

<details>

<summary>withdrawTokens(address beneficiary)</summary>

Withdraw tokens only after crowdsale ends.

</details>

<details>

<summary>balanceOf(address account) ??? uint256</summary>



</details>

<details>

<summary>processPurchase(address beneficiary, uint256 tokenAmount)</summary>

Overrides parent by storing due balances, and delivering tokens to the vault instead of the end user. This ensures that the tokens will be available by the time they are withdrawn (which may not be the case if `_deliverTokens` was called later).

</details>

#### Imported & Utils Contracts

```solidity
import "./TimedPrivateSale.sol";
import "@openzeppelin/contracts/utils/math/SafeMath.sol";
```
