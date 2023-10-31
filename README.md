### Scope

Repository: [DeXe-Protocol](https://github.com/dexe-network/DeXe-Protocol)  
Commit: [f2fe12eeac0c4c63ac39670912640dc91d94bda5](https://github.com/dexe-network/DeXe-Protocol/tree/f2fe12eeac0c4c63ac39670912640dc91d94bda5)

### Findings

**GovPoolCredit.sol line 80, Critical**  
CreditInfo internal representation is not parsed to 18 decimals

Transferring funds in transferCreditAmount() implies native decimals format, not 18. View function getCreditInfo (line 56) also returns native decimals format, but should be internal 18-decimals format.

**GovPoolCommission.sol line 27, Low.**  
Reward token is not TryMinted during commission transfer  

When transferring reward commission, amount is reduced down to the balance of a reward token in treasury. Then sendFunds() is called with the parameter «Mint», but mint is never applied, because of reduction.

**GovPoolUnlock.sol line 53, Info.**
maxUnlocked is never greater than maxLockedAmount

**ERC20Gov.sol line 59, Gas optimisation.**
totalSupply() == params.mintedTotal results in minting 0 tokens
