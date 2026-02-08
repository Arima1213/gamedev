# Item Database
## Mining Materials & Minerals Catalog

---

### Document Information
**Database Type:** Mining Materials  
**Version:** 1.0  
**Last Updated:** February 8, 2026  
**Maintainer:** Content Team

---

## Usage Instructions

**For Designers:**
- Add new mineral entries following the template
- Balance spawn rates with economic value
- Coordinate with Economy team for pricing
- Ensure crafting material tiers align with systems

**For Developers:**
- Use MineralID as unique database key
- Implement spawn weights based on rarity
- Validate tool requirements for mining
- Handle geode loot table generation

---

## Material Entry Template

```
MineralID: MIN_XXX
Name: Mineral Display Name
Rarity: Common/Rare/Epic/Legendary/Mythic
Category: Ore/Gem/Crystal/Special
Tool Required: Pickaxe (Tier X+)
Source Rock Type: Stone/Granite/Obsidian/Special
Spawn Weight: X% (in appropriate zones)
Zone Location: Mining Zone A/B/C/D
Mining Time: X seconds
Durability Damage: X per hit
Sell Value (NPC): X IRF
Stack Size: Max 100/50/25/10
Uses: Crafting/Trading/Alchemy/Decoration
Description: "Flavor text about the mineral."
Crafting Category: Weapons/Armor/Tools/Jewelry/Construction
Special Properties: Any unique attributes
Geode Drop: Can drop from Geode Type (X% chance)
```

---

## Common Ores & Materials

### STONE TIER (Grey - Basic Materials)

#### MIN_001: Stone
- **MineralID:** MIN_001
- **Name:** Stone
- **Rarity:** Common
- **Category:** Basic Material
- **Tool Required:** Any Pickaxe
- **Source Rock Type:** Stone nodes (everywhere)
- **Spawn Weight:** 60%
- **Zone Location:** All Mining Zones
- **Mining Time:** 1 second per hit
- **Durability Damage:** 1 per stone
- **Sell Value:** 1 IRF
- **Stack Size:** 100
- **Uses:** Construction, basic crafting, pathways
- **Description:** "Ordinary stone. The foundation of any miner's collection."
- **Crafting Category:** Construction blocks, basic tools
- **Special Properties:** Used in nearly all construction recipes

#### MIN_002: Coal
- **MineralID:** MIN_002
- **Name:** Coal
- **Rarity:** Common
- **Category:** Fuel
- **Tool Required:** Any Pickaxe
- **Source Rock Type:** Stone nodes
- **Spawn Weight:** 25%
- **Zone Location:** Mining Zone A, B
- **Mining Time:** 1 second
- **Durability Damage:** 1
- **Sell Value:** 3 IRF
- **Stack Size:** 100
- **Uses:** Fuel, smelting, basic crafting
- **Description:** "Dark combustible mineral. Essential for smelting operations."
- **Crafting Category:** Furnace fuel, torch crafting
- **Special Properties:** Burns for 60 seconds in furnaces

#### MIN_003: Copper Ore
- **MineralID:** MIN_003
- **Name:** Copper Ore
- **Rarity:** Common
- **Category:** Ore
- **Tool Required:** Any Pickaxe
- **Source Rock Type:** Stone nodes
- **Spawn Weight:** 20%
- **Zone Location:** Mining Zone A, B
- **Mining Time:** 2 seconds
- **Durability Damage:** 2
- **Sell Value:** 8 IRF
- **Stack Size:** 100
- **Uses:** Copper ingots, basic tools/weapons, wiring
- **Description:** "Reddish-brown ore. First metal most miners discover."
- **Crafting Category:** Basic weapons, tools, construction materials
- **Geode Drop:** Common Geode (5%)

