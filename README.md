# Custom-Blockchain

## Download software for setup
To get software for blockchain mining, follow these steps. 
[Blockchain and CryptoWallet setup](https://smu.bootcampcontent.com/SMU-Coding-Bootcamp/smu-dal-virt-fin-pt-08-2021-u-c/-/blob/master/01-Lesson-Plans/18-Blockchain/Supplemental/blockchain-install-guide.md)

### Starting Blockchain Network

**Step 1** : Activate Conda enviroment

**Step 2** : cd into Blockchain tools and create nodes with  "**./geth account new --datadir node**". You will then be promted to input any password, write down password to remember for future access on both nodes. It will then give you public address for each node when created. Copy and past public address into .txt file onto computer for future setup.

![node creation](https://user-images.githubusercontent.com/86683976/146997684-330b22fe-e776-4984-b3b0-1e9776666bd8.PNG)


**Step 3**: after nodes are created, run **./puppeth** command, you will then be prompted to name your network,input any network name. Click *configure new genesis*, then when prompted select *create new genesis from scratch*, next select *proof-of-authority*. Select *default* for seconds on how long blocks should take. When asked which account to seal, input both public addresses from the created nodes(0x) from step two, 1 at a time. 
Select *"No"* when asked to prefund with wei. Specify chain/network  ID or hit enter for random(make at least 4 digits minimum). *Genesis block should now say it was created*
##### Blocktime- is the time it takes to mine a block, BTC takes about 10 minutes on average while ETH takes between 10-20 seconds. The default blocktime for ETH is 15 seconds.
##### Chain ID - it's required when signing transactions, meaning transactions signed on the ETH network end up with a different hash than those signed on ETC. Before EIP-155, signed transactions on each network would look the same, and could be replayed.



**Step 4**: next we want to export block by selecting *2.Manage existing genesis* then again selecting *2.Export genesis configurations*, then hit enter to create .json files. Hit ctrl+c to exit puppeth.![export](https://user-images.githubusercontent.com/86683976/146998346-085ed1cc-a8c0-470c-beb5-8bec6a57977b.PNG)


**Step 5**: Initialize both nodes. Node 1 command to initialize is **./geth --datadir node1 init networkname.json**, repeat same command and replace node1 input with node2. Now nodes can be set for mining.![init node](https://user-images.githubusercontent.com/86683976/146998470-5f6768a3-b727-4e28-83f0-bfaecb7c26b7.PNG)


**Step 6**: in seperate terminals under blockchain tools run node1 command for mining with "**./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock**", even if there is no prompt to type password, input your password you entered earlier for node 1 then hit enter. Also scroll down until you see an enode address and copy and paste the entire address into node 1 txt. (Keep terminal open)![node 1 mine](https://user-images.githubusercontent.com/86683976/146998631-303fa16d-76a9-4c68-b5e6-1959b83e991a.PNG)


**Step 7**: open up another terminal under blockchain tools and set up rpc port for node 2 mining. input command **./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock** 
##### Your custom blockchain should now be running
![image](https://user-images.githubusercontent.com/86683976/146998724-af998eb7-763a-455e-a968-f7ddfeb68c76.png)

### Setting up my crypto wallet

**Step 1**: open up mycrypto wallet and click change network, then select custom network. In the dropdown scroll to custom. Type ETH in the Currency box. In the Chain ID box, type the chain id you generated during genesis creation. In the URL box type: http://127.0.0.1:8545.  This points to the default RPC port on your local machine, click Save & Use Custom Node.<img width="400" alt="custom-node" src="https://user-images.githubusercontent.com/86683976/146999640-6b1e4ec5-e27f-43ea-8af1-7fecf421d3f5.png">

**Step 2**: Select the View & Send option from the left menu pane, then click Keystore file. On the next screen, click Select Wallet File, then navigate to the keystore directory inside your Node1 directory, select the file located there, provide your password when prompted and then click Unlock. It should then open your wallet.

**Step 3**: In the To Address box, type the account address from Node2, then fill in an amount of ETH. Confirm the transaction by clicking *Send Transaction*, and the *Send* button in the pop-up window. Your transaction should be succesful.![transaction succesful](https://user-images.githubusercontent.com/86683976/147003938-cd80a600-3590-4407-847c-7aa291800d90.PNG)
