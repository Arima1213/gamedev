# Item Database
## Monster & Enemy Catalog

---

### Document Information
**Database Type:** Monsters & Enemies  
**Version:** 1.0  
**Last Updated:** February 8, 2026  
**Maintainer:** Content Team

---

## Usage Instructions

**For Designers:**
- Add new monster entries using the template
- Balance HP and damage with player progression
- Ensure loot tables are economically sound
- Create interesting behavior patterns for AI

**For Developers:**
- Use MonsterID as unique identifier
- Implement AI behaviors from combat system
- Validate loot drop rates and tables
- Handle boss mechanics and phases

---

## Monster Entry Template

```
MonsterID: MON_XXX
Name: Monster Display Name
Rarity: Common/Elite/Boss/World Boss
Type: Melee/Ranged/Magic/Hybrid
Level: X
HP: X
Damage: X per hit
Attack Speed: X hits/sec
Defense: X armor
Movement Speed: Fast/Normal/Slow
Spawn Location: Zone names
Spawn Rate: Common/Uncommon/Rare/Boss
AI Behavior: Melee/Ranged/Elite/Boss type
Abilities: List of special attacks
Resistances: Element resistances
Weaknesses: Element weaknesses
Loot Table: Drop rates and items
XP Reward: X XP
Description: "Flavor text about the monster."
Special Notes: Unique mechanics
```

---

## COMMON ENEMIES (Low level zones)

### Starter Zone (Levels 1-5)

#### MON_001: Slime
- **MonsterID:** MON_001
- **Name:** Green Slime
- **Rarity:** Common
- **Type:** Melee
- **Level:** 1
- **HP:** 50
- **Damage:** 5-8
- **Attack Speed:** 0.8 hits/sec
- **Defense:** 5
- **Movement Speed:** Slow
- **Spawn Location:** Starter Plains, Forest Edge
- **Spawn Rate:** Very Common (60% of spawns)
- **AI Behavior:** Melee Aggro - Slowly approaches and attacks
- **Abilities:** None
- **Resistances:** None
- **Weaknesses:** All damage types
- **Loot Table:**
  - Slime Gel (80%) - 1-3 units
  - Copper Coin (40%) - 2-5 IRF
  - Health Potion (10%) - Small
- **XP Reward:** 10 XP
- **Description:** "Gelatinous blob that absorbs nutrients. Harmless but numerous."
- **Visual Effects:** Green translucent, jiggly movement

#### MON_002: Wolf
- **MonsterID:** MON_002
- **Name:** Gray Wolf
- **Rarity:** Common
- **Type:** Melee
- **Level:** 3
- **HP:** 120
- **Damage:** 10-15
- **Attack Speed:** 1.2 hits/sec
- **Defense:** 10
- **Movement Speed:** Fast
- **Spawn Location:** Forest, Plains
- **Spawn Rate:** Common (40%)
- **AI Behavior:** Melee Aggro - Chases player aggressively
- **Abilities:** **Pack Tactics** - Deals +20% damage if another wolf is nearby
- **Resistances:** None
- **Weaknesses:** Magic damage (+15%)
- **Loot Table:**
  - Wolf Pelt (70%) - 1-2 units
  - Leather (50%) - 1-3 units (crafting material)
  - Wolf Fang (30%) - 1 unit
  - Raw Meat (60%) - 2-4 units
  - Copper/Silver coins (50%) - 5-15 IRF
- **XP Reward:** 25 XP
- **Description:** "Wild predator that hunts in packs. Dangerous in groups."
- **Visual Effects:** Grey fur, aggressive animations, pack howl sound

