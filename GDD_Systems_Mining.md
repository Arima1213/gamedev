# Game Design Document
## Mining System

---

### Document Information
**System Name:** Mining System  
**Document Version:** 1.0  
**Last Updated:** February 8, 2026  
**Owner:** Systems Design Team  
**Status:** Ready for Implementation

---

## Table of Contents
1. [System Overview](#system-overview)
2. [Core Mechanics](#core-mechanics)
3. [Mining Tools](#mining-tools)
4. [Rock Types & Properties](#rock-types--properties)
5. [Resource Yields](#resource-yields)
6. [Geode System](#geode-system)
7. [UI/UX Specifications](#uiux-specifications)
8. [Balance & Progression](#balance--progression)
9. [Technical Implementation](#technical-implementation)

---

## 1. System Overview

### Purpose
The Mining System provides players with a resource gathering mechanic focused on obtaining minerals and materials required for crafting equipment, tools, and progression. Mining occurs exclusively within dungeons, creating a risk-reward dynamic where players must balance resource gathering with combat encounters.

### Design Goals
- **Meaningful Progression**: Tool upgrades provide tangible improvements
- **Risk vs Reward**: Larger rocks offer better yields but take longer, exposing players to danger
- **RNG Management**: Multiple reward tiers balance luck and effort
- **Material Economy**: Minerals form the foundation of the crafting economy

### Player Value Proposition
*"Mining provides essential materials for progression while creating tense, rewarding moments as players decide whether to commit to large rocks or play safely with smaller ones."*

---

## 2. Core Mechanics

### 2.1 Location Requirements
**Rule:** Mining can ONLY be performed inside dungeons.

**Location Properties:**
- Dungeon instances contain designated mining zones
- Rocks spawn in procedurally selected positions
- Mining areas may contain hostile monsters
- Safe zones exist but offer reduced rock spawn rates

**Design Rationale:**
By restricting mining to dungeons, we create:
- Natural player flow between combat and gathering
- Tension during resource collection
- Dungeon replay value beyond combat
- Scarcity that maintains material value

### 2.2 Tool Requirement
**Rule:** Players MUST equip a Mining Tool to interact with rocks.

**Tool Slot:**
- Mining tools occupy the "Tool" equipment slot
- Cannot be used simultaneously with combat weapons
- Must be equipped before approaching rocks
- Quick-swap available via hotkey (configurable)

**Without Tool:**
- No interaction prompt appears on rocks
- Attempting to approach shows tutorial message: *"You need a Mining Tool to mine this rock. Visit the Blacksmith to craft one!"*

### 2.3 Mining Process

#### Step-by-Step Flow:
```
1. Player equips Mining Tool
   ↓
2. Player approaches rock (3 studs proximity)
   ↓
3. Interaction prompt appears [E] "Mine"
   ↓
4. Player initiates mining (hold E or click)
   ↓
5. Mining animation plays
   ↓
6. Rock durability bar depletes based on tool stats
   ↓
7. Rock breaks when durability reaches 0
   ↓
8. Loot calculation occurs
   ↓
9. Items appear and auto-collect to inventory
   ↓
10. Rock despawns, new rock spawns elsewhere
```

#### Mining Interaction:
- **Input Method**: Hold [E] key or click repeatedly
- **Visual Feedback**: 
  - Pickaxe swing animation
  - Impact particles on rock
  - Damage numbers appear (optional, can toggle)
  - Durability bar decreases
  - Screen shake (minimal, scaled with tool power)

- **Audio Feedback**:
  - Pickaxe impact sound (varies by rock type)
  - Mineral chipping sounds
  - Rock breaking sound (satisfying "crunch")
  - Loot drop sound

- **Cancellation**: 
  - Release [E] key to stop mining
  - Moving away >5 studs cancels
  - Taking damage interrupts (stagger mechanic)
  - Manually equipping weapon cancels

---

## 3. Mining Tools

### 3.1 Tool Rarity System

| Rarity | Mining Speed | Crafting Requirements | Visual Identifier |
|--------|--------------|----------------------|-------------------|
| **Common** | 1.0x (Base) | Basic materials + 100 IRF | Stone texture |
| **Rare** | 1.25x | Rare materials + 500 IRF | Blue gem accent |
| **Epic** | 1.5x | Epic materials + 2,000 IRF | Purple aura effect |
| **Legendary** | 2.0x | Legendary materials + 10,000 IRF | Golden glow + particles |
| **Mythic** | 2.75x | Mythic materials + 50,000 IRF | Red glow + intense particles |
| **Special** | 3.5x | Special materials + Quest completion | Rainbow shimmer + trail |

### 3.2 Tool Stats

**Primary Stat: Mining Speed**
- Determines how quickly rock durability depletes
- Calculation: `Durability Damage = (Base Power × Speed Multiplier) per 0.5 seconds`
- Base Power: 10 durability per tick

**Example Calculations:**
- Common Tool: 10 × 1.0 = 10 durability/tick
- Rare Tool: 10 × 1.25 = 12.5 durability/tick
- Mythic Tool: 10 × 2.75 = 27.5 durability/tick

**Secondary Stat: Durability (Tool Condition)**
- All tools have 1000 uses before breaking
- Each rock mined = 1 use consumed
- Durability display in inventory: `(847/1000 Uses)`
- Tools can be repaired at Blacksmith for 25% of crafting cost
- Broken tools remain in inventory but cannot be equipped

### 3.3 Tool Acquisition

#### Crafting at Blacksmith NPC
**Common Pickaxe Recipe:**
- 10× Iron Ore
- 5× Wood (from dungeon crates)
- 100 IRF

**Rare Pickaxe Recipe:**
- 15× Iron Ore
- 10× Copper Ore
- 5× Rare Gem Fragments
- 500 IRF

**Epic Pickaxe Recipe:**
- 20× Iron Ore
- 15× Silver Ore
- 10× Amethyst
- 5× Monster Scales (from dungeon enemies)
- 2,000 IRF

**Legendary+ Tools:**
- Require quest completion from Blacksmith
- Unlock after mining 1,000 rocks (tracked stat)
- Need rare boss materials
- Significantly higher costs

#### Starter Tool
- Players receive **Worn Pickaxe** (0.75x speed) free from tutorial
- 100 uses before breaking
- Must craft Common+ tools for reliable mining
- Tutorial quest teaches crafting process

### 3.4 Tool Enhancement System

**Buff Enhancement** (Applied at Blacksmith):
- Players provide special materials to enhance tool
- Adds visual aura to tool
- Provides stat bonuses

**Enhancement Tiers:**
| Tier | Speed Bonus | Luck Bonus | Visual | Material Cost |
|------|-------------|------------|--------|---------------|
| +1 | +5% | +2% | Faint glow | 5× Enhancement Crystals |
| +2 | +10% | +5% | Medium glow | 10× Enhancement Crystals |
| +3 | +15% | +8% | Bright glow | 20× Enhancement Crystals |
| +4 | +20% | +12% | Intense glow | 40× Enhancement Crystals |
| +5 (Max) | +25% | +15% | Radiant aura | 80× Enhancement Crystals |

**Enhancement Properties:**
- Enhancements persist through repairs
- Cannot be reversed (permanent choice)
- Tool must be at full durability to enhance
- Enhancement Crystals obtained from geodes or trading

---

## 4. Rock Types & Properties

### 4.1 Rock Size Categories

#### Small Rock
- **Durability:** 50 HP
- **Visual Size:** ~3 studs tall
- **Spawn Rate:** 60% of all rocks
- **Mining Time Examples:**
  - Common Tool: 5.0 seconds
  - Rare Tool: 4.0 seconds
  - Mythic Tool: 1.8 seconds

**Loot Table:**
- 40% chance: 1 mineral
- 35% chance: 2 minerals
- 20% chance: 1 geode
- 5% chance: Nothing

#### Medium Rock
- **Durability:** 150 HP
- **Visual Size:** ~5 studs tall
- **Spawn Rate:** 30% of all rocks
- **Mining Time Examples:**
  - Common Tool: 15.0 seconds
  - Rare Tool: 12.0 seconds
  - Mythic Tool: 5.5 seconds

**Loot Table:**
- 10% chance: 1 mineral
- 30% chance: 2 minerals
- 35% chance: 3 minerals
- 15% chance: 1 geode
- 8% chance: 2 geodes
- 2% chance: Nothing

#### Large Rock
- **Durability:** 300 HP
- **Visual Size:** ~8 studs tall
- **Spawn Rate:** 9% of all rocks
- **Mining Time Examples:**
  - Common Tool: 30.0 seconds
  - Rare Tool: 24.0 seconds
  - Mythic Tool: 10.9 seconds

**Loot Table:**
- 5% chance: 2 minerals
- 25% chance: 3 minerals
- 35% chance: 4 minerals
- 20% chance: 5 minerals
- 10% chance: 2 geodes
- 4% chance: 1 Sparkling Geode
- 1% chance: 1 mineral (unlucky)

#### Massive Rock (Rare Spawn)
- **Durability:** 500 HP
- **Visual Size:** ~12 studs tall, glows slightly
- **Spawn Rate:** 1% of all rocks
- **Mining Time Examples:**
  - Common Tool: 50.0 seconds
  - Rare Tool: 40.0 seconds
  - Mythic Tool: 18.2 seconds

**Loot Table:**
- 30% chance: 5 minerals
- 30% chance: 6 minerals
- 20% chance: 7 minerals + 1 geode
- 15% chance: 8 minerals + 2 geodes
- 5% chance: 10 minerals + 1 Sparkling Geode

### 4.2 Rock Spawn System

**Spawn Rules:**
- Maximum 20 rocks per dungeon instance simultaneously
- Rocks spawn in designated zones only
- New rock spawns 2-5 seconds after previous is mined
- Spawn locations are pseudo-random (avoid player collision)
- Size determined by weighted random based on rates above

**Spawn Location Zones:**
- **High Density Zones** (near entrances): Higher small/medium rock ratio
- **Deep Zones** (far from entrance): Higher medium/large rock ratio
- **Elite Zones** (near bosses): Highest chance for Massive rocks
- **Safe Zones**: Only small rocks spawn, but no monsters

**Visual Indicators:**
- Rocks emit faint particles matching mineral type
- Large+ rocks have ambient glow
- Massive rocks have unique model + pulsing effect
- Minimap shows rock locations as grey dots

---

## 5. Resource Yields

### 5.1 Mineral Types

#### Common Minerals (Grey Tier)
**Iron Ore**
- Drop Rate: 45% from any rock
- Base Amount: 1-3 per drop
- Uses: Base crafting material for all tools/weapons
- Stack Size: 999

**Copper Ore**
- Drop Rate: 30% from any rock
- Base Amount: 1-2 per drop
- Uses: Rare+ equipment crafting
- Stack Size: 999

**Stone Chunks**
- Drop Rate: 40% from any rock
- Base Amount: 2-5 per drop
- Uses: Building materials, decorations
- Stack Size: 999

#### Rare Minerals (Blue Tier)
**Silver Ore**
- Drop Rate: 15% from medium+ rocks
- Base Amount: 1-2 per drop
- Uses: Epic equipment crafting
- Stack Size: 999

**Gem Fragments**
- Drop Rate: 10% from any rock
- Base Amount: 1 per drop
- Uses: Enhancement materials
- Stack Size: 500

#### Epic Minerals (Purple Tier)
**Amethyst**
- Drop Rate: 8% from medium+ rocks
- Base Amount: 1 per drop
- Uses: Legendary equipment crafting
- Stack Size: 250

**Gold Ore**
- Drop Rate: 5% from large+ rocks
- Base Amount: 1 per drop
- Uses: High-tier equipment, selling for IRF
- Stack Size: 250

#### Legendary Minerals (Gold Tier)
**Diamond**
- Drop Rate: 3% from large+ rocks
- Base Amount: 1 per drop
- Uses: Mythic equipment crafting
- Stack Size: 100

**Titanium Ore**
- Drop Rate: 2% from massive rocks
- Base Amount: 1 per drop
- Uses: Mythic equipment, special recipes
- Stack Size: 100

#### Mythic Minerals (Red Tier)
**Mythril**
- Drop Rate: 1% from massive rocks
- Base Amount: 1 per drop
- Uses: Mythic equipment, exclusive recipes
- Stack Size: 50

**Orichalcum**
- Drop Rate: 0.5% from massive rocks (luck-dependent)
- Base Amount: 1 per drop
- Uses: Special equipment, ultimate upgrades
- Stack Size: 50

### 5.2 Luck Influence

**Luck Modifier Formula:**
```
Modified Drop Rate = Base Rate × (1 + (Luck Points / 100))
```

**Example:**
- Diamond base rate: 3%
- Player Luck: +50%
- Modified rate: 3% × (1 + 0.5) = 4.5%

**Luck Sources:**
- Tool enhancements: +2% to +15%
- Familiar buffs: +5% to +25%
- Server luck booster: +10% to +50%
- Weather effects: +5% (during rain in dungeon)

**Luck Caps:**
- Maximum total luck: +200% (3x base rates)
- Prevents excessive rate inflation
- Maintains material value

---

## 6. Geode System

### 6.1 Geode Types

#### Standard Geode (Grey/Brown)
- **Drop Rate:** 15% from small rocks, 8% from medium+
- **Contents:** Common-Epic minerals (1-3 items)
- **Opening Cost:** 50 IRF at Blacksmith
- **Visual:** Rough, stone-like appearance

**Loot Table:**
| Rarity | Probability | Quantity |
|--------|-------------|----------|
| Common | 50% | 2-3 minerals |
| Rare | 35% | 1-2 minerals |
| Epic | 15% | 1 mineral |

#### Large Geode (Grey/Brown)
- **Drop Rate:** 5% from medium+, 15% from large+
- **Contents:** Common-Epic minerals (3-10 items)
- **Opening Cost:** 150 IRF at Blacksmith
- **Visual:** Larger, heavier stone appearance

**Loot Table:**
| Rarity | Probability | Quantity |
|--------|-------------|----------|
| Common | 40% | 4-6 minerals |
| Rare | 40% | 3-5 minerals |
| Epic | 20% | 2-4 minerals |

#### Sparkling Geode (Shimmering)
- **Drop Rate:** 3% from large+, 8% from massive
- **Contents:** Legendary-Special minerals (1-3 items)
- **Opening Cost:** 500 IRF at Blacksmith
- **Visual:** Crystalline, emits particles

**Loot Table:**
| Rarity | Probability | Quantity |
|--------|-------------|----------|
| Epic | 30% | 2-3 minerals |
| Legendary | 50% | 1-2 minerals |
| Mythic | 18% | 1 mineral |
| Special | 2% | 1 mineral |

#### Large Sparkling Geode (Radiant)
- **Drop Rate:** 1% from large+, 5% from massive
- **Contents:** Legendary-Special minerals (2-5 items)
- **Opening Cost:** 1,500 IRF at Blacksmith
- **Visual:** Large crystalline, bright glow, particles

**Loot Table:**
| Rarity | Probability | Quantity |
|--------|-------------|----------|
| Epic | 20% | 3-4 minerals |
| Legendary | 45% | 2-3 minerals |
| Mythic | 30% | 1-2 minerals |
| Special | 5% | 1 mineral |

### 6.2 Geode Mechanics

**Opening Process:**
1. Player brings geodes to Blacksmith NPC
2. Click "Open Geodes" option
3. UI shows geode inventory
4. Select geodes to open (batch selection available)
5. Pay cumulative IRF cost
6. Confirmation dialog shows total cost
7. Opening animation plays (cracks, sparkles)
8. Loot reveal screen shows all items obtained
9. Items auto-transfer to inventory

**Geode Properties:**
- Geodes are tradeable between players
- Stack in inventory (max 99 per stack type)
- Can be sold unopened on Global Trading Board
- Luck does NOT affect geode contents (RNG at opening)
- Geode rarity is predetermined when obtained

**Strategic Value:**
- Geodes provide guaranteed mineral chances
- Large geodes more cost-efficient per mineral
- Sparkling geodes only reliable source of mythic minerals
- Trading market for sealed geodes creates speculation economy

---

## 7. UI/UX Specifications

### 7.1 Mining Interface

**HUD Elements During Mining:**
```
┌─────────────────────────────────────┐
│     [Rock Durability Bar]           │
│  ▓▓▓▓▓▓▓▓▓▓▓▓▓░░░░░░░░ 245/300     │
│                                     │
│  [Tool Durability]                  │
│  ⚒ Pickaxe: 847/1000                │
│                                     │
│  [Hold E to Mine] / [Release to Stop]│
└─────────────────────────────────────┘
```

**Components:**
1. **Rock Durability Bar**
   - Color: Yellow→Orange→Red as depletes
   - Numeric display: Current/Max HP
   - Position: Above rock, 4 studs high
   - Always visible when within 10 studs

2. **Tool Durability Indicator**
   - Shows in bottom-right HUD
   - Warning at <100 uses: Orange text
   - Critical at <20 uses: Flashing red
   - Icon shows tool rarity color
   - Tools will break once their durability reaches zero
   - Players are able to repair tools at the Blacksmith NPC, with a maximum of two repairs per tool
   - After a tool has been repaired twice, it will become permanently broken and can no longer be repaired
   - Players must purchase a new tool to replace a permanently broken one

3. **Mining Progress Feedback**
   - Damage numbers optional (settings toggle)
   - Screen edge vignette pulses with hits
   - Controller haptic feedback (if enabled)

### 7.2 Loot Collection UI

**Loot Popup:**
```
┌─────────────────────────────────────┐
│       ✨ ROCK MINED ✨              │
│                                     │
│  [Icon] Iron Ore ×3                 │
│  [Icon] Copper Ore ×1               │
│  [Icon] Standard Geode ×1           │
│                                     │
│         [Auto-Collected]            │
└─────────────────────────────────────┘
```

**Properties:**
- Appears center-screen for 2 seconds
- Lists all items obtained
- Icons use rarity colors
- Fade out animation
- Multiple popups queue if mining rapidly

### 7.3 Tool Selection Interface

**Inventory Equipment Screen:**
```
EQUIPMENT SLOTS:
┌─────────┬─────────┬─────────┐
│ Weapon  │  Tool   │  Armor  │
│ [Sword] │[Pickaxe]│[Helmet] │
│   ⚔️    │   ⚒️    │   🛡️    │
└─────────┴─────────┴─────────┘

QUICK SWAP: [1] Weapon / [2] Tool
```

**Quick Swap Mechanic:**
- Press [1] to equip weapon slot
- Press [2] to equip tool slot
- 0.5 second swap animation
- Cannot swap during mining/combat animations


---

## 8. Balance & Progression

### 8.1 Mining Progression Curve

**Early Game (Levels 1-10):**
- Goal: Learn mining basics, acquire starter materials
- Tool: Worn→Common pickaxe
- Primary Targets: Small rocks exclusively
- Expected Session: 30 rocks/hour = 300 IRF value materials
- Time to First Upgrade: ~2 hours mining

**Mid Game (Levels 11-30):**
- Goal: Efficient material farming, unlock rare equipment
- Tool: Rare→Epic pickaxe
- Primary Targets: Medium rocks, occasional large
- Expected Session: 50 rocks/hour = 1,200 IRF value materials
- Focus: Building material stockpile

**Late Game (Levels 31-50):**
- Goal: Hunt legendary+ materials, geode farming
- Tool: Legendary→Mythic pickaxe
- Primary Targets: Large rocks, hunt massive rocks
- Expected Session: 60 rocks/hour = 3,500 IRF value materials
- Focus: Rare mineral acquisition for mythic crafting

**End Game (Level 50+):**
- Goal: Perfect tool collection, material trading empire
- Tool: Mythic/Special pickaxes (multiple)
- Primary Targets: Massive rocks only (deep dungeon farming)
- Expected Session: 40 rocks/hour = 8,000+ IRF value materials
- Focus: Supplying trade market, completing mineral index

### 8.2 Material Sinks

**Primary Sinks:**
- Equipment crafting (weapons, tools, armor)
- Tool repairs (ongoing cost)
- Trading board fees (10% of trade value)
- NPC vendor sales (immediate IRF conversion)

**Secondary Sinks:**
- Enhancement materials crafting
- Quest requirements
- Event-specific recipes
- Rare decoration crafting

**Economic Balance Goals:**
- Maintain scarcity of legendary+ minerals
- Prevent common mineral inflation
- Reward consistent mining effort
- Allow catch-up mechanics for new players

### 8.3 Anti-Exploitation Measures

**Bot Prevention:**
- Mining requires active input (cannot macro hold)
- Random durability variations (±5%) prevent scripts
- Captcha prompt after 100 continuous rocks mined
- Teleport to safe zone after 3 failed captchas

**Fair Play:**
- Server-side validation of mining speed
- Maximum damage per tick enforced server-side
- Rock loot rolls calculated server-side only
- Impossible to client-side spoof rarity

**AFK Detection:**
- No mining action for 3 minutes = marked AFK
- Kicked from dungeon after 5 minutes AFK
- No progress saved if kicked for AFK

---

## 9. Technical Implementation

### 9.1 Roblox Architecture

**Rock Object Structure:**
```lua
Rock = {
    Model = [Roblox Model],
    Durability = {Current, Max},
    Size = "Small" | "Medium" | "Large" | "Massive",
    LootTable = {...},
    Position = Vector3,
    IsBeingMined = boolean,
    MiningPlayer = Player | nil,
    SpawnTime = tick(),
    UniqueID = UUID
}
```

**Mining Action Handler:**
```lua
-- Server-side mining validation
function ProcessMiningTick(player, rock, tool)
    -- Validate distance
    if (player.Position - rock.Position).Magnitude > 5 then
        return CancelMining(player)
    end
    
    -- Validate tool
    local toolStats = GetToolStats(tool)
    if not toolStats then return end
    
    -- Calculate damage
    local damage = toolStats.BasePower * toolStats.SpeedMultiplier
    
    -- Apply luck modifiers to damage
    local luckBonus = CalculateLuckBonus(player)
    
    -- Damage rock
    rock.Durability.Current -= damage
    
    -- Check if broken
    if rock.Durability.Current <= 0 then
        HandleRockBreak(player, rock, luckBonus)
    end
end
```

### 9.2 Loot Generation System

```lua
function GenerateLoot(rock, playerLuck)
    local lootTable = rock.LootTable
    local results = {}
    
    -- Roll for each possible item
    for _, item in ipairs(lootTable) do
        local modifiedRate = item.BaseRate * (1 + playerLuck / 100)
        modifiedRate = math.min(modifiedRate, item.MaxRate) -- Cap
        
        if math.random() < modifiedRate then
            local quantity = math.random(item.MinAmount, item.MaxAmount)
            table.insert(results, {
                ItemID = item.ID,
                Quantity = quantity,
                Rarity = item.Rarity
            })
        end
    end
    
    -- Guarantee at least something if unlucky
    if #results == 0 and math.random() > 0.05 then
        table.insert(results, GetGuaranteedLoot(rock.Size))
    end
    
    return results
end
```

### 9.3 Performance Considerations

**Rock Spawning:**
- Use object pooling (don't create/destroy constantly)
- Spatial hashing for distance checks
- LOD (Level of Detail) for distant rocks
- Maximum 20 rocks per instance prevents lag

**Particle Effects:**
- Pool particle emitters
- Reduce particle count on low-end devices
- Disable particles beyond 50 studs distance
- Scale effects with graphics quality setting

**Network Optimization:**
- Mining progress sent every 0.5s (not every frame)
- Loot generation server-side only
- Client prediction for durability bar smoothness
- Batch rock spawn updates

**Data Store:**
- Save mined rock count per player
- Save tool durability states
- Cache mineral inventory (save on change, not tick)
- Implement debounce on rapid mining sessions

---

## Implementation Checklist

### Phase 1: Core Mechanics
- [ ] Rock model assets (all sizes)
- [ ] Mining tool models (all rarities)
- [ ] Rock spawning system
- [ ] Mining interaction system
- [ ] Durability calculation logic
- [ ] Basic loot generation

### Phase 2: Polish
- [ ] Mining animations
- [ ] Particle effects
- [ ] Sound effects
- [ ] UI elements
- [ ] Tool enhancement system
- [ ] Luck integration

### Phase 3: Balance
- [ ] Playtesting sessions
- [ ] Drop rate tuning
- [ ] Economy balance
- [ ] Performance optimization
- [ ] Exploit testing

---

**Mining System - End of Document**

*Next System Documentation: [GDD_Systems_Fishing.md](GDD_Systems_Fishing.md)*
