# Transfer Confirmation

Validators constantly monitor bridging events on all supported blockchains. Once they see a transfer event on **source** chain, they start the process of 6 rounds of transaction signing on **destination** chain. This transaction confirms that all the validators seen this event and transfer really took place. After transaction is executed, bridge user receives his funds on **destination** chain.

Not every validator needs to be online when there is need to create mutual transaction signature. This is achieved using threshold signatures, meaning that, let's say only 20 of 30 validators need to  participate in signing, while still allowing them to crate valid mutual signature.

### Threshold signing process

FIrst, before signing something, validators need to decide, what to sign first, as there could be few pending bridge transactions.
