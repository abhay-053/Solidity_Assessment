# MyToken Solidity Contract

This is a digital token smart contract for Ethereum. It facilitates the creation, distribution, and destruction of digital tokens.

## Description

This program represents a basic smart contract written in Solidity, the programming language used for creating smart contracts on the Ethereum blockchain.

## Features

- **Token Metadata**: The contract maintains metadata such as the token name, symbol, and total supply.
- **Token Creation**: The contract creator is initially assigned all tokens specified during contract deployment.
- **Token Minting**: Allows the creation of new tokens and assigns them to a specified address.
- **Token Burning**: Enables the destruction of tokens held by a specified address.

## Getting Started

### Executing the Program

1. **Online IDE**: Utilize Remix, an online Solidity IDE. Access the Remix website at [Remix Ethereum](https://remix.ethereum.org/).
   
2. **Create a New File**: In Remix, click on the "+" icon in the left-hand sidebar to create a new file. Save the file with a .sol extension (e.g., `MyToken.sol`).

3. **Copy and Paste Code**: Copy the provided Solidity code and paste it into the newly created file.
``` solidity
  pragma solidity ^0.8.0;
  contract MyToken {
      string public name;                    
      string public symbol;                   
      uint256 public totalSupply;           
      mapping(address => uint256) public balanceOf;
      constructor(string memory _name, string memory _symbol, uint256 _initialSupply) {
          name = _name;
          symbol = _symbol;
          totalSupply = _initialSupply;
          balanceOf[msg.sender] = _initialSupply; // Assign all tokens to the contract creator initially
      }
      function mint(address _to, uint256 _amount) public {
          require(_amount > 0, "Amount must be greater than 0");
          totalSupply += _amount;
          balanceOf[_to] += _amount;
      }
      function burn(address _from, uint256 _amount) public {
          require(balanceOf[_from] >= _amount, "Insufficient balance");
          require(_amount > 0, "Amount must be greater than 0");
          totalSupply -= _amount;
          balanceOf[_from] -= _amount;
      }
  }
  ```

4. **Compile the Code**: Navigate to the "Solidity Compiler" tab in the left-hand sidebar. Set the "Compiler" option to "0.8.0" (or another compatible version) and click on the "Compile MyToken.sol" button.

5. **Deploy the Contract**: Go to the "Deploy & Run Transactions" tab. Select the MyToken contract from the dropdown menu and click on the "Deploy" button.

6. **Interact with the Contract**: Once deployed, interact with the contract by minting new tokens, transferring tokens, and burning tokens using the provided functions.

## Author:

Abhay Dhek