#### MON_003: Goblin Scout
- **MonsterID:** MON_003
- **Name:** Goblin Scout
- **Rarity:** Common
- **Type:** Melee
- **Level:** 5
- **HP:** 180
- **Damage:** 15-20
- **Attack Speed:** 1.0 hits/sec
- **Defense:** 15
- **Movement Speed:** Normal
- **Spawn Location:** Forest, Goblin Camp
- **Spawn Rate:** Common (35%)
- **AI Behavior:** Melee Aggro - Basic combat, occasionally retreats when low HP
- **Abilities:** **Cowardly** - Runs away when HP < 30%
- **Resistances:** None
- **Weaknesses:** None
- **Loot Table:**
  - Goblin Cloth (60%) - 1-2 units
  - String (40%) - 2-4 units (crafting material)
  - Leather (25%) - 1-2 units (crafting material)
  - Rusty Dagger (20%) - Vendor trash 10 IRF
  - Copper/Silver coins (70%) - 10-25 IRF
  - Health Potion (15%) - Small
- **XP Reward:** 40 XP
- **Description:** "Small, green-skinned humanoid. Weak individually but dangerous in groups."
- **Visual Effects:** Green skin, tattered clothing, crude weapons

---

### Forest Zone (Levels 8-15)

#### MON_004: Bear
- **MonsterID:** MON_004
- **Name:** Forest Bear
- **Rarity:** Common
- **Type:** Melee
- **Level:** 10
- **HP:** 400
- **Damage:** 30-45
- **Attack Speed:** 0.7 hits/sec
- **Defense:** 25
- **Movement Speed:** Normal
- **Spawn Location:** Deep Forest
- **Spawn Rate:** Uncommon (20%)
- **AI Behavior:** Melee Aggro - Powerful but slow attacks
- **Abilities:** **Roar** - Stuns nearby players for 1 second (20 sec cooldown)
- **Resistances:** Physical damage -15%
- **Weaknesses:** None
- **Loot Table:**
  - Bear Pelt (80%) - 2-4 units
  - Bear Claw (50%) - 1-2 units
  - Raw Meat (90%) - 5-10 units
  - Silver/Gold coins (60%) - 30-60 IRF
  - Rare crafting material (5%)
- **XP Reward:** 100 XP
- **Description:** "Massive forest predator. Territorial and powerful."
- **Visual Effects:** Brown fur, intimidating roar animation, claw swipe effects

#### MON_005: Goblin Warrior
- **MonsterID:** MON_005
- **Name:** Goblin Warrior
- **Rarity:** Common
- **Type:** Melee
- **Level:** 12
- **HP:** 500
- **Damage:** 35-50
- **Attack Speed:** 1.1 hits/sec
- **Defense:** 30
- **Movement Speed:** Normal
- **Spawn Location:** Goblin Fortress, Forest Outposts
- **Spawn Rate:** Common (40%)
- **AI Behavior:** Melee Aggro - More aggressive than scouts, uses shield blocks
- **Abilities:** **Shield Block** - 30% chance to block incoming attack
- **Resistances:** Physical damage -20%
- **Weaknesses:** Magic damage (+15%)
- **Loot Table:**
  - Goblin Armor Scrap (70%) - 2-3 units
  - Iron Ore (40%) - 1-3 units
  - Silver/Gold coins (80%) - 40-80 IRF
  - Goblin Shield (10%) - Common equipment
  - Health Potion (20%) - Medium
- **XP Reward:** 120 XP
- **Description:** "Better equipped goblin with armor and shield. More dangerous than scouts."
- **Visual Effects:** Leather armor, wooden shield, iron sword

---

## ELITE ENEMIES (Mid-level zones)

### Cave System (Levels 15-25)

#### MON_006: Cave Spider
- **MonsterID:** MON_006
- **Name:** Giant Cave Spider
- **Rarity:** Common
- **Type:** Melee
- **Level:** 18
- **HP:** 800
- **Damage:** 40-60
- **Attack Speed:** 1.3 hits/sec
- **Defense:** 20
- **Movement Speed:** Fast
- **Spawn Location:** Mining Caves
- **Spawn Rate:** Common (50%)
- **AI Behavior:** Melee Aggro - Ambush from ceilings, web attacks
- **Abilities:** **Poison Bite** - 30% chance to poison (20 damage/sec for 5 sec), **Web Shot** - Slows player by 50% for 3 seconds (15 sec cooldown)
- **Resistances:** Poison immunity
- **Weaknesses:** Magic damage (+25%), Blunt weapons (+15%)
- **Loot Table:**
  - Spider Silk (90%) - 3-6 units
  - String (80%) - 4-8 units (crafting material, major source)
  - Poison Gland (60%) - 1-2 units
  - Silver/Gold coins (70%) - 50-100 IRF
  - Spider Fang (30%) - Crafting material
