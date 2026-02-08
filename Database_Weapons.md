# Item Database
## Weapons Catalog

---

### Document Information
**Database Type:** Weapons & Combat Equipment  
**Version:** 1.0  
**Last Updated:** February 8, 2026  
**Maintainer:** Content Team

---

## Usage Instructions

**For Designers:**
- Add new weapon entries using the template
- Balance damage with attack speed and requirements
- Ensure rarity progression is consistent
- Coordinate special effects with combat system

**For Developers:**
- Use WeaponID as unique identifier
- Implement damage formulas from combat system
- Validate level and material requirements
- Handle special ability triggers

---

## Weapon Entry Template

```
WeaponID: WPN_XXX
Name: Weapon Display Name
Rarity: Common/Rare/Epic/Legendary/Mythic
Type: Sword/Greatsword/Dagger/Spear/Hammer/Bow/Staff
Base Damage: X
Attack Speed: Fast/Normal/Slow
Critical Chance: X%
Critical Damage: X%
Level Requirement: Level X
Crafting Materials: List of materials
Crafting Location: Blacksmith NPC
Crafting Cost: X IRF
Special Ability: Ability name and description
Durability: X uses
Stat Bonuses: +X to stats
Description: "Flavor text about the weapon."
Visual Effects: Particle effects, glow, etc.
```

---

## SWORDS (Balanced weapons)

### Common Tier (Grey)

#### WPN_001: Wooden Sword
- **WeaponID:** WPN_001
- **Name:** Wooden Sword
- **Rarity:** Common
- **Type:** Sword
- **Base Damage:** 15
- **Attack Speed:** Fast (1.2 hits/sec)
- **Critical Chance:** 5%
- **Critical Damage:** 150%
- **Level Requirement:** Level 1
- **Crafting Materials:** 10 Wood, 2 Stone
- **Crafting Location:** Starting Area Workshop
- **Crafting Cost:** Free (tutorial)
- **Special Ability:** None
- **Durability:** 200 uses
- **Stat Bonuses:** None
- **Description:** "A simple wooden training sword. Everyone starts somewhere."
- **Visual Effects:** Basic wood texture

#### WPN_002: Stone Sword
- **WeaponID:** WPN_002
- **Name:** Stone Sword
- **Rarity:** Common
- **Type:** Sword
- **Base Damage:** 25
- **Attack Speed:** Normal (1.0 hits/sec)
- **Critical Chance:** 5%
- **Critical Damage:** 150%
- **Level Requirement:** Level 3
- **Crafting Materials:** 20 Stone, 5 Wood (handle)
- **Crafting Location:** Blacksmith NPC
- **Crafting Cost:** 50 IRF
- **Special Ability:** None
- **Durability:** 300 uses
- **Stat Bonuses:** None
- **Description:** "Crude but effective blade carved from stone. Heavy but durable."
- **Visual Effects:** Grey stone texture

#### WPN_003: Copper Sword
- **WeaponID:** WPN_003
- **Name:** Copper Sword
- **Rarity:** Common
- **Type:** Sword
- **Base Damage:** 50
- **Attack Speed:** Fast (1.2 hits/sec)
- **Critical Chance:** 8%
- **Critical Damage:** 150%
- **Level Requirement:** Level 5
- **Crafting Materials:** 15 Copper Ore, 5 Wood, 3 Leather
- **Crafting Location:** Blacksmith NPC
- **Crafting Cost:** 200 IRF
- **Special Ability:** None
- **Durability:** 500 uses
- **Stat Bonuses:** None
- **Description:** "Your first metal sword. The reddish blade gleams in sunlight."
- **Visual Effects:** Copper-colored metal shine

---

### Rare Tier (Blue)

