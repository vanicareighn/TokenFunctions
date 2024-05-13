# Create, Mint and Transfer Token
ETH Intermediate Module 3: Functions and Errors- this smart contract program demonstrating the assert and revert functions and also the require statements.

## Description

The Smart Contract named MyToken, is an implementation of an ERC20 token on the Ethereum blockchain. It allows for the creation, transfer, and burning of tokens. The contract owner has the exclusive ability to mint new tokens, while any user can transfer tokens to other addresses or burn their own tokens. The contract is built upon OpenZeppelin's ERC20 implementation for standard token functionality and employs a modifier onlyOwner to restrict certain actions to the contract owner.

## Executing the program

To run this program, begin by accessing the Remix Ethereum IDE at https://remix.ethereum.org/. Create a new file in the IDE, ensuring it has a .sol extension, and paste the provided Solidity smart contract code into it. Next, compile the contract by selecting the appropriate Solidity compiler version, which is 0.8.0 in this case, from the Remix compiler tab. Following compilation, deploy the contract by selecting the MyToken contract from the Remix deploy & run tab, then initiate deployment by clicking the deploy button. Once the contract is deployed, you can interact with it through the user-friendly interface provided by Remix. As the contract owner, you hold the privilege to mint new tokens to designated addresses using the mint function. Moreover, any user can facilitate token transfers to other addresses leveraging the transfer function. Additionally, users possess the capability to burn their own tokens utilizing the burn function. Through the Remix Ethereum IDE, you have the opportunity to experiment with these functions, gaining insights into their behavior within Solidity smart contracts. Conduct tests on the contract's functionalities by engaging with the mint, transfer, and burn functions, while also observing the enforcement of ownership and permissions facilitated by the onlyOwner modifier.

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    address public owner;

    constructor() ERC20("FlipCoin", "FTP") {
        owner = msg.sender;
        _mint(msg.sender, 100000); // Given value amount for the Token
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "You must be the contract owner to do this");
        _;
    }

    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    function transfer(address to, uint256 amount) public override returns (bool) {
        _transfer(msg.sender, to, amount);
        return true;
    }

    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }
}
```

## Additional Information

Student Info and Email address

Flores, John Nico M.
National Teachers College - BSIT 3.4
422003560@ntc.edu.ph
