# SupaSwap Testing and Simulation Environment (TSE)

From [BSCScan](https://bscscan.com/):

```typescript
const WBNB_ADDRESS = "0xbb4cdb9cbd36b01bd1cbaebf2de08d9173bc095c";
const BUSD_WBNB_PAIR = "0x58f876857a02d6762e0101bb5c46a8c1ed44dc16"; // created block 589414
const USDT_WBNB_PAIR = "0x16b9a82891338f9ba80e2d6970fdda79d1eb0dae"; // created block 648115

// token where amounts should contribute to tracked volume and liquidity
const WHITELIST: string[] = [
  "0xbb4cdb9cbd36b01bd1cbaebf2de08d9173bc095c", // WBNB -> https://bscscan.com/address/0xbb4cdb9cbd36b01bd1cbaebf2de08d9173bc095c#code
  "0xe9e7cea3dedca5984780bafc599bd69add087d56", // BUSD -> https://bscscan.com/address/0xe9e7cea3dedca5984780bafc599bd69add087d56#code
  "0x55d398326f99059ff775485246999027b3197955", // USDT -> https://bscscan.com/address/0x55d398326f99059ff775485246999027b3197955#code
  "0x8ac76a51cc950d9822d68b83fe1ad97b32cd580d", // USDC ->
  "0x23396cf899ca06c4472205fc903bdb4de249d6fc", // UST
  "0x7130d2a12b9bcbfae4f2634d864a1ee1ce3ead9c", // BTCB
  "0x2170ed0880ac9a755fd29b2688956bd959f933f8", // WETH -> https://bscscan.com/address/0x2170ed0880ac9a755fd29b2688956bd959f933f8#code
];
```

## SCS Chain

**Testnet:**

- WTSCS_ADDRESS: (address) -> created block 648115
- USDTS_ADDRESS: (address) -> created block 648115

**Mainnet:**

- WSCS_ADDRESS: (address) -> created block 648115
- USDTS_ADDRESS: (address) -> created block 648115

# Setup Test Environment

- Install ganache (gui or cli)
- Connect metamask to ganache (for ease of use)
- Import ganache test accounts into metamask
- Connect Remix IDE to metamask (for compiling, deploying and testing of contracts)

**PS:**

- For a native wrapped token like SCS, instead of calling deposit, you can send to the contract address directly

- 1 wad == 1 \* 10^18

- deposit => send SCS or TSCS to contract address
- withdraw => withdraw(wad) OR approve(contractAddress, wad) and then withdraw(wad)

## Resources

- https://superexchain.github.io/
- https://scschain.com/
- https://bscscan.com/
- https://cn.etherscan.com/