#### WPN_004: Iron Sword
- **WeaponID:** WPN_004
- **Name:** Iron Sword
- **Rarity:** Rare
- **Type:** Sword
- **Base Damage:** 100
- **Attack Speed:** Normal (1.0 hits/sec)
- **Critical Chance:** 10%
- **Critical Damage:** 175%
- **Level Requirement:** Level 10
- **Crafting Materials:** 20 Iron Ore, 10 Coal (for smelting), 5 Leather
- **Crafting Location:** Blacksmith NPC
- **Crafting Cost:** 800 IRF
- **Special Ability:** None
- **Durability:** 1,000 uses
- **Stat Bonuses:** +5 Attack Damage
- **Description:** "Reliable iron blade used by soldiers across the realm."
- **Visual Effects:** Metallic grey with slight shine

#### WPN_005: Silver Sword
- **WeaponID:** WPN_005
- **Name:** Silver Sword
- **Rarity:** Rare
- **Type:** Sword
- **Base Damage:** 120
- **Attack Speed:** Fast (1.2 hits/sec)
- **Critical Chance:** 12%
- **Critical Damage:** 180%
- **Level Requirement:** Level 12
- **Crafting Materials:** 15 Silver Ore, 5 Gold Ore, 3 Leather
- **Crafting Location:** Blacksmith NPC
- **Crafting Cost:** 1,500 IRF
- **Special Ability:** **Sanctified Strike** - Deals +50% damage to undead enemies
- **Durability:** 800 uses
- **Stat Bonuses:** +8 Attack Damage, +5% Magic Resistance
- **Description:** "Silver blade blessed by ancient rituals. Bane of dark creatures."
- **Visual Effects:** Silvery-white glow, holy shimmer effect

---

### Epic Tier (Purple)

#### WPN_006: Steel Sword
- **WeaponID:** WPN_006
- **Name:** Steel Sword
- **Rarity:** Epic
- **Type:** Sword
- **Base Damage:** 200
- **Attack Speed:** Normal (1.0 hits/sec)
- **Critical Chance:** 15%
- **Critical Damage:** 200%
- **Level Requirement:** Level 20
- **Crafting Materials:** 25 Iron Ore, 15 Coal, 5 Titanium Ore, 10 Leather
- **Crafting Location:** Master Blacksmith
- **Crafting Cost:** 5,000 IRF
- **Special Ability:** **Blade Dance** - Every 5th hit strikes twice
- **Durability:** 2,000 uses
- **Stat Bonuses:** +15 Attack Damage, +10% Attack Speed
- **Description:** "Perfectly forged steel blade with incredible balance and edge retention."
- **Visual Effects:** Polished steel shine, blue energy trail on swings

#### WPN_007: Flame Sword
- **WeaponID:** WPN_007
- **Name:** Flamebrand
- **Rarity:** Epic
- **Type:** Sword
- **Base Damage:** 250
- **Attack Speed:** Normal (1.0 hits/sec)
- **Critical Chance:** 12%
- **Critical Damage:** 200%
- **Level Requirement:** Level 25
- **Crafting Materials:** 20 Steel, 10 Ruby, 5 Obsidian, 1 Phoenix Pepper
- **Crafting Location:** Master Blacksmith
- **Crafting Cost:** 10,000 IRF
- **Special Ability:** **Burning Strike** - 30% chance to inflict Burn (50 damage over 5 sec)
- **Durability:** 1,500 uses
- **Stat Bonuses:** +20 Attack Damage, +25% Fire Damage
- **Description:** "Blade forged in volcanic fires, eternally wreathed in flames."
- **Visual Effects:** Fire particles along blade, orange-red glow, burning trail

---

### Legendary Tier (Gold)

#### WPN_008: Mithril Sword
- **WeaponID:** WPN_008
- **Name:** Mithril Blade
- **Rarity:** Legendary
- **Type:** Sword
- **Base Damage:** 400
- **Attack Speed:** Fast (1.3 hits/sec)
- **Critical Chance:** 20%
- **Critical Damage:** 250%
- **Level Requirement:** Level 35
- **Crafting Materials:** 15 Mithril Ore, 10 Diamond, 5 Star Sapphire, 20 Steel
- **Crafting Location:** Legendary Blacksmith
- **Crafting Cost:** 50,000 IRF
- **Special Ability:** **Lightweight Mastery** - No movement penalty, +20% dodge chance while equipped
- **Durability:** 5,000 uses
- **Stat Bonuses:** +40 Attack Damage, +20% Attack Speed, +15% Critical Chance
- **Description:** "Legendary blade of silvery-blue mithril. Light as air, cuts through anything."
- **Visual Effects:** Blue-silver glow, starlight particles, magical aura