#### MIN_004: Tin Ore
- **MineralID:** MIN_004
- **Name:** Tin Ore
- **Rarity:** Common
- **Category:** Ore
- **Tool Required:** Any Pickaxe
- **Source Rock Type:** Stone nodes
- **Spawn Weight:** 18%
- **Zone Location:** Mining Zone A, B
- **Mining Time:** 2 seconds
- **Durability Damage:** 2
- **Sell Value:** 7 IRF
- **Stack Size:** 100
- **Uses:** Bronze crafting (with Copper), canning
- **Description:** "Silvery metal that combines well with copper."
- **Crafting Category:** Bronze alloys, containers
- **Geode Drop:** Common Geode (5%)

---

## Rare Ores & Gems

### RARE TIER (Blue)

#### MIN_005: Iron Ore
- **MineralID:** MIN_005
- **Name:** Iron Ore
- **Rarity:** Rare
- **Category:** Ore
- **Tool Required:** Copper Pickaxe+
- **Source Rock Type:** Granite nodes
- **Spawn Weight:** 15%
- **Zone Location:** Mining Zone B (Cave), C (Deep Cave)
- **Mining Time:** 3 seconds
- **Durability Damage:** 3
- **Sell Value:** 25 IRF
- **Stack Size:** 100
- **Uses:** Iron equipment, advanced crafting, rails
- **Description:** "Sturdy grey ore. Backbone of intermediate equipment."
- **Crafting Category:** Intermediate weapons/armor/tools
- **Geode Drop:** Rare Geode (10%)

#### MIN_006: Silver Ore
- **MineralID:** MIN_006
- **Name:** Silver Ore
- **Rarity:** Rare
- **Category:** Ore
- **Tool Required:** Copper Pickaxe+
- **Source Rock Type:** Granite nodes
- **Spawn Weight:** 10%
- **Zone Location:** Mining Zone B, C
- **Mining Time:** 3 seconds
- **Durability Damage:** 3
- **Sell Value:** 40 IRF
- **Stack Size:** 100
- **Uses:** Jewelry, silver weapons (bonus vs undead), currency crafting
- **Description:** "Shining white metal. Valuable for trade and crafting."
- **Crafting Category:** Jewelry, special weapons, decorative items
- **Special Properties:** Weapons deal +20% damage to undead enemies
- **Geode Drop:** Rare Geode (12%)

#### MIN_007: Gold Ore
- **MineralID:** MIN_007
- **Name:** Gold Ore
- **Rarity:** Rare
- **Category:** Ore
- **Tool Required:** Iron Pickaxe+
- **Source Rock Type:** Granite nodes
- **Spawn Weight:** 8%
- **Zone Location:** Mining Zone C (Deep Cave)
- **Mining Time:** 4 seconds
- **Durability Damage:** 4
- **Sell Value:** 60 IRF
- **Stack Size:** 100
- **Uses:** Jewelry, gold coins, high-end crafting
- **Description:** "Precious yellow metal that never tarnishes. Symbol of wealth."
- **Crafting Category:** Jewelry, decorative blocks, currency
- **Special Properties:** Can be crafted into collectible gold coins
- **Geode Drop:** Rare Geode (15%)

#### MIN_008: Sapphire
- **MineralID:** MIN_008
- **Name:** Sapphire
- **Rarity:** Rare
- **Category:** Gem
- **Tool Required:** Iron Pickaxe+
- **Source Rock Type:** Granite nodes, Geodes
- **Spawn Weight:** 5%
- **Zone Location:** Mining Zone C
- **Mining Time:** 4 seconds
- **Durability Damage:** 3
- **Sell Value:** 100 IRF
- **Stack Size:** 50
- **Uses:** Jewelry, magic weapons, enchantments
- **Description:** "Deep blue gemstone. Highly prized by jewelers and enchanters."
- **Crafting Category:** High-end jewelry, magic item enhancement
- **Special Properties:** +5% magic damage when used in weapon crafting
- **Geode Drop:** Rare Geode (20%), Epic Geode (5%)

