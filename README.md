# Bonuscard Showcase Example

## Overview

This repo contains all files to launch a very simple web3 workflow:

1. Voucher Operator(1) transfers an ERC1155 NFT to the customer
2. Customer(2) creates a signature, which allows an touristic operator(3) to redeem the voucher (QR code)
3. Operator scans the QR code and redeems the voucher.
4. Redeem will burn one token quantity, and send 1 CAM to the the touristic service account(4).

### Requirements

* Access to a EVM blockchain like Camino's Columbus network
* Remix IDE (remix.ethereum.org)
* Web server

### Installation

1. Open [ERC1155BonusCard](contracts\ERC1155BonusCard.sol) in Remix IDE, compile and deploy
2. Setup smart contract (Remix IDE):
    * provide NFT metadata: setBaseMetadataURI
    * allow (3) to call redeem: setFlightOperator
    * set fund address (4): setFundAddress
3. Mint n entities of a tokenId of your choice to (1), in general (1) is the account which has deployed the contract
4. Edit the index html files in [passenger](passenger) and [operator](operator) folders and replace the contract address
5. Copy the folders [passenger](passenger) and [operator](operator) to your web server

### Technical Workflow

1. Voucher handler (1) transfers 1 entity of minted tokenId to customer(2) address (Remix IDE / ERC1155 capable wallet)
2. Customer(2) opens passenger web side in mobile MetaMask browser (make sure the correct network is selected), signs that he is willing to spend his NFT -> QR code is generated
3. Operator(3) opens the operator website in a MetaMask browser, activates the QR scanner, and scans the QR code from step 2.  
After successful scan, the balance of (2) is shown and the redeem link (burn and send funds) is available.

&copy;2022 Chain4Travel AG