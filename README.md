# Bridge Overview

ChainFusion is a decentralized bridge that provides fast, cheap and secure cross-chain communication, like sending assets between blockchains. We strongly believe that bridges should be decentralized and trustless, everyone should be able to become a validator and secure the bridge.

Recent events show that current cross-chain solutions are highly vulnerable, sometimes it's enough to compromise few private keys in order to steal all locked value. Risks increase with centralized setups, where only bridge operating company decides who could become a validator.

### Decentralizing the Bridge

On vast majority of the blockchains, to make transaction it's enough to create a valid ECDSA signature using private key. [Recent findings](https://eprint.iacr.org/2020/540) in cryptology propose a solution on how to make such signature by cooperation of any number of parties, without knowing private key. It also allows to identify parties that do not cooperate, effectively allowing to slash (ban) them from being validators using automated voting performed by nodes.

Using algorithm mentioned above, validators generate distributed key by performing several communication rounds between each other. After last round complete, each party derives his own secret key share. This key share allows honest majority of participants to create valid transaction signatures from mutual public key. This mutual public key has the rights to perform bridging actions, like sending assets on destination chain to receiver who deposited asset on source chain. To make this process happen, validators constantly monitor events on each blockchain supported by bridge and then perform signing rounds in cooperation with other validators. At the end of signing rounds, validators compose valid threshold ECDSA signature for transaction.

### Making bridging cheap

In bridges with setup of more than one validator, usually on-chain signature is used. It's costly to check signatures on-chain when number of validators increases, each new signature verification consumes transaction fee. More validators, means more signatures to verify, which means bigger on-chain confirmation costs, resulting in higher bridge fees.

Threshold ECDSA allow us to compose one single signature using majority of validators. It's much cheaper to validate single signature and it does not affect security of validation.

### Supported operations

Currently bridge supports ERC-20 token transfers, our team constantly expands list of supported blockchains and tokens. We plan to also support NFTs and arbitrary data transfer between blockchains soon.

### Ternopil testnet links

We have recently launched Ternopil test network of ChainFusion. Below you can find useful URLs to explore the project.

| Name              | URL                                                                  |
| ----------------- | -------------------------------------------------------------------- |
| Explorer          | [https://explorer.chainfusion.org](https://explorer.chainfusion.org) |
| RPC API           | [https://rpc.chainfusion.org](https://rpc.chainfusion.org)           |
| Websocket RPC API | [https://wc-rpc.chainfusion.org](https://rpc.chainfusion.org)        |
