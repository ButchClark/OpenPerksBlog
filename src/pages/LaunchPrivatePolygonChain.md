
#  Install prerequisite software:

1. Install Homebrew: Follow the instructions at https://brew.sh/
1. Install Node.js: Run brew install node
1. Install Go: Run brew install go
1. Install Truffle: Run npm install -g truffle

# Set up a private Polygon blockchain:
1. Clone the Polygon SDK repository: git clone https://github.com/0xPolygon/polygon-sdk.git
1. Change to the polygon-sdk directory: cd polygon-sdk
1. Build the Polygon SDK: make
1. Create a new Polygon blockchain configuration file: ./build/polygon-sdk server --data-dir ./data --config ./config.json
1. Modify the configuration file to add validators and other required settings for your permissioned network.

# Start the private Polygon blockchain: ./build/polygon-sdk server --config ./config.json
1. Deploy a smart contract on the private Polygon blockchain:
1. Create a new Truffle project: truffle init
1. Update the truffle-config.js file to include the private Polygon blockchain network configuration.

# Write a Smare Contract
1. Write a smart contract in Solidity and save it as a .sol file in the contracts directory.
1. Create a migration script in the migrations directory to deploy the smart contract.
1. Deploy the smart contract: truffle migrate --network <your_private_network_name>

# Set up a bridge between the private Polygon blockchain and the Polygon mainnet:
1. Clone the ChainBridge repository: git clone https://github.com/ChainSafe/chainbridge.git
1. Change to the chainbridge directory: cd chainbridge
1. Build ChainBridge: make build
1. Configure ChainBridge with the required settings for the private Polygon blockchain and the Polygon mainnet.
1. Start the ChainBridge: ./build/chainbridge --config <your_bridge_config_file>

# Deploy a token contract on both the private Polygon blockchain and the Polygon mainnet:
1. Create an ERC-20 token contract in Solidity for both networks.
1. Deploy the token contracts on both networks using Truffle, similar to Step 3.
1. Configure the bridge to handle token transfers:
1. Register the token contracts on both networks with the bridge.
1. Set up event listeners to watch for transfer events on both networks.
1. Implement handlers to process token transfers between the networks.
 
# Test the bridge:
1. Perform token transfers between the private Polygon blockchain and the Polygon mainnet to ensure the bridge is working correctly.


This is a high-level overview, and the specific implementation details may vary based on your requirements. Make sure to follow best practices for security and reliability when building your permissioned Polygon blockchain and bridge.




# --------
Actual cmds:


```
./polygon-edge polybft-secrets --insecure --data-dir test-chain- --num 4
```


```
./polygon-edge manifest \
--validators-path ./ \
--validators-prefix test-chain- \
--path ./manifest.json \
--premine-validators 100
```


```
./polygon-edge genesis \
--block-gas-limit 10000000 \
--epoch-size 10 \
--mintable-native-token
--consensus polybft \
--premine 0x92030Ba096Fa28E2A05892f6443c1BcC9e35308B:1000000 \
--bridge-json-rpc http://127.0.0.1:8545 \
--manifest ./manifest.json
```

## Start the private Polygon blockchain 1:
```
./polygon-edge server --data-dir ./test-chain-1 \
--chain ./genesis.json \
--grpc-address :10000 \
--libp2p :30301 \
--jsonrpc :10002 \
--seal
```

## Start the private Polygon blockchain 2:
```
./polygon-edge server --data-dir ./test-chain-2 \
--chain ./genesis.json \
--grpc-address :20000 \
--libp2p :30302 \
--jsonrpc :20002 \
--seal
```


## Start the private Polygon blockchain 3:
```
./polygon-edge server --data-dir ./test-chain-3 \
--chain ./genesis.json \
--grpc-address :30000 \
--libp2p :30303 \
--jsonrpc :30002 \
--seal
```

## Start the private Polygon blockchain 4:
```
./polygon-edge server --data-dir ./test-chain-4 \
--chain ./genesis.json \
--grpc-address :40000 \
--libp2p :30304 \
--jsonrpc :40002 \
--seal
```
