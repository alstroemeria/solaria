---
sidebar_position: 2
---

# Transfers

Transfer capability of Aether NFTs in OpenSea isn't working because our
constract doesn't include a `safeTransferFrom()` function. So do projects 
like CryptoKitties and Aether have `transfer()` instead? This is because 
these projects was deployed before the final EIP was standardized. 
You can read more NFT history in this thread. [GitHub ERC721](https://github.com/ethereum/eips/issues/721#issuecomment-342943495)

** What is the risk of the `transfer()` function? **`safeTransferFrom()` includes a check that the address a NFT is being
transfered to is able to interact with NFTs. In practice today, most 
transfer will already take into account the recipent address and this
added check is more of a safe measure. Other than this, `transfer()` has 
equivalent functionality. 


## Timeline
- **September 2017** - Dieter Shirley introduces EIP721.
- **December 2017** - CryptoKitties is so popular that it congests the Ethereum network and caused it to slow down significantly.
- **March 2018** - AetherCore contract is deployed with original transfer() function proposal
- **June 2018** - ERC721 is accepted as ‘final’, which means there is a strong consensus among Ethereum developers to accept it as a standard. transfer() is removed, safeTransferFrom() is included


## Transfering

You can transfer properties from the property page (ex: https://aethercity.org/32) by going into the owners settings (the `⚙ Gear` menu) and selecting the `Transfer` option

![Aether Property Setting](/img/aether-wiki-transfer.png)

