# Sample Metadata API for Non-Fungible Tokens (NFTs)

Use this repo to make an API for serving metadata about your tokens ([ERC-721](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-721.md) or [ERC-1155](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1155.md)) to marketplaces like [OpenSea](https://opensea.io) and other third parties. Metadata for each token can include an **image**, **animation**, **attributes**, **scalar properties**, **boost properties**, and more!

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

## Requirements
You need node.js (8.11.* or later) and npm installed. If you want to do a Heroku deployment, download and install the [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli) and run `heroku login` locally.

## Instructions

1. Click the **Deploy to Heroku** button above to instantly get it up and running somewhere. You can pick the URL! For this example, let's say that it's `your-metadata-api.herokuapp.com`.
2. Run `heroku git:clone -a your-metadata-api`, and `cd` into your new directory.
3. Run `npm install`.
4. Save the Heroku URL you picked into `src/constants.js` as the `HOST` variable (e.g. `https://your-metadata-api.herokuapp.com`). This is the root URL for the tokens on your contract.
5. Deploy to Heroku by committing your changes and using `git push heroku master`.
6. Visit your token's metadata at https://your-metadata-api.herokuapp.com/api/token/1 (for token 1).
7. Call [_setTokenURI](https://github.com/OpenZeppelin/openzeppelin-solidity/blob/1fd993bc01890bf6bd974aaf3d709bdf0a79b9bf/contracts/token/ERC721/ERC721Metadata.sol#L68) on your NFT's contract using the URL pattern above, either directly if you exposed that method for the contract `owner`, or by minting new tokens using [mintWithTokenURI](https://github.com/OpenZeppelin/openzeppelin-solidity/blob/master/contracts/token/ERC721/ERC721MetadataMintable.sol#L19).

If you're confused by the last step, here's a [tutorial on setting up a mintable NFT contract](https://docs.opensea.io/docs). Alternatively, you can have your buyers mint the tokens for you (and pay the gas to do that) at purchase-time, using the [OpenSea crowdsale tutorial](https://docs.opensea.io/docs/opensea-initial-item-sale-tutorial).

## Troubleshooting

If you have questions, contact the OpenSea team on [Discord](https://discord.gg/ga8EJbv). We're very responsive!
