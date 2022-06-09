# Transfer Confirmation

Validators constantly monitor bridging events on all supported blockchains. Once they see a transfer event on **source** chain, they start the process of 6 rounds of transaction signing on **destination** chain. This transaction confirms that all the validators seen this event and transfer really took place. After transaction is executed, bridge user receives his funds on **destination** chain.

Not every validator needs to be online when there is need to create mutual transaction signature. This is achieved using threshold signatures, meaning that, let's say only 20 of 30 validators need to  participate in signing, while still allowing them to crate valid mutual signature.

### Keep-alive validator messages

Validators send keep-alive messages peer-to-peer to other validator nodes to report that they are online and able to participate is signing. When validators start to process bridge transfer, they use list of validators that recently send keep-alive messages to form list of active validators.

### Threshold signing process

Each active validator node, maintains pool of unconfirmed transfers, during monitoring of supported blockchains.

Unconfirmed transfers go through 6 round distributed signing process by active validator nodes. During which it's decided what to sign (which transfer, using which gas price and other transaction details), so resulting transaction hash is deterministic. Once transaction is signed, it's being broadcasted by validators on **destination** chain.

Validators don't need to have any amount of native currency on destination blockchains. As all the transactions are being created collectively, from the mutual address. This mutual address is funded from bridge transfer fees.
