---
sidebar_position: 1
---

# Progression


> *"What if someone bought out all our buildings and units only to sit on them? What if Aether became a world of hollow and abandoned buildings?"*

From the very beginning, we knew that fair distribution and growing a healthy community would be Aether’s greatest challenges. We need to both draw attention to the city, and to draw in an active community.
So we decided that Aether needed to be **designed for expansion**. Aether’s core contract composes NFT technology with finite property ownership and growth mechanics.

Aether's is a product of the next generation of Web3 decentralised applications, as such we were ambitiously writing rules and laws for city growth and progression. This makes Aether much more than just a PFP NFT project. In this next section we’ll give deeper into these mechanisms.

## Today

This is Aether today, set at `15` progression. Progression is the number of units away from origin `(0,0)`. As such, our 2018 minted properties currently occupy `30 x 30` in a `100 x 100` world. At the start of the relaunch we have promised to **lock this in for 6 months as our community stabilizes**. This initial community will serve as the backbone for all future growth in Aether.

<div style={{position:"relative", paddingBottom:"calc(64.35% + 44px)"}}><iframe src='https://gfycat.com/ifr/ShallowDishonestIsabellineshrike' frameborder='0' scrolling='no' width='100%' height='100%'style={{position:"absolute",top:0,left:0}} allowfullscreen></iframe></div>


> *Present Day: Progression 15 (`30 x 30`)*

## Expansion

Let’s talk about the expansion part of the AetherCore contract. This comes in two parts, **vertical** expansion and **horizontal** expansion. As a reminder, Aether is `100 x 100 x 100` world.

```jsx title="contracts-origin/AetherBase.sol"
/// @dev Ensures that property occupies unique part of the universe.
bool[100][100][100] public world;
```

> *Aether is a 100 x 100 x 100 Metaverse.*

### Horizontal Expansion

We will place additional buildings around `Generation 0` (2018-2021) Buildings. These new buildings extend out from the center origin at (0,0) and are pulled from the original world generative seed. Notice that these new buildings remain relatively flat. This is because progression limits their vertical size.

<div style={{position:"relative", paddingBottom:"calc(64.35% + 44px)"}}><iframe src='https://gfycat.com/ifr/LimpGreedyFinch' frameborder='0' scrolling='no' width='100%' height='100%'style={{position:"absolute",top:0,left:0}} allowfullscreen></iframe></div>

### Vertical Expansion

During vertical expansion we increase the world progression #. As defined in the contract, the height zoning of all buildings will be recalculated as function of progression. All of the buildings will grow in height with the buildings closest to the center having the highest potential.

```jsx title="contracts-origin/AetherBase.sol"
/// @dev Computing height of a building with respect to city progression.
function _computeHeight(
    uint256 _x,
    uint256 _z,
    uint256 _height
) internal view returns (uint256) {
    uint256 x = _x < 50 ? 50 - _x : _x - 50;
    uint256 z = _z < 50 ? 50 - _z : _z - 50;
    uint256 distance = x > z ? x : z;
    if (distance > progress) {
        return 1;
    }
    uint256 scale = 100 - (distance * 100) / progress ;
    uint256 height = 2 * progress * _height * scale / 10000;
    return height > 0 ? height : 1;
}
```
> *Function _computeHeight() in AetherCore*

<div style={{position:"relative", paddingBottom:"calc(64.35% + 44px)"}}><iframe src='https://gfycat.com/ifr/PoshOpulentGalapagoshawk' frameborder='0' scrolling='no' width='100%' height='100%'style={{position:"absolute",top:0,left:0}} allowfullscreen></iframe></div>

Expansion serves as a lever for world growth, as more people are interested in joining a community, we need units and buildings to facilitate. If units were too scarce, we would prematurely stifle growth and innovation. Ultimately, this contract allows us to facilitate growth at our community’s pace.

Aether’s value will be in its community and we strive to build the best of the best. The community is what will make Aether stand out in this future of a multiple metaverses.

> Do we want this be 250 people, or do we want this to be 10,000 people? What would make Aether truly succeed?

<!-- ## Evaluating Potential

We want to empower our community to make the right investments in the next 6 months leading to our expansion proposals. We hope that these new details will get you even more excited about the utility of our city.

### Building Owners

The community has already started to re-evaluate the utility of their buildings. A member of our community, @katalyst.eth put together a Discord bot to calculate a building’s potential.

In response, I have also shared with the community a Google Sheet outlining the current potential of genesis buildings today at each progression #. These have also been added as properties directly on OpenSea. Here are our 2018 buildings today, realised in their fullest potentials.

<div style={{position:"relative", paddingBottom:"calc(64.35% + 44px)"}}><iframe src='https://gfycat.com/ifr/VillainousWaterloggedGoat' frameborder='0' scrolling='no' width='100%' height='100%'style={{position:"absolute",top:0,left:0}} allowfullscreen></iframe></div>

> *2018 Genesis Buildings: Progression 50 (100 x 100)*

### Units Owners

This news of expansion could deflate the current market value of units. Penthouse units will also no longer hold such esteem once new units are minted above them.

However, we ask that properties owners to think of this opportunity in a different way. There are a finite number of 2018 and Generation 0 units. As an early member you are an insider, you have a chance to make your voice heard and influence our plans for expansion. In part of any expansion proposal we will need to come up with ways to reward Generation 0 who have supported the community. This could come in the form of property airdrops, special reservation to new properties, unit relocation, insider rewards and much more.

> What if owning a genesis unit meant you get insider access to Aether’s future potential?

### Utility

In the next 6 months our roadmap will aim to drive up utility of properties in Aether. We hope that these features will be meaningful for our current and future communities. It will come in the form of creating new social experiences and expressing a freedom that can only come with blockchain ownership. We hope that our community can leverage these next set of features in our roadmap for self expression and to make Aether lively and vibrant. We want people to really get excited about being here and in the prospect of joining us.

## The final question

So by now you might be wondering …. What does Aether look like when it has reached its expansion limits as set about in the contract?

> In all it’s potential, the city of Aether as designed in 2018, at full capacity. Progression 50.

<div style={{position:"relative", paddingBottom:"calc(64.35% + 44px)"}}><iframe src='https://gfycat.com/ifr/GrossCleanGuineafowl' frameborder='0' scrolling='no' width='100%' height='100%'style={{position:"absolute",top:0,left:0}} allowfullscreen></iframe></div>

> *The Dream: Progression 50 (100 x 100)*

While we’re not certain that we’ll make it this far, or how long it might take, we hope that someday people can visit Aether in its true form. Their first impressions being **“What a beautiful city.”** and before heading out **“What an amazing community!”** -->
