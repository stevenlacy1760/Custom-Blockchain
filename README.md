# Custom-Blockchain

### Starting Blockchain Network

**Step 1** : Activate Conda enviroment

**Step 2** : cd into Blockchain tools and create nodes with  "**./geth account new --datadir node**". You will then be promted to input any password, write down password to remember for future access on both nodes. It will then give you public address for each node when created. Copy and past public address into .txt file onto computer for future setup.

**Step 3**: after nodes are created, run **./puppeth** command, you will then be prompted to name your network,input any network name. Click *configure new genesis*, then when prompted select *create new genesis from scratch*, next select *proof-of-authority*. Select *default* for seconds on how long blocks should take. When asked which account to seal, input both public addresses from the created nodes(0x) from step two, 1 at a time. Select *"No"* when asked to prefund with wei. Specify chain/network  ID or hit enter for random(make at least 4 digits minimum). *Genesis block should now say it was created*
##### Blocktime- is the time it takes to mine a block, BTC takes about 10 minutes on average while ETH takes between 10-20 seconds. The default blocktime for ETH is 15 seconds.
##### Chain ID - it's required when signing transactions, meaning transactions signed on the ETH network end up with a different hash than those signed on ETC. Before EIP-155, signed transactions on each network would look the same, and could be replayed.

**Step 4**: next we want to export block by selecting *2.Manage existing genesis* then again selecting *2.Export genesis configurations*, then hit enter to create .json files. Hit ctrl+c to exit puppeth.

**Step 5**: Initialize both nodes. Node 1 command to initialize is **./geth --datadir node1 init networkname.json**, repeat same command and replace node1 input with node2. Now nodes can be set for mining.

**Step 6**: in seperate terminals under blockchain tools run node1 command for mining with "**./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock**", even if there is no prompt to type password, input your password you entered earlier for node 1 then hit enter. Also scroll down until you see an enode address and copy and paste the entire address into node 1 txt. (Keep terminal open)

**Step 7**: open up another terminal under blockchain tools and set up rpc port for node 2 mining. input command **./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock** 
##### Your custom blockchain should now be running

### Setting up my crypto wallet

**Step 1**: open up mycrypto wallet and click change network, then select custom network. 
