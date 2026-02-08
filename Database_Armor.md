# Item Database
## Armor & Equipment Catalog

---

### Document Information
**Database Type:** Armor & Protective Equipment  
**Version:** 1.0  
**Last Updated:** February 8, 2026  
**Maintainer:** Content Team

---

## Usage Instructions

**For Designers:**
- Add new armor entries using the template
- Balance defense with weight and requirements
- Ensure set bonuses are meaningful but not overpowered
- Coordinate stat bonuses with combat system

**For Developers:**
- Use ArmorID as unique identifier
- Implement damage reduction formulas
- Validate set bonus activation
- Handle equipment slot restrictions

---

## Armor Entry Template

```
ArmorID: ARM_XXX
Name: Armor Piece Display Name
Rarity: Common/Rare/Epic/Legendary/Mythic
Type: Helmet/Chestplate/Leggings
Armor Value: X (damage reduction)
Weight: Light/Medium/Heavy
Level Requirement: Level X
Crafting Materials: List of materials
Crafting Location: Blacksmith/Armorer NPC
Crafting Cost: X IRF
Special Properties: Unique effects
Durability: X damage absorbed before breaking
Stat Bonuses: +X to stats
Set Name: Name of armor set (if applicable)
Set Bonus: Bonus when wearing X pieces
Description: "Flavor text about the armor."
Visual Effects: Glow, particles, etc.
```

---

## LEATHER ARMOR SETS (Light - High mobility)

### Common Tier (Grey)

#### SET: Novice Leather Armor

**ARM_001: Novice Leather Cap**
- **ArmorID:** ARM_001
- **Name:** Novice Leather Cap
- **Rarity:** Common
- **Type:** Helmet
- **Armor Value:** 5
- **Weight:** Light
- **Level Requirement:** Level 1
- **Crafting Materials:** 8 Leather, 2 String
- **Crafting Location:** Starting Area Armorer
- **Crafting Cost:** Free (tutorial)
- **Special Properties:** None
- **Durability:** 200 damage
- **Stat Bonuses:** None
- **Set Name:** Novice Leather Set
- **Set Bonus (2pc):** +5% Movement Speed
- **Set Bonus (3pc):** +5% Movement Speed, +10% Dodge Chance
- **Description:** "Simple leather cap. Provides basic protection for new adventurers."
- **Visual Effects:** Brown leather, basic design

**ARM_002: Novice Leather Vest**
- **ArmorID:** ARM_002
- **Name:** Novice Leather Vest
- **Rarity:** Common
- **Type:** Chestplate
- **Armor Value:** 10
- **Weight:** Light
- **Level Requirement:** Level 1
- **Crafting Materials:** 15 Leather, 5 String
- **Crafting Location:** Starting Area Armorer
- **Crafting Cost:** Free (tutorial)
- **Special Properties:** None
- **Durability:** 400 damage
- **Stat Bonuses:** None
- **Set Name:** Novice Leather Set
- **Description:** "Lightweight leather vest. Won't slow you down."

**ARM_003: Novice Leather Pants**
- **ArmorID:** ARM_003
- **Name:** Novice Leather Pants
- **Rarity:** Common
- **Type:** Leggings
- **Armor Value:** 8
- **Weight:** Light
- **Level Requirement:** Level 1
- **Crafting Materials:** 12 Leather, 3 String
- **Crafting Location:** Starting Area Armorer
- **Crafting Cost:** Free (tutorial)
- **Special Properties:** None
- **Durability:** 300 damage
- **Stat Bonuses:** None
- **Set Name:** Novice Leather Set
- **Description:** "Comfortable leather pants for mobility."

---

### Rare Tier (Blue)

#### SET: Shadow Walker Armor

**ARM_004: Shadow Hood**
- **ArmorID:** ARM_004
- **Name:** Shadow Hood
- **Rarity:** Rare
- **Type:** Helmet
- **Armor Value:** 20
- **Weight:** Light
- **Level Requirement:** Level 15
- **Crafting Materials:** 15 Dark Leather, 5 Shadow Silk, 3 Silver
- **Crafting Location:** Rogue Trainer
- **Crafting Cost:** 3,000 IRF
- **Special Properties:** +10% Stealth Effectiveness
- **Durability:** 800 damage
- **Stat Bonuses:** +5 Agility, +8% Critical Chance
- **Set Name:** Shadow Walker Set
- **Set Bonus (2pc):** +15% Critical Chance
- **Set Bonus (3pc):** +15% Critical Chance, +20% Backstab Damage, Enemies take 2 sec longer to detect you
- **Description:** "Dark hood favored by rogues and assassins. Blends with shadows."
- **Visual Effects:** Dark grey-black leather, shadowy mist effect

