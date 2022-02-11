---
sidebar_position: 2
---

# Metadata

Aether's contract was deployed on March 11, 2018 and is based off of
CryptoKitties contract written in 2017. Aether takes this new idea of an
NFT and introduces additional code for world definition, scarcity, 
expansion, zoning rules, and class inheritance. Together these new additions we 
were able to launch the first metaverse city back in 2018.

A front-end client parses this onchain metadata and builds a visualization on-top
of it to render Aether. In addition thanks to flexibily of our meta-data storage
we are also able to gradually evolve our clients as needed. Aether's contract can 
also be read by third-part clients as our location metadata is immortalized on chain.

## Core Data
Aether has its own field that defines metadata. Heres an example of how 
we store location information on chain. A property is allocated a unqiue position
in our `100 x 100 x 100` world. We also have fields that track parent relationships
to store connections between `units`, `buildings` and `districts`.

```jsx title="getProperty()"
  parent   uint32 :  1
  class   uint8 :  1
  x   uint8 :  44
  y   uint8 :  11
  z   uint8 :  56
  dx   uint8 :  1
  dz   uint8 :  1
  height   uint8 :  65
```

## Customizable Data
We also leverage a second metadata field that enables the owner to store any string.
This was so that properties are free to store any type of data on chain. This model
was intentionally chosen so that we can iterate on the storage model after the contract
is finalized.

```jsx title="propertyIndexToData()"
string :  {"vers":1
  "title":"Aspheris Tower"
  "desc":"Founder of Aether | BAYC #7018 | JustBricks #362"
  "image":"https://aether-image.s3.amazonaws.com/BAYC7018.png"
  "link":"https://twitter.com/aspheris"}
```

## Images & Attributes
After ERC721 was finalized mid 2018, NFTs were required to provide a `tokenURI()` function.
This allows anyone to parse the image metadata and display an NFT. Unfortunately Aether does
not implement this function, nor do we have any onchain equivalent to store thumbnails. 
Aether was always meant to be Metaverse first.

So how do we show our NFTs?  We use additional infrastructure to serve and host Aether 
thumbnails and attributes. OpenSea uses this API to fetch up to date API data from each 
Aether token. This is standard practice for NFTs that predate the `final` version of ERC721
and powers our OpenSea presence today.

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