- **XP Reward:** 180 XP
- **Description:** "Eight-legged nightmare lurking in dark caves. Poisonous and aggressive."
- **Visual Effects:** Black chitinous body, green venom drips, web shooting animation

#### MON_007: Orc Warrior
- **MonsterID:** MON_007
- **Name:** Orc Warrior
- **Rarity:** Elite
- **Type:** Melee
- **Level:** 22
- **HP:** 1,500
- **Damage:** 60-90
- **Attack Speed:** 0.9 hits/sec
- **Defense:** 50
- **Movement Speed:** Normal
- **Spawn Location:** Orc Camp, Mountain Pass
- **Spawn Rate:** Uncommon (15%)
- **AI Behavior:** Elite Melee - Uses power attacks, smash abilities
- **Abilities:** 
  - **Power Strike** - Charged attack dealing 150% damage (10 sec cooldown)
  - **War Cry** - Buffs nearby orcs +20% damage (30 sec cooldown)
- **Resistances:** Physical damage -25%
- **Weaknesses:** Magic damage (+20%)
- **Loot Table:**
  - Orc Steel (80%) - 3-5 units
  - Iron/Steel Ore (70%) - 5-10 units
  - Gold coins (90%) - 100-200 IRF
  - Rare weapon (15%) - Iron/Steel tier
  - Health Potion (40%) - Large
- **XP Reward:** 300 XP
- **Description:** "Large, green-skinned brute with incredible strength. Seasoned warrior."
- **Visual Effects:** Green muscular body, heavy armor, large weapons, intimidating presence

---

### Volcanic Zone (Levels 25-35)

#### MON_008: Fire Elemental
- **MonsterID:** MON_008
- **Name:** Fire Elemental
- **Rarity:** Elite
- **Type:** Magic
- **Level:** 28
- **HP:** 1,200
- **Damage:** 80-120 (magic/fire)
- **Attack Speed:** 1.5 casts/sec
- **Defense:** 30
- **Movement Speed:** Fast (floats)
- **Spawn Location:** Volcanic Core, Lava Fields
- **Spawn Rate:** Uncommon (20%)
- **AI Behavior:** Ranged Magic - Shoots fireballs, keeps distance
- **Abilities:**
  - **Fireball** - Ranged magic projectile
  - **Flame Burst** - AoE explosion around self (300 damage, 5m radius, 20 sec cooldown)
  - **Burning Aura** - Deals 10 damage/sec to nearby players (applies burn status)
- **Resistances:** Physical damage -50%, Burn immunity
- **Weaknesses:** Magic damage (+50%)
- **Loot Table:**
  - Fire Essence (90%) - 5-10 units
  - Ruby (40%) - 1-2 units
  - Obsidian (30%) - 2-4 units
  - Gold/Platinum coins (80%) - 150-300 IRF
  - Fire Crafting Material (25%)
- **XP Reward:** 400 XP
- **Description:** "Living flame given form. Burns everything it touches."
- **Visual Effects:** Humanoid flame shape, constant fire particles, heat distortion, burning sounds

#### MON_009: Lava Golem
- **MonsterID:** MON_009
- **Name:** Lava Golem
- **Rarity:** Elite
- **Type:** Melee/Tank
- **Level:** 32
- **HP:** 3,000
- **Damage:** 100-150
- **Attack Speed:** 0.6 hits/sec
- **Defense:** 80
- **Movement Speed:** Slow
- **Spawn Location:** Volcanic Core (deepest sections)
- **Spawn Rate:** Rare (5%)
- **AI Behavior:** Elite Tank - Slow but devastating, high HP
- **Abilities:**
  - **Earthquake Stomp** - Stuns all nearby players 2 sec, 200 AoE damage (25 sec cooldown)
  - **Lava Armor** - Reflects 20% of melee damage back to attacker
  - **Molten Core** - When HP < 30%, damage increases by 50%
