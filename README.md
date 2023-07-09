# Creating a token

This Solidity program is a simple  program that demonstrates the creation of a token named Streax. 

## Description

The provided code represents a smart contract written in Solidity that creates a token called "Streax" with the symbol "STX" on the Ethereum blockchain. Let's break down its functionality:

Contract Inheritance: The contract inherits from three other contracts: ERC20, ERC20Burnable, and Ownable. These contracts are part of the OpenZeppelin library and provide functionalities for creating ERC20 tokens, enabling burning of tokens, and managing ownership permissions, respectively.

Constructor: The constructor function is executed when the contract is deployed. It initializes the token by calling the constructor of the ERC20 contract with the parameters "Streax" as the name and "STX" as the symbol. Additionally, it mints 1 token (represented as 1 * 10 ** decimals()) and assigns it to the deployer's address (i.e., msg.sender).

Mint Function: The mint function allows the contract owner (deployer) to mint additional tokens. It takes two parameters: to (the address to which the new tokens will be minted) and amount (the number of tokens to be minted). The function is restricted to be called only by the contract owner (onlyOwner modifier), which is inherited from the Ownable contract. The _mint function from the ERC20 contract is used internally to create and assign the new tokens to the specified address.

The purpose of this contract is to create a token called "Streax" with the symbol "STX" and an initial supply of 1 token. The contract owner has the ability to mint additional tokens as needed.



## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., module3.sol). Copy and paste the following code into the file:

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.9;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract Streax is ERC20, ERC20Burnable, Ownable {
    constructor() ERC20("Streax", "STX") {
        _mint(msg.sender, 1 * 10 ** decimals());
    }

    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }
}

```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.9" (or another compatible version), and then click on the "Compile module3.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "HelloWorld" contract from the dropdown menu, and then click on the "Deploy" button.

To deploy on hardhat network, run the following commands:
```
npx hardhat node
npx hardhat run --network localhost scripts/deploy.js
```


## Authors

Aditya Raju

adrocxsmma@gmail.com


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
