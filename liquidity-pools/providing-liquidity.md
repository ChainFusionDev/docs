# Providing Liquidity

Some tokens are not originated from this bridge and already deployed on several blockchains. To make cross-chain transfers of these tokens possible, bridge needs liquidity. To incentivise providing of liquidity, bridge distributes part of collected fees during bridge transfers to liquidity providers.

### Providing liquidity

To provide liquidity, you can deposit to [liquidity pools contract](https://gitlab.com/chainfusion/chainfusion-contracts/-/blob/main/contracts/bridge/LiquidityPools.sol) with any supported token.

### Calculating rewards

Liquidity rewards depends on liquidity pool fee, transfer volume of provided token and relative share of provided liquidity between other liquidity providers.

Let's say you provided **1000 USDT** on Ethereum liquidity pool, which is **5%** of all liquidity provided to **USDT** on this chain (relative to other liquidity providers). Some bridge user transfers **100 USDT** from other chain to Ethereum. In case liquidity pool fee is **1%**, you will get `(100 USDT * 1%) * 5%`, resulting in **0.05 USDT** of rewards on this transaction. More volume goes through the pool, more rewards you receive.

### Withdrawing rewards

Liquidity pools do not have any limitation on when or how much liquidity provider can withdraw from it.