- **Resistances:** Physical damage -40%, Heat immunity (environmental)
- **Weaknesses:** Magic damage (+50%)
- **Loot Table:**
  - Lava Core (100%) - 1 unit (rare crafting)
  - Obsidian (95%) - 10-20 units
  - Ruby/Black Diamond (50%) - 2-5 units
  - Titanium Ore (60%) - 5-10 units
  - Gold/Platinum coins (100%) - 300-600 IRF
  - Epic weapon/armor (10%)
- **XP Reward:** 800 XP
- **Description:** "Massive construct of molten rock and magma. Nearly indestructible."
- **Visual Effects:** Stone body with glowing lava cracks, magma drips, earthquake effects, intimidating size

---

## BOSS ENEMIES

### Dungeon Bosses (Levels 15-30)

#### MON_010: Goblin King
- **MonsterID:** MON_010
- **Name:** Goblin King
- **Rarity:** Boss
- **Type:** Melee/Summoner
- **Level:** 20
- **HP:** 8,000
- **Damage:** 80-120
- **Attack Speed:** 1.0 hits/sec
- **Defense:** 60
- **Movement Speed:** Normal
- **Spawn Location:** Goblin Fortress Throne Room (Dungeon Boss)
- **Spawn Rate:** Boss (1 per dungeon instance)
- **AI Behavior:** Boss - Multi-phase, summons minions
- **Phases:**
  1. **Phase 1 (100-60% HP):** Melee combat, calls 3 Goblin Warriors every 30 sec
  2. **Phase 2 (60-30% HP):** Enrages (+30% damage, +20% speed), summons 5 Goblin Warriors
  3. **Phase 3 (<30% HP):** Desperate assault, constant goblin spawns, uses all abilities
- **Abilities:**
  - **Summon Guards** - Calls 3-5 Goblin Warriors
  - **Royal Command** - Buffs all goblins +40% damage for 15 seconds (40 sec cooldown)
  - **Cleave Attack** - Wide swing hitting all players in front (150 damage)
  - **Enrage** - Triggers at low HP
- **Resistances:** Physical damage -30%
- **Weaknesses:** Magic damage (+20%), Critical hits (+10%)
- **Loot Table (Guaranteed):**
  - Goblin Crown (100%) - Trophy item, 1,000 IRF value
  - Epic Geode (80%) - 1-2 units
  - Gold/Platinum coins (100%) - 1,000-2,000 IRF
  - Epic weapon or armor (40%) - One guaranteed
  - Rare crafting materials (100%) - 10-20 assorted
  - Boss Achievement Token (100%)
- **XP Reward:** 2,000 XP
- **Description:** "Ruthless leader of the goblin horde. Wears a crude crown and commands absolute loyalty."
- **Visual Effects:** Larger than normal goblins, ornate crown, royal robes, powerful aura, throne room arena

---

#### MON_011: Ancient Crystal Guardian
- **MonsterID:** MON_011
- **Name:** Ancient Crystal Guardian
- **Rarity:** Boss
- **Type:** Magic/Tank
- **Level:** 30
- **HP:** 15,000
- **Damage:** 120-180 (magic)
- **Attack Speed:** 1.2 casts/sec
- **Defense:** 100
- **Movement Speed:** Slow
- **Spawn Location:** Crystal Cavern (Special Dungeon)
- **Spawn Rate:** Boss (1 per dungeon)
- **AI Behavior:** Boss - Shield mechanics, AoE magic
- **Phases:**
  1. **Phase 1 (100-70% HP):** Crystal Shield active (must destroy 4 crystals to damage boss), casts Crystal Spikes
  2. **Phase 2 (70-40% HP):** Shield down, aggressive magic attacks, summons Crystal Elementals
  3. **Phase 3 (<40% HP):** Shield reforms (destroy 6 crystals), rapid-fire abilities, arena hazards