#### WPN_009: Dragon Slayer Sword
- **WeaponID:** WPN_009
- **Name:** Dragon Slayer
- **Rarity:** Legendary
- **Type:** Greatsword (counts as sword)
- **Base Damage:** 500
- **Attack Speed:** Slow (0.7 hits/sec)
- **Critical Chance:** 18%
- **Critical Damage:** 300%
- **Level Requirement:** Level 40
- **Crafting Materials:** 10 Adamantite Ore, 5 Black Diamond, 3 Dragon Scale, 1 Dragon Heart Gem
- **Crafting Location:** Legendary Blacksmith
- **Crafting Cost:** 100,000 IRF
- **Special Ability:** **Dragonbane** - Deals 3× damage to dragon-type enemies. 10% chance to instantly kill lesser dragons.
- **Durability:** 10,000 uses
- **Stat Bonuses:** +60 Attack Damage, +30% Critical Damage, +50% damage vs Dragons
- **Description:** "Massive blade forged from a dragon's own heart. The ultimate dragon-hunting weapon."
- **Visual Effects:** Dark crimson glow, draconic runes, dragon aura, roaring sound effect

---

### Mythic Tier (Red)

#### WPN_010: Celestial Blade
- **WeaponID:** WPN_010
- **Name:** Starfall Celestial Blade
- **Rarity:** Mythic
- **Type:** Sword
- **Base Damage:** 800
- **Attack Speed:** Fast (1.4 hits/sec)
- **Critical Chance:** 30%
- **Critical Damage:** 400%
- **Level Requirement:** Level 50
- **Crafting Materials:** 10 Celestium Crystal, 5 Mithril, 5 Aether Opal, 1 Star Sapphire
- **Crafting Location:** Cosmic Forge (special location)
- **Crafting Cost:** 500,000 IRF
- **Special Ability:** **Cosmic Strike** - Every attack releases a star projectile that seeks enemies (50% weapon damage). Critical hits cause stellar explosions (200 AoE damage).
- **Durability:** Infinite (never breaks)
- **Stat Bonuses:** +100 Attack Damage, +30% Attack Speed, +25% Critical Chance, +50% Critical Damage
- **Description:** "Blade forged from crystallized starlight. Wield the power of the cosmos itself."
- **Visual Effects:** Brilliant white-blue glow, constellation patterns on blade, shooting star trails, cosmic particles, nebula aura

---

## GREATSWORDS (Heavy, slow, high damage)

### Common Tier

#### WPN_011: Iron Greatsword
- **WeaponID:** WPN_011
- **Name:** Iron Greatsword
- **Rarity:** Common
- **Type:** Greatsword
- **Base Damage:** 120
- **Attack Speed:** Slow (0.6 hits/sec)
- **Critical Chance:** 8%
- **Critical Damage:** 200%
- **Level Requirement:** Level 10
- **Crafting Materials:** 40 Iron Ore, 20 Coal, 10 Wood
- **Crafting Location:** Blacksmith NPC
- **Crafting Cost:** 1,200 IRF
- **Special Ability:** **Heavy Strike** - Charged attacks deal +50% damage
- **Durability:** 1,000 uses
- **Stat Bonuses:** +8 Attack Damage, -10% Movement Speed
- **Description:** "Massive two-handed blade. Slow but devastating."
- **Visual Effects:** Large iron blade, heavy impact effects

---

### Legendary Tier

