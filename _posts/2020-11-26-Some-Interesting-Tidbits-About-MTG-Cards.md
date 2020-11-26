---
layout: post
author: Nate Hofmann
---

As apart of my ever ongoing project [mtg-analysis](https://github.com/njhofmann/mtg-analysis), I created a small SQL database of every MTG card ever printed by drawing from the wonderful [Scryfall Api](scryfall.com/docs/api) - tracking card information, reprints, and other basic information. Combining this with the power of some simple SQL queries allows for some basic (but interesting!) questions to be answered.

First some caveats, underlying assumptions, and other info:

    1. Includes cards printed up until Commander Legends.
    
    2. Schemes, tokens, Avatars, Emblems, Planes, and other cards with "non-standard" types are not considered.  
    
    3. All printings are considered, this may give different numbers from Scryfall's listings. 
    
    4. For most answers, the top 5-10 results will be displayed. 

    5. Cards with multiple types have each type counted separately.

    6. Don't consider cards from Un-sets.

    7. Double faced cards are treated as one card.

If you have any questions about or suggestions for this article - please reach out to me!

## ___ cards with the most reprints?

### Overall

| Card                 | Reprints | 
| :------------------- | :------- | 
| [Giant Growth](https://scryfall.com/card/war/162/giant-growth)         | 46       | 
| [Serra Angel](https://scryfall.com/card/jmp/132/serra-angel)          | 43       |
| [Counterspell](https://scryfall.com/card/cmr/395/counterspell)         | 41       |
| [Disenchant](https://scryfall.com/card/cmr/372/disenchant)           | 40       |
| [Llanowar Elves](https://scryfall.com/card/m19/314/llanowar-elves)       | 40       |
| [Dark Ritual](https://scryfall.com/card/a25/82/dark-ritual)          | 39       |
| [Evolving Wilds](https://scryfall.com/card/cmr/482/evolving-wilds)       | 38       |
| [Swords to Plowshares](https://scryfall.com/card/cmr/387/swords-to-plowshares) | 35       |
| [Fireball](https://scryfall.com/card/ima/128/fireball)             | 33       |
| [Air Elemental](https://scryfall.com/card/m20/44/air-elemental)        | 32       | 

### Artifact

| Card                 | Reprints | 
| :------------------- | :------- |  
| [Sol Ring](https://scryfall.com/card/cmr/472/sol-ring)             |   31
| [Nevinyrral's Disk](https://scryfall.com/card/cmr/328/nevinyrrals-disk)    |   24
| [Juggernaut](https://scryfall.com/card/jmp/471/juggernaut)           |   22
| [Howling Mine](https://scryfall.com/card/c16/257/howling-mine)         |   21
| [Jayemdae Tome](https://scryfall.com/card/ori/231/jayemdae-tome)        |   21
| [Ornithopter](https://scryfall.com/card/klr/255/ornithopter           )          |   21
| [Rod of Ruin](https://scryfall.com/card/m14/217/rod-of-ruin)          |   20
| [Lightning Greaves](https://scryfall.com/card/2xm/267/lightning-greaves)    |   20
| [Meekstone](https://scryfall.com/card/7ed/307/meekstone)            |   17
| [Mana Vault](https://scryfall.com/card/uma/229/mana-vault)           |   17 

### Creatures

| Card                 | Reprints | 
| :------------------- | :------- |  
| [Serra Angel](https://scryfall.com/card/jmp/132/serra-angel)          | 43       |
| [Llanowar Elves](https://scryfall.com/card/m19/314/llanowar-elves)       | 40       |
| [Air Elemental](https://scryfall.com/card/m20/44/air-elemental)        | 32       | 
| [Shivan Dragon](https://scryfall.com/card/m20/335/shivan-dragon)        | 31       | 
| [Birds of Paradise](https://scryfall.com/card/cn2/176/birds-of-paradise)    | 30       | 
| [Sendir Vampire](https://scryfall.com/card/lea/127/sengir-vampire)       | 29       | 
| [Giant Spider](https://scryfall.com/card/m19/183/giant-spider)         | 29       | 
| [Gravedigger](https://scryfall.com/card/m20/103/gravedigger)          | 27       | 
| [MMahamoti Djinn](https://scryfall.com/card/uma/64/mahamoti-djinn)         | 23       | 
| [Juggernaut](https://scryfall.com/card/jmp/471/juggernaut)           | 22       | 

### Legendary 

| Card                     | Reprints
| :-                       | :-
| [Niv-Mizzet, the Firemind](https://scryfall.com/card/c20/225/niv-mizzet-the-firemind) |   10
| [Talrand, Sky Summoner](https://scryfall.com/card/jmp/181/talrand-sky-summoner)    |    9
| [Reya Dawnbringer](https://scryfall.com/card/uma/32/reya-dawnbringer)         |    9
| [Kamahl, Pit Fighter](https://scryfall.com/card/arc/61/kamahl-fist-of-krosa)      |    9
| [Karakas](https://scryfall.com/card/uma/244/karakas)                  |    8
| [Emrakul, the Aeons Torn](https://scryfall.com/card/plist/2/emrakul-the-aeons-torn)  |    8
| [Bladewing the Risen](https://scryfall.com/card/ima/193/bladewing-the-risen)      |    8
| [Arcanis the Omnipotent](https://scryfall.com/card/c17/80/arcanis-the-omnipotent)   | 7
| [Nezumi Graverobber // Nighteyes the Descreator](https://scryfall.com/card/plist/108/nezumi-graverobber-nighteyes-the-desecrator) | 7
| [Ryuesi, the Falling Start](https://scryfall.com/card/ima/144/ryusei-the-falling-star) | 7

### Enchantments

| Card                        | Reprints | 
| :-------------------------- | :------- |
| [Pacifism](https://scryfall.com/card/jmp/125/pacifism)                    |   31
| [Circle of Protection: Red](https://scryfall.com/card/9ed/11/circle-of-protection:-red)   |   24
| [Lure](https://scryfall.com/card/ima/175/lure)                        |   22
| [Unholy Strength](https://scryfall.com/card/dvd/47/unholy-strength)             |   22
| [Circle of Protection: Black](https://scryfall.com/card/9ed/10/circle-of-protection:-black) |   21
| [Control Magic](https://scryfall.com/card/cma/34/control-magic)               |   19
| [Regeneration](https://scryfall.com/card/10e/290/regeneration)                |   18
| [Holy Strength](https://scryfall.com/card/m11/16/holy-strength)               |   18
| [Fear](https://scryfall.com/card/10e/142/fear)                        |   17
| [Firebreathing](https://scryfall.com/card/m12/132/firebreathing)               |   17

### Instants

| Card                 | Reprints | 
| :------------------- | :------- | 
| [Giant Growth](https://scryfall.com/card/war/162/giant-growth)         |   46
| [Counterspell](https://scryfall.com/card/cmr/395/counterspell)        |   41
| [Disenchant](https://scryfall.com/card/cmr/372/disenchant)           |   40
| [Dark Ritual](https://scryfall.com/card/a25/82/dark-ritual)          |   39
| [Swords to Plowshares](https://scryfall.com/card/cmr/387/swords-to-plowshares) |   35
| [Unsummon](https://scryfall.com/card/m20/78/unsummon)             |   29
| [Lightning Bolt](https://scryfall.com/card/jmp/342/lightning-bolt)       |   29
| [Shock](https://scryfall.com/card/m21/159/shock)                |   26
| [Shatter](https://scryfall.com/card/m21/159/shock)              |   26
| [Terror](https://scryfall.com/card/me4/99/terror)               |   26

### Land

| Card                    | Reprints | 
| :---------------------- | :------- | 
| [Evolving Wilds](https://scryfall.com/card/cmr/482/evolving-wilds)          |   38
| [Terramorphic Expanse](https://scryfall.com/card/cmr/357/terramorphic-expanse)    |   31
| [Forgotten Cave](https://scryfall.com/card/cmr/483/forgotten-cave)          |   20
| [Secluded Steppe](https://scryfall.com/card/cmr/491/secluded-steppe)         |   19
| [City of Brass](https://scryfall.com/card/mma/221/city-of-brass)           |   19
| [Tranquil Thicket](https://scryfall.com/card/mh1/248/tranquil-thicket)        |   18
| [Command Tower](https://scryfall.com/card/cmr/350/command-tower)           |   18
| [Barren Moor](https://scryfall.com/card/c19/229/barren-moor)             |   18
| [Selesnya Sanctuary](https://scryfall.com/card/znc/140/selesnya-sanctuary)      |   18
 [Temple of the False God](https://scryfall.com/card/c20/319/temple-of-the-false-god)  |   17

### Sorceries

| Card                 | Reprints | 
| :------------------- | :------- | 
| [Fireball](https://scryfall.com/card/ima/128/fireball)             |   33
| [Wrath of God](https://scryfall.com/card/plist/43/wrath-of-god)         |   32
| [Stone Rain](https://scryfall.com/card/plist/156/stone-rain)           |   29
| [Duress](https://scryfall.com/card/m21/96/duress)               |   27
| [Armageddon](https://scryfall.com/card/a25/5/armageddon)           |   27
| [Rampant Growth](https://scryfall.com/card/cmr/432/rampant-growth)       |   25
| [Mind Rot](https://scryfall.com/card/klr/101/mind-rot)             |   25
| [Hurricane](https://scryfall.com/card/10e/270/hurricane)            |   24
| [Earthquake](https://scryfall.com/card/cm2/95/earthquake)           |   24
| [Raise Dead](https://scryfall.com/card/w17/18/raise-dead)           |   23


### Planeswalkers

| Card | Reprints |
| :--- | :--- |
| [Garruk Wildspeaker](https://scryfall.com/card/gvl/1/garruk-wildspeaker) | 8 |
| [Jace Beleren](https://scryfall.com/card/jvc/1/jace-beleren) | 8 |
| [Liliana Vess](https://scryfall.com/card/gvl/32/liliana-vess) | 8 |
| [Jace, the Mind Sculptor](https://scryfall.com/card/2xm/56/jace-the-mind-sculptor) | 7 |
| [Chandra, Torch of Defiance](https://scryfall.com/card/klr/117/chandra-torch-of-defiance) | 7 |
| [Chandra, Pyromaster](https://scryfall.com/card/e01/42/chandra-pyromaster) | 7 |
| [Daretti, Scrap Savant](https://scryfall.com/card/cm2/4/daretti-scrap-savant) | 6 |
| [Liliana of the Veil](https://scryfall.com/card/gvl/32/liliana-vess) | 6 |
| [Gideon of the Trials](https://scryfall.com/card/akh/14/gideon-of-the-trials) | 6 |
| [Gideon Jura](https://scryfall.com/card/e01/10/gideon-jura) | 6 |


### Tribes (elves, goblins, etc.)

Doesn't consider supertypes like creature, legendary, etc.

| Type      | Count 
| :-------- | :---
| human     |  2529
| warrior   |   800
| wizard    |   791
| soldier   |   716
| zombie    |   513
| elemental |   499
| spirit    |   488
| cleric    |   441
| beast     |   437
| elf       |   429

### Secondary Tribes (elf warriors, goblin scouts, etc.)

Doesn't consider supertypes like creature, legendary, etc.

| First Type | Second Type | Count |
| :--- | :--- | :--- |
| human | wizard | 406 |
| human | soldier | 364 |
| human | cleric | 244 |
| human | knight | 193 |
| human | warrior | 193 |
| human | rogue | 113 |
| human | shaman | 97 |
| goblin | warrior | 93 |
| merfolk | wizard | 90 |
| elf | druid | 76 |


## Number of unique cards printed by ___? 

### Color

`c` is for colorless cards, multicolored cards are considered twice.

| Color | Count |
| :--- | :--- |
| w | 4273 |
| b | 4248 |
| r | 4208 |
| u | 4188 |
| g | 4177 |
| c | 311 |

### Type

Major types like creature, artifact, etc.

| Type | Count |
| :--- | :--- |
| creature | 11593 |
| enchantment | 2599 |
| instant | 2596 |
| sorcery | 2384 |
| artifact | 2169 |
| planeswalker | 228 |

## Cards with the most text?

Does include reminder text; text for suspend, cumulative upkeep, and banding are the longest contributors.

| card | Text Size |
| :--- | :--- |
| [Dance of the Dead](https://scryfall.com/card/me2/83/dance-of-the-dead) | 657 |
| [Master of the Wild Hunt](https://scryfall.com/card/me2/83/dance-of-the-dead) | 627 |
| [Camouflage](https://scryfall.com/card/2ed/188/camouflage) | 589 |
| [Riftmarked Knight](https://scryfall.com/card/plc/14/riftmarked-knight) | 580 |
| [Takklemaggot](https://scryfall.com/card/me3/76/takklemaggot) | 561 |
| [Necromancy](https://scryfall.com/card/plist/107/necromancy) | 552 |
| [Tombstone Stairwell](https://scryfall.com/card/mir/149/tombstone-stairwell) | 543 |
| [Illusionary Mask](https://scryfall.com/card/me3/197/illusionary-mask) | 534 |
| [Roiling Horror](https://scryfall.com/card/plc/79/roiling-horror) | 531 |
| [Nalathni Dragon](https://scryfall.com/card/plc/79/roiling-horror) | 515 |

## Cards with the most subtypes?

Only really interesting entry here is that only one creature has four subtypes

| Card | Number of Types |
| :--- | :--- |
| [Seton's Scout](https://scryfall.com/card/tor/138/setons-scout) | 4 |

## Cards with the longest name?

This does include spaces.

| Card | Name Length |
| :- | :- 
| [Okina, Temple to the Grandfathers](https://scryfall.com/card/chk/280/okina-temple-to-the-grandfathers) | 33
| [Circle of Protection: Artifacts](https://scryfall.com/card/5dn/8/circle-of-protection:-artifacts) | 31 
| [Oviya Pashiri, Sage Lifecrafter](https://scryfall.com/card/klr/174/oviya-pashiri-sage-lifecrafter) | 31
| [Sunhome, Fortress of the Legion](https://scryfall.com/card/cmr/496/sunhome-fortress-of-the-legion) | 31 
| [The Tabernacle at Pendrell Vale](https://scryfall.com/card/me3/212/the-tabernacle-at-pendrell-vale) | 31
| [Hanweir, the Writhing Township](https://scryfall.com/card/emn/130b/hanweir-the-writhing-township) | 30
| [Ib Halfheart, Goblin Tactician](https://scryfall.com/card/emn/130b/hanweir-the-writhing-township) | 30
| [Kroxa, Titan of Death's Hunger](https://scryfall.com/card/thb/221/kroxa-titan-of-deaths-hunger) | 30
| [Minamo, School at Water's Edge](https://scryfall.com/card/chk/279/minamo-school-at-waters-edge) | 30
| [Rebbec, Architect of Ascension](https://scryfall.com/card/cmr/42/rebbec-architect-of-ascension) | 30
| [Tezzeret, Master of the Bridge](https://scryfall.com/card/war/275/tezzeret-master-of-the-bridge) | 30 

## Average converted mana cost of every MTG set ___?

Only considering "main" sets; core releases, major expansions, etc. - not supplemental products, promotional products, etc. Does consider lands.

| Card | Average CMC
| :- | :-
| Fifth Dawn | 3.933
| Scourge | 3.9091
| Alara Reborn | 3.876
| Legions | 3.848
| Dragon's Maze | 3.648
| Prophecy | 3.594
| Darksteel | 3.5576
| New Phyrexia | 3.517
| Battlebond | 3.492
| Mirrodin Besieged | 3.48

## Average power and toughness of every creature?

Ignoring cards with a variable power or toughness.

| Avg Power | Avg Toughness |
| :--- | :--- |
| 2.5708 | 2.7551   |

## Most common power & toughness pairings?

| Power | Toughness | Count |
| :--- | :--- | :--- |
| 2 | 2 | 1929 |
| 1 | 1 | 1618 |
| 3 | 3 | 1095 |
| 2 | 1 | 701 |
| 4 | 4 | 648 |
| 2 | 3 | 542 |
| 3 | 2 | 427 |
| 1 | 2 | 384 |
| 5 | 5 | 370 |
| 1 | 3 | 308 |

## Least common power & toughness pairings?

These all seemed worthwhile to include

| Power | Toughness | Count |
| :--- | :--- | :--- |
| 7 | 8 | 1 |
| 6 | 9 | 1 |
| 1 | 0 | 1 |
| 10 | 6 | 1 |
| -1 | -1 | 1 |
| 4 | 0 | 1 |
| 9 | 5 | 1 |
| 9 | 10 | 1 |
| 5 | 9 | 1 |
| 16 | 16 | 1 |
| 1 | 8 | 1 |
| 10 | 4 | 1 |
| 9 | 14 | 1 |
| 2 | 10 | 1 |
| 8 | 9 | 1 |
| 8 | 0 | 1 |
| 10 | 9 | 1 |
| 7 | 1 | 1 |
| 9 | 3 | 1 |
| 7 | 10 | 1 |
| 10 | 7 | 1 |
| 0 | 17 | 1 |
| 9 | 8 | 1 |
| 9 | 7 | 1 |
| -1 | 3 | 1 |
| 10 | 2 | 1 |
| 11 | 9 | 1 |
| 3 | 8 | 1 |