- **Abilities:**
  - **Crystal Shield** - Invulnerable until crystals destroyed
  - **Crystal Spike Rain** - Spikes fall from ceiling (100 damage each, dodge required)
  - **Prismatic Beam** - Sweeping laser beam (250 damage, 20m range, 15 sec cooldown)
  - **Summon Crystal Minions** - Creates 4 Crystal Elementals (2,000 HP each)
  - **Crystal Explosion** - When crystals destroyed, AoE damage 300, 8m radius
- **Resistances:** Physical damage -50%, Magic resistance +30%
- **Weaknesses:** Hammer/Blunt weapons (+40% to crystals)
- **Loot Table (Guaranteed):**
  - Ancient Crystal Core (100%) - Legendary crafting material, 5,000 IRF value
  - Legendary Geode (60%) - 1 unit
  - Amethyst Cluster (100%) - 20-30 units
  - Diamond (80%) - 10-15 units
  - Platinum/Mithril coins (100%) - 3,000-5,000 IRF
  - Legendary weapon or armor (25%) - Crystal-themed
  - Epic equipment (80%) - 2-3 pieces
  - Boss Achievement Token (100%)
- **XP Reward:** 5,000 XP
- **Description:** "Ancient construct protecting the crystal caverns for millennia. Its power is legendary."
- **Visual Effects:** Massive crystalline golem, glowing core, prismatic light effects, crystal formations, magical aura

---

### World Bosses (Levels 35-50)

#### MON_012: Elder Dragon
- **MonsterID:** MON_012
- **Name:** Ignis the Elder Dragon
- **Rarity:** World Boss
- **Type:** Hybrid (Melee/Magic/Flying)
- **Level:** 45
- **HP:** 100,000
- **Damage:** 300-500 (varies by attack)
- **Attack Speed:** Varies
- **Defense:** 150
- **Movement Speed:** Fast (flies)
- **Spawn Location:** Dragon's Peak (World Boss Arena, requires 10+ players)
- **Spawn Rate:** World Boss (spawns every 6 hours real-time)
- **AI Behavior:** Complex Boss - Flight phases, breath weapons, multiple mechanics
- **Phases:**
  1. **Phase 1 - Ground Combat (100-75% HP):**
     - Melee claw attacks (300 damage)
     - Tail swipe (250 AoE damage)
     - Fire breath cone (400 damage, 20m range)
     - Summons 5 Dragon Whelps (5,000 HP each)
  
  2. **Phase 2 - Flight Phase (75-50% HP):**
     - Takes flight, becomes harder to hit
     - Aerial fire bombing (200 damage per bomb, multiple targets)
     - Divebomb attack (500 damage, knockback)
     - Must use ranged attacks or wait for land
  
  3. **Phase 3 - Enraged Ground (50-25% HP):**
     - Returns to ground, enraged (+50% damage, +30% speed)
     - Inferno breath (600 damage, 30m cone, burns arena)
     - Earthquake stomp (300 AoE, stuns 3 sec)
     - Summons 10 Dragon Whelps
  
  4. **Phase 4 - Desperate Flight (<25% HP):**
     - Final flight phase, extreme aggression
     - Meteor rain from above (150 damage per meteor, covers arena)
     - Ultimate dive bomb (800 damage)
     - Must kill quickly or mechanics become overwhelming
- **Abilities:**
  - **Fire Breath** - Massive cone of dragon fire
  - **Tail Whip** - 360° AoE around dragon
  - **Wing Buffet** - Knockback all nearby players
  - **Dragon Roar** - Fear effect, reduces damage dealt -30% for 10 sec
  - **Summon Whelps** - Calls dragon offspring to aid
  - **Inferno Mode** - Burns entire arena, safe zones shrink
  - **Meteor Storm** - Ultimate ability, rain of fire
