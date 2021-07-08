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
  8. 
