---
sidebar_position: 1
---

# Token Metadata

After ERC721 was finalized mid 2018, NFTs were required to provide a `tokenURI()` function.
This allows anyone to parse the image metadata and display an NFT. Unfortunately Aether does
not implement this function, nor do we have any onchain equivalent to store thumbnails.
Aether was always meant to be Metaverse first so we didn't consider that NFT ownership would also require an image preview.

## Metadata API

We use additional infrastructure to serve and host Aether
thumbnails and attributes. **OpenSea** uses this API to fetch up to date API data for each
Aether token. This is standard practice for NFTs that predate the `final` version of ERC721
and powers our OpenSea presence today.

![OpenSea](/img/aether-opensea.png)

Here's an example of the API we use to provide marketplaces Aether metadata.

```jsx title="https://api.aethercity.org/786"
// 20220211160627
// https://api.aethercity.org/786

{
  "name": "Aether 786",
  "description": "Property #786 (-7, 1) is a Unit located in Building 40.",
  "image": "https://aether-thumbnails.s3.amazonaws.com/786.png",
  "external_url": "https://aethercity.org/786",
  "attributes": [
    {
      "value": "Unit",
      "trait_type": "Type"
    },
    {
      "value": 7,
      "trait_type": "Distance From Center"
    },
    {
      "value": "1",
      "trait_type": "Land Area"
    },
    {
      "value": 1,
      "trait_type": "Land Area"
    },
    {
      "value": "2021",
      "trait_type": "Mint Year"
    },
    {
      "value": "Building 40",
      "trait_type": "Location"
    }
  ],
  "animation_url": "https://preview.aethercity.org/?id=786&zoom=1&x=-459&y=527&z=275"
}
```
