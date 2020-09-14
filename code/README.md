# Project 6: Fair Trade Coffe Supply Chain - Write Up

## 1. Versions, libraries and dependencies

- **Truffle v5.1.14-nodeLTS.0 (core: 5.1.13)**: used to develop, test and deploy the smart contracts of the "Coffe Supply Chain" Tracker-DApp.
- **Solidity v0.5.16 (solc-js)**: used to write smart contracts.
- **Node v12.16.3**: used for deploying UI to browser (for building network applications).
- **Web3.js v1.2.1**: DApp interaction with local or remote Ethereum node (via HTTP).
- **Infura**: connecting the DApp to the Ethereum (Rinkeby) network without the need to set up a complete Ethereum node or wallet by using a hosted Ethereum node cluster. 

***Note:** In order to connect to the Infura Node, the 'truffle-hdwallet-provider' still needs to be installed by running the command 'npm install --save truffle-hdwallet-provider'. This command installs an additional directory called 'node_modules'. The latter, however, apparently comprises of too many files to submit it through the Udacity Submission portal (I tried as Github Repo and as .zip-file, neither worked :(), being the reason I have removed it and added this note.*

## 2. General write-up

**Contract addresses on Rinkeby Network:** 

Starting migrations...
======================
> Network name:    'rinkeby'
> Network id:      4
> Block gas limit: 0x989680


1_initial_migration.js
======================

   Deploying 'Migrations'
   ----------------------
   > transaction hash:    0x105ed6d922ac969ef3e0ad131e7bec0aa6b0947a2cefd30448ce30c6fdaf0b2d
   > Blocks: 1            Seconds: 16
   > contract address:    0x8a53E5fE55c6325775A017e9098BDC6b22971f55
   > block number:        7190453
   > block timestamp:     1600012807
   > account:             0x8D8029fbDB15591122054FEC8567acC3b0A01bcf
   > balance:             2.974789884
   > gas used:            225237
   > gas price:           10 gwei
   > value sent:          0 ETH
   > total cost:          0.00225237 ETH


   > Saving migration to chain.
   > Saving artifacts
   -------------------------------------
   > Total cost:          0.00225237 ETH


2_deploy_contracts.js
=====================

   Deploying 'FarmerRole'
   ----------------------
   > transaction hash:    0x5e8ba8664675ece64a0a80cb17e5872a3d992cfb98982e1f510413c6bc1fb956
   > Blocks: 0            Seconds: 12
   > contract address:    0xe83992a4Ea1Fec026284D843B09eb478E7c2bdE8
   > block number:        7190455
   > block timestamp:     1600012837
   > account:             0x8D8029fbDB15591122054FEC8567acC3b0A01bcf
   > balance:             2.971305414
   > gas used:            306084
   > gas price:           10 gwei
   > value sent:          0 ETH
   > total cost:          0.00306084 ETH


   Deploying 'DistributorRole'
   ---------------------------
   > transaction hash:    0x256701aca263800b68e46554e3699c41e00d4d488dd394579fa56bcbaf5cbc55
   > Blocks: 0            Seconds: 8
   > contract address:    0x37A57f3F8bCc3A03be1886A1760f52b3A341a1e0
   > block number:        7190456
   > block timestamp:     1600012852
   > account:             0x8D8029fbDB15591122054FEC8567acC3b0A01bcf
   > balance:             2.968244694
   > gas used:            306072
   > gas price:           10 gwei
   > value sent:          0 ETH
   > total cost:          0.00306072 ETH


   Deploying 'RetailerRole'
   ------------------------
   > transaction hash:    0xe5e08b3da529549b18353e568809e5bcf9dcc6183d5a0f10c26dae035fe1014a
   > Blocks: 0            Seconds: 8
   > contract address:    0x65c6621Ce690AA9d9dC51a1Cd3916B692AACfA10
   > block number:        7190457
   > block timestamp:     1600012867
   > account:             0x8D8029fbDB15591122054FEC8567acC3b0A01bcf
   > balance:             2.965183854
   > gas used:            306084
   > gas price:           10 gwei
   > value sent:          0 ETH
   > total cost:          0.00306084 ETH


   Deploying 'ConsumerRole'
   ------------------------
   > transaction hash:    0x3a3e28f525b90fee059a007338996fb37f30ee89390fa1e0d4214bbb8f502f28
   > Blocks: 0            Seconds: 8
   > contract address:    0xCE8Cdb3CF569f43C076fBc35f6e78cCB53065eFb
   > block number:        7190458
   > block timestamp:     1600012882
   > account:             0x8D8029fbDB15591122054FEC8567acC3b0A01bcf
   > balance:             2.962123014
   > gas used:            306084
   > gas price:           10 gwei
   > value sent:          0 ETH
   > total cost:          0.00306084 ETH


   Deploying 'SupplyChain'
   -----------------------
   > transaction hash:    0xb345593e7440808690969a83880dbc1a88d0ca099eb2a3d79a8381ab998a8582
   > Blocks: 0            Seconds: 8
   > contract address:    0xEc857BBE2c622A8e3213D3e8c43DEB9a3904b6e2
   > block number:        7190459
   > block timestamp:     1600012897
   > account:             0x8D8029fbDB15591122054FEC8567acC3b0A01bcf
   > balance:             2.935889954
   > gas used:            2623306
   > gas price:           10 gwei
   > value sent:          0 ETH
   > total cost:          0.02623306 ETH


   > Saving migration to chain.
   > Saving artifacts
   -------------------------------------
   > Total cost:           0.0384763 ETH


Summary
=======
> Total deployments:   6
> Final cost:          0.04072867 ETH

**Main steps:** 

*1. Define basic architecture for tracking-application via UML diagrams*
By defining dedicated diagrams with respect to the Unified Modeling Language (UML), the various stakeholders and their respective activities ([UML-Activity diagram](../architecture/FTC_UML-activity-diagram.drawio.pdf)), states ([UML-State diagram](../architecture/FTC_UML-state-diagram.drawio.pdf)) and sequences ([UML-Sequence diagram](../architecture/FTC_UML-sequence-diagram.drawio.pdf)) can be visualized in a standardized manner. Additionally, the smart contract structure as key component of a blockchain-based system, can be clarified by defining a [UML-class diagram](../architecture/FTC_UML-class-diagram.drawio.pdf).

In this case the supply chain of coffee shall be established as transparent and traceable as possible, clearly stating the individual rights of the involved stakeholders, being Farmers, Distributors, Retailers and Consumers, as well as the exact steps the coffee undergoes from harvesting to its final consumption by the Consumer.

*2. Write Smart Contracts*
The structure of the smart contracts is divided into three separate "categories", being [coffeeaccesscontrol](https://github.com/patrem98/Udacity-Blockchain-Nanodegree/tree/master/Fair_Trade_Coffe_Supply_Chain/code/contracts/coffeeaccesscontrol), [coffeebase](https://github.com/patrem98/Udacity-Blockchain-Nanodegree/tree/master/Fair_Trade_Coffe_Supply_Chain/code/contracts/coffeebase) and [coffeecore](https://github.com/patrem98/Udacity-Blockchain-Nanodegree/tree/master/Fair_Trade_Coffe_Supply_Chain/code/contracts/coffeecore). While all contracts belonging to the [coffeeaccesscontrol](https://github.com/patrem98/Udacity-Blockchain-Nanodegree/tree/master/Fair_Trade_Coffe_Supply_Chain/code/contracts/coffeeaccesscontrol) deal with the respective rights of the involved stakeholders with regards to the process step in the supply chain, the Ownable.sol contract (belonging to the coffeecore category) deals with the transfer of the contract-ownership of the [SupplyChain.sol](https://github.com/patrem98/Udacity-Blockchain-Nanodegree/tree/master/Fair_Trade_Coffe_Supply_Chain/code/contracts/coffeebase/SupplyChain.sol). The latter being part of the [coffeebase](https://github.com/patrem98/Udacity-Blockchain-Nanodegree/tree/master/Fair_Trade_Coffe_Supply_Chain/code/contracts/coffeebase) category represents the main smart contract relevant for the entire process structure of the supply chain. It comprises of the following main functions:

- harvestItem()
- processItem()
- packItem()
- sellItem()
- buyItem()
- shipItem()
- receiveItem()
- purchaseItem()
- fetchItemBufferOne()
- fetchItemBufferTwo()

These function shall model the most important steps in the supply chain and serve as trackers of each "Coffee-item" that undergoes all process steps from harvesting to being purchased by the consumer. A "Coffee-item" comprises the following attributes:

    struct Item 
    {  
    uint    sku;  // Stock Keeping Unit (SKU)
    uint    upc; // Universal Product Code (UPC), generated by the Farmer, goes on the package, can be verified by the Consumer
    address payable ownerID;  // Metamask-Ethereum address of the current owner as the product moves through 8 stages
    address payable originFarmerID; // Metamask-Ethereum address of the Farmer
    string  originFarmName; // Farmer Name
    string  originFarmInformation;  // Farmer Information
    string  originFarmLatitude; // Farm Latitude
    string  originFarmLongitude;  // Farm Longitude
    uint    productID;  // Product ID potentially a combination of upc + sku
    string  productNotes; // Product Notes
    uint    productPrice; // Product Price
    State   itemState;  // Product State as represented in the enum above
    address payable distributorID;  // Metamask-Ethereum address of the Distributor
    address payable retailerID; // Metamask-Ethereum address of the Retailer
    address payable consumerID; // Metamask-Ethereum address of the Consumer
    }

All the information stated above can be accessed by all stakeholders via the fetchItemBufferOne() and fetchItemBufferTwo() methods.

*3. Test Smart Contracts*
After drafting all relevant smart contracts, it is vital to test them. For this, dedicated tests have been written in the [TestSupplychain.js](https://github.com/patrem98/Udacity-Blockchain-Nanodegree/tree/master/Fair_Trade_Coffe_Supply_Chain/code/test/TestSupplychain.js) file, testing the correct operation principle of the main functions written in the smart contracts, more specifically in the [SupplyChain.sol](https://github.com/patrem98/Udacity-Blockchain-Nanodegree/tree/master/Fair_Trade_Coffe_Supply_Chain/code/contracts/coffeebase/SupplyChain.sol) file. 

For all 10 methods listed above (harvestItem(), processItem(), etc.) a dedicated test has been written in in the truffle testing environment using the "async/await notation" in JavaScript. For detailed information, see file [TestSupplychain.js](https://github.com/patrem98/Udacity-Blockchain-Nanodegree/tree/master/Fair_Trade_Coffe_Supply_Chain/code/test/TestSupplychain.js).

*4. Deploy Smart contracts on a public test network (Rinkeby)*

## 3. UML diagrams

- [Activity diagram](../architecture/FTC_UML-activity-diagram.drawio.pdf)

- [Sequence diagram](../architecture/FTC_UML-sequence-diagram.drawio.pdf)

- [State diagram](../architecture/FTC_UML-state-diagram.drawio.pdf)

- [Class diagram (Data model)](../architecture/FTC_UML-class-diagram.drawio.pdf)

## 4. Future work (optional)

In order to make the established blockchain-based coffee supply chain more sophisticated the following steps are still possible:

- Adding a distributed file storage with the InterPlanetary File System (IPFS)
- Enancing the access control potential of all stakeholders by implementing additional modifiers for the respective functions, so that e.g. a Consumer is not able to put Coffe beans "sellItem()". This bases on the inherited contracts (e.g. [DistributorRole.sol](https://github.com/patrem98/Udacity-Blockchain-Nanodegree/tree/master/Fair_Trade_Coffe_Supply_Chain/code/contracts/coffeeaccesscontrol/DistributorRole.sol)) in the [SupplyChain.sol](https://github.com/patrem98/Udacity-Blockchain-Nanodegree/tree/master/Fair_Trade_Coffe_Supply_Chain/code/contracts/coffeebase/SupplyChain.sol) contract.
- Adding pictures of items or a barcode to scan (a typical feature in standard supply chain), in order to enhance traceability and tracking possibility of every item and further simplify the interaction for the user.
