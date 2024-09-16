# MyToken Solidity Contract

## Overview

The `MyToken` contract is a basic implementation of a token in Solidity. It allows users to mint new tokens and burn existing ones, tracking token balances and the total supply.

## Contract Details

- **Token Name**: META
- **Token Abbreviation**: NTA
- **Total Supply**: Initialized to 0, can be increased or decreased via minting and burning functions.

## Smart Contract Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity =0.8.18;

contract MyToken {
    string public tokenName = "META";
    string public tokenAbbry = "NTA"; 
    uint public totalSupply = 0;

    mapping(address => uint) public balances;

    function mint(address _to, uint _value) public {
        totalSupply += _value;
        balances[_to] += _value;
    }

    function burn(address _from, uint _value) public {
        require(balances[_from] >= _value, "Not enough balance");  // check if sender has enough balance to burn
        totalSupply -= _value;
        balances[_from] -= _value;
    }
}
