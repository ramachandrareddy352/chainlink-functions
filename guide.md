https://usechainlinkfunctions.com/

https://github.com/smartcontractkit/functions-hardhat-starter-kit

0. Get MATIC and LINK https://faucet.polygon.technology/ https://faucets.chain.link/mumbai

1. Install node and deno

```shell
curl -fsSL https://deno.land/x/install/install.sh | sh
```

2. Install

```shell
git clone https://github.com/smartcontractkit/functions-hardhat-starter-kit
npm i
```

3. Get github token

4. Get polygon mumbai rpc url alchemy

5. Get polygon scan api key https://polygonscan.com/

6. Get metamask private key

```shell
# Set encryption password
npx env-enc set-pw

npx env-enc set
npx env-enc view
npx env-enc remove ENV_NAME
npx env-enc remove-all

GITHUB_API_TOKEN
POLYGON_MUMBAI_RPC_URL
POLYGONSCAN_API_KEY
PRIVATE_KEY
```

### Review code

calculation-example.js contracts/FunctionsConsumer.sol Functions-request-config.js

### Commands

```shell
# Simulate script
npx hardhat functions-simulate-script

# Deploy
npx hardhat functions-deploy-consumer --network polygonMumbai --verify true

# 0xBF6ADb9C154Eb708De90B6a9d12848b090322F92

# 0x604630Fab10baa3cC8BBBC383cf4ddeb16CEE4C0
# Check contract verified
# https://mumbai.polygonscan.com/

# Create subscription - must deposit mimimum 2 LINK on testnet
# Check subscriptions
# https://functions.chain.link/mumbai
CONTRACT_ADDR=0xBF6ADb9C154Eb708De90B6a9d12848b090322F92
npx hardhat functions-sub-create --network polygonMumbai --amount 15 --contract $CONTRACT_ADDR

# Fund more
SUB_ID=3156
npx hardhat functions-sub-fund --network polygonMumbai --amount 10 --subid $SUB_ID

# Run functions (FunctionConsumers.sendRequest)
npx hardhat functions-request --network polygonMumbai --contract $CONTRACT_ADDR --subid $SUB_ID --simulate true

# Check request transaction
https://mumbai.polygonscan.com/tx/0x6812adc9d70278b36df3f8a68a728e4bff5a80e2363b434ccd8584810d74dc3f
# Find response transaction from https://functions.chain.link/mumbai

# Check contract and decode bytes
```

### Weather API example

1. Execute `weather-api-example.js`
2. Copy `calculation-example.js` and create `weather-func.js`
3. Modify `Functions-request-config.js`
4. Setup OPEN_WEATHER_API_KEY into env-enc

```shell
npx env-enc set-pw
npx env-enc set
```

5. Execute weather API

```shell
# Simulate
npx hardhat functions-simulate-script

# Execute
CONTRACT_ADDR=0xBF6ADb9C154Eb708De90B6a9d12848b090322F92
SUB_ID=3156
npx hardhat functions-request --network polygonMumbai --contract $CONTRACT_ADDR --subid $SUB_ID --simulate true
```

6. Call contract, get data, decode data