# ERC20 Standard
 

## Abstract
---

* Name: **Token** standard
* Description: This standard provides basic functionality to **transfer** tokens, as well as allow tokens to be **approved** so they can be spent by another on-chain third party.
* Motivation: A standard interface allows any tokens on Ethereum to be **re-used** by other applications: from **wallets** to **decentralized exchanges**.
*  Offcial document : [EIP-20](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-20.md)

## Example
---
There are so many ERC20 Tokens exist on ethereum already. One good practice can see [ERC20 in OpenZeppelin](https://github.com/OpenZeppelin/zeppelin-solidity/tree/master/contracts/token/ERC20).

## Specification
---

### Required Method
#### totalSupply

Returns the total token supply.

``` js
function totalSupply() view returns (uint256 totalSupply)
```



#### balanceOf

Returns the account balance of another account with address `_owner`.

``` js
function balanceOf(address _owner) view returns (uint256 balance)
```



#### transfer

Transfers `_value` amount of tokens to address `_to`, and MUST fire the `Transfer` event.

``` js
function transfer(address _to, uint256 _value) returns (bool success)
```



#### transferFrom

Transfers `_value` amount of tokens from address `_from` to address `_to`, and MUST fire the `Transfer` event.

The `transferFrom` method is used for a withdraw workflow, allowing contracts to transfer tokens on your behalf.
This can be used for example to allow a contract to transfer tokens on your behalf and/or to charge fees in sub-currencies.

``` js
function transferFrom(address _from, address _to, uint256 _value) returns (bool success)
```

#### approve

Allows `_spender` to withdraw from your account multiple times, up to the `_value` amount. If this function is called again it overwrites the current allowance with `_value`.

``` js
function approve(address _spender, uint256 _value) returns (bool success)
```


#### allowance

Returns the amount which `_spender` is still allowed to withdraw from `_owner`.

``` js
function allowance(address _owner, address _spender) view returns (uint256 remaining)
```



### Optional Method
#### name

Returns the name of the token - e.g. `"MyToken"`.
``` js
function name() view returns (string name)
```

#### symbol
Returns the symbol of the token. E.g. "HIX".
``` js
function symbol() view returns (string symbol)
```



#### decimals

Returns the number of decimals the token uses - e.g. `8`, means to divide the token amount by `100000000` to get its user representation.
``` js
function decimals() view returns (uint8 decimals)
```

### Events


#### Transfer

MUST trigger when tokens are transferred, including zero value transfers.

``` js
event Transfer(address indexed _from, address indexed _to, uint256 _value)
```



#### Approval

MUST trigger on any successful call to `approve(address _spender, uint256 _value)`.

``` js
event Approval(address indexed _owner, address indexed _spender, uint256 _value)
```
## Appendix
---