**ARM_005: Shadow Vest**
- **ArmorID:** ARM_005
- **Name:** Shadow Vest
- **Rarity:** Rare
- **Type:** Chestplate
- **Armor Value:** 35
- **Weight:** Light
- **Level Requirement:** Level 15
- **Crafting Materials:** 25 Dark Leather, 10 Shadow Silk, 5 Silver
- **Crafting Location:** Rogue Trainer
- **Crafting Cost:** 5,000 IRF
- **Special Properties:** +15% Dodge Chance
- **Durability:** 1,500 damage
- **Stat Bonuses:** +10 Agility, +10% Attack Speed
- **Set Name:** Shadow Walker Set
- **Description:** "Lightweight vest allowing swift, silent movement."

**ARM_006: Shadow Leggings**
- **ArmorID:** ARM_006
- **Name:** Shadow Leggings
- **Rarity:** Rare
- **Type:** Leggings
- **Armor Value:** 25
- **Weight:** Light
- **Level Requirement:** Level 15
- **Crafting Materials:** 20 Dark Leather, 8 Shadow Silk, 4 Silver
- **Crafting Location:** Rogue Trainer
- **Crafting Cost:** 4,000 IRF
- **Special Properties:** +10% Movement Speed
- **Durability:** 1,000 damage
- **Stat Bonuses:** +8 Agility, +5% Dodge
- **Set Name:** Shadow Walker Set
- **Description:** "Silent footsteps even on gravel."

---

## CHAINMAIL ARMOR SETS (Medium - Balanced)

### Rare Tier (Blue)

#### SET: Iron Chainmail Armor

**ARM_007: Iron Chain Coif**
- **ArmorID:** ARM_007
- **Name:** Iron Chain Coif
- **Rarity:** Rare
- **Type:** Helmet
- **Armor Value:** 30
- **Weight:** Medium
- **Level Requirement:** Level 12
- **Crafting Materials:** 20 Iron Ore, 10 Coal, 8 Leather
- **Crafting Location:** Blacksmith NPC
- **Crafting Cost:** 2,500 IRF
- **Special Properties:** None
- **Durability:** 1,200 damage
- **Stat Bonuses:** +15 HP, +5 Defense
- **Set Name:** Iron Chainmail Set
- **Set Bonus (2pc):** +10% Physical Resistance
- **Set Bonus (3pc):** +10% Physical Resistance, +20 HP, Reduce physical damage by 15
- **Description:** "Interlocking iron rings provide good protection without excessive weight."
- **Visual Effects:** Metallic grey chainmail texture

**ARM_008: Iron Chain Hauberk**
- **ArmorID:** ARM_008
- **Name:** Iron Chain Hauberk
- **Rarity:** Rare
- **Type:** Chestplate
- **Armor Value:** 50
- **Weight:** Medium
- **Level Requirement:** Level 12
- **Crafting Materials:** 35 Iron Ore, 20 Coal, 15 Leather
- **Crafting Location:** Blacksmith NPC
- **Crafting Cost:** 4,500 IRF
- **Special Properties:** None
- **Durability:** 2,000 damage
- **Stat Bonuses:** +30 HP, +10 Defense
- **Set Name:** Iron Chainmail Set
- **Description:** "Traditional chainmail shirt worn by soldiers."

**ARM_009: Iron Chain Leggings**
- **ArmorID:** ARM_009
- **Name:** Iron Chain Leggings
- **Rarity:** Rare
- **Type:** Leggings
- **Armor Value:** 40
- **Weight:** Medium
- **Level Requirement:** Level 12
- **Crafting Materials:** 25 Iron Ore, 15 Coal, 12 Leather
- **Crafting Location:** Blacksmith NPC
- **Crafting Cost:** 3,500 IRF
- **Special Properties:** None
- **Durability:** 1,500 damage
- **Stat Bonuses:** +20 HP, +8 Defense
- **Set Name:** Iron Chainmail Set
- **Description:** "Chainmail leggings protecting the legs without hindering movement too much."

