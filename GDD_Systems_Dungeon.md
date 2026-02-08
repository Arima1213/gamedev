# IRIFA: Realms of Harvest & Adventure
## Game Design Document - Dungeon System

---

### Document Information
**Document Type:** System Design  
**System:** Dungeon & Instance System  
**Version:** 1.0  
**Last Updated:** February 8, 2026  
**Status:** Implementation Ready

---

## Table of Contents
1. [Overview](#1-overview)
2. [Dungeon Types](#2-dungeon-types)
3. [Instance System](#3-instance-system)
4. [Difficulty Tiers](#4-difficulty-tiers)
5. [Dungeon Mechanics](#5-dungeon-mechanics)
6. [Boss Encounters](#6-boss-encounters)
7. [Loot System](#7-loot-system)
8. [Progression & Unlocks](#8-progression--unlocks)
9. [Technical Implementation](#9-technical-implementation)
10. [Balance & Economy](#10-balance--economy)

---

## 1. Overview

### 1.1 System Purpose
Dungeons provide structured PvE content for solo players and groups, offering:
- Progressive difficulty challenges
- Guaranteed high-value loot
- Boss encounters with unique mechanics
- Social multiplayer content
- Endgame repeatable content

### 1.2 Core Design Pillars
- **Instancing:** Private copies for each party
- **Progression:** Unlock harder dungeons through completion
- **Replayability:** Randomized elements, daily/weekly resets
- **Cooperation:** Designed for 1-5 players
- **Risk/Reward:** Higher difficulty = better loot

### 1.3 Integration Points
- **Combat System:** Uses weapon/armor/enemy data
- **Loot System:** Generates equipment from dungeon loot tables
- **Party System:** Group formation and instance entry
- **Progression:** Level requirements and achievements

---

## 2. Dungeon Types & Complete Database

**IMPORTANT SYSTEM RULES:**
- **Party Flexibility:** All dungeons (except Raid) can be entered solo (1 player) or party (up to 5 players)
- **No Separate Queues:** There are NO "solo-only" or "party-only" versions - same dungeon scales for 1-5 players
- **Personal Loot:** Each player receives their own chest after boss defeat (NOT shared loot)
- **Exit System:** Portal spawns after boss defeat with 3-minute countdown, then force-teleports all players to Main Town
- **Emergency Exit:** Players can use Teleportation Scroll (bought from Gruff the Blacksmith, 100 IRF) to leave anytime

---

### Total Dungeons: 4 Permanent Dungeons

| Dungeon Name | Type | Min Level | Recommended Level | Party Size | Length |
|--------------|------|-----------|-------------------|------------|--------|
| **Goblin Fortress** | Normal Dungeon | 10 | 12-18 | 1-5 players | 20-30 min |
| **Crystal Cavern** | Elite Dungeon | 25 | 28-35 | 1-5 players | 35-45 min |
| **Volcanic Core** | Elite Dungeon | 35 | 38-45 | 1-5 players | 40-50 min |
| **Dragon's Lair** | Raid Dungeon | 45 | 48-50 | 3-8 players | 60-90 min |

---

## DUNGEON 1: GOBLIN FORTRESS

### 2.1.1 Basic Information

**Dungeon Type:** Normal Dungeon  
**Theme:** Medieval fortress siege, goblin warfare  
**Minimum Level:** 10  
**Recommended Level:** 12-18  
**Party Size:** 1-5 players (scalable difficulty)  
**Estimated Clear Time:** 20-30 minutes  
**Difficulty Rating:** ⭐⭐ (Easy-Medium)

**Unlock Requirements:**
- Reach Player Level 10
- Complete Quest: "Threat from the Forest" (from Captain Zara)
- Pay Unlock Fee: 1,000 IRF (one-time)

**Entry Location:**
- Town Hub → Forest Gate → Goblin Territory Entrance
- Interact with Dungeon Portal (glowing green gate)

---

### 2.1.2 Dungeon Structure (Linear Layout)

```
[ENTRANCE] 
    ↓
[OUTER COURTYARD] (Monster Zone 1)
    ↓
[FORTRESS WALLS] (Monster Zone 2)
    ↓
[INNER KEEP] (Monster Zone 3)
    ↓
[THRONE ROOM] (Boss Arena)
    ↓
[EXIT PORTAL] (spawns after boss defeat)
```

**Total Distance:** ~800 meters linear path  
**Checkpoint System:** 2 checkpoints (Courtyard cleared, Inner Keep entered)  
**Respawn:** Players respawn at last checkpoint if they die

---

### 2.1.3 Monster Distribution

#### Zone 1: Outer Courtyard (Entry Area)

**Monster 1: Goblin Scout (MON_003)**
- **Level:** 12 (scaled to dungeon)
- **HP:** 350 (dungeon-buffed from base 180)
- **Spawn Count:** 8-12 goblins
- **Spawn Pattern:** Patrolling in pairs around courtyard
- **Density:** Medium (2-3 packs of 2-4 goblins)
- **Location:** Scattered around entrance, near campfires
- **Behavior:** 
  - Patrol in set paths (predictable)
  - Aggro range: 15 meters
  - Alert nearby goblins when attacked
  - Run away when HP < 20% (cowardly trait)
- **Loot:** Goblin Cloth, String, Small IRF (10-25)

**Monster 2: Gray Wolf (MON_002)**
- **Level:** 11
- **HP:** 280 (dungeon-buffed)
- **Spawn Count:** 4-6 wolves
- **Spawn Pattern:** Roaming in packs of 2-3
- **Density:** Low (2 wolf packs)
- **Location:** Near forest edge of courtyard
- **Behavior:**
  - Pack hunting (attack together)
  - Fast movement, chases aggressively
  - +20% damage if another wolf nearby (Pack Tactics)
  - Aggro range: 20 meters
- **Loot:** Wolf Pelt, Raw Meat, Leather

**Environmental Hazards:**
- Wooden spike traps (100 damage if stepped on)
- Explosive barrels (can be shot to AoE damage goblins)

---

#### Zone 2: Fortress Walls (Mid-Section)

**Monster 3: Goblin Warrior (MON_005)**
- **Level:** 14
- **HP:** 850 (dungeon-buffed from base 500)
- **Spawn Count:** 10-15 warriors
- **Spawn Pattern:** Guarding key choke points
- **Density:** High (3-4 warriors per checkpoint)
- **Location:** 
  - 4 warriors at main gate (must defeat to progress)
  - 3 warriors on wall platforms
  - 5-8 warriors patrolling inner walls
- **Behavior:**
  - Defensive stance (uses shield block 30% of time)
  - Guards choke points (blocks progression)
  - Does NOT run away (brave warriors)
  - Aggro range: 18 meters
  - Calls for help if player detected
- **Loot:** Goblin Armor Scrap, Iron Ore, Health Potions

**Monster 4: Goblin Scout (MON_003) - Archers**
- **Level:** 12
- **HP:** 300
- **Spawn Count:** 6-8 archers
- **Spawn Pattern:** Positioned on elevated platforms
- **Density:** Medium (2-3 archers per platform)
- **Location:** Wall towers, elevated platforms (hard to reach)
- **Behavior:**
  - Ranged attacks (shoots arrows from distance)
  - Stays on elevated positions
  - Runs away if player gets close (melee range)
  - Shoots at lowest HP player
  - Aggro range: 25 meters
- **Loot:** Goblin Cloth, Arrows, String

**Environmental Hazards:**
- Oil slicks (can be ignited for 200 fire damage/sec)
- Falling rocks from damaged walls (300 damage)

**Checkpoint 1:** After clearing main gate and wall section

---

#### Zone 3: Inner Keep (Pre-Boss Area)

**Monster 5: Goblin Warrior (MON_005) - Elite Guards**
- **Level:** 16
- **HP:** 1,200 (elite variants)
- **Spawn Count:** 6-8 elite warriors
- **Spawn Pattern:** Guarding throne room entrance in formation
- **Density:** High (clustered near boss door)
- **Location:** 
  - 4 warriors blocking throne room door (must clear)
  - 2-4 warriors patrolling keep halls
- **Behavior:**
  - Defensive formation (protect each other)
  - Shield Wall tactic (3+ warriors = reduced damage)
  - Elite AI (smarter positioning)
  - Does NOT aggro until player enters inner keep
- **Loot:** Epic Geode (15%), Goblin Steel, Gold coins (40-80 IRF)

**Monster 6: Gray Wolf (MON_002) - War Wolves**
- **Level:** 15
- **HP:** 600 (trained war wolves, stronger)
- **Spawn Count:** 4 wolves
- **Spawn Pattern:** Patrolling with elite warriors
- **Density:** Low (paired with warriors)
- **Location:** Accompanying goblin elite guards
- **Behavior:**
  - Loyal to goblins (attacks player on sight)
  - Pack Tactics with ANY nearby enemy (not just wolves)
  - Fast interceptors (rushes ranged players)
  - Howl alerts ALL nearby enemies
- **Loot:** Quality Wolf Pelt, Raw Meat

**Checkpoint 2:** After clearing inner keep, before boss door

**Pre-Boss Safe Zone:**
- Small room before throne room
- Can rest, prepare buffs
- Cannot be attacked by monsters
- Shrine to restore HP/MP to full

---

#### Zone 4: Throne Room (Boss Arena)

**BOSS: Goblin King (MON_010)**
- **Level:** 20
- **HP:** 12,000 (scaled for 1-5 players dynamically)
- **Arena:** Large circular throne room, 40m diameter
- **See Section 2.1.5 for full boss mechanics**

---

### 2.1.4 Dungeon Scaling System

**Dynamic Difficulty Scaling:**
```lua
-- Scaling Formula
MonsterHP = BaseHP × (1 + 0.3 × (PartySize - 1))
BossHP = BaseBossHP × (0.8 + 0.3 × PartySize)

Examples:
1 player solo: Boss HP = 9,600 (80% of base)
2 players: Boss HP = 13,200 (110%)
3 players: Boss HP = 16,800 (140%)
4 players: Boss HP = 20,400 (170%)
5 players: Boss HP = 24,000 (200%)
```

**Monster Spawn Scaling:**
- 1 player: Minimum spawns (8 goblins in Zone 1)
- 2-3 players: Medium spawns (10 goblins)
- 4-5 players: Maximum spawns (12 goblins)

**Loot Scaling:**
- Each player gets PERSONAL chest regardless of party size
- Loot quality does NOT change with party size
- Boss always drops same quality per-player

---

### 2.1.5 Boss Fight: Goblin King

**Boss Arena Layout:**
- Circular throne room, 40 meters diameter
- Throne at north end
- 4 pillars (can be used for cover)
- No environmental hazards (pure combat focus)

**Phase 1 (100-60% HP):**

**Behavior:**
- Melee combat from throne platform
- Summons Goblin Warriors periodically
- Basic attack rotation

**Abilities:**
- **Cleave Attack:** Wide frontal swing, 120 damage, 120° arc, 1.5 sec telegraph
- **Summon Royal Guards:** Calls 3 Goblin Warriors (800 HP each) every 30 seconds
  - Warriors must be killed or they buff king (+10% damage per guard alive)
  - Max 6 warriors alive at once
- **Royal Command:** Buffs all goblins +40% damage for 15 seconds (60 sec cooldown)
  - Visual: Golden aura appears on all goblins
  - Counter: Kill adds quickly before buff applied

**Phase 2 (60-30% HP):**

**Transition:** 
- Goblin King jumps off throne
- Drinks rage potion (2 sec animation)
- Roars (intimidation effect)

**Behavior:**
- More aggressive, faster movement (+30% speed)
- Leaps to players
- Increased summon rate

**New Abilities:**
- **Leap Slam:** Jumps to random player, 200 damage + 5m knockback
  - Warning: Red target circle 2 sec before impact
  - Counter: Move out of circle
  - Cooldown: 15 seconds
- **Enhanced Summon:** Now calls 5 Goblin Warriors instead of 3
- **Whirlwind Spin:** Spins with weapon extended, 120 damage per hit, hits every 0.5 sec
  - Duration: 4 seconds
  - 360° rotation
  - Counter: Ranged attacks or run away
  - Cooldown: 25 seconds

**Phase 3 (<30% HP):**

**Transition:**
- Throws crown to ground
- Enters berserk rage
- Red aura surrounds him

**Behavior:**
- Desperate all-out assault
- Continuous goblin spawns
- Highest damage output

**Mechanics:**
- **Enrage Buff:** +50% attack speed, +40% damage, permanent
- **Desperate Summons:** Goblin Warriors spawn every 15 seconds (continuous)
  - Must use AoE to control adds
  - Max 10 warriors active
- **Execute Phase:** Must burn boss down quickly or overwhelmed
- **Final Stand:** At 5% HP, does massive AoE slam (300 damage, entire arena)
  - Can be interrupted by stunning the king during windup

**Victory Condition:**
- Goblin King dies
- All remaining Goblin Warriors flee (despawn)
- Victory music plays
- Treasure chests spawn for each player
- Exit portal appears (3-minute countdown starts)

---

### 2.1.6 Loot System & Rewards

**Personal Chest System:**
- Each player receives individual chest
- Chests spawn at throne platform after boss death
- Chests have player names above them (cannot loot others)
- 3-minute timer to loot before force-teleport

**Chest Rarity Roll Per Player:**
```lua
-- Each player rolls independently
RarityRoll = math.random(1, 100)

if RarityRoll <= 5 then
    ChestRarity = "Legendary" -- 5% chance
elseif RarityRoll <= 20 then
    ChestRarity = "Epic" -- 15% chance
elseif RarityRoll <= 50 then
    ChestRarity = "Rare" -- 30% chance
else
    ChestRarity = "Common" -- 50% chance
end
```

**Chest Contents by Rarity:**

**Common Chest (50% chance):**
- 500-800 IRF
- Goblin Steel: 5-10 units
- Iron Ore: 10-20 units
- 1× Rare equipment (Level 12-18)
- 2× Common equipment
- 5× Health Potions (Medium)

**Rare Chest (30% chance):**
- 1,200-1,800 IRF
- Goblin Steel: 10-20 units
- Gold Ore: 5-10 units
- 2× Rare equipment (Level 12-18)
- 1× Epic equipment (30% chance)
- Epic Geode: 1-2 units
- 10× Health Potions (Medium)

**Epic Chest (15% chance):**
- 2,500-4,000 IRF
- Goblin Steel: 20-30 units
- Gold Ore: 10-20 units
- 2× Epic equipment (Level 14-18)
- 1× Legendary equipment (20% chance)
- Epic Geode: 3-5 units
- Legendary Geode: 1 unit (40% chance)
- 15× Health Potions (Large)

**Legendary Chest (5% chance):**
- 5,000-8,000 IRF
- Goblin Steel: 40-60 units
- Mithril Ore: 5-10 units
- 3× Epic equipment
- 1× Legendary equipment (guaranteed)
- Legendary Geode: 2-3 units
- **Goblin Mount Egg** (10% chance within Legendary chest)
- **Goblin King Crown** (cosmetic hat, 5% chance)
- 20× Health Potions (Large)

**Guaranteed Boss Drops (ALL players receive):**
- Achievement: "Goblin Slayer" (first clear)
- 200 XP (base) × party size multiplier
- Goblin King Trophy (quest item for Captain Zara)

---

### 2.1.7 Exit System

**Exit Portal Mechanics:**

**Portal Spawn:**
- Appears 5 seconds after boss death
- Location: Center of throne room
- Visual: Glowing blue swirling portal
- Sound: Mystical humming

**3-Minute Countdown:**
- Countdown UI appears top of screen
- Text: "Portal closing in 2:45..."
- Warning at 1 minute: "Portal closing soon!"
- Warning at 30 seconds: "Portal closing! Finish looting!"

**Force Teleport:**
- At 0:00, ALL remaining players teleported to Main Town
- Teleports to Town Square spawn point
- Unlocked chests are LOST if not looted
- Warning message: "You have been teleported out of the dungeon"

**Manual Exit (Teleportation Scroll):**
- Item: Teleportation Scroll
- Purchase from: **Gruff the Blacksmith** (Town Hub, Blacksmith Shop)
- Cost: 100 IRF per scroll
- Usage: Right-click scroll in inventory → "Use" → instant teleport to Main Town
- Can be used ANYWHERE in dungeon (even during combat)
- Has 3-second cast time (can be interrupted by damage)
- Visual: Blue magic circle appears under player

---

### 2.1.8 Daily Lockout System

**Completion Limits:**
- Can run dungeon **3 times per day** (resets at midnight UTC)
- Loot Quality:
  - **1st run:** 100% loot (full rewards)
  - **2nd run:** 60% loot (reduced chest quality)
  - **3rd run:** 30% loot (minimal rewards)
- XP always full (no reduction)
- Achievements only granted on first-ever clear

**Lockout Display:**
- Dungeon portal shows: "Runs remaining today: 2/3"
- After 3 runs: "Daily limit reached. Resets in 8 hours"

---

---

## DUNGEON 2: CRYSTAL CAVERN

### 2.2.1 Basic Information

**Dungeon Type:** Elite Dungeon  
**Theme:** Magical crystal caves, arcane guardians  
**Minimum Level:** 25  
**Recommended Level:** 28-35  
**Party Size:** 1-5 players (scalable difficulty)  
**Estimated Clear Time:** 35-45 minutes  
**Difficulty Rating:** ⭐⭐⭐⭐ (Medium-Hard)

**Unlock Requirements:**
- Reach Player Level 25
- Clear Goblin Fortress at least once
- Complete Quest: "Mysterious Crystal Signals" (from Elder Willow)
- Pay Unlock Fee: 5,000 IRF (one-time)

**Entry Location:**
- Mountain Pass → Crystal Canyon → Cavern Entrance
- Large crystal formation acts as portal

---

### 2.2.2 Dungeon Structure (Linear Layout)

```
[ENTRANCE CHAMBER]
    ↓
[CRYSTAL MAZE] (Puzzle + Monster Zone 1)
    ↓
[UNDERGROUND LAKE] (Monster Zone 2)
    ↓
[CRYSTAL FOREST] (Monster Zone 3)
    ↓
[GUARDIAN SANCTUM] (Boss Arena)
    ↓
[EXIT PORTAL]
```

**Total Distance:** ~1,200 meters  
**Checkpoint System:** 3 checkpoints  
**Special Feature:** Puzzle mechanics integrated

---

### 2.2.3 Monster Distribution

#### Zone 1: Crystal Maze (Entry + Puzzle Area)

**Monster 1: Giant Cave Spider (MON_006)**
- **Level:** 28
- **HP:** 1,800 (dungeon-buffed)
- **Spawn Count:** 10-15 spiders
- **Spawn Pattern:** Hanging from ceiling, ambush-style
- **Density:** High (narrow corridors = frequent encounters)
- **Location:**
  - 4-6 spiders in entrance chamber
  - 6-9 spiders throughout maze corridors
  - Ambush points at puzzle switches
- **Behavior:**
  - Drops from ceiling (surprise attacks)
  - Poison Bite (30% chance, 25 damage/sec for 5 sec)
  - Web Shot (slows player 50% for 3 sec, 15 sec cooldown)
  - Aggro range: 12 meters
  - Groups of 2-3 attack together
- **Loot:** Spider Silk, String, Poison Gland

**Environmental Puzzle:**
- **Crystal Color Matching Puzzle**
- 4 colored crystals (Red, Blue, Green, Purple)
- Must activate in correct sequence (shown in murals on walls)
- Wrong order = electric shock (150 damage + stun 2 sec)
- Correct order = gate opens to next area
- Spiders respawn if puzzle takes too long (5 minutes)

---

#### Zone 2: Underground Lake (Water Area)

**Monster 2: Fire Elemental (MON_008) - Crystal Variant**
- **Level:** 30
- **HP:** 2,200 (dungeon-buffed)
- **Damage:** Crystal magic instead of fire
- **Spawn Count:** 8-12 elementals
- **Spawn Pattern:** Floating around lake shores and platforms
- **Density:** Medium (spread across large area)
- **Location:**
  - 4-5 elementals near shore entrances
  - 4-6 elementals on floating platforms
  - 2-3 elementals guarding checkpoint
- **Behavior:**
  - Ranged crystal shard projectiles (120 damage)
  - Crystal Burst AoE (200 damage, 5m radius, 20 sec cooldown)
  - Floating/flying (immune to ground effects)
  - Keeps distance from melee players
  - Aggro range: 20 meters
- **Resistances:** Physical -40%, Magic -20%
- **Weaknesses:** Blunt weapons +30%
- **Loot:** Crystal Essence, Amethyst, Ruby

**Environmental Hazards:**
- Deep water (players can't swim, instant death if fall in)
- Floating platform bridges (must jump carefully)
- Crystal stalactites (fall if vibrations, 300 damage)

**Checkpoint 2:** Safe platform after crossing lake

---

#### Zone 3: Crystal Forest (Pre-Boss Area)

**Monster 3: Orc Warrior (MON_007) - Crystal Cultists**
- **Level:** 32
- **HP:** 3,000 (elite dungeon variant)
- **Spawn Count:** 8-10 cultist orcs
- **Spawn Pattern:** Patrolling and praying at crystal shrines
- **Density:** High (clustered near boss entrance)
- **Location:**
  - 3-4 orcs guarding bridge to boss area
  - 2-3 orcs at each crystal shrine (2 shrines)
  - 2 orcs patrolling main path
- **Behavior:**
  - Power Strike (200 damage, 10 sec cooldown)
  - War Cry buffs nearby enemies +25% damage
  - Crystal Armor buff (absorbs 500 damage)
  - Aggressive charge attacks
  - Does NOT retreat
- **Loot:** Orc Steel, Gold Ore, Epic equipment (20%)

**Monster 4: Giant Cave Spider (MON_006) - Elite Variants**
- **Level:** 30
- **HP:** 2,400 (elite spiders)
- **Spawn Count:** 6 elite spiders
- **Spawn Pattern:** Guarding crystal formations
- **Density:** Low (paired with orcs)
- **Location:** Accompanying orc cultists
- **Behavior:**
  - Enhanced Web Shot (70% slow for 5 sec)
  - Poison Bite always applies (not chance-based)
  - Pack coordination with orcs
- **Loot:** Quality Spider Silk, Epic Geode (15%)

**Pre-Boss Chamber:**
- Large crystal formation arena entrance
- Safe zone before boss
- Healing shrine available
- Lore stone (readable text about Guardian)

**Checkpoint 3:** Before boss door

---

### 2.2.4 Boss Fight: Ancient Crystal Guardian

**BOSS: Ancient Crystal Guardian (MON_011)**
- **Level:** 35
- **HP:** 30,000 (scaled for 1-5 players)
- **Arena:** Massive circular crystal chamber, 60m diameter, floating platforms

**Boss Scaling:**
- 1 player: 24,000 HP
- 2 players: 33,000 HP
- 3 players: 42,000 HP
- 4 players: 51,000 HP
- 5 players: 60,000 HP

**Phase 1 (100-70% HP): Crystal Shield Active**

**Core Mechanic:**
- Boss has INVULNERABLE shield
- 4 Power Crystals around arena must be destroyed
- Each crystal has 3,000 HP
- Boss can only be damaged after all 4 crystals destroyed

**Boss Behavior:**
- Stationary in center of arena
- Casts defensive magic
- Summons Crystal Elementals

**Abilities:**
- **Crystal Spike Rain:** Spikes fall from ceiling (120 damage each, dodge circles)
  - Frequency: Every 10 seconds
  - Affects random 5m circles across arena
- **Summon Crystal Minions:** Creates 4 Crystal Elementals
  - Elementals: 2,500 HP each, ranged attacks
  - Spawn every 45 seconds
  - Must be cleared to focus on crystals
- **Shield Pulse:** Damages players within 10m of boss (50 damage/sec)
  - Forces players to destroy crystals from range

**Crystal Destruction:**
- Players must destroy 4 crystals around arena perimeter
- Crystals glow (Red, Blue, Green, Purple)
- Each crystal destroyed = Guardian takes 5% max HP damage
- When all 4 destroyed: Shield shatters, Phase 2 begins

**Phase 2 (70-40% HP): Aggressive Assault**

**Transition:**
- Shield shatters (animation)
- Guardian roars (screen shake)
- Becomes mobile and aggressive

**Boss Behavior:**
- Moves around arena
- Melee and ranged magic attacks
- Much more dangerous

**Abilities:**
- **Crystal Slam:** Melee attack, 250 damage, small AoE
  - Swing animation 1.5 sec telegraph
- **Prismatic Beam:** Sweeping laser beam across arena
  - 400 damage if hit
  - Beam sweeps 180° over 3 seconds
  - Clear audio warning ("PRISM CHARGING")
  - Counter: Run perpendicular to beam
  - Cooldown: 25 seconds
- **Crystal Spike Barrage:** Rapid-fire spike projectiles at players
  - 80 damage per spike
  - Shoots 15 spikes over 5 seconds
  - Targets random players
- **Crystal Storm AoE:** Creates crystal explosions across arena
  - 200 damage per explosion
  - 5 random locations
  - Warning: Ground cracks appear 2 sec before

**Phase 3 (<40% HP): Shield Reformation**

**Transition:**
- Guardian reforms crystal shield
- Now 6 Power Crystals instead of 4
- Boss becomes invulnerable again

**Boss Behavior:**
- Even more aggressive when vulnerable
- Uses ALL previous abilities
- Faster ability cooldowns

**Mechanics:**
- Must destroy 6 crystals (3,500 HP each)
- Crystals now respawn if not destroyed fast enough (2-minute timer)
- Guardian summons Crystal Elementals more frequently (every 30 sec)
- Arena hazards intensify:
  - More Crystal Spike Rain
  - Faster Prismatic Beam sweeps
  - Continuous Crystal Storms

**Final Burn Phase (<40% HP, crystals destroyed):**
- All abilities active
- Enrage timer (10 minutes from start, soft enrage)
- If enrage reached: Boss gains +100% damage (likely wipe)
- Must coordinate and burn boss down quickly

**Victory:**
- Guardian shatters into crystal fragments
- Central crystal core remains (lootable)
- Victory fanfare
- Personal chests spawn for each player
- Exit portal appears with 3-minute countdown

---

### 2.2.5 Loot System & Rewards

**Personal Chest Rarity Roll:**
```lua
-- Higher chance for better loot (Elite Dungeon)
RarityRoll = math.random(1, 100)

if RarityRoll <= 10 then
    ChestRarity = "Legendary" -- 10% chance
elseif RarityRoll <= 35 then
    ChestRarity = "Epic" -- 25% chance
elseif RarityRoll <= 70 then
    ChestRarity = "Rare" -- 35% chance
else
    ChestRarity = "Common" -- 30% chance
end
```

**Common Chest (30%):**
- 2,000-3,500 IRF
- Crystal Essence: 10-20 units
- Amethyst: 5-10 units
- 2× Epic equipment (Level 28-35)
- Epic Geode: 2-3 units

**Rare Chest (35%):**
- 4,500-7,000 IRF
- Crystal Essence: 20-40 units
- Amethyst: 10-20 units
- Diamond: 3-6 units
- 3× Epic equipment
- 1× Legendary equipment (40% chance)
- Legendary Geode: 1-2 units

**Epic Chest (25%):**
- 9,000-15,000 IRF
- Crystal Core Fragment: 5-10 units (rare crafting)
- Diamond: 10-20 units
- Mythril Ore: 3-6 units
- 2× Legendary equipment
- Legendary Geode: 3-5 units
- Mythic Geode: 1 unit (30% chance)

**Legendary Chest (10%):**
- 20,000-35,000 IRF
- Ancient Crystal Core: 1 unit (Mythic crafting, 10,000 IRF value)
- Diamond: 30-50 units
- Mythril Ore: 10-20 units
- 3× Legendary equipment
- Mythic Geode: 2-4 units
- **Crystal Guardian Pet Egg** (5% chance, Legendary familiar)
- **Crystal Weapon/Armor Set Piece** (15% chance, special visual effects)

**Guaranteed Drops (ALL players):**
- Achievement: "Crystal Champion" (first clear)
- Title: "Crystal Champion" (first clear)
- 800 XP base
- Crystal Guardian Trophy

---

---

## DUNGEON 3: VOLCANIC CORE

### 2.3.1 Basic Information

**Dungeon Type:** Elite Dungeon  
**Theme:** Lava, fire, volcanic environment  
**Minimum Level:** 35  
**Recommended Level:** 38-45  
**Party Size:** 1-5 players (scalable)  
**Estimated Clear Time:** 40-50 minutes  
**Difficulty Rating:** ⭐⭐⭐⭐⭐ (Hard)

**Unlock Requirements:**
- Reach Player Level 35
- Clear Crystal Cavern at least once
- Complete Quest: "The Volcanic Threat" (from Captain Zara)
- Pay Unlock Fee: 15,000 IRF

**Entry Location:**
- Volcanic Region → Lava Fields → Core Entrance
- Entrance is a massive lava cave

---

### 2.3.2 Dungeon Structure

```
[LAVA ENTRANCE]
    ↓
[MAGMA TUNNELS] (Monster Zone 1)
    ↓
[OBSIDIAN CHAMBER] (Monster Zone 2 + Miniboss)
    ↓
[MOLTEN CORE] (Monster Zone 3)
    ↓
[GOLEM FORGE] (Boss Arena)
    ↓
[EXIT PORTAL]
```

**Total Distance:** ~1,500 meters  
**Environmental Danger:** Constant heat (10 damage/sec if not on safe platforms)

---

### 2.3.3 Monster Distribution

#### Zone 1: Magma Tunnels

**Monster 1: Fire Elemental (MON_008)**
- **Level:** 38
- **HP:** 3,200
- **Spawn Count:** 15-20 elementals
- **Spawn Pattern:** Floating along lava rivers
- **Density:** Very High
- **Location:** Throughout tunnels
- **Behavior:**
  - Fireball attacks (140 damage)
  - Flame Burst AoE (300 damage, 5m)
  - Burning Aura (15 damage/sec nearby)
- **Loot:** Fire Essence, Ruby, Obsidian

#### Zone 2: Obsidian Chamber

**Monster 2: Lava Golem (MON_009) - Miniboss**
- **Level:** 40
- **HP:** 15,000 (miniboss)
- **Spawn Count:** 1 miniboss
- **Location:** Center of chamber (blocks progression)
- **Behavior:**
  - Earthquake Stomp (250 AoE, stuns 2 sec)
  - Lava Armor (reflects 25% melee damage)
  - Molten Core enrage at 30% HP
- **Loot:** Lava Core (100%), Obsidian (20-40 units), Epic/Legendary gear (50%)

**Monster 3: Fire Elemental (MON_008)**
- **Level:** 39
- **HP:** 3,400
- **Spawn Count:** 8-12 elementals
- **Location:** Supporting miniboss
- **Behavior:** Standard fire elemental tactics

#### Zone 3: Molten Core (Pre-Boss)

**Monster 4: Orc Warrior (MON_007) - Fire Cultists**
- **Level:** 42
- **HP:** 4,500
- **Spawn Count:** 10-12 orcs
- **Location:** Guarding forge entrance
- **Behavior:**
  - Enhanced Power Strike (300 damage)
  - Fire-enchanted weapons
  - War Cry + fire buff

**Monster 5: Lava Golem (MON_009) - Guards**
- **Level:** 41
- **HP:** 8,000
- **Spawn Count:** 2 golems
- **Location:** Flanking boss door
- **Behavior:** Standard golem mechanics

---

### 2.3.4 Boss Fight: Molten Titan

**BOSS: Molten Titan (Enhanced Lava Golem)**
- **Level:** 45
- **HP:** 80,000 (scaled 1-5 players)
- **Arena:** Circular forge, lava pools, platforms

**Phase 1 (100-60% HP):**
- Earthquake Stomp (300 damage, 3 sec stun)
- Lava Geyser (400 damage, erupts under random player)
- Summon 4 Fire Elementals every 40 seconds

**Phase 2 (60-30% HP):**
- Molten Armor (reflects 50% damage)
- Magma Wave (sweeps across arena, 500 damage)
- Arena lava rises (reduces safe platforms)

**Phase 3 (<30% HP):**
- Enrage mode (+80% damage)
- Continuous Fire Elemental spawns
- Meteor Storm (200 damage meteors rain down)
- Must burn quickly or wipe

**Loot:** Similar structure to Crystal Cavern, higher IRF/materials  
Legendary Chest can contain: **Molten Mount Egg (8%), Lava Core Weapon (12%)**

---

---

## DUNGEON 4: DRAGON'S LAIR

### 2.4.1 Basic Information

**Dungeon Type:** Raid Dungeon  
**Theme:** Epic dragon lair, ultimate challenge  
**Minimum Level:** 45  
**Recommended Level:** 48-50  
**Party Size:** 3-8 players (REQUIRES minimum 3 players)  
**Estimated Clear Time:** 60-90 minutes  
**Difficulty Rating:** ⭐⭐⭐⭐⭐⭐ (Extreme)

**Unlock Requirements:**
- Reach Player Level 45
- Clear ALL 3 previous dungeons
- Complete Quest Chain: "The Dragon Threat" (5-part quest from Captain Zara)
- Pay Unlock Fee: 50,000 IRF

**IMPORTANT:** Cannot enter solo - requires 3-8 players in party

---

### 2.4.2 Dungeon Structure

```
[MOUNTAIN ENTRANCE]
    ↓
[DRAGON HOARD] (Monster Zone 1)
    ↓
[LAVA CHAMBERS] (Monster Zone 2 + Hazards)
    ↓
[DRAKE NESTS] (Monster Zone 3 + Mini-bosses)
    ↓
[DRAGON'S THRONE] (Final Boss Arena)
    ↓
[EXIT PORTAL]
```

**Total Distance:** ~2,500 meters (longest dungeon)

---

### 2.4.3 Monster Distribution

#### Zone 1: Dragon Hoard

**Monster 1: Orc Warrior (MON_007) - Dragon Cultists**
- **Level:** 46
- **HP:** 6,000
- **Spawn Count:** 20-30 cultists
- **Density:** Very High (guards treasure)
- **Location:** Patrolling hoard chamber
- **Behavior:** Elite tactics, dragon-empowered

**Monster 2: Fire Elemental (MON_008)**
- **Level:** 47
- **HP:** 4,500
- **Spawn Count:** 15-20 elementals
- **Location:** Floating near lava pools

#### Zone 2: Lava Chambers

**Environmental Challenges:**
- Moving lava flows (500 damage/sec if touched)
- Collapsing bridges
- Timed platforming sections

**Monster 3: Lava Golem (MON_009) - Elite Guardians**
- **Level:** 48
- **HP:** 12,000
- **Spawn Count:** 4-6 golems
- **Location:** Blocking key passages

#### Zone 3: Drake Nests (3 Mini-Bosses)

**Mini-Boss 1: Fire Drake Alpha**
- **Level:** 49
- **HP:** 40,000
- **Mechanics:** Dragon breath, flight phases
- **Must defeat to progress**

**Mini-Boss 2: Shadow Drake**
- **Level:** 49
- **HP:** 35,000
- **Mechanics:** Stealth attacks, poison

**Mini-Boss 3: Storm Drake**
- **Level:** 49
- **HP:** 35,000
- **Mechanics:** Lightning, wind attacks

---

### 2.4.4 Boss Fight: Elder Dragon Ignis

**BOSS: Ignis the Elder Dragon (MON_012)**
- **Level:** 50
- **HP:** 200,000 (scaled for 3-8 players)
- **Arena:** Massive open-air dragon throne, 100m diameter

**Party Scaling:**
- 3 players: 150,000 HP
- 4 players: 175,000 HP
- 5 players: 200,000 HP
- 6 players: 225,000 HP
- 7 players: 250,000 HP
- 8 players: 280,000 HP

**Phase 1 (100-75% HP): Ground Combat**
- Claw attacks (400 damage)
- Tail swipe (350 AoE)
- Fire breath cone (500 damage, 25m)
- Summon 6 Dragon Whelps (7,000 HP each) every 60 sec

**Phase 2 (75-50% HP): Flight Phase**
- Dragon takes flight
- Aerial fire bombing (250 damage per bomb)
- Divebomb attacks (600 damage + knockback)
- Must use ranged attacks

**Phase 3 (50-25% HP): Enraged Ground**
- Returns to ground, enraged
- Inferno breath (800 damage, 35m cone)
- Earthquake stomp (400 AoE, 4 sec stun)
- Summons 12 Dragon Whelps
- Arena burns (200 damage/sec outside safe zones)

**Phase 4 (<25% HP): Desperate Flight**
- Final flight phase
- Meteor rain (200 damage per meteor, covers arena)
- Ultimate divebomb (1,000 damage)
- Must kill before mechanics overwhelm

**Special Mechanic: Tank Requirement**
- Dragon's attacks deal massive damage
- Requires dedicated tank with heavy armor
- Healers recommended for raid survival

---

### 2.4.5 Loot System & Rewards (Raid-Tier)

**Legendary Chest (Guaranteed for all players):**
- 50,000-100,000 IRF per player
- Dragon Scale: 100-200 units
- Dragon Heart Gem: 1 unit (30% chance, Mythic material)
- 4× Legendary equipment (Level 45-50)
- Mythic Geode: 3-6 units
- Mythril/Adamantite: 100-200 units

**Ultra-Rare Drops (Individual rolls):**
- **Dragon Mount Egg:** 8% chance (flying mount)
- **Dragon Weapon Set:** 15% chance (special dragon-tier weapons with fire effects)
- **Dragon Armor Set:** 12% chance (highest defense in game)
- **Void Crystal:** 5% chance (ultimate crafting material)

**Guaranteed Rewards:**
- Achievement: "Dragon Slayer"
- Title: "Dragonbane"
- 5,000 XP
- Dragon Trophy (prestigious item)

**Weekly Lockout:**
- Can only loot boss ONCE per week per difficulty
- Resets Monday 00:00 UTC
- Can help friends but won't receive loot after weekly clear
- XP still awarded on repeat kills

---

---

## Summary Table: All 4 Dungeons

| Dungeon | Type | Min Lvl | Rec Lvl | Party Size | Length | Boss | Difficulty |
|---------|------|---------|---------|------------|--------|------|------------|
| **Goblin Fortress** | Normal | 10 | 12-18 | 1-5 | 20-30m | Goblin King | ⭐⭐ |
| **Crystal Cavern** | Elite | 25 | 28-35 | 1-5 | 35-45m | Crystal Guardian | ⭐⭐⭐⭐ |
| **Volcanic Core** | Elite | 35 | 38-45 | 1-5 | 40-50m | Molten Titan | ⭐⭐⭐⭐⭐ |
| **Dragon's Lair** | Raid | 45 | 48-50 | 3-8 | 60-90m | Elder Dragon | ⭐⭐⭐⭐⭐⭐ |

---

## 3. Instance System

### 3.1 Instancing Mechanics

#### Private Instances
Each party gets a separate copy of the dungeon:
```lua
-- Instance Creation
local DungeonService = {}

function DungeonService:CreateInstance(dungeonId, partyLeader, partyMembers)
    local instance = {
        InstanceId = HttpService:GenerateGUID(false),
        DungeonId = dungeonId,
        PartyLeader = partyLeader,
        PartyMembers = partyMembers,
        CreatedAt = os.time(),
        Difficulty = "Normal", -- Normal, Hard, Nightmare
        Status = "Active", -- Active, Completed, Abandoned
        Progress = {
            BossesKilled = {},
            CheckpointsReached = {},
            SecretsFound = {}
        }
    }
    
    -- Reserve a server for this instance
    local reservedServer = TeleportService:ReserveServer(dungeonPlaceId)
    instance.ServerCode = reservedServer
    
    -- Store instance data
    InstanceDataStore:SetAsync(instance.InstanceId, instance)
    
    return instance
end

function DungeonService:TeleportToInstance(instance, players)
    local teleportOptions = Instance.new("TeleportOptions")
    teleportOptions.ReservedServerAccessCode = instance.ServerCode
    
    TeleportService:TeleportAsync(dungeonPlaceId, players, teleportOptions)
end
```

#### Instance Lifespan
- **Active:** Instance exists for 2 hours or until completion
- **Abandoned:** If all players leave for >10 minutes
- **Completed:** Boss defeated, 15-minute cooldown before forced exit
- **Expired:** Auto-destroyed after time limit

### 3.2 Party Formation

#### Creating a Dungeon Party
```lua
function PartyService:CreateDungeonParty(leaderId, dungeonId)
    local party = {
        PartyId = HttpService:GenerateGUID(false),
        LeaderId = leaderId,
        Members = {leaderId},
        DungeonId = dungeonId,
        Status = "Forming", -- Forming, Ready, InProgress
        MaxSize = DungeonData[dungeonId].MaxPlayers,
        MinSize = DungeonData[dungeonId].MinPlayers
    }
    
    -- Send invites
    PartyInviteRemote:FireClient(Players:GetPlayerByUserId(leaderId), party)
    
    return party
end

function PartyService:StartDungeon(partyId)
    local party = PartyData[partyId]
    
    -- Validate party
    if #party.Members < party.MinSize then
        return false, "Not enough players"
    end
    
    -- Check level requirements
    for _, memberId in ipairs(party.Members) do
        local level = PlayerDataService:GetLevel(memberId)
        if level < DungeonData[party.DungeonId].MinLevel then
            return false, "Player level too low"
        end
    end
    
    -- Create instance and teleport
    local instance = DungeonService:CreateInstance(
        party.DungeonId,
        party.LeaderId,
        party.Members
    )
    
    local players = {}
    for _, memberId in ipairs(party.Members) do
        table.insert(players, Players:GetPlayerByUserId(memberId))
    end
    
    DungeonService:TeleportToInstance(instance, players)
    party.Status = "InProgress"
    
    return true
end
```

### 3.3 Matchmaking (Optional)

#### Queue System
Players can queue for random parties:
- **Role Selection:** Tank, DPS, Healer (based on equipment)
- **Matching Algorithm:** Balances party composition
- **Wait Time:** Max 5 minutes, else solo/smaller party option
- **Rewards Bonus:** +10% loot for using matchmaking

---

## 4. Difficulty Tiers

### 4.1 Normal Mode
**Purpose:** Accessible content, learning mechanics  
**Modifiers:**
- Enemy HP: 100%
- Enemy Damage: 100%
- Loot Quality: Base rates

**Rewards:**
- Common/Rare equipment
- Standard material drops
- Base IRF rewards

### 4.2 Hard Mode
**Requirements:** Complete Normal mode first  
**Modifiers:**
- Enemy HP: 200%
- Enemy Damage: 150%
- New mechanics added to bosses
- Loot Quality: +50% better rolls

**Rewards:**
- Rare/Epic equipment (increased rates)
- 2× material drops
- 1.5× IRF rewards
- Hard Mode Achievement

### 4.3 Nightmare Mode
**Requirements:** Complete Hard mode + Level cap  
**Modifiers:**
- Enemy HP: 400%
- Enemy Damage: 250%
- All boss mechanics active
- Enrage timers added
- Permadeath (kicked from dungeon if die)
- Loot Quality: Best possible rolls

**Rewards:**
- Epic/Legendary equipment (guaranteed)
- 5× material drops
- 3× IRF rewards
- Mythic Geode (10% chance)
- Exclusive cosmetics
- Nightmare Achievement + Title

---

## 5. Dungeon Mechanics

### 5.1 Environmental Hazards

#### Lava/Fire
- Deals 50 damage/sec
- Visual warning (orange glow)
- Safe paths clearly marked

#### Poison Gas
- Reduces max HP by 50% while in cloud
- Can be cleared with wind abilities
- Green particle effects

#### Collapsing Ceiling
- Timer-based pressure mechanic
- 300 damage if hit by rocks
- Audio cues (rumbling)

#### Spike Traps
- Floor traps in corridors
- 200 damage + bleed effect
- Visible pressure plates

### 5.2 Puzzle Elements

#### Crystal Matching Puzzle
Used in Crystal Cavern:
1. Four colored crystals (Red, Blue, Green, Purple)
2. Must activate in correct sequence
3. Wrong order = electric shock (100 damage)
4. Correct order = door opens
5. Sequence shown in murals on walls

#### Lever Coordination
Requires multiple players:
1. 3 levers in different rooms
2. Must be pulled simultaneously (within 3 seconds)
3. Opens main gate
4. Resets if not synchronized

#### Light Beam Redirect
Crystal Cavern mechanic:
1. Use mirrors to redirect light beams
2. Hit all 4 receiver crystals
3. Powers the boss arena shields
4. Physics-based puzzle

### 5.3 Secret Areas

#### Hidden Treasure Rooms
- Found by exploring thoroughly
- Destructible walls (crack visual hints)
- Contains:
  - Extra loot chest (Epic+ items)
  - Rare crafting materials
  - Achievement progress
  - Lore books/notes

#### Secret Boss (Optional Challenge)
Some dungeons have hidden bosses:
- Requires finding 3 hidden keys
- Bonus boss harder than main boss
- Exclusive loot pool (cosmetics, mounts)
- Achievement: "Secret Keeper"

---

## 6. Boss Encounters

### 6.1 Boss Design Philosophy
All dungeon bosses follow this structure:
- **Phase-based combat:** 2-3 phases minimum
- **Telegraphed attacks:** Clear visual warnings (1-2 sec)
- **Add mechanics:** Summon minions periodically
- **Environmental use:** Arena hazards
- **Enrage timer:** 10-15 minutes (Nightmare mode only)

### 6.2 Example Boss: Goblin King

#### Phase 1 (100-60% HP)
**Behavior:** Melee combat with basic adds  
**Abilities:**
- **Cleave Attack:** Wide frontal swing (80 damage, 120° arc)
  - Warning: Raises weapon 1 second before
  - Counter: Move behind or sides
  
- **Summon Guards:** Calls 3 Goblin Warriors every 30 sec
  - Warriors have 500 HP each
  - Must kill or they buff king (+10% damage per guard alive)
  
- **Royal Command:** Buffs all goblins +40% damage (15 sec duration, 60 sec cooldown)
  - Visual: Golden aura on all goblins
  - Counter: Kill adds quickly or kite

#### Phase 2 (60-30% HP)
**Transition:** Jumps to throne, drinks potion  
**Behavior:** Enraged, faster attacks  
**New Abilities:**
- **Leap Slam:** Jumps to target player (150 damage, 5m knockback)
  - Warning: Red target circle appears 2 sec before
  - Counter: Move out of circle
  
- **Goblin Horde:** Summons 5 Goblin Warriors instead of 3
  
- **Whirlwind:** Spins with weapon (100 damage/hit, hits rapidly)
  - Duration: 5 seconds
  - Counter: Run away, use ranged attacks

#### Phase 3 (<30% HP)
**Transition:** Throws crown, goes berserk  
**Behavior:** Desperate, chaotic  
**Mechanics:**
- **Continuous Spawns:** Goblins spawn every 15 sec (must AoE)
- **Enrage Buff:** +50% attack speed, +30% damage
- **Execution Phase:** Must kill quickly or overwhelmed by adds

**Victory:**
- Goblin King dies, adds flee
- Treasure chest appears (guaranteed loot)
- Exit portal opens
- 30-second timer to loot before auto-exit

### 6.3 Boss Loot System

#### Loot Distribution (Party Dungeons)
```lua
function BossLootService:DistributeLoot(bossId, partyMembers)
    local lootTable = BossLootTables[bossId]
    local difficulty = Instance.Difficulty
    
    -- Generate loot pool
    local lootPool = {}
    
    for _, lootEntry in ipairs(lootTable) do
        local roll = math.random(1, 100)
        local dropChance = lootEntry.DropRate * DifficultyMultipliers[difficulty]
        
        if roll <= dropChance then
            table.insert(lootPool, lootEntry.ItemId)
        end
    end
    
    -- Currency rewards (split)
    local currencyReward = lootTable.BaseCurrency * DifficultyMultipliers[difficulty]
    local currencyPerPlayer = math.floor(currencyReward / #partyMembers)
    
    -- Equipment distribution (need/greed system)
    for _, itemId in ipairs(lootPool) do
        local needRolls = {}
        local greedRolls = {}
        
        -- Players roll
        for _, playerId in ipairs(partyMembers) do
            local canUse = ItemService:CanPlayerUse(playerId, itemId)
            
            if canUse then
                -- Need roll (1-100)
                needRolls[playerId] = math.random(1, 100)
            else
                -- Greed roll (1-50)
                greedRolls[playerId] = math.random(1, 50)
            end
        end
        
        -- Award to highest roller
        local winner = DetermineWinner(needRolls, greedRolls)
        ItemService:AwardItem(winner, itemId)
    end
    
    -- Award currency to all
    for _, playerId in ipairs(partyMembers) do
        CurrencyService:AddCurrency(playerId, currencyPerPlayer)
    end
    
    return lootPool
end
```

---

## 7. Loot System

### 7.1 Chest Types

#### Wooden Chest (Common)
Found throughout dungeon:
- 50-100 IRF
- Common materials (10-20 units)
- 20% chance for Common equipment
- Always appears in same locations

#### Silver Chest (Rare)
Hidden or guarded:
- 200-400 IRF
- Rare materials (5-10 units)
- 40% chance for Rare equipment
- 10% chance for Epic equipment
- Sometimes requires key

#### Boss Chest (Guaranteed)
Appears after boss defeat:
- Difficulty-scaled IRF (1,000-50,000)
- Epic+ materials (10-30 units)
- Guaranteed equipment drops (1-3 items)
- Dungeon-specific unique items
- Achievement items

### 7.2 Loot Tables

#### Goblin Fortress Boss Loot Table
```lua
GoblinKingLoot = {
    BaseCurrency = 5000, -- Split among party
    
    GuaranteedDrops = {
        {ItemId = "GOBLIN_CROWN", Quantity = 1}, -- Trophy
        {ItemId = "EPIC_GEODE", Quantity = {1, 2}, Chance = 80},
    },
    
    EquipmentPool = {
        -- Weapons (40% for one)
        {ItemId = "WPN_GOBLIN_SLAYER_SWORD", Rarity = "Epic", Chance = 15},
        {ItemId = "WPN_GOBLIN_KING_MACE", Rarity = "Epic", Chance = 15},
        {ItemId = "WPN_ROYAL_SPEAR", Rarity = "Epic", Chance = 10},
        
        -- Armor (40% for one piece)
        {ItemId = "ARM_GOBLIN_PLATE_HELMET", Rarity = "Epic", Chance = 15},
        {ItemId = "ARM_GOBLIN_PLATE_CHEST", Rarity = "Epic", Chance = 15},
        {ItemId = "ARM_GOBLIN_PLATE_LEGS", Rarity = "Epic", Chance = 10},
    },
    
    MaterialsPool = {
        {ItemId = "GOBLIN_STEEL", Quantity = {10, 20}, Chance = 100},
        {ItemId = "IRON_ORE", Quantity = {20, 40}, Chance = 90},
        {ItemId = "GOLD_ORE", Quantity = {5, 15}, Chance = 60},
    },
    
    RareDrops = {
        {ItemId = "GOBLIN_MOUNT_EGG", Rarity = "Legendary", Chance = 5},
        {ItemId = "LEGENDARY_GEODE", Rarity = "Legendary", Chance = 10},
    }
}
```

### 7.3 Daily/Weekly Lockouts

#### Daily Lockouts
- Each dungeon can be run 3 times per day (resets at midnight UTC)
- Full loot on first run
- 50% loot on second run
- 25% loot on third run
- XP always full

#### Weekly Lockouts
- Raid dungeons (Dragon's Lair): 1 full clear per week
- Boss loot: Once per week per difficulty
- Can help friends but no loot after first kill
- Weekly reset: Monday 00:00 UTC

#### Reset Tokens (Robux)
- Can purchase dungeon reset token: 50 Robux
- Resets lockout for one dungeon
- Max 1 purchase per dungeon per day
- Does NOT reset weekly raid lockouts

---

## 8. Progression & Unlocks

### 8.1 Dungeon Unlock Requirements

| Dungeon | Min Level | Prerequisite | Cost to Unlock |
|---------|-----------|--------------|----------------|
| Abandoned Mine | 5 | Complete Tutorial | Free |
| Haunted Crypt | 15 | Clear Abandoned Mine | 500 IRF |
| Goblin Fortress | 10 | Level requirement | 1,000 IRF |
| Crystal Cavern | 25 | Clear 3 other dungeons | 5,000 IRF |
| Dragon's Lair | 40 | Defeat all Hard modes | 20,000 IRF |
| Event Dungeons | Varies | Seasonal availability | Event tokens |

### 8.2 Achievement System

#### Dungeon Achievements

**First Clear Achievements:**
- "First Delve" - Clear first dungeon (500 IRF reward + Title)
- "Goblin Slayer" - Defeat Goblin King
- "Crystal Champion" - Clear Crystal Cavern
- "Dragon Slayer" - Defeat Elder Dragon (Title reward)

**Challenge Achievements:**
- "Speedrunner" - Clear any dungeon in under 10 minutes
- "No Deaths" - Complete dungeon without dying
- "Solo Legend" - Clear party dungeon alone
- "Secret Keeper" - Find all secrets in all dungeons

**Collection Achievements:**
- "Dungeon Master" - Clear all dungeons (10,000 IRF reward + Exclusive cosmetic)
- "Nightmare Conqueror" - Clear all Nightmare modes (Exclusive cosmetic)

### 8.3 Leaderboards

#### Per-Dungeon Leaderboards
Track:
- **Fastest Clear Time**
- **Highest Damage Dealt**
- **Most Clears (Weekly)**
- **Solo Clears**

Rewards:
- Top 10 weekly: Exclusive cosmetic
- Top 100: Title for the week
- Personal bests: Badge display

---

## 9. Technical Implementation

### 9.1 Server Architecture

```lua
-- Dungeon Server Script
local DungeonManager = {}
DungeonManager.ActiveInstance = nil
DungeonManager.PartyMembers = {}
DungeonManager.StartTime = 0
DungeonManager.BossesKilled = {}

function DungeonManager:Initialize(instanceData)
    self.ActiveInstance = instanceData
    self.PartyMembers = instanceData.PartyMembers
    self.StartTime = os.time()
    
    -- Spawn enemies
    self:SpawnWave(1)
    
    -- Setup boss encounters
    for _, bossData in ipairs(DungeonData[instanceData.DungeonId].Bosses) do
        self:SetupBoss(bossData)
    end
    
    -- Start hazards
    self:StartHazardSystems()
end

function DungeonManager:SpawnWave(waveNumber)
    local waveData = DungeonData[self.ActiveInstance.DungeonId].Waves[waveNumber]
    
    for _, enemyData in ipairs(waveData.Enemies) do
        local enemy = EnemyService:SpawnEnemy(
            enemyData.MonsterId,
            enemyData.SpawnPoint,
            self.ActiveInstance.Difficulty
        )
        
        enemy.Died:Connect(function()
            self:OnEnemyKilled(enemy)
        end)
    end
end

function DungeonManager:OnBossKilled(bossId)
    table.insert(self.BossesKilled, bossId)
    
    -- Check if dungeon complete
    if #self.BossesKilled >= #DungeonData[self.ActiveInstance.DungeonId].Bosses then
        self:CompleteDungeon()
    end
end

function DungeonManager:CompleteDungeon()
    local clearTime = os.time() - self.StartTime
    
    -- Award loot
    for _, playerId in ipairs(self.PartyMembers) do
        local player = Players:GetPlayerByUserId(playerId)
        if player then
            -- XP reward
            local xp = DungeonData[self.ActiveInstance.DungeonId].XPReward
            PlayerDataService:AddXP(player, xp)
            
            -- Achievement check
            AchievementService:CheckDungeonAchievements(player, {
                DungeonId = self.ActiveInstance.DungeonId,
                ClearTime = clearTime,
                Deaths = PlayerDataService:GetDungeonDeaths(player),
                Difficulty = self.ActiveInstance.Difficulty
            })
        end
    end
    
    -- Spawn exit portal
    self:SpawnExitPortal()
    
    -- Set 15-minute timer before shutdown
    task.delay(900, function()
        TeleportService:TeleportAsync(MainGamePlaceId, Players:GetPlayers())
    end)
end
```

### 9.2 Data Persistence

```lua
-- Save dungeon progress (for disconnects)
function DungeonDataService:SaveProgress(instanceId, progressData)
    local data = {
        InstanceId = instanceId,
        Progress = progressData,
        SavedAt = os.time(),
        ExpiresAt = os.time() + 7200 -- 2 hours
    }
    
    DungeonProgressStore:SetAsync(instanceId, data)
end

-- Restore progress on rejoin
function DungeonDataService:RestoreProgress(player, instanceId)
    local data = DungeonProgressStore:GetAsync(instanceId)
    
    if data and data.ExpiresAt > os.time() then
        -- Teleport back to instance
        local instance = InstanceDataStore:GetAsync(instanceId)
        if instance and instance.Status == "Active" then
            DungeonService:TeleportToInstance(instance, {player})
            return true
        end
    end
    
    return false
end
```

### 9.3 Performance Optimization

#### Enemy Pooling
```lua
local EnemyPool = {}

function EnemyPoolService:GetEnemy(monsterId)
    if not EnemyPool[monsterId] then
        EnemyPool[monsterId] = {}
    end
    
    -- Reuse inactive enemy
    for _, enemy in ipairs(EnemyPool[monsterId]) do
        if not enemy.Active then
            enemy.Active = true
            return enemy
        end
    end
    
    -- Create new if pool empty
    local newEnemy = EnemyService:CreateEnemy(monsterId)
    table.insert(EnemyPool[monsterId], newEnemy)
    return newEnemy
end

function EnemyPoolService:ReturnEnemy(enemy)
    enemy.Active = false
    enemy.Model.Parent = nil
    enemy.Health = enemy.MaxHealth
end
```

---

## 10. Balance & Economy

### 10.1 Reward Scaling

#### IRF per Minute Guidelines
Target earnings for efficient dungeon runs:

| Dungeon Level | Normal Mode | Hard Mode | Nightmare Mode |
|---------------|-------------|-----------|----------------|
| 5-10 | 100-200 IRF/min | 150-300 IRF/min | 300-500 IRF/min |
| 10-20 | 200-400 IRF/min | 400-800 IRF/min | 800-1,200 IRF/min |
| 20-30 | 400-800 IRF/min | 800-1,500 IRF/min | 1,500-2,500 IRF/min |
| 30-40 | 800-1,500 IRF/min | 1,500-2,500 IRF/min | 2,500-4,000 IRF/min |
| 40+ (Raids) | 1,500-3,000 IRF/min | 3,000-5,000 IRF/min | 5,000-8,000 IRF/min |

### 10.2 Equipment Drop Rates

#### Target Drop Rates per Run:
- **Common Equipment:** 60-80% (early dungeons)
- **Rare Equipment:** 40-60% (mid dungeons)
- **Epic Equipment:** 20-40% (late dungeons)
- **Legendary Equipment:** 10-25% (raid bosses, Nightmare mode)
- **Mythic Materials:** 5-15% (endgame raids)

### 10.3 Balancing Dungeons vs Other Activities

**Dungeons should:**
- Reward 2-3× more IRF/hour than farming mobs
- Provide guaranteed progression (equipment upgrades)
- Offer exclusive items not available elsewhere
- Require more skill/coordination (justified reward)

**BUT should not:**
- Make open-world content obsolete
- Be mandatory for all players (solo alternative paths exist)
- Provide all best-in-slot items (other systems contribute)

---

## Implementation Checklist

### Phase 1: Core System (Month 3-4)
- [ ] Instance system (private server reservation)
- [ ] Party formation and invites
- [ ] Basic dungeon: Abandoned Mine
- [ ] Boss encounter system (phase-based AI)
- [ ] Loot generation and distribution
- [ ] Dungeon UI (party frames, boss HP)

### Phase 2: Expansion (Month 5-6)
- [ ] 3 additional dungeons (variety of themes)
- [ ] Difficulty tiers (Normal, Hard, Nightmare)
- [ ] Matchmaking system
- [ ] Leaderboards and achievements
- [ ] Secret areas and optional bosses

### Phase 3: Endgame (Month 7-8)
- [ ] Raid dungeon (Dragon's Lair)
- [ ] Weekly lockout system
- [ ] Dungeon-specific cosmetic rewards
- [ ] Challenge modes and modifiers

### Phase 4: Polish (Month 9-10)
- [ ] Event dungeons (seasonal)
- [ ] Speedrun mode with timers
- [ ] Replay system (record runs)
- [ ] Advanced boss mechanics refinement

---

## Related Documentation
- [GDD_Systems_Combat.md](GDD_Systems_Combat.md) - Combat mechanics used in dungeons
- [Database_Monsters.md](Database_Monsters.md) - Enemy and boss data
- [Database_Weapons.md](Database_Weapons.md) - Equipment loot tables
- [GDD_Economy.md](GDD_Economy.md) - Reward balancing

---

**Document End - Dungeon System Design**  
*Ready for implementation and iteration based on playtesting feedback*
