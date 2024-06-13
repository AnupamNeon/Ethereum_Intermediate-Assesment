
# MyToken Smart Contract

This repository contains the Solidity code for the MyToken smart contract. This contract implements a basic token system with functionalities to mint and burn tokens. It is written in Solidity version 0.8.26 and is intended for deployment on the Ethereum blockchain.

## Getting Started

### Executing Program
1. Open Remix IDE or your preferred development environment.
2. Copy the MyToken contract code into a new Solidity file (e.g., MyToken.sol).
3. Compile the contract using Solidity version 0.8.26.
4. Deploy the contract to a local blockchain or any Ethereum testnet/mainnet.


```

 // SPDX-License-Identifier: MIT
pragma solidity 0.8.26;

contract MyToken {
    // Public variables to store the details about the coin
    string public tokenName = "Anupam Kumar";
    string public tokenAbbrv = "AK";
    uint256 public totalSupply = 0;

    // Mapping of addresses to balances
    mapping(address => uint256) public balances;

    // Mint function to increase the total supply and the balance of the sender
    function mint(address _to, uint256 _value) public payable  {
        totalSupply += _value; // totalSupply = totalSupply + _value
        balances[_to] += _value;
    }

    // Burn function to decrease the total supply and the balance of the specified address
    function burn(address _from, uint256 _value) public {
        if (balances[_from] >= _value) {
            totalSupply -= _value;
            balances[_from] -= _value;
            payable(_from).transfer(_value);
        }
        else {
            revert("Insufficient balance to burn");
        }
    }
}
```

## Authors

Anupam Kumar
- [@AnupamNeon](https://github.com/AnupamNeon)


## License

This project is licensed under the MIT License - see the LICENSE file for details.

