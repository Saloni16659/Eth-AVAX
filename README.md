# Create-and-mint-tokens
# Description
This Solidity code provides a comprehensive implementation of the ERC20 token standard. In this code we have public view functions, Token transfer functions, Allowance functions, and Internal Functions. 
# Getting started
# Installing
We need to import the following:
import "IREC20.sol";
import "context.sol";
We can run the code on Online Etherium IDE i.e. Remix IDE. Firstly open Remix IDE. Create a new Solidity file. Write the code and then compile the contract. After that Deploy the contract using the Deploy & Run Transactions tab.
# Executing program
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

import "IREC20.sol";
import "context.sol";

contract ERC20 is Context, IERC20 {
    mapping (address => uint256) private _balances;

    mapping (address => mapping (address => uint256)) private _allowances;

    uint256 private _totalSupply;

    string private _name;
    string private _symbol;

    constructor (string memory name_, string memory symbol_) {
        name = name;
        symbol = symbol;
    }

    /**
     * Returns the name of the token.
     */
    function name() public view virtual returns (string memory) {
        return _name;
    }

    /**
     * Returns the symbol of the token, usually a shorter version of the
     * name.
     */
    function symbol() public view virtual returns (string memory) {
        return _symbol;
    }

    /**
     * Returns the number of decimals used to get its user representation.
     * For example, if decimals equals 2, a balance of 505 tokens should
     * be displayed to a user as 5,05 (505 / 10 ** 2).
     *
     * Tokens usually opt for a value of 18, imitating the relationship between
     * Ether and Wei. This is the value {ERC20} uses, unless this function is
     * overloaded;
     *
     * NOTE: This information is only used for display purposes: it in
     * no way affects any of the arithmetic of the contract, including
     * {IERC20-balanceOf} and {IERC20-transfer}.
     */
    function decimals() public view virtual returns (uint8) {
        return 18;
    }

    /**
     * See {IERC20-totalSupply}.
     */
    function totalSupply() public view virtual override returns (uint256) {
        return _totalSupply;
    }

    /**
     * See {IERC20-balanceOf}.
     */
    function balanceOf(address account) public view virtual override returns (uint256) {
        return _balances[account];
    }

    /**
     * See {IERC20-transfer}.
     *
     * Requirements:
     *
     * - recipient cannot be the zero address.
     * - the caller must have a balance of at least amount.
     */
    function transfer(address recipient, uint256 amount) public virtual override returns (bool) {
        _transfer(_msgSender(), recipient, amount);
        return true;
    }

    /**
     *  See {IERC20-allowance}.
     */
    function allowance(address owner, address spender) public view virtual override returns (uint256) {
        return _allowances[owner][spender];
    }

    /**
     * See {IERC20-approve}.
     *

## Authors
Saloni Gupta
salonig16659@gamil.com

## License

This project is licensed under the MIT License - see the LICENSE.md file for details
