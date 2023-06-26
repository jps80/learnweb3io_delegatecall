# learnweb3io_delegatecall
in this project you can learn about delegatecall method in Solidity and its risks
This code is part of https://learnweb3.io/degrees/ethereum-developer-degree/senior/run-code-from-other-contracts-inside-your-own-using-delegatecall/ 

## DelegateCall

.delegatecall() is a method in Solidity used to call a function in a target contract from an original contract. However, unlike other methods, when the function is executed in the target contract using .delegatecall(), the context is passed from the original contract i.e. the code executes in the target contract, but variables get modified in the original contract.

.delegatecall() is heavily used within proxy (upgradeable) contracts. Since smart contracts are not upgradeable by default, the way to make them upgradeable is typically by having one storage contract containing an address for an implementation contract that does not change. If you wanted to update your contract code, you change the address of the implementation contract to something new. The storage contract makes all calls using .delegatecall() which allows to run different versions of the code while maintaining the same persisted storage over time, no matter how many implementation contracts you change. Therefore, the logic can change, but the data is never fragmented.

## Attack using delegatecall

But, since .delegatecall() modifies the storage of the contract calling the function, there are some nasty attacks that can be designed if .delegatecall() is not properly implemented

## Quickstart

```node
npm install
npx hardhat test
```