---

## PLATE ARMOR SETS (Heavy - Maximum defense)

### Epic Tier (Purple)

#### SET: Steel Fortress Armor

**ARM_010: Steel Great Helm**
- **ArmorID:** ARM_010
- **Name:** Steel Great Helm
- **Rarity:** Epic
- **Type:** Helmet
- **Armor Value:** 60
- **Weight:** Heavy
- **Level Requirement:** Level 22
- **Crafting Materials:** 30 Steel, 10 Titanium, 5 Diamond
- **Crafting Location:** Master Blacksmith
- **Crafting Cost:** 15,000 IRF
- **Special Properties:** +20% Stun Resistance
- **Durability:** 3,000 damage
- **Stat Bonuses:** +40 HP, +15 Defense, +10 Armor
- **Set Name:** Steel Fortress Set
- **Set Bonus (2pc):** +25% Physical Resistance, +50 HP
- **Set Bonus (3pc):** +25% Physical Resistance, +50 HP, +30 Armor, Reflect 10% of melee damage back to attacker
- **Description:** "Imposing helmet with a T-shaped visor. Face of an unstoppable warrior."
- **Visual Effects:** Polished steel shine, intimidating presence

**ARM_011: Steel Plate Cuirass**
- **ArmorID:** ARM_011
- **Name:** Steel Plate Cuirass
- **Rarity:** Epic
- **Type:** Chestplate
- **Armor Value:** 100
- **Weight:** Heavy
- **Level Requirement:** Level 22
- **Crafting Materials:** 50 Steel, 20 Titanium, 10 Diamond
- **Crafting Location:** Master Blacksmith
- **Crafting Cost:** 25,000 IRF
- **Special Properties:** +30% Knockback Resistance
- **Durability:** 5,000 damage
- **Stat Bonuses:** +80 HP, +25 Defense, +20 Armor
- **Set Name:** Steel Fortress Set
- **Description:** "Thick steel plate covering vital organs. A walking fortress."

**ARM_012: Steel Plate Greaves**
- **ArmorID:** ARM_012
- **Name:** Steel Plate Greaves
- **Rarity:** Epic
- **Type:** Leggings
- **Armor Value:** 80
- **Weight:** Heavy
- **Level Requirement:** Level 22
- **Crafting Materials:** 40 Steel, 15 Titanium, 8 Diamond
- **Crafting Location:** Master Blacksmith
- **Crafting Cost:** 20,000 IRF
- **Special Properties:** -10% Movement Speed, Immune to Leg Injury effects
- **Durability:** 4,000 damage
- **Stat Bonuses:** +60 HP, +20 Defense, +15 Armor
- **Set Name:** Steel Fortress Set
- **Description:** "Heavy leg armor protecting from knee to ankle. Built like a tank."

---

### Legendary Tier (Gold)

#### SET: Adamantite Bulwark Armor

**ARM_013: Adamantite Crown Helm**
- **ArmorID:** ARM_013
- **Name:** Adamantite Crown Helm
- **Rarity:** Legendary
- **Type:** Helmet
- **Armor Value:** 120
- **Weight:** Heavy (feels Medium due to Adamantite properties)
- **Level Requirement:** Level 38
- **Crafting Materials:** 15 Adamantite Ore, 10 Mithril, 5 Black Diamond, 20 Steel
- **Crafting Location:** Legendary Blacksmith
- **Crafting Cost:** 100,000 IRF
- **Special Properties:** Immune to Stun, Confusion, and Fear effects
- **Durability:** 10,000 damage
- **Stat Bonuses:** +100 HP, +30 Defense, +25 Armor, +15% All Resistances
- **Set Name:** Adamantite Bulwark Set
- **Set Bonus (2pc):** +40% Physical Resistance, +100 HP, +30 Armor
- **Set Bonus (3pc):** +40% Physical Resistance, +100 HP, +30 Armor, +25% All Resistances, Damage reduction increased by 50, Immune to Armor Break effects
- **Description:** "Crown-like helmet forged from indestructible adamantite. Marks you as a legendary warrior."
- **Visual Effects:** Black metal with gold trim, regal appearance, commanding aura