#### MIN_009: Ruby
- **MineralID:** MIN_009
- **Name:** Ruby
- **Rarity:** Rare
- **Category:** Gem
- **Tool Required:** Iron Pickaxe+
- **Source Rock Type:** Granite nodes, Geodes
- **Spawn Weight:** 5%
- **Zone Location:** Mining Zone C
- **Mining Time:** 4 seconds
- **Durability Damage:** 3
- **Sell Value:** 100 IRF
- **Stack Size:** 50
- **Uses:** Jewelry, fire weapons, enchantments
- **Description:** "Brilliant red gemstone that seems to glow with inner fire."
- **Crafting Category:** Jewelry, fire-elemental weapons
- **Special Properties:** +5% fire damage when used in weapon crafting
- **Geode Drop:** Rare Geode (20%), Epic Geode (5%)

#### MIN_010: Emerald
- **MineralID:** MIN_010
- **Name:** Emerald
- **Rarity:** Rare
- **Category:** Gem
- **Tool Required:** Iron Pickaxe+
- **Source Rock Type:** Granite nodes, Geodes
- **Spawn Weight:** 5%
- **Zone Location:** Mining Zone C
- **Mining Time:** 4 seconds
- **Durability Damage:** 3
- **Sell Value:** 100 IRF
- **Stack Size:** 50
- **Uses:** Jewelry, nature weapons, healing potions
- **Description:** "Vibrant green gem associated with life and growth."
- **Crafting Category:** Jewelry, nature-elemental items, alchemy
- **Special Properties:** +10% healing effect in potion crafting
- **Geode Drop:** Rare Geode (20%), Epic Geode (5%)

---

## Epic Materials & Crystals

### EPIC TIER (Purple)

#### MIN_011: Titanium Ore
- **MineralID:** MIN_011
- **Name:** Titanium Ore
- **Rarity:** Epic
- **Category:** Ore
- **Tool Required:** Steel Pickaxe+
- **Source Rock Type:** Obsidian nodes
- **Spawn Weight:** 6%
- **Zone Location:** Mining Zone D (Volcanic Core)
- **Mining Time:** 5 seconds
- **Durability Damage:** 5
- **Sell Value:** 200 IRF
- **Stack Size:** 50
- **Uses:** High-end equipment, spacecraft parts (future)
- **Description:** "Incredibly strong and lightweight metal. Used in advanced engineering."
- **Crafting Category:** Epic weapons/armor, advanced machinery
- **Special Properties:** Equipment has 50% more durability
- **Geode Drop:** Epic Geode (15%)

#### MIN_012: Platinum Ore
- **MineralID:** MIN_012
- **Name:** Platinum Ore
- **Rarity:** Epic
- **Category:** Ore
- **Tool Required:** Steel Pickaxe+
- **Source Rock Type:** Obsidian nodes
- **Spawn Weight:** 4%
- **Zone Location:** Mining Zone D
- **Mining Time:** 5 seconds
- **Durability Damage:** 5
- **Sell Value:** 300 IRF
- **Stack Size:** 50
- **Uses:** Premium jewelry, rare crafting, catalyst
- **Description:** "Rarest precious metal. Silvery-white and highly resistant to corrosion."
- **Crafting Category:** Luxury jewelry, high-end decorations
- **Special Properties:** Never degrades or tarnishes
- **Geode Drop:** Epic Geode (18%)

#### MIN_013: Diamond
- **MineralID:** MIN_013
- **Name:** Diamond
- **Rarity:** Epic
- **Category:** Gem
- **Tool Required:** Gold Pickaxe+
- **Source Rock Type:** Obsidian nodes, Geodes
- **Spawn Weight:** 3%
- **Zone Location:** Mining Zone D
- **Mining Time:** 6 seconds
- **Durability Damage:** 4
- **Sell Value:** 500 IRF
- **Stack Size:** 25
- **Uses:** Top-tier equipment, jewelry, cutting tools
- **Description:** "Hardest natural material. Crystal clear and brilliantly refractive."
- **Crafting Category:** Epic weapons/armor/tools, premium jewelry
- **Special Properties:** Equipment has +25% damage/armor value
- **Geode Drop:** Epic Geode (25%), Legendary Geode (5%)

