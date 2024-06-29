# MyToken Solidity Smart Contract

## Overview

MyToken is a simple Ethereum smart contract written in Solidity. It represents a basic token with functionalities to mint and burn tokens. This contract is intended for educational purposes to understand the basics of token creation and management on the Ethereum blockchain.

## Features

1. **Public Variables**
   - `tokenName`: The name of the token.
   - `tokenAbbrv`: The abbreviation of the token.
   - `totalSupply`: The total supply of the token.

2. **Mapping**
   - `balances`: A mapping of addresses to their respective balances.

3. **Mint Function**
   - Increases the total supply of the token.
   - Increases the balance of the specified address.

4. **Burn Function**
   - Decreases the total supply of the token.
   - Decreases the balance of the specified address.
   - Ensures the balance of the address is greater than or equal to the amount to be burned.

## Smart Contract Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {

    // Public variables
    string public tokenName = "LAPTOP";
    string public tokenAbbrv = "LAP";
    uint public totalSupply = 10;

    // Mapping of addresses to balances
    mapping(address => uint) public balances;

    // Mint function
    function mint (address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    // Burn function
    function burn (address _address, uint _value) public {
        if (balances[_address] >= _value) {
            totalSupply -= _value;
            balances[_address] -= _value;
        }
    }
}
