# 1. Summary

[Sparkle Token](https://etherscan.io/address/0x4b7ad3a56810032782afce12d7d27122bdb96eff#code) smart contract security audit report performed by [Callisto Security Audit Department](https://github.com/EthereumCommonwealth/Auditing)

Token description:

	Symbol      : SPRKL
	Name        : Sparkle
	Total supply: 70,000,000
	Decimals    : 8
	Standard    : ERC20

# 2. In scope

- [Sparkle.sol](https://gist.github.com/yuriy77k/c754b9ecad920f8e38a31d31e27019fa)

# 3. Findings

In total, **4 issues** were reported including:

- 2 low severity issues.

- 2 minor observation.

No critical security issues were found.

## 3.1. Naming Compatibility

### Severity: minor observation

### Description

`increaseAllowance` and `decreaseAllowance` functions should be renamed to the most adopted naming `increaseApproval` and `decreaseApproval` to avoid compatibility issues.

### Code snippet

https://gist.github.com/yuriy77k/c754b9ecad920f8e38a31d31e27019fa#file-sparkle-sol-L212

https://gist.github.com/yuriy77k/c754b9ecad920f8e38a31d31e27019fa#file-sparkle-sol-L236

## 3.2. Approval Decrease
 
### Severity: low

### Description

`decreaseAllowance` function revert if the value to be decreased from the total allowed is higher than the allowance (most implementations set the value to zero in this case), a racing condition can occur in this case between the spender and approver and the approver can lose tokens under some specific cases.

### Code snippet

https://gist.github.com/yuriy77k/c754b9ecad920f8e38a31d31e27019fa#file-sparkle-sol-L236

### Recommendation

Set the value of the allowance to zero if the amount to be decreased is higher than the remaining allowance.

## 3.3. Known vulnerabilities of ERC-20 token

### Severity: low

### Description

1. It is possible to double withdrawal attack. More details [here](https://docs.google.com/document/d/1YLPtQxZu1UAvO9cZ1O2RPXBbT0mooh4DYKjA_jp-RLM/edit)
2. Lack of transaction handling mechanism issue. [WARNING!](https://gist.github.com/Dexaran/ddb3e89fe64bf2e06ed15fbd5679bd20) This is a very common issue and it already caused millions of dollars losses for lots of token users! More details [here](https://docs.google.com/document/d/1Feh5sP6oQL1-1NHi-X1dbgT3ch2WdhbXRevDN681Jv4/edit)

### Recommendation

Add into a function `transfer(address _to, ... )` following code:
```solidity
require( _to != address(this) );
```

## 3.4. Code Removal

### Severity: minor observation

### Description

Function such as `_burn` and `_burnFrom` are internal and unused and can be removed from the code to avoid confusion from users.

### Code snippet

https://gist.github.com/yuriy77k/c754b9ecad920f8e38a31d31e27019fa#file-sparkle-sol-L302

https://gist.github.com/yuriy77k/c754b9ecad920f8e38a31d31e27019fa#file-sparkle-sol-L286

# 4. Conclusion

The contract can be deployed, however, the highlighted issues should be taken into consideration.

# 5. Revealing audit reports

https://gist.github.com/yuriy77k/b672041e4fc6a9d180243a5ebe028d63

https://gist.github.com/yuriy77k/355550ea54cbaca306e19841cc067908

https://gist.github.com/yuriy77k/e1c37d23de979155557961c5884b9949