#### MIN_014: Amethyst Crystal
- **MineralID:** MIN_014
- **Name:** Amethyst Crystal
- **Rarity:** Epic
- **Category:** Crystal
- **Tool Required:** Gold Pickaxe+
- **Source Rock Type:** Crystal formations, Geodes
- **Spawn Weight:** 4%
- **Zone Location:** Mining Zone C, D (Crystal Cavern)
- **Mining Time:** 5 seconds
- **Durability Damage:** 3
- **Sell Value:** 400 IRF
- **Stack Size:** 25
- **Uses:** Magic amplification, alchemy, decoration
- **Description:** "Purple crystal cluster that resonates with magical energy."
- **Crafting Category:** Magic weapons, enchantment focus, crystalware
- **Special Properties:** +15% magic power in enchanted items
- **Geode Drop:** Epic Geode (20%)

#### MIN_015: Obsidian
- **MineralID:** MIN_015
- **Name:** Obsidian
- **Rarity:** Epic
- **Category:** Volcanic Glass
- **Tool Required:** Diamond Pickaxe+
- **Source Rock Type:** Obsidian nodes (Volcanic Zone only)
- **Spawn Weight:** 8%
- **Zone Location:** Mining Zone D (Volcanic Core)
- **Mining Time:** 8 seconds (very tough)
- **Durability Damage:** 6
- **Sell Value:** 350 IRF
- **Stack Size:** 50
- **Uses:** Sharp weapons, portal frames (future), construction
- **Description:** "Jet-black volcanic glass. Extremely sharp when fractured."
- **Crafting Category:** Obsidian weapons (highest sharpness), portals
- **Special Properties:** Weapons have +30% critical damage
- **Geode Drop:** Epic Geode (10%)

---

## Legendary Materials

### LEGENDARY TIER (Gold)

#### MIN_016: Mithril Ore
- **MineralID:** MIN_016
- **Name:** Mithril Ore
- **Rarity:** Legendary
- **Category:** Ore (Mythical Metal)
- **Tool Required:** Diamond Pickaxe+
- **Source Rock Type:** Special Mithril nodes (rare spawns)
- **Spawn Weight:** 1.5%
- **Zone Location:** Mining Zone D (Volcanic Core, deepest sections)
- **Mining Time:** 10 seconds
- **Durability Damage:** 7
- **Sell Value:** 2,000 IRF
- **Stack Size:** 25
- **Uses:** Legendary equipment, magic conductors
- **Description:** "Silvery-blue mythical metal, light as a feather yet stronger than steel."
- **Crafting Category:** Legendary weapons/armor
- **Special Properties:** 
  - Equipment weighs 50% less (no speed penalty)
  - +40% magic conductivity
  - Natural enchantment resistance
- **Geode Drop:** Legendary Geode (20%)

#### MIN_017: Adamantite Ore
- **MineralID:** MIN_017
- **Name:** Adamantite Ore
- **Rarity:** Legendary
- **Category:** Ore (Indestructible Metal)
- **Tool Required:** Mithril Pickaxe only
- **Source Rock Type:** Adamantite nodes (extremely rare)
- **Spawn Weight:** 1%
- **Zone Location:** Mining Zone D (bottom layer only)
- **Mining Time:** 12 seconds
- **Durability Damage:** 8
- **Sell Value:** 3,000 IRF
- **Stack Size:** 10
- **Uses:** Ultimate equipment, indestructible structures
- **Description:** "Nearly indestructible black metal. Legends say it fell from the stars."
- **Crafting Category:** Legendary armor/shields, vault construction
- **Special Properties:**
  - Equipment has 5× normal durability
  - Armor provides +50% damage reduction
  - Cannot be broken by normal means
