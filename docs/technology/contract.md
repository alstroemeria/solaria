---
sidebar_position: 1
---

# Smart Contract

Aether's contract ([AetherCore](https://etherscan.io/address/0x31d4c5be1082a88f2abafea549b6c189c2cf057f#code))
was deployed on March 11, 2018 and is based off of
CryptoKitties contract written in 2017. Aether takes this new idea of an
NFT and introduces additional code for world definition, scarcity, 
expansion, zoning rules, and class inheritance. Together these new additions we 
were able to launch the first metaverse city back in 2018.

A front-end client parses this onchain metadata and builds a visualization on-top
of it to render Aether. In addition thanks to flexibily of our meta-data storage
we are also able to gradually evolve our clients as needed. Aether's contract can 
also be read by third-part clients as our location metadata is stored on-chain.

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
{
  "vers":1
  "title":"Aspheris Tower"
  "desc":"Founder of Aether | BAYC #7018 | JustBricks #362"
  "image":"https://aether-image.s3.amazonaws.com/BAYC7018.png"
  "link":"https://twitter.com/aspheris"
}
```