#### WPN_012: Titan's Edge
- **WeaponID:** WPN_012
- **Name:** Titan's Edge
- **Rarity:** Legendary
- **Type:** Greatsword
- **Base Damage:** 650
- **Attack Speed:** Slow (0.5 hits/sec)
- **Critical Chance:** 15%
- **Critical Damage:** 350%
- **Level Requirement:** Level 38
- **Crafting Materials:** 20 Adamantite Ore, 10 Titanium Ore, 5 Black Diamond
- **Crafting Location:** Legendary Blacksmith
- **Crafting Cost:** 80,000 IRF
- **Special Ability:** **Earthquake Slam** - Ground pound creates shockwave (300 damage, 10m radius, 30 sec cooldown)
- **Durability:** 8,000 uses
- **Stat Bonuses:** +70 Attack Damage, +40% Critical Damage, -15% Movement Speed
- **Description:** "Colossal blade wielded by ancient titans. The ground trembles with each swing."
- **Visual Effects:** Massive size, earth particles, shockwave effects, rumbling sounds

---

## DAGGERS (Fast, high crit, low damage)

### Rare Tier

#### WPN_013: Steel Dagger
- **WeaponID:** WPN_013
- **Name:** Steel Dagger
- **Rarity:** Rare
- **Type:** Dagger
- **Base Damage:** 80
- **Attack Speed:** Very Fast (2.0 hits/sec)
- **Critical Chance:** 25%
- **Critical Damage:** 200%
- **Level Requirement:** Level 15
- **Crafting Materials:** 10 Steel, 5 Leather, 3 Silver
- **Crafting Location:** Blacksmith NPC
- **Crafting Cost:** 2,500 IRF
- **Special Ability:** **Backstab** - Attacks from behind deal +100% damage
- **Durability:** 1,200 uses
- **Stat Bonuses:** +10 Attack Damage, +20% Critical Chance, +10% Movement Speed
- **Description:** "Swift and deadly. Perfect for quick strikes and assassinations."
- **Visual Effects:** Sleek design, quick slashing effects

---

### Mythic Tier

#### WPN_014: Void Ripper
- **WeaponID:** WPN_014
- **Name:** Void Ripper
- **Rarity:** Mythic
- **Type:** Dagger (Dual-wield set)
- **Base Damage:** 600 (300 each)
- **Attack Speed:** Extreme (2.5 hits/sec)
- **Critical Chance:** 40%
- **Critical Damage:** 500%
- **Level Requirement:** Level 50
- **Crafting Materials:** 8 Void Crystal, 5 Adamantite, 3 Black Diamond
- **Crafting Location:** Void Forge (special)
- **Crafting Cost:** 600,000 IRF
- **Special Ability:** **Phase Strike** - Teleport behind enemy on critical hit. Ignore 50% of armor. Crits apply 3-second Void Bleed (200 damage/sec).
- **Durability:** Infinite
- **Stat Bonuses:** +90 Attack Damage, +35% Critical Chance, +50% Critical Damage, +25% Movement Speed
- **Description:** "Twin daggers forged from void crystals. Strike from between dimensions."
- **Visual Effects:** Purple-black void energy, phase effects, dimensional rifts on strikes, shadowy afterimages

---

## SPEARS (Medium range, balanced)

### Epic Tier

#### WPN_015: Dragon Lance
- **WeaponID:** WPN_015
- **Name:** Dragon Lance
- **Rarity:** Epic
- **Type:** Spear
- **Base Damage:** 280
- **Attack Speed:** Normal (1.0 hits/sec)
- **Critical Chance:** 14%
- **Critical Damage:** 225%
- **Level Requirement:** Level 28
- **Crafting Materials:** 15 Titanium, 10 Dragon Scale, 5 Ruby
- **Crafting Location:** Master Blacksmith
- **Crafting Cost:** 15,000 IRF
- **Special Ability:** **Pierce** - Attacks hit all enemies in a line (5m range). +20% damage to armored foes.
- **Durability:** 2,500 uses
- **Stat Bonuses:** +25 Attack Damage, +2m Attack Range, +15% Armor Penetration
- **Description:** "Ornate spear decorated with dragon scales. Exceptional reach and penetration."
- **Visual Effects:** Red scale patterns, piercing energy trail, dragon motifs