- **Geode Drop:** Legendary Geode (15%), Mythic Geode (3%)

#### MIN_018: Star Sapphire
- **MineralID:** MIN_018
- **Name:** Star Sapphire
- **Rarity:** Legendary
- **Category:** Gem (Celestial)
- **Tool Required:** Diamond Pickaxe+
- **Source Rock Type:** Geodes only
- **Spawn Weight:** 0.8% (node), Geode primary
- **Zone Location:** Mining Zone D
- **Mining Time:** 8 seconds
- **Durability Damage:** 4
- **Sell Value:** 4,000 IRF
- **Stack Size:** 10
- **Uses:** Legendary jewelry, star magic, navigation
- **Description:** "Rare sapphire with a six-pointed star visible within. Guides lost travelers."
- **Crafting Category:** Legendary jewelry, celestial magic items
- **Special Properties:**
  - +20% magic power
  - Jewelry provides navigation bonus (compass effect)
  - Glows in darkness
- **Geode Drop:** Legendary Geode (30%)

#### MIN_019: Black Diamond
- **MineralID:** MIN_019
- **Name:** Black Diamond
- **Rarity:** Legendary
- **Category:** Gem (Dark)
- **Tool Required:** Mithril Pickaxe+
- **Source Rock Type:** Obsidian nodes (ultra-rare), Geodes
- **Spawn Weight:** 0.5%
- **Zone Location:** Mining Zone D (Volcanic Core)
- **Mining Time:** 10 seconds
- **Durability Damage:** 5
- **Sell Value:** 5,000 IRF
- **Stack Size:** 10
- **Uses:** Dark enchantments, legendary weapons, prestige jewelry
- **Description:** "Jet-black diamond that seems to absorb light. Mysterious and powerful."
- **Crafting Category:** Dark magic items, legendary equipment
- **Special Properties:**
  - Weapons deal +50% damage
  - Absorbs 10% of damage as health drain
  - Shadow effects
- **Geode Drop:** Legendary Geode (25%), Mythic Geode (5%)

---

## Mythic Crystals & Cosmic Materials

### MYTHIC TIER (Red)

#### MIN_020: Celestium Crystal
- **MineralID:** MIN_020
- **Name:** Celestium Crystal
- **Rarity:** Mythic
- **Category:** Crystal (Cosmic)
- **Tool Required:** Adamantite Pickaxe only
- **Source Rock Type:** Celestium nodes (extremely rare, glowing)
- **Spawn Weight:** 0.3%
- **Zone Location:** Mining Zone D (deepest layer), Meteorite crash sites (random world events)
- **Mining Time:** 15 seconds
- **Durability Damage:** 10
- **Sell Value:** 15,000 IRF
- **Stack Size:** 5
- **Uses:** Mythic equipment, cosmic magic, ultimate crafting
- **Description:** "Crystallized starlight from beyond this world. Pulses with cosmic energy."
- **Crafting Category:** Mythic weapons/armor, cosmic magic items
- **Special Properties:**
  - Equipment glows with stellar particles
  - +100% magic power
  - Grants "Starborne" buff (various bonuses)
  - Never degrades
- **Geode Drop:** Mythic Geode (40%)
- **Special Notes:** Can rarely be found at meteorite crash sites (special world event)

#### MIN_021: Void Crystal
- **MineralID:** MIN_021
- **Name:** Void Crystal
- **Rarity:** Mythic
- **Category:** Crystal (Void)
- **Tool Required:** Adamantite Pickaxe only
- **Source Rock Type:** Void Rifts (rare dimensional tears in deepest mines)
- **Spawn Weight:** 0.2%
- **Zone Location:** Mining Zone D (Void Rifts - random spawn events)
- **Mining Time:** 20 seconds
- **Durability Damage:** 12
- **Sell Value:** 20,000 IRF
- **Stack Size:** 5
- **Uses:** Void magic, dimensional crafting, ultimate weapons
- **Description:** "Dark purple crystal that exists between dimensions. Looking into it shows glimpses of other worlds."
- **Crafting Category:** Void weapons, dimensional magic, teleportation
- **Special Properties:**
  - Weapons ignore 50% of armor
  - Grants brief invulnerability on hit (void phase)
  - Teleportation abilities
  - Void particle effects