**ARM_014: Adamantite Breastplate**
- **ArmorID:** ARM_014
- **Name:** Adamantite Breastplate
- **Rarity:** Legendary
- **Type:** Chestplate
- **Armor Value:** 200
- **Weight:** Heavy (feels Medium)
- **Level Requirement:** Level 38
- **Crafting Materials:** 25 Adamantite Ore, 15 Mithril, 10 Black Diamond, 30 Steel
- **Crafting Location:** Legendary Blacksmith
- **Crafting Cost:** 180,000 IRF
- **Special Properties:** Regenerate 2% HP per second in combat
- **Durability:** 20,000 damage
- **Stat Bonuses:** +200 HP, +50 Defense, +40 Armor, +20% All Resistances
- **Set Name:** Adamantite Bulwark Set
- **Description:** "Legendary breastplate that has never been pierced. You are nearly invincible."

**ARM_015: Adamantite Legguards**
- **ArmorID:** ARM_015
- **Name:** Adamantite Legguards
- **Rarity:** Legendary
- **Type:** Leggings
- **Armor Value:** 160
- **Weight:** Heavy (feels Medium)
- **Level Requirement:** Level 38
- **Crafting Materials:** 20 Adamantite Ore, 12 Mithril, 8 Black Diamond, 25 Steel
- **Crafting Location:** Legendary Blacksmith
- **Crafting Cost:** 140,000 IRF
- **Special Properties:** No movement speed penalty despite heavy weight
- **Durability:** 15,000 damage
- **Stat Bonuses:** +150 HP, +40 Defense, +35 Armor, +15% All Resistances
- **Set Name:** Adamantite Bulwark Set
- **Description:** "Leg armor that defies physics—heavy as a mountain, light as air."

---

## MAGE ROBES (Cloth - Magic focused)

### Epic Tier (Purple)

#### SET: Archmage's Regalia

**ARM_016: Archmage's Cowl**
- **ArmorID:** ARM_016
- **Name:** Archmage's Cowl
- **Rarity:** Epic
- **Type:** Helmet
- **Armor Value:** 15
- **Weight:** Light
- **Level Requirement:** Level 24
- **Crafting Materials:** 20 Enchanted Silk, 10 Amethyst, 5 Star Sapphire, 15 Gold Thread
- **Crafting Location:** Enchanter NPC
- **Crafting Cost:** 18,000 IRF
- **Special Properties:** +50 Mana, +15% Magic Damage
- **Durability:** 1,500 damage
- **Stat Bonuses:** +20 Magic Power, +30 Mana, +10% Cooldown Reduction
- **Set Name:** Archmage's Regalia
- **Set Bonus (2pc):** +30% Magic Damage, +100 Mana
- **Set Bonus (3pc):** +30% Magic Damage, +100 Mana, +20% Cooldown Reduction, Spells cost 20% less mana, +15% Magic Crit Chance
- **Description:** "Deep purple cowl worn by powerful archmages. Hums with magical energy."
- **Visual Effects:** Purple glow, floating runes, arcane particles

**ARM_017: Archmage's Robes**
- **ArmorID:** ARM_017
- **Name:** Archmage's Robes
- **Rarity:** Epic
- **Type:** Chestplate
- **Armor Value:** 30
- **Weight:** Light
- **Level Requirement:** Level 24
- **Crafting Materials:** 35 Enchanted Silk, 15 Amethyst, 10 Star Sapphire, 25 Gold Thread
- **Crafting Location:** Enchanter NPC
- **Crafting Cost:** 30,000 IRF
- **Special Properties:** +100 Mana, +20% Magic Damage
- **Durability:** 2,500 damage
- **Stat Bonuses:** +40 Magic Power, +60 Mana, +15% Magic Resistance
- **Set Name:** Archmage's Regalia
- **Description:** "Flowing robes inscribed with powerful enchantments."

