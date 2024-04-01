# Personal Crypto Smart Contract Code
This is a smart contract application that I wrote for meta crafters to create my crypto called presi Crypto and Added a burn and mint function to add and remove from it's total supply bal

## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The contract has multiple function Called Mint and Burn to add and increase the total supply of my coin, the event function to display this contract to the public and so much more

## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., PresiCrypto.sol). Copy and paste the following code 

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MyToken {

    struct PresiCrypto {
        string TokenName;
        string TokenAbbrv;
        uint256 TotalSupply;
        address entityAddress;
    }

    PresiCrypto public presiCrypto;

    mapping(address => uint256) public balances;

    event Mint(address indexed recipient, uint256 value);
    event Burn(address indexed owner, uint256 value);

    constructor(string memory _name, string memory _TokenAbbrv, uint256 _totalSupply) {
        presiCrypto.TokenName = _name;
        presiCrypto.TokenAbbrv = _TokenAbbrv;
        presiCrypto.TotalSupply = _totalSupply;
        balances[msg.sender] = _totalSupply;
    }

    function mint(address _recipient, uint256 _value) public {
        require(_recipient != address(0), "Invalid recipient address");
        
        presiCrypto.TotalSupply += _value;
        // Increase recipient's balance
        balances[_recipient] += _value;
        
        // Emit mint event
        emit Mint(_recipient, _value);
    }

    function burn(address _owner, uint256 _value) public {
        require(_owner != address(0), "Invalid owner address");
        require(balances[_owner] >= _value, "Insufficient balance");
        presiCrypto.TotalSupply -= _value;

        // Decrease owner's balance
        balances[_owner] -= _value;

        // Emit burn event
        emit Burn(_owner, _value);
    }
}

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.4" (or another compatible version), and then click on the "Compile PresiCrypto.sol" button.

Once the contract is deployed, you can interact with it by calling the sayHello function. Click on the "HelloWorld" contract in the left-hand sidebar, and then click on the "sayHello" function. Finally, click on the "transact" button to execute the function and retrieve the "Hello World!" message.

## Contributors
Omojola David O
https://www.linkedin.com/in/omojola-david-36b212235

## License

This project is licensed under the MIT License - see the LICENSE.md file for details