- **Geode Drop:** Mythic Geode (30%)
- **Special Notes:** Mining triggers minor void enemies spawn, high risk/high reward

#### MIN_022: Dragon Heart Gem
- **MineralID:** MIN_022
- **Name:** Dragon Heart Gem
- **Rarity:** Mythic
- **Category:** Gem (Draconic)
- **Tool Required:** Mythic Pickaxe
- **Source Rock Type:** Dragon Geodes ONLY (from defeating dragons)
- **Spawn Weight:** N/A (Boss drop only)
- **Zone Location:** Dragon boss lairs
- **Mining Time:** N/A (boss reward)
- **Durability Damage:** N/A
- **Sell Value:** 50,000 IRF (but almost no one sells these)
- **Stack Size:** 1 (unique)
- **Uses:** Ultimate dragon equipment, dragon transformation magic
- **Description:** "Crystallized essence of a dragon's heart. Burns with eternal flame and ancient power."
- **Crafting Category:** Dragon-tier equipment, transformation items
- **Special Properties:**
  - Crafted equipment grants dragon abilities (flight, breath weapon)
  - +200% fire damage
  - Fire immunity
  - Dragon aura effects
- **Geode Drop:** Dragon Geode (100% - boss reward container)
- **Special Notes:** Each dragon drops only ONE gem. Legendary prestige item.

#### MIN_023: Aether Opal
- **MineralID:** MIN_023
- **Name:** Aether Opal
- **Rarity:** Mythic
- **Category:** Gem (Elemental Fusion)
- **Tool Required:** Mythic Pickaxe
- **Source Rock Type:** Mythic Geodes, Elemental Convergence nodes (ultra-rare)
- **Spawn Weight:** 0.1%
- **Zone Location:** Where multiple elemental zones converge (extremely rare)
- **Mining Time:** 18 seconds
- **Durability Damage:** 10
- **Sell Value:** 30,000 IRF
- **Stack Size:** 5
- **Uses:** Multi-elemental magic, legendary fusion crafting
- **Description:** "Opal containing all elemental forces in perfect balance. Shifts through colors of fire, water, earth, and air."
- **Crafting Category:** Omni-elemental equipment, fusion magic
- **Special Properties:**
  - Equipment gains ALL elemental damage types
  - Cycles through elemental buffs automatically
  - Spectacular rainbow particle effects
  - Adaptive resistances
- **Geode Drop:** Mythic Geode (35%)

---

## Special & Event Materials

### TIME-TRAVEL EVENT

#### MIN_EVENT_001: Temporal Ore
- **MineralID:** MIN_EVENT_001
- **Name:** Temporal Ore
- **Rarity:** Special (Event)
- **Category:** Ore (Time-elemental)
- **Tool Required:** Diamond Pickaxe+
- **Source Rock Type:** Time Rift nodes (event only)
- **Spawn Weight:** 5% (in event zones)
- **Zone Location:** Time Rift Mining Event
- **Mining Time:** 6 seconds (time fluctuates)
- **Durability Damage:** 5
- **Sell Value:** 5,000 IRF or 500 Event Tokens
- **Stack Size:** 25
- **Uses:** Time-themed weapons, event crafting, chrono potions
- **Description:** "Ore that exists across multiple time periods simultaneously. Shimmers between past and future."
- **Crafting Category:** Event-exclusive time weapons
- **Special Properties:**
  - Weapons have "Rewind" ability (undo last hit taken)
  - Time distortion visual effects
  - Limited availability
- **Special Notes:** Only available during annual Time Event