**ARM_018: Archmage's Leggings**
- **ArmorID:** ARM_018
- **Name:** Archmage's Leggings
- **Rarity:** Epic
- **Type:** Leggings
- **Armor Value:** 20
- **Weight:** Light
- **Level Requirement:** Level 24
- **Crafting Materials:** 25 Enchanted Silk, 12 Amethyst, 8 Star Sapphire, 20 Gold Thread
- **Crafting Location:** Enchanter NPC
- **Crafting Cost:** 22,000 IRF
- **Special Properties:** +75 Mana, +12% Movement Speed
- **Durability:** 2,000 damage
- **Stat Bonuses:** +30 Magic Power, +50 Mana, +10% Cooldown Reduction
- **Set Name:** Archmage's Regalia
- **Description:** "Lightweight leggings allowing free movement for spellcasting."

---

### Mythic Tier (Red)

#### SET: Celestial Oracle Robes

**ARM_019: Celestial Oracle Crown**
- **ArmorID:** ARM_019
- **Name:** Celestial Oracle Crown
- **Rarity:** Mythic
- **Type:** Helmet
- **Armor Value:** 50
- **Weight:** Light
- **Level Requirement:** Level 50
- **Crafting Materials:** 10 Celestium Crystal, 5 Aether Opal, 3 Star Sapphire, 1 Divine Cloth (boss drop)
- **Crafting Location:** Cosmic Forge
- **Crafting Cost:** 600,000 IRF
- **Special Properties:** +200 Mana, +40% Magic Damage, See through illusions and stealth
- **Durability:** Infinite
- **Stat Bonuses:** +100 Magic Power, +150 Mana, +25% Magic Crit Chance, +20% Cooldown Reduction
- **Set Name:** Celestial Oracle Set
- **Set Bonus (2pc):** +60% Magic Damage, +300 Mana, +30% Cooldown Reduction
- **Set Bonus (3pc):** +60% Magic Damage, +300 Mana, +30% Cooldown Reduction, Spells cost 50% less mana, Magic crits restore 10% of max mana, Cast while moving, Cosmic Magic Enhancement (all spells gain celestial effects)
- **Description:** "Crown woven from starlight itself. Channel the power of the cosmos."
- **Visual Effects:** Brilliant white-blue glow, constellation patterns, orbiting stars, cosmic aura

**ARM_020: Celestial Oracle Robes**
- **ArmorID:** ARM_020
- **Name:** Celestial Oracle Robes
- **Rarity:** Mythic
- **Type:** Chestplate
- **Armor Value:** 80
- **Weight:** Light
- **Level Requirement:** Level 50
- **Crafting Materials:** 15 Celestium Crystal, 8 Aether Opal, 5 Star Sapphire, 2 Divine Cloth
- **Crafting Location:** Cosmic Forge
- **Crafting Cost:** 800,000 IRF
- **Special Properties:** +300 Mana, +50% Magic Damage, Immune to Silence
- **Durability:** Infinite
- **Stat Bonuses:** +150 Magic Power, +250 Mana, +30% Magic Resistance, +25% All Resistances
- **Set Name:** Celestial Oracle Set
- **Description:** "Robes that shimmer like the night sky. Reality bends around you."

**ARM_021: Celestial Oracle Leggings**
- **ArmorID:** ARM_021
- **Name:** Celestial Oracle Leggings
- **Rarity:** Mythic
- **Type:** Leggings
- **Armor Value:** 60
- **Weight:** Light
- **Level Requirement:** Level 50
- **Crafting Materials:** 12 Celestium Crystal, 6 Aether Opal, 4 Star Sapphire, 1 Divine Cloth
- **Crafting Location:** Cosmic Forge
- **Crafting Cost:** 700,000 IRF
- **Special Properties:** +250 Mana, +20% Movement Speed, Leave starlight trail
- **Durability:** Infinite
- **Stat Bonuses:** +120 Magic Power, +200 Mana, +20% Cooldown Reduction, +15% Dodge
- **Set Name:** Celestial Oracle Set
- **Description:** "Leggings allowing you to glide as if walking on clouds among stars."

---

## DRAGON SCALE ARMOR (Hybrid - Fire resistance)

### Legendary Tier (Gold)

#### SET: Dragon Knight Armor