---

## HAMMERS (Slow, stun chance, armor break)

### Legendary Tier

#### WPN_016: Mjolnir's Echo
- **WeaponID:** WPN_016
- **Name:** Mjolnir's Echo
- **Rarity:** Legendary
- **Type:** Hammer
- **Base Damage:** 550
- **Attack Speed:** Very Slow (0.4 hits/sec)
- **Critical Chance:** 10%
- **Critical Damage:** 400%
- **Level Requirement:** Level 42
- **Crafting Materials:** 15 Adamantite, 10 Platinum, 5 Sapphire, 1 Storm Core (boss drop)
- **Crafting Location:** Legendary Blacksmith
- **Crafting Cost:** 120,000 IRF
- **Special Ability:** **Thunderstrike** - 40% chance to stun for 3 seconds. Crits call down lightning (500 electric damage, chains to nearby enemies).
- **Durability:** 7,000 uses
- **Stat Bonuses:** +65 Attack Damage, +30% Stun Chance, +50% Armor Break
- **Description:** "Hammer blessed by the god of thunder. Each strike calls forth lightning."
- **Visual Effects:** Electric blue glow, lightning arcs, thunder sounds, storm particles

---

## BOWS (Ranged physical)

### Rare Tier

#### WPN_017: Hunter's Bow
- **WeaponID:** WPN_017
- **Name:** Hunter's Longbow
- **Rarity:** Rare
- **Type:** Bow
- **Base Damage:** 110
- **Attack Speed:** Normal (1.2 shots/sec)
- **Critical Chance:** 18%
- **Critical Damage:** 250%
- **Level Requirement:** Level 14
- **Crafting Materials:** 20 Wood, 10 Leather, 5 Iron, 10 String
- **Crafting Location:** Fletcher NPC
- **Crafting Cost:** 3,000 IRF
- **Special Ability:** **Headshot** - Crits from max range deal +100% damage
- **Durability:** 1,000 uses
- **Stat Bonuses:** +12 Attack Damage, +15% Critical Chance, +10m Range
- **Description:** "Finely crafted longbow. Deadly in skilled hands."
- **Visual Effects:** Wood grain, arrow trails

---

### Mythic Tier

