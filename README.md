# ZWorld Testnet Instructions
* GitBash command inputs referenced "< >"

## Create New Nodes
1. <./geth account new --datadir node01>
2. <./geth account new --datadir node02>
* public addresses will be created for each node
* passwords set to 'zbank' for each node

## Create New Network
1. <./puppeth>
2. "Please specify a network name":  <zworld>
* 'zworld' is the network name chosen for our testnet

## Create Genesis Block
1. "What would you like to do? (default=stats):  <2>  Configure new genesis
2. "Which accounts are allowed to seal?":  Input node public addresses separately without leading '0x' which will be pre-populated
3. "Which accounts are allowed to pre-fund?":  Repeat previous step
4. "Should the pre-compile-addresses ... be pre-funded with 1 wei (advisable=yes):  <no>
5. "What would you like to do? (default=stats):  <2>  Manage existing genesis
6. [menu options repeated from previous step]:   <2>  Export genesis configurations
7. <CTRL + C>
  
## Initialize Nodes
  