- **Resistances:** Fire immunity, Physical damage -60%
- **Weaknesses:** Ice/Water damage (+50%), Dragon Slayer weapons (+100%)
- **Loot Table (Guaranteed per player):**
  - Dragon Scale (100%) - 50-100 units
  - Dragon Heart Gem (30%) - 1 unit (Mythic crafting)
  - Mythic Geode (50%) - 1-2 units
  - Legendary equipment (70%) - 2-3 pieces
  - Dragon Weapon/Armor (20%) - Special dragon-tier
  - Mithril/Adamantite (100%) - 50-100 units
  - Platinum coins (100%) - 10,000-20,000 IRF
  - Dragon Achievement (100%) - Prestige title
  - Dragon Mount Egg (5%) - Ultra-rare, dragon familiar
- **XP Reward:** 20,000 XP
- **Description:** "Ancient red dragon that has terrorized the realm for centuries. Defeating it is the ultimate test of strength."
- **Visual Effects:** Massive crimson dragon, fire particles everywhere, wing flaps create wind, roar shakes screen, burning arena, epic boss music

#### MON_013: Void Leviathan
- **MonsterID:** MON_013
- **Name:** The Void Leviathan
- **Rarity:** World Boss
- **Type:** Magic/Void
- **Level:** 50
- **HP:** 200,000
- **Damage:** 400-700 (void/magic)
- **Attack Speed:** Varies
- **Defense:** 120 (but high magic resistance)
- **Movement Speed:** Fast (phases through reality)
- **Spawn Location:** Void Rift (Special Event, 20+ players recommended)
- **Spawn Rate:** Rare World Boss (spawns once per week, 2-hour window)
- **AI Behavior:** Ultimate Boss - Dimensional mechanics, reality-warping
- **Phases:**
  1. **Phase 1 - Material Realm (100-80% HP):**
     - Void tentacle attacks (350 damage)
     - Dimensional rift spawns void creatures
     - Reality tear AoE (250 damage, teleports hit players)
  
  2. **Phase 2 - Phase Shift (80-60% HP):**
     - Leviathan becomes partially invisible (50% dodge chance)
     - Void portals appear (must close or adds spawn infinitely)
     - Void pulse AoE (400 damage, ignores armor)
  
  3. **Phase 3 - Void Consumption (60-40% HP):**
     - Arena starts collapsing into void
     - Players must stand on safe platforms
     - Void beam (600 damage, sweeps across arena)
     - Summons Void Avatars (15,000 HP each, 5 total)
  
  4. **Phase 4 - Reality Break (40-20% HP):**
     - All abilities intensify
     - Arena fully in void dimension (constant damage if not on platforms)
     - Void storm (200 damage/sec to entire arena)
     - Leviathan splits into 3 forms (must kill all within 60 seconds or they merge and heal)
  
  5. **Phase 5 - Final Desperation (<20% HP):**
     - Void Singularity channeling (if completes, wipes raid)
     - Must burn down boss within 90 seconds
     - All mechanics active simultaneously
     - Void tendrils grab players (1,000 damage if not freed)
- **Abilities:**
  - **Void Tentacles** - Multiple melee tentacle attacks
  - **Reality Tear** - Teleports and damages players randomly
  - **Void Pulse** - AoE that ignores armor
  - **Dimensional Rift** - Spawns portals and void creatures
  - **Phase Shift** - Becomes partially invulnerable
  - **Void Beam** - Sweeping laser of void energy
  - **Summon Void Avatars** - Creates powerful adds
  - **Reality Break** - Warps arena itself
  - **Void Singularity** - Ultimate wipe mechanic if not stopped
