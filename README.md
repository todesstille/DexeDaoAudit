### Scope

Repository: [DeXe-Protocol](https://github.com/dexe-network/DeXe-Protocol)  
Commit: [f2fe12eeac0c4c63ac39670912640dc91d94bda5](https://github.com/dexe-network/DeXe-Protocol/tree/f2fe12eeac0c4c63ac39670912640dc91d94bda5)

### Findings

**GovPoolCommission.sol line 27, Low.**  
Reward token is not TryMinted during commission transfer  

When transferring reward commission, amount is reduced down to the balance of a reward token in treasury. Then sendFunds() is called with the parameter «Mint», but mint is never applied, because of reduction.