#### WPN_018: Celestial Starbow
- **WeaponID:** WPN_018
- **Name:** Celestial Starbow
- **Rarity:** Mythic
- **Type:** Bow
- **Base Damage:** 750
- **Attack Speed:** Fast (1.5 shots/sec)
- **Critical Chance:** 35%
- **Critical Damage:** 450%
- **Level Requirement:** Level 50
- **Crafting Materials:** 10 Celestium Crystal, 5 Mithril, 3 Star Sapphire, 1 Phoenix Feather
- **Crafting Location:** Cosmic Forge
- **Crafting Cost:** 550,000 IRF
- **Special Ability:** **Star Arrow Volley** - Arrows split into 3 seeking projectiles on hit. Crits create miniature supernovas (400 AoE damage, 8m radius). Infinite arrows (doesn't consume ammo).
- **Durability:** Infinite
- **Stat Bonuses:** +95 Attack Damage, +30% Critical Chance, +40% Critical Damage, +20m Range
- **Description:** "Bow carved from a fallen star. Arrows of pure starlight never miss their mark."
- **Visual Effects:** Glowing white-blue bow, constellation engravings, star projectiles, nebula effects, cosmic trails

---

## STAVES (Magic weapons)

### Epic Tier

#### WPN_019: Archmage Staff
- **WeaponID:** WPN_019
- **Name:** Archmage's Staff
- **Rarity:** Epic
- **Type:** Staff
- **Base Damage:** 220 (magic)
- **Attack Speed:** Normal (1.0 casts/sec)
- **Critical Chance:** 20%
- **Critical Damage:** 200%
- **Level Requirement:** Level 24
- **Crafting Materials:** 15 Gold, 10 Amethyst, 5 Celestial Sage, 20 Enchanted Wood
- **Crafting Location:** Enchanter NPC
- **Crafting Cost:** 12,000 IRF
- **Special Ability:** **Mana Efficiency** - Spells cost 30% less mana. 15% chance to not consume mana on cast.
- **Durability:** 2,000 uses
- **Stat Bonuses:** +30 Magic Power, +50 Mana, +20% Magic Damage
- **Description:** "Staff carried by powerful archmages. Channels magic with incredible efficiency."
- **Visual Effects:** Purple crystal orb, arcane symbols, magic particles

---

### Mythic Tier

#### WPN_020: Void Scepter
- **WeaponID:** WPN_020
- **Name:** Scepter of the Void
- **Rarity:** Mythic
- **Type:** Staff
- **Base Damage:** 850 (magic)
- **Attack Speed:** Fast (1.3 casts/sec)
- **Critical Chance:** 28%
- **Critical Damage:** 400%
- **Level Requirement:** Level 50
- **Crafting Materials:** 10 Void Crystal, 5 Black Diamond, 3 Aether Opal, 1 Void Heart (boss drop)
- **Crafting Location:** Void Forge
- **Crafting Cost:** 700,000 IRF
- **Special Ability:** **Void Mastery** - Spells ignore 70% magic resistance. Crits open void rifts that deal damage over time (300/sec for 5 sec, 5m radius). Infinite mana regeneration.
- **Durability:** Infinite
- **Stat Bonuses:** +120 Magic Power, +200 Mana, +50% Magic Damage, +30% Cooldown Reduction
- **Description:** "Scepter channeling the pure essence of the void. Reality bends to your will."
- **Visual Effects:** Dark purple-black void energy, dimensional tears, swirling void particles, reality distortion effects

---

## Database Management Notes

### Weapon Balancing Formula:
```
DPS = Base Damage × Attack Speed
Effective DPS = DPS × (1 + (Crit Chance × Crit Damage Multiplier))
Price roughly scales with: DPS × Rarity Multiplier × Special Ability Value
```

### Rarity Scaling (Base Damage):
- Common: 15-120
- Rare: 80-200
- Epic: 200-400
- Legendary: 400-700
- Mythic: 600-1000+

### Attack Speed Classification:
- **Very Slow:** 0.3-0.5 hits/sec (Greathammers)
- **Slow:** 0.6-0.8 hits/sec (Greatswords, Hammers)
- **Normal:** 0.9-1.2 hits/sec (Swords, Spears, Bows, Staves)
- **Fast:** 1.3-1.8 hits/sec (Light Swords, Daggers)
- **Very Fast:** 1.9-2.5 hits/sec (Dual Daggers)
- **Extreme:** 2.6+ hits/sec (Special mythic weapons)

### Special Ability Tiers:
- **Common:** Passive stat bonuses only
- **Rare:** Simple proc effects (burn, extra damage type)
- **Epic:** Complex proc effects + passives
- **Legendary:** Powerful active/passive combos, unique mechanics
- **Mythic:** Game-changing abilities, infinite durability, multiple effects

### Adding New Weapons Checklist:
- [ ] Assign unique WeaponID
- [ ] Balance DPS with weapon type standards
- [ ] Define crafting materials (match rarity tier)
- [ ] Create special ability (must be unique and useful)
- [ ] Set level requirement (10 levels per rarity tier)
- [ ] Write compelling lore description
- [ ] Design visual effects
- [ ] Test combat balance
- [ ] Verify crafting costs align with economy

---

## Version History:
- v1.0 (Feb 8, 2026): Initial database with 20 weapons across all types and rarities
- v1.1 (Planned): Elemental weapon variants (Ice, Nature, Holy, Dark)
- v1.2 (Planned): Craftable weapon upgrades, enchantment system integration

---

**Weapons Database - End of Document**

*Total Weapons: 20*  
*Types: Swords (10), Greatswords (2), Daggers (2), Spears (1), Hammers (1), Bows (2), Staves (2)*  
*Target Total (Future): 100+ unique weapons*