**ARM_022: Dragon Scale Helm**
- **ArmorID:** ARM_022
- **Name:** Dragon Scale Helm
- **Rarity:** Legendary
- **Type:** Helmet
- **Armor Value:** 110
- **Weight:** Medium
- **Level Requirement:** Level 42
- **Crafting Materials:** 20 Dragon Scale, 10 Adamantite, 5 Ruby, 1 Dragon Horn
- **Crafting Location:** Dragon Forge (special)
- **Crafting Cost:** 150,000 IRF
- **Special Properties:** Immune to Fire Damage, +50% Fire Resistance, Dragon Fear Immunity
- **Durability:** 12,000 damage
- **Stat Bonuses:** +90 HP, +25 Defense, +20 Armor, +40% Fire Damage
- **Set Name:** Dragon Knight Set
- **Set Bonus (2pc):** +100% Fire Damage, Immune to all fire effects, +150 HP
- **Set Bonus (3pc):** +100% Fire Damage, Immune to fire, +150 HP, Dragon's Breath ability (breath fire, 500 damage cone, 15 sec cooldown), +50% Physical Resistance, Dragon Wings (glide ability)
- **Description:** "Helmet crafted from authentic dragon scales. Feel the power of dragons."
- **Visual Effects:** Red-black dragon scales, flame particles, draconic aura, horned design

**ARM_023: Dragon Scale Cuirass**
- **ArmorID:** ARM_023
- **Name:** Dragon Scale Cuirass
- **Rarity:** Legendary
- **Type:** Chestplate
- **Armor Value:** 180
- **Weight:** Medium
- **Level Requirement:** Level 42
- **Crafting Materials:** 35 Dragon Scale, 15 Adamantite, 10 Ruby, 1 Dragon Heart Gem
- **Crafting Location:** Dragon Forge
- **Crafting Cost:** 250,000 IRF
- **Special Properties:** Immune to Fire, Burn, and Bleed effects
- **Durability:** 20,000 damage
- **Stat Bonuses:** +180 HP, +40 Defense, +35 Armor, +60% Fire Damage
- **Set Name:** Dragon Knight Set
- **Description:** "Armor of overlapping dragon scales. Virtually impenetrable and fireproof."

**ARM_024: Dragon Scale Greaves**
- **ArmorID:** ARM_024
- **Name:** Dragon Scale Greaves
- **Rarity:** Legendary
- **Type:** Leggings
- **Armor Value:** 140
- **Weight:** Medium
- **Level Requirement:** Level 42
- **Crafting Materials:** 25 Dragon Scale, 12 Adamantite, 8 Ruby, 1 Dragon Talon
- **Crafting Location:** Dragon Forge
- **Crafting Cost:** 180,000 IRF
- **Special Properties:** +15% Movement Speed, Leave burning footprints
- **Durability:** 15,000 damage
- **Stat Bonuses:** +120 HP, +30 Defense, +28 Armor, +50% Fire Damage
- **Set Name:** Dragon Knight Set
- **Description:** "Leg armor allowing dragon-like agility despite its strength."

---

## VOID ARMOR (Mythic - Dimensional)

### Mythic Tier (Red)

#### SET: Void Sovereign Armor

**ARM_025: Void Crown**
- **ArmorID:** ARM_025
- **Name:** Void Sovereign Crown
- **Rarity:** Mythic
- **Type:** Helmet
- **Armor Value:** 150
- **Weight:** None (exists between dimensions)
- **Level Requirement:** Level 50
- **Crafting Materials:** 15 Void Crystal, 10 Adamantite, 5 Black Diamond, 1 Void Heart
- **Crafting Location:** Void Forge
- **Crafting Cost:** 750,000 IRF
- **Special Properties:** Phase through walls (5 sec duration, 30 sec cooldown), Immune to all crowd control
- **Durability:** Infinite
- **Stat Bonuses:** +200 HP, +60 Defense, +50 Armor, +100 Magic Power, +30% All Resistances
- **Set Name:** Void Sovereign Set
- **Set Bonus (2pc):** +50% All Resistances, +300 HP, Phase ability cooldown reduced to 15 sec
- **Set Bonus (3pc):** +50% All Resistances, +300 HP, Phase cooldown 10 sec, Void Walker (become invulnerable for 3 sec when HP drops below 20%, 60 sec cooldown), Damage taken has 25% chance to be negated, Void Aura (enemies near you take 100 damage/sec)
- **Description:** "Crown of the Void Sovereign. Exist in multiple dimensions simultaneously."
- **Visual Effects:** Dark purple-black void energy, dimensional phase effects, reality tears, void particles swirling

