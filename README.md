# Sample Metadata API for Non-Fungible Tokens (NFTs) <!-- omit in toc -->

Use this repo to make an API for serving metadata about your tokens ([ERC-721](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-721.md) or [ERC-1155](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1155.md)) to marketplaces like [OpenSea](https://opensea.io) and other third parties.

Metadata for each token can include an image, animation, attributes, scalar properties, boost properties, and more!

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

- [Getting Started](#getting-started)
  - [Requirements](#requirements)
- [Minting Tokens](#minting-tokens)
- [Selling Tokens](#selling-tokens)
  - [Selling in Bulk](#selling-in-bulk)
- [Troubleshooting](#troubleshooting)

## Getting Started

### Requirements
You need node.js (8.11.* or later) and npm installed. If you want to do a Heroku deployment, download and install the [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli) and run `heroku login` locally.

1. Click the **Deploy to Heroku** button above to instantly get it up and running somewhere. You can pick the URL! For this example, let's say that it's `your-metadata-api.herokuapp.com`.
2. Run `heroku git:clone -a your-metadata-api`, and `cd` into your new directory.
3. Run `npm install`.
4. Save the Heroku URL you picked into `src/constants.js` as the `HOST` variable (e.g. `https://your-metadata-api.herokuapp.com`). This is the root URL for the tokens on your contract.
5. Deploy to Heroku by committing your changes and using `git push heroku master`.
6. Visit your token's metadata at https://your-metadata-api.herokuapp.com/api/token/1 (for token 1).

## Minting Tokens

Here's a [tutorial on setting up a mintable NFT contract](https://docs.opensea.io/docs). Alternatively, you can have your buyers mint the tokens for you (and pay the gas to do that) at purchase-time, using the [OpenSea Crowdsale Tutorial](https://docs.opensea.io/docs/opensea-initial-item-sale-tutorial).

Now that you a contract and a token URI for each of your tokens, there's a nice [mint.js script](https://github.com/ProjectOpenSea/opensea-creatures/blob/master/scripts/mint.js) that you can run locally to mint them on a testnet like Rinkeby and on mainnet Ethereum.

If you want more control over the minting process, call [_setTokenURI](https://github.com/OpenZeppelin/openzeppelin-solidity/blob/1fd993bc01890bf6bd974aaf3d709bdf0a79b9bf/contracts/token/ERC721/ERC721Metadata.sol#L68) on your NFT's contract using the URL pattern above, either directly if you exposed that method for the contract `owner`, or by minting new tokens using [mintWithTokenURI](https://github.com/OpenZeppelin/openzeppelin-solidity/blob/master/contracts/token/ERC721/ERC721MetadataMintable.sol#L19).

## Selling Tokens

If you're signed into MetaMask as the owner of your contract, you can click the "SELL" button on any asset to sell it immediately on OpenSea, using Dutch (declining price), English (to the highest bidder), and fixed-price auctions.

### Selling in Bulk

You can also use the OpenSea.js SDK to create sell orders. You can [create sell orders in bulk](https://github.com/ProjectOpenSea/opensea-js#running-crowdsales) if you followed the [Crowdsale Tutorial](https://docs.opensea.io/docs/opensea-initial-item-sale-tutorial) above.

## Troubleshooting

If you have questions, contact the OpenSea team on [Discord](https://discord.gg/ga8EJbv). We're very responsive!
