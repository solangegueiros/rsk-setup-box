# RSK Truffle Token Box

Truffle box with everything you need to start creating a token using Open Zeppelin smart contracts library in Truffle framework, connected to a RSK local node or RSK testnet.
It includes network configurations for local node (regtest) and Testnet.

## Installation

1. Install Truffle globally

    ```shell
    npm install -g truffle
    ```

2. Create a new folder. 
For example, create the folder `myproject`.
Navigate to the folder in the terminal.

    ```shell
    mkdir rsk-project
    cd rsk-project
    ```

3. Run the unbox command. 
This also takes care of installing the necessary dependencies.

    ```shell
    truffle unbox rsksmart/rsk-setup-box
    ```

4. Run the development console.

    ```shell
    truffle develop
    ```

5. Compile and migrate the smart contracts. 
Note inside the development console we don't preface commands with `truffle`.

    ```shell
    compile
    migrate
    ```

**NOTE**: This truffle box is not a complete dapp.

## RSK

### RSK regtest (Local node)

- To install and run a local node, follow [these instructions](https://developers.rsk.co/quick-start/step1-install-rsk-local-node/ "Install RSK local node - RSK developers portal").

### Setup an account & get R-BTC

- Create a wallet using the instructions in [account based RSK addresses - RSK developers portal](https://developers.rsk.co/rsk/architecture/account-based/ "account based RSK addresses - RSK developers portal").
- Paste the wallet mnemonic in the file `.secret`, located in the folder project, and save it.
- For the RSK Testnet, get tRBTC from [our faucet](https://faucet.testnet.rsk.co/).
- For the RSK Mainnet, get RBTC from [an exchange](https://www.rsk.co/#exchanges-rsk).

In `truffle-config.js`, note that we are using `HDWalletProvider` with RSK Networks derivations path:
- RSK Mainnet dpath: `m/44’/137’/0’/0`
- RSK Testnet dpath: `m/44’/37310’/0’/0`

For more information check [RSKIP57](https://github.com/rsksmart/RSKIPs/blob/master/IPs/RSKIP57.md).

### Setup the gas price

Get the current gas price of the testnet network, and save to `.gas-price-testnet.json`.

In your project folder, run this cURL command:

```shell
curl https://public-node.testnet.rsk.co/2.0.1/ -X POST -H "Content-Type: application/json" --data '{"jsonrpc":"2.0","method":"eth_gasPrice","params":[],"id":1}' > .gas-price-testnet.json
```

You should receive a response similar to the following in the file:

```json
{"jsonrpc":"2.0","id":1,"result":"0x3938700"}
```

The result value is presented in hexadecimal.

For more information about the **Gas** and **minimumGasPrice** please go [here](https://developers.rsk.co/rsk/rbtc/gas/ "Gas - RSK developers portal").

### Connect to RSK regtest (local node)

First ensure you have a local node running.

```shell
truffle console
```

> Any network defined with the name `development` is considered the default network.

### Connect to RSK testnet

```shell
truffle console --network testnet
```
### Test the connection to RSK network

On any of the networks, run this commands in the Truffle console:

#### Block number
Shows the last block number.

```javascript
(await web3.eth.getBlockNumber()).toString()
```
#### Network ID

To get the network ID, run this command:

```javascript
(await web3.eth.net.getId()).toString()
```

For the local node, the network ID is `33`.

![getId local](/assets/img/tutorials/setup-truffle-oz/image-31.png)

And for testnet, it is `31`.

![getId testnet](/assets/img/tutorials/setup-truffle-oz/image-32.png)

### Compile and migrate the smart contracts. 

Note that inside the development console, we don't preface commands with `truffle`.

```shell
compile
migrate
```

### Exit Truffle console

In the Truffle console, enter this command to exit the terminal:

```shell
.exit
```

### Where to go from here

At this point, we have installed all requirements and created an empty project using Truffle framework and Open Zeppelin smart contracts library,
connected to both an RSK local node (Regtest) and the RSK Testnet.

We have not developed anything yet,
but you are now ready to move on to the next tutorials,
where we will develop some very cool projects!

Choose any of these to tutorials to begin:

- [Create your first Token](https://developers.rsk.co/tutorials/tokens/create-a-token/ "Create your first Token - RSK developers portal")
- [Create your own collectable token](https://developers.rsk.co/tutorials/tokens/create-a-collectable-token/ "Create your own collectable token - RSK developers portal")

