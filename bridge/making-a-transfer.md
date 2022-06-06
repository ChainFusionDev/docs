# Making a Transfer

To transfer assets from one blockchain to another, you would need to use **Bridge** contract's `deposit()` function. Deposit function has four parameters:

* token - address of token to deposit, on the chain, you are transferring from
* chainId - identifier of blockchain you are transferring to
* receiver - address of receiver, you are transferring to (usually the same account you are transferring from)
* amount - amount of tokens to transfer through bridge

After you made a deposit, usually it takes few minutes for validators to confirm your transfer and compose transaction on destination chain.