---

## Geode Contents Reference

### Common Geode (100 IRF to open)
- Stone (40%)
- Coal (25%)
- Copper Ore (15%)
- Tin Ore (15%)
- Copper/Tin chance (5%)

### Rare Geode (500 IRF to open)
- Iron Ore (30%)
- Silver Ore (25%)
- Gold Ore (20%)
- Sapphire/Ruby/Emerald (20% combined)
- Iron + Gem combo (5%)

### Epic Geode (2,000 IRF to open)
- Titanium Ore (25%)
- Platinum Ore (20%)
- Diamond (15%)
- Amethyst Crystal (15%)
- Obsidian (10%)
- Multiple gems (10%)
- Legendary material chance (5%)

### Legendary Geode (10,000 IRF to open)
- Mithril Ore (30%)
- Adamantite Ore (20%)
- Star Sapphire (15%)
- Black Diamond (15%)
- Multiple Epic materials (15%)
- Mythic material chance (5%)

### Mythic Geode (50,000 IRF to open)
- Celestium Crystal (30%)
- Void Crystal (25%)
- Aether Opal (20%)
- Multiple Legendary materials (20%)
- Dragon Heart Gem (1% - extremely rare)
- Full resource jackpot (4%)

---

## Crafting Material Requirements (Reference)

### Weapon Tiers:
- **Common Weapons:** Stone, Copper, Tin
- **Rare Weapons:** Iron, Silver, Bronze
- **Epic Weapons:** Steel, Gold, Titanium, Diamonds
- **Legendary Weapons:** Mithril, Adamantite, Star Sapphire, Black Diamond
- **Mythic Weapons:** Celestium, Void Crystal, Dragon Heart, Aether Opal

### Armor Tiers:
- **Common Armor:** Copper, Bronze
- **Rare Armor:** Iron, Silver
- **Epic Armor:** Steel, Titanium, Platinum
- **Legendary Armor:** Mithril, Adamantite
- **Mythic Armor:** Celestium, Void Crystal (plus Legendary base)

### Tool Progression:
1. Stone Pickaxe (starter)
2. Copper Pickaxe (10 Copper Ore)
3. Iron Pickaxe (20 Iron Ore)
4. Steel Pickaxe (15 Iron + 5 Coal)
5. Gold Pickaxe (25 Gold Ore) - faster but fragile
6. Diamond Pickaxe (10 Diamonds + 15 Iron)
7. Mithril Pickaxe (5 Mithril + 3 Diamonds)
8. Adamantite Pickaxe (3 Adamantite + 2 Mithril)
9. Mythic Pickaxe (1 Celestium + 1 Void Crystal + 2 Adamantite)

---

## Database Management Notes

### Adding New Minerals:
1. Assign unique MineralID
2. Balance spawn rate with value
3. Define tool requirements (progression gates)
4. Set appropriate zone locations
5. Create crafting uses (minimum 2)
6. Test mining time vs. reward
7. Add to geode loot tables if applicable
8. Implement particle/visual effects

### Economic Balance:
- Common: 1-10 IRF each
- Rare: 10-100 IRF each
- Epic: 100-1,000 IRF each
- Legendary: 1,000-10,000 IRF each
- Mythic: 10,000-100,000 IRF each

### Spawn Weight Guidelines:
- Total spawn weights per zone should equal 100%
- Rarer materials compensate with higher value
- Deep zones have better material distribution
- Event materials have separate spawn tables

---

## Version History:
- v1.0 (Feb 8, 2026): Initial database with 23 permanent materials + 1 event material
- v1.1 (Planned): Gemstone expansion, crystal varieties
- v1.2 (Planned): Alloy system, material fusion

---

**Mining Materials Database - End of Document**

*Total Materials: 24 (23 permanent + 1 event)*  
*Categories: Ores (10), Gems (7), Crystals (5), Special (2)*  
*Target Total (Future): 60+ unique materials*
