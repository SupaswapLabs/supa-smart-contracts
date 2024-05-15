# SupaSwap Exchange Protocol Deployment Guide for Beginners

This guide walks you through deploying a basic PancakeSwap exchange protocol using a scenario approach. 

**Important:** This is a simplified guide for educational purposes only. Deploying real contracts involves financial risks and requires thorough understanding and security audits.

**Who is this for?**

This guide is for beginners interested in understanding the deployment process of a PancakeSwap-like exchange protocol. You'll need some basic familiarity with smart contracts and Ethereum development.

**Characters:**

- Alice: The primary user deploying the contracts.
- Bob, Carol, David, Erin: Other users interacting with the exchange.

**Steps:**

**Deployment:**

1. **Factory Contract:**
    - Deploy the `PancakeFactory.sol` contract.
    - Set `_feeToSetter` to Alice's address (who collects fees).
    - Deploy by Alice.

2. **Wrapped Native Token:**
    - If not already deployed, deploy a wrapped token representing the native currency (e.g., WBNB).
    - Deploy by Alice (optional, might already exist).

3. **Router Contract:**
    - Deploy the `PancakeRouter.sol` contract.
    - Provide the factory contract address, wrapped token address.
    - Deploy by Alice.

4. **ZapV1 (Optional):**
    - Deploy the `PancakeZapV1.sol` contract (enables adding liquidity with one token).
    - Provide wrapped token address, router contract address, and maxZapReverseRatio.
    - Deploy by Alice (optional).

**Scenario Mocking:**

1. **Deploy Mock Tokens:**
    - Deploy two ERC20 token contracts (`MockERC20.sol`) representing Token A and Token C.
    - Use the wrapped native token as Token B.
    - Deploy by Alice.

2. **Create Liquidity Pools (LP Tokens):**
    - Use the factory contract to create three LP token pairs:
        - pairAB (Token A & Wrapped Native Token)
        - pairBC (Wrapped Native Token & Token C)
        - pairAC (Token A & Token C)
    - Deploy by Alice.

3. **Verify LP Token Supply:**
    - Check if the initial supply of each LP token is zero.

4. **Mint and Approve Tokens:**
    - For each user (Alice, Bob, Carol, David, Erin):
        - Mint 2,000,000 tokens of A and C to their addresses.
        - Approve spending of all tokens for the router and Zap contracts (if used).


## Normal Cases for Liquidity Provision and Zap Ins Documentation

This document describes the normal cases for liquidity provision and zap ins using the provided code.

### Liquidity Provision

The code demonstrates liquidity provision for three different pairs:

* **tokenA/tokenC**: Add equal amounts of tokenA and tokenC to the liquidity pool using `addLiquidity`.
* **tokenA/BNB**: Add tokenA and an equivalent amount of BNB to the liquidity pool using `addLiquidityETH`.
* **tokenC/BNB**: Add tokenC and an equivalent amount of BNB to the liquidity pool using `addLiquidityETH`.

Each scenario verifies the expected changes in token balances, LP token balances, and total supply of the LP token.

### Zap Ins

The code demonstrates zap ins for various scenarios:

* **Zap In with tokenA (pair tokenA/tokenC)**: Adds tokenA directly to the LP token in exchange for a proportional amount of the LP token.
* **Zap In with BNB (pair BNB/tokenC)**: Adds BNB directly to the LP token in exchange for a proportional amount of the LP token.
* **Zap In Rebalancing with BNB (pair BNB/tokenC)**: Adds both BNB and tokenC to the LP token while maintaining a specific ratio between the tokens.
* **Zap In Rebalancing with tokens (tokenA/tokenC)**: Adds both tokenA and tokenC to the LP token while maintaining a specific ratio between the tokens.
* **Zap Out to token (tokenA/tokenC)**: Removes LP tokens and receives tokenA in return.
* **Zap Out to BNB (BNB/tokenC)**: Removes LP tokens and receives BNB in return.

Each scenario verifies the expected changes in token balances, LP token balances, and the amount of tokens received or paid.

### Additional Notes

* The code includes checks for slippage to ensure users receive a minimum amount of tokens from zap ins and zap outs.
* The code includes checks for invalid token combinations and trade directions to prevent unexpected behavior.


**Remember:**

- This is a simplified example. Real deployments involve more complexity and security considerations.
- Always test thoroughly and understand the risks before deploying real contracts.
- Consider seeking professional help for complex deployments.

## Additional Resources

- PancakeSwap Documentation: [https://docs.pancakeswap.finance/](https://docs.pancakeswap.finance/)
- Smart Contract Development Tutorials: [https://consensys.io/academy](https://consensys.io/academy)
- Ethereum Documentation: [https://ethereum.org/developers/docs](https://ethereum.org/developers/docs)
- https://forum.openzeppelin.com/t/using-the-maximum-integer-in-solidity/3000
- https://forum.openzeppelin.com/t/unable-to-deploy-from-remix-invalid-opcode-push0/38054/6

uint256 MAX_INT = 115792089237316195423570985008687907853269984665640564039457584007913129639935

## Rough Work

pairAB = {
	"0": "address: pair 0x7E3448a8a5B5372061e979Bae926b94e527f859F"
}


pairBC = {
	"0": "address: pair 0x3db5DE1FB08B9b5a7537659c73b9cb1834451193"
}


pairAC = {
	"0": "address: pair 0x95d8145Ef95b86Fef938E4506e67309F46a1A864"
}


## SCS Testnet

Account 1 => 0xB26444db4062440543919361d7A19db1495F5785 (alice)
Account 2 => 0xF529878AF3e043479D831398C0F47A06B12E60b2 (bob)


FACTORY: 0x9d00348e4fcd5CF5Bee24611421d126a2fff47D2
INIT_CODE_PAIR_HASH: 0xa253c5010701b4a0bee32702f070ba5a04ad9ce0fad1b4778b7fd756ae4ccdfc

WTSCS: 0xFb19C1592F52Ce3798BE3183a16386ca1e548550 (Token B)

Router: 0xFFA077589D42e95453EdE577c80034bA6df84427

ZapV1: 0x08D5C564ca26D7A4e72b13F707B4cb2b03936266

Supa Token A: 0x8906B89901Cdc8Ed2eAa4B7E3A4FFF95dbe94Ad1

Supa Token C: 0xF96CaBf3BF1E37e8d97adBCb7Ccea2cC89C9363F


pairAB: 0xa85dB444970bC837cE139fd03BF6e922aCe8E540
pairBC: 0x5460E701F5Ce5bf2b4a39F3686630E7922e312D8
pairAC: 0x95576F5d35cEDce0DB3720a748A19Bd76ED62228

```json
MultiCall3: {
      address: '0x873FBd9D050A0EB69adf53a29df235252A34d869',
      blockCreated: 7894188,
      tx: 'https://testnetscan.scschain.com/tx/0x261a4b7bcd6af0678789b7ef5576ab21faf7c4c28b50d7fcc55ce8dfbef150ad'
}
```

**bsc scan:** https://bscscan.com/address/0xca11bde05977b3631167028862be2a173976ca11#code



## Resources

https://blog.cryptostars.is/how-to-build-a-decentralized-exchange-dex-like-uniswap-e31bb03062b3

https://medium.com/coinmonks/build-your-own-decentralized-exchange-like-uniswap-v1-aa9c91b36cc

https://medium.com/coinmonks/21dayssoliditychallenge-day-9-unleash-the-power-of-decentralized-finance-building-a-3875b53765d3

https://github.com/AzureKn1ght/Defi-Exchange

