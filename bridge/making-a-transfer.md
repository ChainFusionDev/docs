# Making a Transfer

ChainFusion bridge allows to transfer assets between various blockchains and makes it fast, cheap, secure in a decentralized fashion.

### Transferring assets using smart contract directly

To transfer assets from one blockchain to another, you would need to use [bridge contract's](https://gitlab.com/chainfusion/chainfusion-contracts/-/blob/main/contracts/bridge/Bridge.sol) `deposit()` function. Deposit function has four parameters:

* `token` - address of token to deposit, on the chain, you are transferring from
* `chainId` - identifier of blockchain you are transferring to
* `receiver` - address of receiver, you are transferring to (usually the same account you are transferring from)
* `amount` - amount of tokens to transfer through bridge

After you made a deposit, usually it takes few minutes for validators to confirm your transfer and compose transaction on destination chain.

### Transferring assets using Bridge UI

Bridge UI is in active development and expected to be available soon...