- **Resistances:** Void immunity, Magic resistance +50%, Physical damage -70%
- **Weaknesses:** Holy/Light damage (+80%), Celestium weapons (+100%)
- **Loot Table (Guaranteed per player):**
  - Void Crystal (100%) - 100-200 units
  - Void Heart (50%) - 1 unit (Ultimate crafting material)
  - Mythic Geode (80%) - 3-5 units
  - Mythic equipment (40%) - 1-2 pieces (Void-themed)
  - Legendary equipment (100%) - 3-5 pieces
  - Celestium/Aether materials (60%) - 20-50 units
  - Adamantite (100%) - 100-200 units
  - Platinum coins (100%) - 50,000-100,000 IRF
  - Void Leviathan Achievement (100%) - Ultimate prestige title "Void Slayer"
  - Void Mount (10%) - Legendary void creature mount
  - Void Familiar Egg (5%) - Mythic familiar
  - Custom Name Tag (2%) - Legendary cosmetic, name appears in purple
- **XP Reward:** 50,000 XP
- **Description:** "Incomprehensible entity from beyond reality. Its very presence tears at the fabric of existence. Only the bravest heroes dare face it."
- **Visual Effects:** Massive void serpent with reality-warping form, purple-black void energy everywhere, dimensional tears, players see multiple overlapping realities, void particles, screen distortion effects, ominous void sounds, epic orchestral boss music

---

## SPECIAL EVENT ENEMIES

### Halloween Event

#### MON_EVENT_001: Pumpkin Fiend
- **MonsterID:** MON_EVENT_001
- **Name:** Pumpkin Fiend
- **Rarity:** Elite
- **Type:** Melee/Fire
- **Level:** 25
- **HP:** 2,500
- **Damage:** 90-140
- **Attack Speed:** 0.8 hits/sec
- **Defense:** 50
- **Movement Speed:** Normal
- **Spawn Location:** Halloween Event Zone
- **Spawn Rate:** Event only (Common during event)
- **AI Behavior:** Elite - Jack-o'-lantern head shoots fireballs
- **Abilities:**
  - **Pumpkin Bomb** - Throws exploding pumpkin (200 AoE damage)
  - **Flame Head** - Fire aura deals 20 damage/sec nearby
- **Resistances:** Fire immunity
- **Weaknesses:** Water damage (+50%)
- **Loot Table:**
  - Halloween Token (100%) - 50-100 tokens
  - Ghost Pumpkin Seeds (40%) - 3-5 seeds
  - Pumpkin material (90%) - 10-20 units
  - Event-exclusive cosmetics (15%)
  - Gold coins (100%) - 200-400 IRF
- **XP Reward:** 500 XP
- **Description:** "Possessed pumpkin creature that appears during Halloween. Its head burns with cursed fire."
- **Visual Effects:** Giant pumpkin with carved face, flame effects, spooky laugh sounds

---

## MINIBOSS ENEMIES (Overworld Rare Spawns)

#### MON_014: Wandering Knight
- **MonsterID:** MON_014
- **Name:** Cursed Knight
- **Rarity:** Miniboss
- **Type:** Melee/Tank
- **Level:** 35
- **HP:** 20,000
- **Damage:** 200-300
- **Attack Speed:** 0.8 hits/sec
- **Defense:** 120
- **Movement Speed:** Normal
- **Spawn Location:** Random overworld spawn (Forest, Plains, Mountains)
- **Spawn Rate:** Rare (1% chance to spawn in zone, 1-hour respawn)
- **AI Behavior:** Elite Boss - Powerful solo enemy
- **Abilities:**
  - **Sword Slash** - Wide arc dealing heavy damage
  - **Shield Bash** - Stuns for 2 seconds
  - **Dark Aura** - Heals 1% HP per second
- **Resistances:** Physical damage -40%, Dark immunity
- **Weaknesses:** Holy damage (+60%)
- **Loot Table:**
  - Cursed Armor Fragment (100%) - 5-10 units
  - Epic weapon (50%) - One guaranteed
  - Adamantite (60%) - 10-20 units
  - Platinum/Mithril coins (100%) - 5,000-10,000 IRF
  - Legendary Geode (30%)
  - Rare mount drop (5%) - Undead Horse
