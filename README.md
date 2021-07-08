# Homework_18_Knife1

## Introduction

This is the walkthrough for creating a test blockchain network, in this example we're assuming this network will be used for a small private bank. 

### First

We must have the appropriate installations on our drive. Geth implements Ethereum protocol. The link for installation for your specific OS can be found [here](https://geth.ethereum.org/).
Create a new folder that allows easy access on your desktop. Navigate to where geth was installed on your OS. Move the geth files to your new folder. This will allow geth to operate properly when you create your test blockchain. 

#### Blockchain Creation
We're going to create two nodes that will mine and communicate with each other. Navigate to the folder you created that now houses geth with your command line. Now we're going to create the two nodes. Type this code into the CL.
`./geth --datadir node1 account new`
Follow all the prompts, and in a notepad file, save all passwords, private/public keys. It's very important to save your passwords!
Let's create the second node. Type this code into the CL.
`./geth --datadir node2 account new`
Same as before, follow all prompts and save all important information in the notepad file. 
Now we're going to generate our blockchain genesis block using puppeth.
  1. In the same folder as geth on the CL, run this code. 
  `./puppeth`
  2. Follow the prompts to create a new network and create a new genesis block. This is the beginning of your blockchain. Name your network, and for good measure save the name and all passwords in the same notepad file as your node information. Choose the `Proof of Authority (Clique)` consensus algorithm. 
  3. Under accounts to seal, paste both account addresses. These start with 0x and should be saved in your notepad file. 
  4. Paste them in accounts to pre-fund as well. 
  5. You can choose `no` for pre-funding the accounts with wei. This keeps the genesis cleaner.
  6. Complete the prompts and then choose `Manage existing genesis`.
  7. Export genesis configurations, some might fail but the only one that is important is the `networkname.json`
Now we must initialize each node we created earlier. Open a new terminal and navigate to your folder that geth is in. Files for your nodes should've been created in this folder when you generated them earlier. 
  1. Type this line of code to initialize your nodes. Do each one seperately. 
    `./geth --datadir node1 init networkname.json`
    `./geth --datadir node2 init networkname.json`
Let's begin mining! In two seperate terminals for each node, run the lines of code below. Type your password in for each, there won't be a prompt for them or show them when you type them out, but the CL will be waiting for it. 
`./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock`
 SEALER_ONE_ADDRESS  is the line for node1 that starts with 0x.
 Then run in the other terminal window
 `./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock`
 SEALER_ONE_ENODE_ADDRESS is the enode address for node 1. 
 Both nodes should now be running. We can test them on the MyCrypto, which you can install on your OS [here](https://mycrypto.com/).
 Open the app, and click "change network" in the lower lefthand corner. 
  1.Click "Add custom node", and enter the name of the network you created earlier. 
  2. Make sure you choose "Custom" in the "Network" column to expand more options. 
  3. Use ETH in the currency box.
  4. In the Chain ID box, type the chain id you made for your network during genesis creation.
  5. n the URL box type `http://127.0.0.1:8545`  This points to the default RPC port on your local machine.
  6. Save your custom node. 

Now we can test our network. 
  1. Click "View and Send" and then click "Keystore file".
  2. Click "Select Wallet File" and navigate to the keystore directory in your Node1 folder. This should start with UTC.
  3. Type your node password and click unlock. This opens your wallet file in MyCrypto.
  4. Let's send ETH to the second node! In the "To Address" box, paste the account address for Node2 (0x...) and choose an amount of ETH to send.
  5. Click Send!
 Let's check our transaction status! 
  1. Click "Check TX Status"
  2. The transaction should go from "Pending" to "Successful" in the amount of time you chose earlier when creating creating your new genesis block. That's the amount of time it takes to mine.

You just created a blockchain! Woohoo!

 
