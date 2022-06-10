# Slashing

During validation process, participants actively monitor each other to check if everyone cooperate according to consensus rules. In case validators nodes see any non-cooperative participant, they vote against him on-chain, which may result in slashing. During slashing misbehaving participant is removed from validator list and his stake is distributed to other validators as a reward for keeping bridge secure.

### Validator responsibilities

List of main validator responsibilities:

* producing new blocks in ChainFusion network
* participating in DKG process when validators list is changed
* participating in threshold signatures creation to confirm bridge transfers
* slashing misbehaving validators
* sending keep-alive packets to P2P network of validator nodes

