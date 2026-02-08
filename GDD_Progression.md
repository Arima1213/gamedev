# IRIFA: Realms of Harvest & Adventure
## Game Design Document - Progression System

---

### Document Information
**Document Type:** Core System Design  
**System:** Player Progression & Advancement  
**Version:** 1.0  
**Last Updated:** February 9, 2026  
**Status:** Implementation Ready

---

## Table of Contents
1. [Overview](#1-overview)
2. [Level System](#2-level-system)
3. [Skill Proficiencies](#3-skill-proficiencies)
4. [Achievement System](#4-achievement-system)
5. [Quest System](#5-quest-system)
6. [Progression Milestones](#6-progression-milestones)
7. [Unlock Requirements](#7-unlock-requirements)
8. [Power Curve Design](#8-power-curve-design)
9. [Endgame Progression](#9-endgame-progression)
10. [Technical Implementation](#10-technical-implementation)

---

## 1. Overview

### 1.1 Progression Philosophy

**Multi-Path Progression:**
- No single "correct" way to progress
- All activities contribute to overall advancement
- Players can focus on preferred content
- **BUT** must engage with multiple systems for optimal progress

**Interconnected Growth:**
```
Mining Level → Better Tools → Rare Materials → Craft Better Gear → 
Harder Dungeons → Legendary Loot → Sell for Profit → 
Expand Island → Better Farming → Premium Crops → 
Feed Familiars → Stronger Companions → All Systems Enhanced
```

### 1.2 Progression Layers

| Layer | Purpose | Unlock |
|-------|---------|--------|
| Player Level | Overall progression, unlock systems | All activities give XP |
| Skill Proficiency | Mastery in specific activities | Focused grinding |
| Equipment Power | Combat effectiveness | Crafting + Dungeons |
| Island Development | Quality of life + economy | IRF investment |
| Collection Completion | Prestige + bonuses | Long-term engagement |
| Achievements | Milestone tracking | Challenging goals |

---

## 2. Level System

### 2.1 Player Level

**Max Level:** 100

**XP Sources:**
- Mining: 10 XP per ore mined
- Fishing: 15 XP per fish caught
- Farming: 20 XP per crop harvested
- Combat: 50-500 XP per monster killed (scales with rarity)
- Dungeon completion: 500-5,000 XP (scales with difficulty)
- Quests: 100-10,000 XP (varies by quest)
- Taming: 100-2,000 XP per creature tamed

**Level-Up Curve:**
```lua
function ProgressionService:CalculateRequiredXP(level)
    -- Exponential curve, slows at higher levels
    local baseXP = 100
    local exponent = 1.5
    
    return math.floor(baseXP * (level ^ exponent))
end

-- Examples:
-- Level 1→2: 100 XP
-- Level 10→11: 3,162 XP
-- Level 50→51: 353,553 XP
-- Level 99→100: 1,000,000 XP
```

**Level-Up Rewards:**
| Level Range | Rewards |
|-------------|---------|
| 1-10 (Tutorial) | System unlocks, free equipment |
| 11-30 (Early Game) | Stat boosts, new recipes, IRF bonuses |
| 31-60 (Mid Game) | Advanced content access, rare recipes |
| 61-90 (Late Game) | Legendary content, prestige items |
| 91-100 (Endgame) | Mythic recipes, exclusive titles |

### 2.2 Stats Per Level

**Base Stats (Level 1):**
- HP: 100
- Attack: 20
- Defense: 10
- Stamina: 100

**Per Level Gains:**
- HP: +10 per level (Max 1,100 at level 100)
- Attack: +2 per level (Max 218 at level 100)
- Defense: +1 per level (Max 109 at level 100)
- Stamina: +5 per level (Max 595 at level 100)

**Equipment adds to these base stats**, creating total player power.

---

## 3. Skill Proficiencies

### 3.1 Six Core Proficiencies

Each activity has separate skill progression:

#### Mining Proficiency
**Max Level:** 100

**Benefits per level:**
- Mining speed: +0.5% per level (50% faster at 100)
- Rare ore chance: +0.1% per level (10% bonus at 100)
- Geode find rate: +0.2% per level (20% bonus at 100)

**Milestone Unlocks:**
| Level | Unlock |
|-------|--------|
| 10 | Iron Pickaxe recipe |
| 25 | Deep Cave access |
| 50 | Mithril Pickaxe recipe |
| 75 | Dragon Heart Gem spawn unlock |
| 100 | Master Miner title, +20% all mining rewards |

#### Fishing Proficiency
**Max Level:** 100

**Benefits per level:**
- Catch speed: +0.3% per level
- Rare fish chance: +0.15% per level
- Multiple fish chance: +0.1% per level (can catch 2-3 fish)

**Milestone Unlocks:**
| Level | Unlock |
|-------|--------|
| 10 | Ocean fishing access |
| 25 | Storm fishing unlocked |
| 50 | Legendary fish spawn |
| 75 | Night fishing mastery (2× XP) |
| 100 | Master Angler title, Mythic fish guaranteed 1/day |

#### Farming Proficiency
**Max Level:** 100

**Benefits per level:**
- Growth speed: +0.5% per level
- Perfect quality chance: +0.2% per level
- Extra harvest: +0.1% per level (chance for bonus crops)

**Milestone Unlocks:**
| Level | Unlock |
|-------|--------|
| 10 | Rare seed access |
| 25 | Greenhouse structure |
| 50 | Epic seed access |
| 75 | Automatic harvesting |
| 100 | Master Farmer title, 2× harvest guaranteed |

#### Combat Proficiency
**Max Level:** 100

**Benefits per level:**
- Damage: +1% per level
- Critical chance: +0.1% per level
- Loot quality: +0.2% per level

**Milestone Unlocks:**
| Level | Unlock |
|-------|--------|
| 10 | Normal dungeons |
| 25 | Hard dungeons |
| 50 | Raid dungeons |
| 75 | Nightmare difficulty |
| 100 | Dungeon Master title, Boss keys guaranteed |

#### Taming Proficiency
**Max Level:** 100

**Benefits per level:**
- Taming success: +0.3% per level
- Familiar XP gain: +1% per level
- Bond speed: +0.5% per level

**Milestone Unlocks:**
| Level | Unlock |
|-------|--------|
| 10 | Rare creature taming |
| 25 | Breeding system |
| 50 | Epic creature taming |
| 75 | Legendary creature taming |
| 100 | Beast Master title, Mythic creature spawn |

#### Crafting Proficiency
**Max Level:** 100

**Benefits per level:**
- Craft speed: +0.5% per level
- Quality chance: +0.2% per level
- Material efficiency: +0.1% per level (chance to save materials)

**Milestone Unlocks:**
| Level | Unlock |
|-------|--------|
| 10 | Rare recipes |
| 25 | Enhancement system |
| 50 | Epic recipes |
| 75 | Legendary recipes |
| 100 | Master Craftsman title, Signature items |

### 3.2 Proficiency XP

```lua
function ProgressionService:AddProficiencyXP(player, proficiency, amount)
    local currentLevel = player.Proficiencies[proficiency].Level
    local currentXP = player.Proficiencies[proficiency].XP
    local requiredXP = CalculateProficiencyXP(currentLevel)
    
    currentXP = currentXP + amount
    
    -- Level up check
    while currentXP >= requiredXP and currentLevel < 100 do
        currentLevel = currentLevel + 1
        currentXP = currentXP - requiredXP
        requiredXP = CalculateProficiencyXP(currentLevel)
        
        -- Award level up rewards
        OnProficiencyLevelUp(player, proficiency, currentLevel)
    end
    
    player.Proficiencies[proficiency].Level = currentLevel
    player.Proficiencies[proficiency].XP = currentXP
end

function CalculateProficiencyXP(level)
    -- Similar curve to player level but scaled
    return math.floor(50 * (level ^ 1.5))
end
```

---

## 4. Achievement System

### 4.1 Achievement Categories

#### Collection Achievements
- **Fish Collector I-V:** Catch 10/50/100/300/all fish species
- **Mineral Hoarder I-V:** Mine 10/50/100/300/all mineral types
- **Green Thumb I-V:** Grow 10/50/100/300/all crop varieties
- **Beast Tamer I-V:** Tame 5/20/50/100/all creature types

**Rewards:** Titles, cosmetic items, stat bonuses

#### Combat Achievements
- **Monster Hunter I-V:** Defeat 100/500/1,000/5,000/10,000 monsters
- **Boss Slayer I-V:** Defeat 5/20/50/100/all bosses
- **Dungeon Delver I-V:** Complete 10/50/100/500/1,000 dungeons
- **Speedrunner:** Complete any dungeon under 5 minutes
- **Solo Legend:** Solo a party dungeon
- **Raid Leader:** Complete raid with 10 players

**Rewards:** Exclusive equipment, titles, dungeon keys

#### Economy Achievements
- **Entrepreneur I-V:** Earn 10K/100K/1M/10M/100M total IRF
- **Master Trader I-V:** Complete 50/200/500/1,000/5,000 trades
- **Market Mogul:** Have 100 successful market listings
- **Philanthropist:** Give away 1M IRF to other players

**Rewards:** Trading fee reduction, market slot expansion

#### Island Achievements
- **Architect I-V:** Place 50/200/500/1,000/2,000 decorations
- **Paradise Creator:** Reach 15,000 aesthetic score
- **Social Butterfly:** Receive 1,000 island visits
- **Five Star Island:** Maintain 5-star rating for 30 days

**Rewards:** Exclusive decorations, island expansion discounts

#### Progression Achievements
- **Rising Star:** Reach level 25
- **Veteran Adventurer:** Reach level 50
- **Legendary Hero:** Reach level 75
- **Master of All:** Reach level 100
- **Jack of All Trades:** Level 50 in all proficiencies
- **True Master:** Level 100 in any proficiency

**Rewards:** Stat boosts, titles, permanent luck bonus

### 4.2 Achievement Points

Each achievement awards points:
- Common achievements: 10 points
- Rare achievements: 25 points
- Epic achievements: 50 points
- Legendary achievements: 100 points
- Mythic achievements: 250 points

**Total Achievement Points unlock:**
- 1,000 AP: Exclusive title "Achiever"
- 2,500 AP: +5% luck permanently
- 5,000 AP: Exclusive mount
- 10,000 AP: Exclusive familiar
- 25,000 AP: Ultimate title "The Completionist"

---

## 5. Quest System

### 5.1 Quest Types

#### Main Story Quests
- Linear progression through game narrative
- Unlock major systems
- Cannot be abandoned
- Large XP and IRF rewards

**Main Quest Chain:**
1. **Welcome to IRIFA** - Meet Mayor (Tutorial)
2. **First Harvest** - Learn farming
3. **Angler's Apprentice** - Learn fishing
4. **Into the Depths** - Unlock mining/dungeons
5. **Forging Ahead** - Learn crafting
6. **Creature Comfort** - Unlock taming
7. **Trading Places** - Unlock trading
8. **Island Living** - Expand private island
9. **The Legendary Beast** - Tame legendary familiar
10. **The Void Rift** - Final story boss (unlock endgame)

#### Side Quests (NPC Quests)
- Optional, repeatable quests from NPCs
- Various requirements and rewards
- Can have multiple active simultaneously

**Example Side Quests:**
- **Blacksmith's Order:** Craft 5 Iron Swords (Reward: 1,000 IRF, Blacksmithing XP)
- **Fisher's Challenge:** Catch 10 Rare fish (Reward: Better fishing rod)
- **Farmer's Bounty:** Deliver 20 Perfect crops (Reward: Rare seeds)

#### Daily Quests
- Refresh every 24 hours (real-time)
- Simple, quick objectives
- Encourages daily login

**Daily Quest Examples:**
- Mine 50 ores (Reward: 500 IRF, Mining XP)
- Catch 20 fish (Reward: 500 IRF, Fishing XP)
- Harvest 30 crops (Reward: 500 IRF, Farming XP)
- Defeat 20 monsters (Reward: 500 IRF, Combat XP)

**Max 5 dailies per day**, player chooses which to accept.

#### Weekly Quests
- Refresh every 7 days
- More challenging, higher rewards
- Encourage sustained engagement

**Weekly Quest Examples:**
- Complete 10 dungeons (Reward: 5,000 IRF, Rare equipment box)
- Tame 3 rare creatures (Reward: Legendary familiar egg)
- Earn 50,000 IRF from trading (Reward: Market expansion)

### 5.2 Quest Structure

```lua
QuestData = {
    QuestId = "MAIN_001",
    Name = "Welcome to IRIFA",
    Type = "MainStory",
    Description = "Meet the Mayor and learn about your new home",
    
    Objectives = {
        {Type = "TalkToNPC", Target = "NPC_MAYOR", Quantity = 1},
        {Type = "VisitLocation", Target = "PRIVATE_ISLAND", Quantity = 1},
        {Type = "TalkToNPC", Target = "NPC_FARMER", Quantity = 1}
    },
    
    Requirements = {
        Level = 1,
        PreviousQuest = nil
    },
    
    Rewards = {
        XP = 100,
        IRF = 500,
        Items = {
            {ItemId = "TOOL_WOODEN_HOE", Quantity = 1},
            {ItemId = "SEED_POTATO", Quantity = 5}
        },
        UnlockSystem = "Farming"
    }
}
```

---

## 6. Progression Milestones

### 6.1 Early Game (Levels 1-30)

**Goals:**
- Learn all basic systems
- Complete tutorial quests
- Build starter equipment
- Expand island once
- Tame first familiar

**Playtime:** 10-20 hours

**Key Unlocks:**
- Level 5: Private Island
- Level 10: Dungeon access
- Level 15: Taming system
- Level 20: Material Bank
- Level 25: Rare equipment crafting
- Level 30: Hard dungeons

### 6.2 Mid Game (Levels 31-60)

**Goals:**
- Master preferred proficiency
- Craft Epic equipment
- Complete collection indexes 50%
- Expand island to tier 4
- Form dungeon party

**Playtime:** 30-60 hours total

**Key Unlocks:**
- Level 35: Breeding system
- Level 40: Epic recipes
- Level 45: Raid dungeons
- Level 50: Choose specialization
- Level 55: Legendary content access
- Level 60: Nightmare dungeons

### 6.3 Late Game (Levels 61-90)

**Goals:**
- Craft Legendary equipment
- Complete raid content
- Achieve 75%+ collection
- Max out island
- Multiple level 100 proficiencies

**Playtime:** 80-150 hours total

**Key Unlocks:**
- Level 65: Legendary recipes
- Level 70: World boss access
- Level 75: Mythic familiar taming
- Level 80: Signature item crafting
- Level 85: Ultimate dungeon
- Level 90: Mythic recipes

### 6.4 Endgame (Levels 91-100)

**Goals:**
- 100% collection completion
- All achievements
- Perfect equipment sets
- Aesthetic island showcase
- Trading empire

**Playtime:** 150+ hours

**Key Unlocks:**
- Level 95: Endgame content
- Level 100: Max power, all systems mastered

---

## 7. Unlock Requirements

### 7.1 System Unlocks

```lua
SystemUnlocks = {
    Mining = {Level = 1, Quest = nil}, -- Available immediately
    Fishing = {Level = 1, Quest = "MAIN_002"},
    Farming = {Level = 5, Quest = "MAIN_001"},
    PrivateIsland = {Level = 5, Quest = "MAIN_001"},
    Combat = {Level = 10, Quest = "MAIN_004"},
    Dungeons = {Level = 10, Quest = "MAIN_004"},
    Crafting = {Level = 10, Quest = "MAIN_005"},
    Taming = {Level = 15, Quest = "MAIN_006"},
    Trading = {Level = 20, Quest = "MAIN_007"},
    MaterialBank = {Level = 20, IRF = 10000},
    Breeding = {Level = 35, Quest = "BREED_MASTER"},
    Raids = {Level = 45, DungeonsCompleted = 50},
    WorldBosses = {Level = 70, Quest = "WORLD_THREAT"}
}
```

### 7.2 Recipe Unlocks

Recipes unlock through:
1. **Level Requirements:** Automatic unlock at certain levels
2. **Quest Completion:** Complete NPC quest chains
3. **Discovery:** Experiment with materials
4. **Boss Drops:** Rare recipe scrolls
5. **Purchase:** Buy from NPCs with IRF

**Example Progression:**
- Level 1: Wooden tools
- Level 10: Stone tools, Copper equipment
- Level 20: Iron equipment
- Level 30: Steel equipment
- Level 40: Mithril equipment
- Level 50: Adamantite equipment
- Level 60: Dragon equipment
- Level 70: Void equipment

---

## 8. Power Curve Design

### 8.1 Damage Formula

```lua
function CombatService:CalculateDamage(attacker, defender, weapon)
    -- Base damage
    local baseDamage = attacker.Stats.Attack + weapon.Damage
    
    -- Proficiency bonus
    local profBonus = 1 + (attacker.CombatProficiency * 0.01)
    
    -- Equipment quality bonus
    local qualityBonus = weapon.Quality or 1.0
    
    -- Critical strike
    local critMult = 1.0
    if math.random() < attacker.Stats.CritChance then
        critMult = 1 + attacker.Stats.CritDamage
    end
    
    -- Calculate total damage
    local totalDamage = baseDamage * profBonus * qualityBonus * critMult
    
    -- Defense reduction
    local defense = defender.Stats.Defense
    local reduction = defense / (defense + 100)
    
    local finalDamage = totalDamage * (1 - reduction)
    
    return math.floor(finalDamage)
end
```

### 8.2 Power Scaling

**Expected Power Levels:**

| Level | Player HP | Player DPS | Enemy HP | Enemy DPS |
|-------|-----------|------------|----------|-----------|
| 1 | 100 | 20 | 50 | 10 |
| 10 | 200 | 60 | 200 | 30 |
| 25 | 350 | 150 | 800 | 80 |
| 50 | 600 | 400 | 3,000 | 200 |
| 75 | 850 | 800 | 10,000 | 400 |
| 100 | 1,100 | 1,500 | 30,000 | 800 |

**With maxed equipment:**
- Level 100 + Mythic gear: 3,000+ DPS
- Allows tackling world bosses (100K-200K HP)

---

## 9. Endgame Progression

### 9.1 Prestige System (Post-100)

**Option 1: Paragon Levels**
- Continue earning XP after level 100
- Every 1M XP = 1 Paragon level
- Each Paragon level: +0.5% to all stats
- No cap, endless progression

**Option 2: Mastery Tiers**
- Complete endgame challenges
- Unlock mastery tiers (Bronze → Silver → Gold → Platinum → Diamond)
- Each tier: Cosmetic upgrade + small stat boost

### 9.2 Endgame Activities

- **Weekly Raid Bosses:** Rotating ultra-hard bosses
- **Leaderboard Competitions:** Fastest dungeon clears
- **Seasonal Ladder:** Compete for top ranks each season
- **Perfect Collection:** 100% all indexes
- **Island Perfection:** Max aesthetic score
- **Trading Empire:** Become top trader

---

## 10. Technical Implementation

### 10.1 Progression Data Structure

```lua
PlayerProgression = {
    Level = 1,
    XP = 0,
    
    Proficiencies = {
        Mining = {Level = 1, XP = 0},
        Fishing = {Level = 1, XP = 0},
        Farming = {Level = 1, XP = 0},
        Combat = {Level = 1, XP = 0},
        Taming = {Level = 1, XP = 0},
        Crafting = {Level = 1, XP = 0}
    },
    
    Achievements = {
        Unlocked = {},
        TotalPoints = 0
    },
    
    Quests = {
        Active = {},
        Completed = {},
        Daily = {},
        Weekly = {}
    },
    
    Unlocks = {
        Systems = {},
        Recipes = {},
        Locations = {}
    }
}
```

### 10.2 Saving Progression

```lua
function ProgressionService:SaveProgression(player)
    local data = {
        Level = player.Level,
        XP = player.XP,
        Proficiencies = SerializeProficiencies(player),
        Achievements = SerializeAchievements(player),
        Quests = SerializeQuests(player)
    }
    
    ProgressionDataStore:SetAsync("Prog_" .. player.UserId, data)
end
```

---

## Implementation Checklist

### Phase 1: Core Progression (Month 2)
- [ ] Player level system (1-100)
- [ ] XP from all activities
- [ ] Basic stat scaling
- [ ] Level-up rewards
- [ ] UI for level display

### Phase 2: Proficiencies (Month 3)
- [ ] Six proficiency tracks
- [ ] Proficiency XP tracking
- [ ] Milestone unlocks
- [ ] Proficiency UI

### Phase 3: Achievements (Month 4)
- [ ] Achievement system framework
- [ ] 50+ achievements
- [ ] Achievement UI
- [ ] Point system and rewards

### Phase 4: Quests (Month 5)
- [ ] Main story quest chain (10 quests)
- [ ] Side quest system
- [ ] Daily quest rotation
- [ ] Weekly quest rotation
- [ ] Quest UI

### Phase 5: Endgame (Month 8-12)
- [ ] Prestige/Paragon system
- [ ] Endgame content
- [ ] Leaderboards
- [ ] Seasonal competitions

---

## Related Documentation
- All system docs (progression touches everything)
- [GDD_Economy.md](GDD_Economy.md) - IRF rewards
- [GDD_Systems_Combat.md](GDD_Systems_Combat.md) - Power scaling

---

**Document End - Progression System**  
*Multiple paths to mastery, all roads lead to greatness*