- **XP Reward:** 8,000 XP
- **Description:** "Fallen knight cursed to wander eternally. Seeks worthy opponents to break curse."
- **Visual Effects:** Black armor with purple curse aura, glowing eyes, dark particles

---

## Database Management Notes

### Level Scaling Formula:
```
HP = Base HP × (1 + 0.15 × Level)
Damage = Base Damage × (1 + 0.12 × Level)
Defense = Base Defense × (1 + 0.10 × Level)
```

### Rarity Classifications:
- **Common:** 75-85% of zone spawns
- **Elite:** 10-15% of zone spawns, 2-3× common stats
- **Miniboss:** Rare overworld spawns, 5-10× common stats
- **Boss:** Dungeon/Raid encounters, 10-20× common stats
- **World Boss:** Server-wide events, 50-100× common stats

### AI Behavior Types:
- **Melee Aggro:** Chases player, basic attacks
- **Ranged Kiting:** Keeps distance, ranged attacks
- **Elite Melee:** Advanced combos, blocking, abilities
- **Elite Ranged:** Multiple spell types, positioning
- **Boss Multi-phase:** Phase transitions, adds, mechanics

### Loot Drop Rate Standards:
- Common materials: 60-90%
- Uncommon materials: 30-60%
- Rare materials: 10-30%
- Currency: 50-100% (varies by enemy)
- Equipment drops:
  - Common enemies: 5-15% (grey/blue items)
  - Elite enemies: 20-40% (blue/purple items)
  - Bosses: 50-100% (purple/gold items)
  - World Bosses: 100% (gold/red items)

### XP Reward Scaling:
- Common: Level × 10
- Elite: Level × 30-50
- Miniboss: Level × 200-300
- Boss: Level × 500-1000
- World Boss: Level × 1000-2000

### Boss Design Checklist:
- [ ] Create multi-phase design (minimum 2 phases)
- [ ] Define unique mechanics (not just stat increases)
- [ ] Balance HP pool for intended group size
- [ ] Design arena/environment hazards
- [ ] Create engaging add/minion spawns
- [ ] Define enrage timer (if applicable)
- [ ] Design guaranteed loot tables
- [ ] Create achievement/title rewards
- [ ] Script voice lines/dialogue (if applicable)
- [ ] Design epic visual effects and music

### Adding New Monsters Checklist:
- [ ] Assign unique MonsterID
- [ ] Balance stats for intended level range
- [ ] Define AI behavior pattern
- [ ] Create ability list with cooldowns
- [ ] Set resistances and weaknesses (if any)
- [ ] Design loot table (match rarity tier)
- [ ] Calculate XP reward (use formula)
- [ ] Write compelling description
- [ ] Design visual effects and sounds
- [ ] Test combat balance with appropriate gear level

---

## Economic Balancing Notes:

### Average Loot Value by Rarity:
- **Common Enemy:** 5-50 IRF per kill
- **Elite Enemy:** 100-500 IRF per kill
- **Miniboss:** 5,000-15,000 IRF per kill
- **Boss:** 20,000-100,000 IRF per kill
- **World Boss:** 100,000-500,000 IRF per kill (distributed among participants)

### Farming Efficiency:
Target: Players should earn approximately:
- Level 1-10: 50-100 IRF/hour from combat
- Level 10-20: 200-500 IRF/hour
- Level 20-30: 1,000-2,000 IRF/hour
- Level 30-40: 3,000-5,000 IRF/hour
- Level 40-50: 8,000-15,000 IRF/hour

---

## Version History:
- v1.0 (Feb 8, 2026): Initial database with 15 monsters + 1 event enemy
- v1.1 (Planned): Additional miniboss variants, seasonal event enemies
- v1.2 (Planned): New world boss (Ice Titan), dungeon boss expansions

---

**Monster Database - End of Document**

*Total Enemies: 16 (15 permanent + 1 event)*  
*Categories: Common (8), Elite (4), Miniboss (1), Boss (2), World Boss (2), Event (1)*  
*Target Total (Future): 100+ unique enemies*
