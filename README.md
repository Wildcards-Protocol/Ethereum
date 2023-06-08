# Wildcards Protocol

Welcome to the Wildcards Protocol repository. Our protocol empowers NFT projects by enabling wildcard domains for their Ethereum Name Service (ENS) names. By linking an ENS name to an NFT collection, individual holders will automatically receive wildcard subdomains. 

For example, [69.dippies.eth](https://app.ens.domains/69.dippies.eth) will always point to the owner of Dippies #69.

## Ethereum Contract Address

The smart contract for the Wildcards Protocol is deployed on the Ethereum Mainnet at [this address](https://etherscan.io/address/0x53e42d7b919C72678996C3F3486F93E75946A47C#code).

This contract is a slight modification of the official ENS Public Resolver, which is deployed [here](https://etherscan.io/address/0x4976fb03C32e5B8cfe2b6cCB31c09Ba78EBaBa41#code). Most functions found in the public resolver such as `setAddr`, `setContentHash`, and `setText` have been implemented, allowing the main domain (i.e., dippies.eth) to retain normal on-chain record setting via the resolver. The domain's controller/manager can also set normal on-chain subdomains. NFT Wildcard resolution only kicks in when a subdomain does not 'exist' in the registry.

## Getting Started

Linking your ENS name to your NFT collection is a two-step process.

1. Set the Wildcards Protocol as your ENS Domain Resolver: Start by setting our smart contract address, [0x53e42d7b919C72678996C3F3486F93E75946A47C](https://etherscan.io/address/0x53e42d7b919C72678996C3F3486F93E75946A47C#code), as your ENS domain resolver. This can be done through the official [ENS App](https://app.ens.domains/).

<img src="https://gcdnb.pbrd.co/images/g9ZBXluLsLWq.png?o=1" width="480" height="289">

2. Link your ENS Name to your NFT Contract: Once you've set the Wildcards Protocol as your domain resolver, you can now link your ENS name to your NFT contract address while also providing the chain ID (chain ID for Ethereum is 1).

You will use the setLinkedContract function in our contract to complete this process:

```solidity
function setLinkedContract(string memory name, uint256 NFTchainId, address nftaddr)
```

When calling this function, NFT projects should provide the following information:

- `name`: This is the ENS name that you want to link to your NFT collection. For example, "dippies.eth".
- `NFTchainId`: This is the chain ID of the network where the NFT contract is deployed. For Ethereum, this will be 1.
- `nftaddr`: This is the address of the NFT contract that you want to link with the ENS name. For example, "0x82f5ef9ddc3d231962ba57a9c2ebb307dc8d26c2".

<img src="https://i.ibb.co/T8xbj4Q/Screen-Shot-2023-06-08-at-3-02-17-PM.png" width="480" height="289">




## Optimism Support
While the Wildcards Protocol also supports the Optimism network, we would like to clarify that our Optimism-specific resolver, deployed [here](https://optimistic.etherscan.io/address/0xf12ca7007d5258a5d98c5da6437674ca704a2561#code), is solely used for resolving NFT ownership & records on Optimism. It is not intended for users to directly interact with this resolver.

Instead, NFT project owners wishing to link their ENS names to collections on the Optimism network should still utilize our Ethereum mainnet [contract](https://etherscan.io/address/0x53e42d7b919C72678996C3F3486F93E75946A47C#code) to do so.

The purpose of our Optimism resolver is to facilitate the Cross-Chain Interoperability Protocol (CCIP) in our back-end processes. Our CCIP gateway server directly forwards all queries it receives to the 'resolve' function of this Optimism resolver. The gateway server performs zero processing on its end, ensuring a completely transparent and trustless process for ENS resolution on the Optimism network.


## Resolving a Wildcard Domain

Many popular libraries such as ethers.js and web3.js support resolving of wildcard ENS domains out of the box. This functionality is also supported by many popular wallets, including MetaMask, Trust Wallet, and Uniswap Wallet.

## Contribution

Any contribution to the development of Wildcards Protocol is highly appreciated. You can contribute by:

- Suggesting or implementing new features.
- Reporting bugs and issues found within the protocol.
- Improving the code quality or documentation.


## License

Wildcards Protocol is released under the MIT License.

## Contact

If you have any questions, please feel free to reach out to us. You can [create an issue on GitHub](https://github.com/Wildcards-Protocol/Ethereum/issues) or contact us directly on [Twitter](https://twitter.com/wildcardswtf).
