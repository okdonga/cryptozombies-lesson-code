# cryptozombies-lesson-code

Here I organize different concepts, terminologies I learnt during my study of solidity.

## Terms

tokens

> a smart contract that follows some common rules. all ERC20 tokens share the same set of functions with the same names

ERC-20

> fungible tokens (tradable, divisible)

ERC-721

> non-fungible tokens (NFT).
> not interchangeable since each one is assumed to be unique, and are not divisible. You can only trade them in whole units, and each one has a unique ID. eg art piece, game character,

msg.sender

> it's a global variable available to all functions - refers to the address of the sender

Wei

> the smallest sub-unit of Ether — there are 10^18 wei in one ether

Web3.js

> a JavaScript library from the Ethereum Foundation. Ethereum nodes only speak a language called JSON-RPC, which isn't very human-readable. A query to tell the node you want to call a function on a contract looks something like this:
> `{"jsonrpc":"2.0","method":"eth_sendTransaction","params":[{"from":"0xb60e8dd61c5d32be8058bb8eb970870f07233155","to":"0xd46e8dd67c5d32be8058bb8eb970870f07244567","gas":"0x76c0","gasPrice":"0x9184e72a000","value":"0x9184e72a","data":"0xd46e8dd67c5d32be8d46e8dd67c5d32be8058bb8eb970870f072445675058bb8eb970870f072445675"}],"id":1}`

call

> used for `view` and `pure` functions. It only runs on the local node, and won't create a transaction on the blockchain. `view` and `pure` functions are read-only and don't change state on the blockchain. They also don't cost any gas, and the user won't be prompted to sign a transaction with MetaMask.

send

> creates a transaction and change data on the blockchain. You'll need to use send for any functions that aren't `view` or `pure`.

assert vs require

> assert is similar to require, where it will throw an error if false. require will refund the user the rest of their gas when a function fails, whereas assert will not. assert is typically used when something has gone horribly wrong with the code (like a uint overflow).

Web3 Provider

> Setting a Web3 Provider in Web3.js tells our code which node we should be talking to handle our reads and writes. It's kind of like setting the URL of the remote web server for your API calls in a traditional web app.

Infura

> Infura is a service that maintains a set of Ethereum nodes with a caching layer for fast reads, which you can access for free through their API. Using Infura as a provider, you can reliably send and receive messages to/from the Ethereum blockchain without needing to set up and maintain your own node.

Metamask

> browser extension for Chrome and Firefox that lets users securely manage their Ethereum accounts and private keys, and use these accounts to interact with websites that are using Web3.js.
> Metamask uses Infura's servers under the hood as a web3 provider, just like we did above — but it also gives the user the option to choose their own web3 provider. So by using Metamask's web3 provider, you're giving the user a choice, and it's one less thing you have to worry about in your app.
> Metamask uses Infura's servers under the hood as a web3 provider, just like we did above — but it also gives the user the option to choose their own web3 provider. So by using Metamask's web3 provider, you're giving the user a choice, and it's one less thing you have to worry about in your app.

ABI

> ABI stands for Application Binary Interface. Basically it's a representation of your contracts' methods in JSON format that tells Web3.js how to format function calls in a way your contract will understand.

> When you compile your contract to deploy to Ethereum (which we'll cover in Lesson 7), the Solidity compiler will give you the ABI,

Ropsten(https://ropsten.etherscan.io/)

> A proof-of-work blockchain that most closely resembles Ethereum; you can easily mine faux-Ether.

[Kovan](https://kovan.etherscan.io/)

> A proof-of-authority blockchain, started by the Parity team. Ether can’t be mined; it has to be [requested](https://github.com/kovan-testnet/faucet).

[Rinkeby](https://rinkeby.etherscan.io/)

> A proof-of-authority blockchain, started by the Geth team. Ether can’t be mined; it has to be [requested](https://faucet.rinkeby.io/).

### Types

uint

> equivalent to uint256

string

struct

### Visibility modifier

private

> it's only callable from other functions inside the contract

internal

> it's like private, but can also be called by contracts that inherit from this one

external

> can only be called outside the contract

public

> can be called anywhere, both internally and externally. In Solidity, when you declare a variable public, it automatically creates a public "getter" function with the same name.

indexed

> in order to filter events and only listen for changes related to the current user, the Solidity contract would have to use the indexed keyword

### State modifier

view

> no data is saved/changed. no gas cost if called externally from outside the contract (but do coast gas if called internally by another function)

pure

> doesn't read any data from the blockchain. no gas cost if called externally from outside the contract(but do coast gas if called internally by another function)

### Custom modifier

> define custom logic to determine how they affect a function eg validations in `onlyOwner`, `aboveLevel`.

### Payable modifier

> a special type of function that can receive Ether.