**ARM_026: Void Plate**
- **ArmorID:** ARM_026
- **Name:** Void Sovereign Plate
- **Rarity:** Mythic
- **Type:** Chestplate
- **Armor Value:** 250
- **Weight:** None
- **Level Requirement:** Level 50
- **Crafting Materials:** 25 Void Crystal, 15 Adamantite, 10 Black Diamond, 2 Void Heart
- **Crafting Location:** Void Forge
- **Crafting Cost:** 1,000,000 IRF
- **Special Properties:** Attacks ignore 30% of your armor have a 50% chance to miss entirely
- **Durability:** Infinite
- **Stat Bonuses:** +350 HP, +100 Defense, +80 Armor, +150 Magic Power, +40% All Resistances
- **Set Name:** Void Sovereign Set
- **Description:** "Armor existing between realities. Attacks literally can't find you."

**ARM_027: Void Greaves**
- **ArmorID:** ARM_027
- **Name:** Void Sovereign Greaves
- **Rarity:** Mythic
- **Type:** Leggings
- **Armor Value:** 200
- **Weight:** None
- **Level Requirement:** Level 50
- **Crafting Materials:** 20 Void Crystal, 12 Adamantite, 8 Black Diamond, 1 Void Heart
- **Crafting Location:** Void Forge
- **Crafting Cost:** 850,000 IRF
- **Special Properties:** +30% Movement Speed, Teleport 10m (10 sec cooldown)
- **Durability:** Infinite
- **Stat Bonuses:** +250 HP, +70 Defense, +60 Armor, +120 Magic Power, +35% All Resistances
- **Set Name:** Void Sovereign Set
- **Description:** "Walk between dimensions. You are everywhere and nowhere."

---

## Database Management Notes

### Armor Value Explanation:
```
Damage Reduction = Armor Value / (Armor Value + 100)
Example: 100 Armor = 50% damage reduction
         200 Armor = 66.7% damage reduction
         300 Armor = 75% damage reduction
```

### Weight Classification Effects:
- **Light:** No speed penalty, +10% Dodge, Low armor values
- **Medium:** -5% speed penalty, Balanced stats
- **Heavy:** -15% speed penalty (unless special property), High armor values, Best for tanks

### Rarity Scaling (Total Set Armor Value):
- Common: 20-40 total
- Rare: 80-120 total
- Epic: 200-300 total
- Legendary: 400-500 total
- Mythic: 600-800 total

### Set Bonus Philosophy:
- **2-piece:** Meaningful stat boost (20-30% in primary stat)
- **3-piece:** Game-changing ability + additional stats
- Must incentivize wearing full set without making mixed sets useless

### Armor Categories & Roles:
- **Leather:** Rogues, Rangers, Agility builds
- **Chainmail:** Warriors, Balanced fighters
- **Plate:** Tanks, Heavy fighters
- **Robes:** Mages, Magic users
- **Dragon Scale:** Hybrid damage dealers
- **Void:** Ultimate endgame, all roles

### Adding New Armor Checklist:
- [ ] Assign unique ArmorID
- [ ] Balance armor value with weight class
- [ ] Define complete set (helmet, chest, legs)
- [ ] Create meaningful 2pc and 3pc set bonuses
- [ ] Set level requirements (scale with rarity)
- [ ] Calculate crafting costs (economy balance)
- [ ] Write compelling descriptions
- [ ] Design visual effects/appearance
- [ ] Test damage reduction formulas
- [ ] Verify set bonuses aren't overpowered

---

## Crafting Cost Guidelines:
- **Common Set:** 100-500 IRF total
- **Rare Set:** 5,000-15,000 IRF total
- **Epic Set:** 30,000-100,000 IRF total
- **Legendary Set:** 200,000-500,000 IRF total
- **Mythic Set:** 1,000,000+ IRF total

---

## Version History:
- v1.0 (Feb 8, 2026): Initial database with 27 armor pieces across 9 complete sets
- v1.1 (Planned): Additional hybrid sets, elemental variants
- v1.2 (Planned): Upgrade system, enhancement mechanics

---

**Armor Database - End of Document**

*Total Armor Pieces: 27 (9 complete sets)*  
*Weight Classes: Light (6 sets), Medium (1 set), Heavy (2 sets), None (1 set)*  
*Target Total (Future): 20+ complete armor sets*
