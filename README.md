# Solana NFT and Token Creation Guide

This guide provides step-by-step instructions for creating Solana NFTs and tokens using Metaplex's Candy Machine, and SPL tokens.

## Prerequisites
- **[NodeJs:](https://nodejs.org/)** Version 16 or higher
- **[Install Solana CLI:](https://docs.solana.com/cli/install-solana-cli)** If you haven't already, follow the Solana CLI Installation Guide to install the Solana Command Line Interface (CLI).
- **[Set up Phantom wallet:](https://phantom.app/)** Download and create a new wallet or use an existing one. You'll need this wallet to interact with Solana and perform the tasks below.
- **[Sugar CLI:](https://github.com/metaplex-foundation/sugar/releases/tag/v1.2.2)** Legacy Version, V1.x

##  Clone the project
- Open your terminal.
```bash
    git clone https://github.com/metaplex-foundation/candy-machine-ui
    cd spl-token-nft-mint
```
## Generate a Solana Keypair
```bash
   solana-keygen new --outfile wallet.json
```
- This will create a new keypair and store it in a **wallet.json** file.
- Also airdrop 1 SOL to the account:
```bash
    solana airdrop 1 <wallet-public-key> --url https://api.devnet.solana.com
```
### (Optional)
- Import the wallet's private key to Phantom wallet.


# Setting up the SPL Token 
```bash
    cd Module2-create-spl-token-js
    npm install
```
- create a **.env** file and copy the content of **.env.example**  and paste it in your .env file
- Copy the **PRIVATE KEY** from your phantom wallet
- Replace your **your-private-key** with the **PRIVATE KEY** that you copied
- run the command below in your terminal to deploy, mint and transfer spl token to your phantom wallet address 
```bash
node index.js
```
- Copy the **transfer tx:** log in the terminal e.g `2Nn4k4tTyQhYuzh7C22DBP76vkFaxV1kxNWK6k3AfTHSkcbxj34xQczaGPt4SpjHs5hFpiCFw8b5BSy6aGpbPE5P`
- Visit [solscan](https://explorer.solana.com/) and paste it there
- Scroll down to **Token Balances** section and copy the address under the token tab e.g `9KGgsZ5LnZdLNKeGKMMnehXnzo9G7S785AqMMdpk72ip` 
- You can save it somewhere to be reused later.
  
**Note**   
you should see a balance of 1.



# Setting (Create and Deploy with sugar CLI) up the Candy Machine
```bash
    cd ..
    cd Module3-Candymachine
```
- open the **config.json** file
- chnage the **splTokenAccount** to the spl token address you got after setting the spl token.
- change the **solTreasuryAccount** and **address** to your phantom wallet address 
  
### Confirm your sugar CLI version:

   ```
   sugar --version
   `or`
   ./sugar --version
   ```
Ensure your sugar version is the legacy version 1.x or reinstall.

### Validate, Upload, Deploy, and Verify your NFT assets
    
    sugar launch

`sugar launch` starts a chain of commands:
- `sugar validate`
- `sugar upload`
- `sugar deploy`
- `sugar verify`

Copy your **Candy machine ID** after `sugar deploy`\
A **config.json** file is generated after `sugar launch` is done running. This file contains the details of how the NFTs are to be minted.

**Note**   
We are using our SPL tokens to mint the nft, that is why we specify the SPL token address in the **config.json** file.



# Setting up Candy Machine UI
```bash
    cd ..
    cd candy-machine-ui
```
- Rename the file **.env.example** to **.env** After changing the file name, you can change the values in there to the following:
- change *<YOUR CANDY MACHINE PROGRAM ID>* to the **Candy machine ID** that you copied after deployment
- change *https://metaplex.devnet.rpcpool.com/* to a valid rpc url

**Note**   
Solana devnet rpc url can be gotten from Alchemy, Infura, QuickNode e.t.c

- After updating the **.env**
-  run the following commands:
```bash
    yarn install
    yarn start
```
This will open up a browser at localhost:3000, where you can connect your wallet and have the ability to mint an NFT. Confirm that your Phantom Wallet is set to devnet and not mainnet before proceeding.

You'll need devnet SOL in your Phantom wallet to mint an NFT. You can use Solana CLI to airdrop to your Phantom wallet by entering this command in your terminal: 
  
```bash
    solana airdrop 1 YOUR_PHANTOM_WALLET_ADDRESS
```

Once you're ready, click **Mint**. If done successfully, you should see a website like this:
![ScreenShot](/mintPage.png)

you will notice a reduction from 10 to 9










