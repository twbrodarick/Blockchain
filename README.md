# Testnet Creation Instructions - GitBash
* GitBash command inputs referenced "< >"

## Create New Nodes
1. <./geth account new --datadir node01>
* node names are chosen by developer
2. <./geth account new --datadir node02>
* public addresses will be created for each node
* passwords are chosen by developer. Passwords were set to '1234' for each node in this testnet. Our experience shows numeric passwords have had better success in sealing blocks than alpha passwords

## Create New Network
1. <./puppeth>
2. "Please specify a network name":  <zworld>
* 'zworld' is the network name chosen for our testnet

## Create Genesis Block
1. "What would you like to do? (default = stats):  <2>  Configure new genesis
2. "What would you like to do? (default = create):  <1>  Create new genesis from scratch
3. "What consensus engine to use? (default = clique):  <2>  Clique - proof-of-authority
4. "How many seconds should blocks take? (default = 15):  <enter>
5. "Which accounts are allowed to seal?":  Input node public addresses separately without leading '0x' which will be pre-populated
6. "Which accounts are allowed to pre-fund?":  Repeat previous step
7. "Should the pre-compile-addresses ... be pre-funded with 1 wei (advisable=yes):  <no>
8. "Specify your chain/network ID if you want an explicit one (default = random):  <321>
* '321' was the network ID chosen for our testnet.
9. "What would you like to do? (default=stats):  <2>  Manage existing genesis
10. [menu options repeated from previous step]:   <2>  Export genesis configurations
11. "Which folder to save the genesis specs into? (default = current):  <enter> then <CTRL + C>
  
## Initialize Nodes
1. <./geth init zworld.json --datadir node01> 
2. <./geth init zworld.json --datadir node02>
* zworld and node01 and node02 reflect network name and node names selected by developer

## Run Node 1
1. <./geth --datadir node01 --unlock "0x3217c2f345FB50D5B939E6F6fd264e7d77324644" --mine --rpc --allow-insecure-unlock
* public address of node01 is pasted between ""
* allow-insecure-unlock is required for user with password to enter and show authority to mine on this blockchain
2. "Password: ":  <1234>
3. Once Node 1 is running, look for a line of code reading "Started P2P Networking":  copy the alpha-numeric sequence starting with "enode:"

## Run Node 2 (in a new GitBash terminal)
1. <./geth --datadir node02 --unlock "0x7b6870C454Df67a3026FbB9DE9Ce1b904Dd67EFD" --mine --port 30304 --bootnodes "enode: e142e01065b5b1494aa9aac3a64be0737eb8aeb627d0013039f3fa297ce725aa6aaa69da8514334b7e502a252f98e9e02571cde7f9a7b626c1fed44cb7de12b7@127.0.0.1:30303" --ipcdisable>
2. "Password: " prompt may not be obvious but type <1234> after running command above

# Adding Custom Network to MyCrypto
1. Change network to zworld (custom network) before attempting to login
2. Login with Keystore file from Node 1 and enter password <1234>
3. Under the network names: Select "Add Custom Node"
4. "Select Custom Node" Dialog Box: 
  * "Node Name":  <zworld>
  * "Network:  Drop-down to "Custom"
  * "Network Name":  <zworld>
  * "Currency":  <ETH>
  * "Chain ID":  <321>
  * "URL":  <http://127.0.0.1:8545
  * Save and & Use Custom Node
                                   
## Sending a Transaction from Custom Network
1. Select "Send Ether & Tokens at top of screen
2. Enter a valid public address in the "to" field
3. Enter number of tokens and crypto and select Send
4. Select "Tx Status" at bottom of screen to view transactions details including transaction hash
