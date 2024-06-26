# MyToken Contract

This Solidity smart contract implements a basic token system with minting and burning functionalities. Below are the details and requirements for the contract.

## Contract Details

- **Token Name**: BANKER
- **Token Abbreviation**: BKR
- **Total Supply**: Dynamic (starts at 0 and can be increased or decreased through minting and burning)

## Requirements

1. **Public Variables**:
    - `string public _tokenName`: Stores the name of the token.
    - `string public _tokenAbbr`: Stores the abbreviation of the token.
    - `uint public _totalSupply`: Stores the total supply of the token.
    
2. **Mapping**:
    - `mapping(address => uint) public balances`: Maps addresses to their respective token balances.

3. **Mint Function**:
    - Increases the total supply and the balance of the specified address.
    - Parameters:
        - `address addr`: The address to which tokens will be minted.
        - `uint value`: The number of tokens to be minted.

4. **Burn Function**:
    - Decreases the total supply and the balance of the specified address.
    - Parameters:
        - `address addr`: The address from which tokens will be burned.
        - `uint value`: The number of tokens to be burned.
    - Conditions:
        - Ensures that the balance of the specified address is greater than or equal to the amount to be burned.

## Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {
    // Public variables here
    string public _tokenName = "BANKER";
    string public _tokenAbbr = "BKR";
    uint public _totalSupply = 0;

    // Mapping variable here
    mapping(address => uint) public balances;

    // Mint function
    function mint(address addr, uint value) public {
        _totalSupply += value;
        balances[addr] += value;
    }

    // Burn function
    function burn(address addr, uint value) public {
        if (balances[addr] >= value) {
            _totalSupply -= value;
            balances[addr] -= value;
        }
    }
}
```

## Usage

- **Minting Tokens**: Call the `mint` function with the desired address and value to increase the total supply and the balance of the address.
- **Burning Tokens**: Call the `burn` function with the desired address and value to decrease the total supply and the balance of the address. Ensure that the address has a sufficient balance before burning tokens.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
