# Distributed Key Generation

To confirm bridge transfers, validators use distributed key. Validators participate in distributed key generation (DKG) process to come up with individual secret key shares, which later allows them to create signatures from mutual account. No one has access to full private key, from which signatures are created.

### Key generation process

Once validators list is changed, due to [staking](../validation/becoming-a-validator.md) or [slashing](../validation/slashing.md), they participate in four rounds of key generation. Each next round requires completion of previous round by all the DKG participants. Results of each round is written to special [DKG smart contract](https://gitlab.com/chainfusion/chainfusion-contracts/-/blob/main/contracts/system/DKG.sol). Round result includes public data, for all participants, encrypted private data for other participants and encrypted intermediate data for validator itself. Intermediate data in contract allows to restore validator secret share, even if node is restarted from scratch and synchronized from the first block.

### Avoiding misbehaving validators

It's not a secret that we live in a not ideal world and we cannot be sure that validators will run their nodes with 100% uptime, or that validators won't submit any corrupted data as a round results.

To address this issue, validators, during DKG process can vote against misbehaving participants on-chain and restart the DKG process without them. Fortunately DKG algorithm that we use allows to identify misbehaving participants. If validators misbehave too often, they are being [slashed](../validation/slashing.md).
