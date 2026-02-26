***Storage Factory & Smart Contract Inheritance***


This project demonstrates the power of composability in Solidity. Instead of just deploying a single contract, we explore how to build a Factory that can deploy multiple instances of a contract, and how to use Inheritance to modify existing logic without rewriting it from scratch.

📁 Contract Overviews
The project is split into three main parts:

1. SimpleStorage.sol
The base building block. It’s a clean, simple contract that allows you to:

Store a favorite number.

Create a list of people (structs).

Map names to favorite numbers for quick lookups.

2. StorageFactory.sol
This is the "manager" contract. It uses the new keyword to deploy new instances of SimpleStorage directly from the blockchain.

Create: You can generate a whole list of independent storage contracts.

Interact: It includes "sfStore" and "sfGet" functions, which show you how to talk to another contract as long as you have its Address and ABI.

3. AddFiveStorage.sol
This demonstrates Inheritance. By using contract AddFiveStorage is SimpleStorage, it "borrows" everything from the original contract.

The Twist: It uses the override keyword on the store function.

Whenever you try to store a number here, it automatically adds 5 to it. It’s a simple example of how you can build specialized versions of base contracts.

🏗️ Technical Concepts
The Factory Pattern: Useful for building decentralized apps where every user needs their own personal instance of a contract.

Composability: One contract calling functions on another contract.

Shadowing & Overriding: Using virtual in the parent and override in the child to change function behavior.

🚀 How to Run (Hardhat)
Installation
Bash
npm install
npx hardhat compile
Deployment Strategy
When deploying, you’ll usually want to deploy the StorageFactory first. Once deployed, you don't need to manually deploy SimpleStorage ever again—just call createSimpleStorageContract() and let the factory do the work for you!

Bash
npx hardhat run scripts/deploy.js
📝 Learning Notes
This project is inspired by the Patrick Collins FreeCodeCamp curriculum. It’s designed to help you move away from thinking about contracts as single files and start thinking of them as modular pieces of a larger system.
