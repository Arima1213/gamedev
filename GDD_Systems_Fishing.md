# Game Design Document
## Fishing System

---

### Document Information
**System Name:** Fishing System  
**Document Version:** 1.0  
**Last Updated:** February 8, 2026  
**Owner:** Systems Design Team  
**Status:** Ready for Implementation

---

## Table of Contents
1. [System Overview](#system-overview)
2. [Core Mechanics](#core-mechanics)
3. [Fishing Rods](#fishing-rods)
4. [Location System](#location-system)
5. [Fish Species & Catalog](#fish-species--catalog)
6. [Weather & Time Influences](#weather--time-influences)
7. [Treasure System](#treasure-system)
8. [UI/UX Specifications](#uiux-specifications)
9. [Balance & Progression](#balance--progression)
10. [Technical Implementation](#technical-implementation)

---

## 1. System Overview

### Purpose
The Fishing System provides a relaxing, collection-focused gameplay loop where players catch various fish species across different locations. Fish serve as crafting materials, familiar food, and tradeable commodities, creating economic value and encouraging exploration.

### Design Goals
- **Zen Gameplay**: Peaceful activity contrasting with dungeon combat
- **Collection Drive**: Extensive fish catalog encourages completionism
- **Location Exploration**: Different areas yield unique species
- **Weather Integration**: Environmental factors create dynamic experiences
- **Economic Participation**: Fish have value in multiple game systems

### Player Value Proposition
*"Fishing offers a meditative gameplay experience with satisfying collection mechanics, while contributing to creature taming, trading economy, and personal wealth building."*

---

## 2. Core Mechanics

### 2.1 Location Requirements

**Valid Fishing Locations:**
- Ocean zones (designated water bodies labeled "Ocean")
- River zones (flowing water bodies labeled "River")
- Special event waters (seasonal locations)

**Invalid Locations:**
- Puddles or shallow water (<4 studs deep)
- Private island ponds (unless upgraded)
- Dungeon water areas
- Town fountain decorations

**Visual Indicators:**
- Blue fishing icon appears on minimap near valid spots
- Water ripples indicate active fishing zone
- Fish silhouettes occasionally visible in water
- Weather effects (rain ripples, mist)

### 2.2 Fishing Rod Requirement

**Equipment Slot:**
- Fishing rods occupy "Tool" slot
- Cannot fish with weapon equipped
- Quick-swap hotkey available [1]/[2]
- Rod stats display when hovering in inventory

**Rod Inspection:**
- Right-click rod in inventory to view details
- Shows: Rarity, Enhancement level, Buff stats, Durability
- Compare feature shows stat differences

### 2.3 Fishing Process Flow

```
1. Player equips Fishing Rod
   ↓
2. Approaches valid water (within 5 studs)
   ↓
3. Presses [E] "Cast Line"
   ↓
4. Casting animation plays (0.8 seconds)
   ↓
5. Bobber lands in water (physics-based)
   ↓
6. Waiting phase (3-15 seconds, randomized)
   ↓
7. Bite indication (visual + audio + prompt)
   ↓
8. Player presses [E] within 2-second window
   ↓
9. Fish type determined (rarity check vs rod rarity)
   ↓
10. Mini-game plays (tension bar mechanic)
   ↓
11. Success = fish caught / Fail = fish escapes
   ↓
12. Loot collected automatically
   ↓
13. Repeat or move to new spot
```

### 2.4 Catch Mechanic: Tension Bar Mini-Game

**Mini-Game Description:**
A tension bar appears with a moving indicator. Player must keep indicator in "green zone" by timing button presses.

**UI Layout:**
```
┌─────────────────────────────────────────────┐
│   TENSION BAR                               │
│ ╔═══════════════════════════════════════╗   │
│ ║ ▓▓▓[▼]░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ ║   │
│ ╚═══════════════════════════════════════╝   │
│  ┃Green┃Yellow┃ Orange ┃  RED (Break!)     │
│                                             │
│  [SPACE] Reel In  |  [SHIFT] Release        │
│  Fish Stamina: ▓▓▓▓▓░░░░░░ 50/100           │
└─────────────────────────────────────────────┘
```

**Mechanics:**
- Tension increases when reeling [SPACE]
- Tension decreases when releasing [SHIFT]
- Indicator bounces back and forth
- Stay in green = optimal, yellow = acceptable, orange = risky, red = breaks line

**Fish Stamina:**
- Each fish has stamina points (varies by rarity)
- Reeling in green zone depletes stamina efficiently
- Reeling in yellow/orange = slower depletion
- Reeling in red = no stamina depletion + risk

**Success/Failure:**
- **Success:** Stamina reaches 0 = fish caught
- **Failure:** Tension bar fills completely = line breaks, fish escapes
- **Timeout:** 30 seconds without progress = auto-fail

**Difficulty Scaling:**
- Common fish: Slow indicator, high stamina depletion
- Rare fish: Medium indicator speed, moderate stamina
- Epic+ fish: Fast indicator, large stamina pool
- Legendary+ fish: Erratic indicator, massive stamina
- Mythic/Special: Expert-level timing required

**Rod Quality Impact:**
- Higher rarity rods have larger "green zone"
- Enhanced rods reduce fish stamina pool
- Buffed rods slow indicator movement speed

---

## 3. Fishing Rods

### 3.1 Rod Rarity & Stats

| Rarity | Green Zone Size | Catch Rate Modifier | Acquisition Method | Cost |
|--------|-----------------|---------------------|---------------------|------|
| **Common** | 15% of bar | 1.0x | Buy from Fisherman | 200 IRF |
| **Rare** | 18% of bar | 1.0x + Rare fish | Complete 10 Fish Quest | 1,000 IRF |
| **Epic** | 22% of bar | 1.0x + Epic fish | Complete 50 Fish Quest | 5,000 IRF |
| **Legendary** | 28% of bar | 1.0x + Legendary fish | Complete 150 Fish Quest | 25,000 IRF |
| **Mythic** | 35% of bar | 1.0x + Mythic fish | Complete 300 Fish Quest + Boss Material | 100,000 IRF |
| **Special** | 45% of bar | 1.0x + All fish | Special Event / Robux Shop | N/A |

**Catch Rate Modifier Explained:**
- Rod rarity determines WHICH fish you can catch
- Common rod: Only catches Common fish
- Rare rod: Catches Common + Rare fish
- Epic rod: Catches Common + Rare + Epic fish
- Higher rods unlock higher rarity fish encounters

### 3.2 Rod Enhancement System

**Blacksmith Rod Buffing:**
Players bring materials to Blacksmith to permanently enhance rods.

**Enhancement Types:**

| Enhancement | Effect | Materials Required | Visual |
|-------------|--------|-------------------|---------|
| **Speed Boost** | -10% indicator speed | 10× Fish Scales + 5× Silver | Blue aura |
| **Stamina Drain** | -20% fish stamina | 15× Shark Teeth + 10× Gold | Green aura |
| **Luck Infusion** | +15% rare catch rate | 20× Lucky Clover + 15× Amethyst | Gold sparkles |
| **Zone Expansion** | +5% green zone | 25× Sturdy Bones + 20× Titanium | Purple aura |
| **Master's Touch** | All above (reduced) | 50× Mythril + 30× Orichalcum | Rainbow aura |

**Enhancement Rules:**
- Only ONE enhancement per rod
- Cannot remove or change enhancement
- Visual aura persists and displays during fishing
- Enhanced rod = higher trade value
- Enhancements stack with rod base stats

### 3.3 Rod Skins (Robux Shop)

**Cosmetic Skins:**
- Do NOT affect stats (purely cosmetic)
- Can be applied to any rod rarity
- Purchasable in Robux Shop
- Tradeable between players

**Example Skins:**
- **Golden Angler:** Shimmering gold rod with sparkles (400 Robux)
- **Neon Techno:** Cyberpunk-themed rod with neon lights (500 Robux)
- **Bamboo Zen:** Traditional wooden rod aesthetic (300 Robux)
- **Oceanic Trident:** Trident-shaped rod with water effects (600 Robux)
- **Dragon's Whisker:** Dragon-themed rod with scales and fire (800 Robux)

**Seasonal Skins:**
- Halloween: Spooky Ghost Rod (400 Robux)
- Winter: Candy Cane Rod (400 Robux)
- Summer: Beach Party Rod (400 Robux)
- Limited availability during events

---

## 4. Location System

### 4.1 Ocean Zones

**Ocean Zone A: Starter Beach**
- **Location:** Near town spawn, easily accessible
- **Difficulty:** Beginner-friendly
- **Common Fish:** Cod, Mackerel, Sardine
- **Rare Fish:** Tuna, Sea Bass
- **Epic Fish:** None
- **Special Feature:** Tutorial fishing spot

**Ocean Zone B: Rocky Coast**
- **Location:** North of town, requires 10-minute travel
- **Difficulty:** Intermediate
- **Common Fish:** Mackerel, Anchovy
- **Rare Fish:** Sea Bass, Snapper
- **Epic Fish:** Swordfish, Marlin
- **Special Feature:** Rock pools have unique crabs

**Ocean Zone C: Deep Sea Port**
- **Location:** West docks, accessible after quest
- **Difficulty:** Advanced
- **Common Fish:** Rare (intentionally sparse)
- **Rare Fish:** Tuna, Grouper
- **Epic Fish:** Marlin, Mahi-Mahi
- **Legendary Fish:** Blue Marlin, Giant Tuna
- **Special Feature:** Chance for treasure chests

**Ocean Zone D: Tropical Reef**
- **Location:** Southern island, requires boat travel
- **Difficulty:** Expert
- **Common Fish:** Parrotfish, Clownfish
- **Rare Fish:** Angelfish, Butterfly Fish
- **Epic Fish:** Reef Shark, Stingray
- **Legendary Fish:** Manta Ray
- **Mythic Fish:** Celestial Jellyfish (0.5% chance)
- **Special Feature:** Most beautiful fish, high trade value

### 4.2 River Zones

**River Zone A: Town River**
- **Location:** Runs through town center
- **Difficulty:** Beginner
- **Common Fish:** Trout, Minnow, Carp
- **Rare Fish:** Salmon, Pike
- **Epic Fish:** None
- **Special Feature:** Always accessible

**River Zone B: Forest Stream**
- **Location:** Northeast forest area
- **Difficulty:** Intermediate
- **Common Fish:** Trout, Catfish
- **Rare Fish:** Pike, Bass
- **Epic Fish:** King Salmon, Sturgeon
- **Special Feature:** Beautiful scenery, relaxing atmosphere

**River Zone C: Mountain Rapids**
- **Location:** Mountain base, requires hiking
- **Difficulty:** Advanced
- **Common Fish:** Rainbow Trout
- **Rare Fish:** Steelhead, Brook Trout
- **Epic Fish:** Golden Trout
- **Legendary Fish:** Ancient Sturgeon
- **Special Feature:** Fast-moving water, unique fish

**River Zone D: Mysterious Lake**
- **Location:** Hidden lake, requires quest unlock
- **Difficulty:** Expert
- **Common Fish:** None (all rare+)
- **Rare Fish:** Koi, Lotus Carp
- **Epic Fish:** Dragon Koi
- **Legendary Fish:** Moonlight Koi
- **Mythic Fish:** Phoenix Koi (0.8% chance)
- **Special Feature:** Spiritual atmosphere, glowing fish

### 4.3 Special Event Waters

**Seasonal Fishing Spots:**
- **Winter Ice Lake:** Special ice-hole fishing (December-February)
- **Spring Blossom Pond:** Cherry blossom-themed fish (March-May)
- **Summer Lagoon:** Tropical event fish (June-August)
- **Autumn River:** Fall-themed species (September-November)

**Event-Exclusive Fish:**
- Cannot be caught outside event period
- Highly sought after for collections
- Often required for event quests
- High trade value after event ends

---

## 5. Fish Species & Catalog

### 5.1 Fish Rarity Distribution

**Catch Rate Formula:**
```
Base Catch Rate × Location Modifier × Weather Modifier × Rod Rarity Check × Luck Bonus
```

### 5.2 Fish Database Structure

Each fish has the following properties:

| Property | Description | Example |
|----------|-------------|---------|
| **ID** | Unique identifier | FISH_001 |
| **Name** | Display name | "Golden Trout" |
| **Rarity** | Tier (Common-Special) | Epic |
| **Base Catch Rate** | Percentage chance | 5% |
| **Location** | Where it spawns | River Zone C |
| **Time** | Time of day | Any / Day / Night |
| **Weather** | Required weather | Clear / Rain / Any |
| **Season** | Available months | All / Event-specific |
| **Size Range** | Min-Max weight | 2-8 kg |
| **Sell Value** | Base IRF price | 150 IRF |
| **Stamina** | Mini-game difficulty | 80 HP |
| **Index Number** | Catalog position | #042 |
| **Description** | Flavor text | "A rare mountain trout with shimmering golden scales." |
| **Uses** | System integration | Carnivore familiar food, trading |

### 5.3 Example Fish Species

#### Ocean Fish

**Common Tier:**
1. **Cod** - Base 40%, 0.5-2 kg, 10 IRF, Any weather
2. **Mackerel** - Base 35%, 0.3-1 kg, 8 IRF, Any weather
3. **Sardine** - Base 45%, 0.1-0.5 kg, 5 IRF, Any weather
4. **Anchovy** - Base 40%, 0.1-0.4 kg, 5 IRF, Any weather

**Rare Tier:**
5. **Sea Bass** - Base 20%, 2-5 kg, 50 IRF, Clear weather
6. **Tuna** - Base 15%, 5-15 kg, 80 IRF, Any weather
7. **Snapper** - Base 18%, 1-4 kg, 60 IRF, Day only

**Epic Tier:**
8. **Swordfish** - Base 8%, 20-50 kg, 300 IRF, Day/Clear
9. **Marlin** - Base 6%, 30-80 kg, 400 IRF, Day/Clear
10. **Mahi-Mahi** - Base 7%, 5-15 kg, 250 IRF, Any

**Legendary Tier:**
11. **Blue Marlin** - Base 3%, 100-200 kg, 1,500 IRF, Day/Clear
12. **Giant Tuna** - Base 2.5%, 150-300 kg, 2,000 IRF, Any

**Mythic Tier:**
13. **Celestial Jellyfish** - Base 0.5%, N/A, 10,000 IRF, Night/Clear
14. **Leviathan Eel** - Base 0.3%, ???, 15,000 IRF, Storm only

#### River Fish

**Common Tier:**
15. **Trout** - Base 40%, 0.5-2 kg, 12 IRF, Any
16. **Carp** - Base 35%, 1-5 kg, 15 IRF, Any
17. **Minnow** - Base 50%, 0.1-0.3 kg, 3 IRF, Any
18. **Catfish** - Base 30%, 2-10 kg, 25 IRF, Night

**Rare Tier:**
19. **Salmon** - Base 18%, 3-8 kg, 70 IRF, Day
20. **Pike** - Base 15%, 5-15 kg, 90 IRF, Any
21. **Bass** - Base 20%, 1-4 kg, 55 IRF, Any

**Epic Tier:**
22. **King Salmon** - Base 7%, 10-25 kg, 350 IRF, Day/Rain
23. **Sturgeon** - Base 5%, 20-80 kg, 500 IRF, Any
24. **Golden Trout** - Base 6%, 2-6 kg, 400 IRF, Clear

**Legendary Tier:**
25. **Ancient Sturgeon** - Base 2%, 100-250 kg, 2,500 IRF, Any
26. **Moonlight Koi** - Base 2.5%, 5-12 kg, 3,000 IRF, Night/Full Moon

**Mythic Tier:**
27. **Phoenix Koi** - Base 0.8%, 15-30 kg, 12,000 IRF, Night/Clear
28. **Dragon Carp** - Base 0.5%, 50-100 kg, 18,000 IRF, Rain/Thunderstorm

### 5.4 Fish Index System

**Catalog UI:**
```
╔════════════════════════════════════════════╗
║       FISH INDEX - OCEAN                   ║
║  Discovered: 24/45                         ║
╠════════════════════════════════════════════╣
║                                            ║
║  [★] #001 Cod - COMMON                     ║
║      Caught: 47 | Largest: 1.8 kg          ║
║                                            ║
║  [★] #002 Mackerel - COMMON                ║
║      Caught: 32 | Largest: 0.9 kg          ║
║                                            ║
║  [?] #003 ??? - ???                        ║
║      Not yet discovered                    ║
║                                            ║
║  [Filters: All | Common | Rare | Epic...]  ║
╚════════════════════════════════════════════╝
```

**Index Features:**
- Shows silhouette of undiscovered fish
- Tracks total catches per species
- Records personal best (largest catch)
- Displays locations where fish can be found
- Shows time/weather requirements
- Completion rewards (titles, decorations)

**Completion Milestones:**
- 25% Complete: "Novice Angler" title
- 50% Complete: Fishing Rod Skin unlock
- 75% Complete: "Master Angler" title + Decoration
- 100% Complete: "Legendary Angler" title + Special Rod Skin + 50,000 IRF

---

## 6. Weather & Time Influences

### 6.1 Weather Effects

**Clear Weather (60% of time):**
- Standard fish spawns
- All fish available per location
- No bonuses or penalties

**Rain (25% of time):**
- +15% catch rate for all fish
- Certain fish ONLY spawn in rain (King Salmon, Dragon Carp)
- Plants grow faster (cross-system benefit)
- Visual: Rain particles, sound effects

**Storm/Thunderstorm (10% of time):**
- +25% catch rate for rare+ fish
- Unique storm-exclusive fish (Leviathan Eel)
- Dangerous: Lightning can damage player (5% per 30s)
- High risk, high reward

**Fog (5% of time):**
- Reduced visibility
- +10% legendary fish catch rate
- Mysterious atmosphere
- Rare spawn conditions

### 6.2 Time of Day Influences

**Morning (6 AM - 12 PM in-game):**
- Standard spawns
- Most players online (prime time)
- Good for social fishing

**Afternoon (12 PM - 6 PM):**
- +5% catch rate
- Best weather variety
- Optimal fishing time

**Evening (6 PM - 12 AM):**
- +10% rare fish spawns
- Beautiful sunset visuals
- Relaxing atmosphere

**Night (12 AM - 6 AM):**
- Nocturnal fish active
- +20% chance for night-exclusive species
- +5% treasure chance
- Glow effects on special fish
- Fewer players (quiet experience)

### 6.3 Seasonal Events

**Spring (March-May):**
- Cherry Blossom Koi event
- +15% catch rate in River Zone D
- Pink-themed fish variants
- Special "Spring Festival" quests

**Summer (June-August):**
- Tropical fish migration
- New fish appear in Ocean Zone D
- Beach party events
- Increased treasure spawns

**Autumn (September-November):**
- Salmon run event
- Massive salmon spawns in rivers
- Fall-colored fish variants
- Harvest festival tie-in

**Winter (December-February):**
- Ice fishing mechanics
- Winter-exclusive fish
- Frozen lakes (special areas)
- Holiday-themed species

---

## 7. Treasure System

### 7.1 Treasure Chest Types

**Small Treasure Chest:**
- **Drop Rate:** 2% chance when fishing
- **Replaces:** Fish catch
- **Contents:** 100-500 IRF, Common materials, Common decorations
- **Visual:** Wooden chest, small

**Large Treasure Chest:**
- **Drop Rate:** 0.5% chance when fishing
- **Replaces:** Fish catch
- **Contents:** 500-2,000 IRF, Rare materials, Rare seeds, Rare decorations
- **Visual:** Iron-bound chest, medium

**Legendary Treasure:**
- **Drop Rate:** 0.1% chance when fishing
- **Replaces:** Fish catch
- **Contents:** 2,000-10,000 IRF, Epic+ materials, Geodes, Exclusive decorations
- **Visual:** Golden chest, large, glowing

**Mythic Treasure:**
- **Drop Rate:** 0.05% chance (luck-dependent)
- **Replaces:** Fish catch
- **Contents:** 10,000-50,000 IRF, Mythic materials, Rare seeds, Exclusive equipment
- **Visual:** Ornate chest, rainbow aura

### 7.2 Treasure Contents Table

| Chest Type | IRF Range | Material Rarity | Seed Chance | Decoration Chance | Special Item Chance |
|------------|-----------|-----------------|-------------|-------------------|---------------------|
| Small | 100-500 | Common | 20% | 30% | 5% |
| Large | 500-2,000 | Common-Rare | 40% | 50% | 15% |
| Legendary | 2,000-10,000 | Rare-Epic | 60% | 70% | 30% |
| Mythic | 10,000-50,000 | Epic-Mythic | 80% | 90% | 50% |

**Special Items:**
- Exclusive fishing rod skins
- Enhancement crystals
- Pet eggs (rare familiars)
- Recipe scrolls (unique crafting)
- Event tickets

### 7.3 Treasure Luck Scaling

**Luck Impact on Treasure:**
```
Modified Treasure Rate = Base Rate × (1 + (Luck / 200))
```

**Example:**
- Base Mythic Treasure: 0.05%
- Player Luck: +100%
- Modified Rate: 0.05% × (1 + 0.5) = 0.075%

**Treasure Hunting Strategy:**
- Max luck build specifically for treasure farming
- Night fishing (higher treasure chance)
- Deep Sea Port (best treasure location)
- Storm weather (+treasure chance)

---

## 8. UI/UX Specifications

### 8.1 Fishing HUD

**Active Fishing Display:**
```
┌─────────────────────────────────────────────┐
│  Fishing Rod: [Legendary Rod] (952/1000)    │
│  Location: Ocean Zone C - Deep Sea Port     │
│  Weather: Clear ☀️ | Time: 14:32 (Day)      │
│                                             │
│  [CAST LINE - Press E]                      │
│                                             │
│  Recent Catches:                            │
│   🐟 Tuna (5.2 kg)                          │
│   🐟 Sea Bass (3.1 kg)                      │
│   🐟 Mackerel (0.8 kg)                      │
└─────────────────────────────────────────────┘
```

### 8.2 Catch Result Screen

```
╔═══════════════════════════════════════════╗
║          🎣 FISH CAUGHT! 🎣              ║
╠═══════════════════════════════════════════╣
║                                           ║
║        [3D Model of Fish Rotating]        ║
║                                           ║
║         🌟 BLUE MARLIN 🌟                 ║
║         Legendary Rarity                  ║
║                                           ║
║  Weight: 156.3 kg (Personal Best! 🏆)     ║
║  Value: 1,500 IRF                         ║
║                                           ║
║  [NEW] Index Entry Unlocked! #11          ║
║                                           ║
║  [Keep in Inventory] [Sell Immediately]   ║
╚═══════════════════════════════════════════╝
```

### 8.3 Location Selection Map

**World Map - Fishing Spots:**
```
╔═════════════════════════════════════════╗
║       FISHING LOCATION MAP               ║
╠═════════════════════════════════════════╣
║                                         ║
║  🌊 OCEAN ZONES:                        ║
║   [📍] Zone A: Starter Beach            ║
║   [📍] Zone B: Rocky Coast              ║
║   [📍] Zone C: Deep Sea Port            ║
║   [🔒] Zone D: Tropical Reef (Quest)    ║
║                                         ║
║  🏞️ RIVER ZONES:                        ║
║   [📍] Zone A: Town River               ║
║   [📍] Zone B: Forest Stream            ║
║   [📍] Zone C: Mountain Rapids          ║
║   [🔒] Zone D: Mysterious Lake (Quest)  ║
║                                         ║
║  [Fast Travel] [Close]                  ║
╚═════════════════════════════════════════╝
```

---

## 9. Balance & Progression

### 9.1 Fishing Progression Path

**Early Game (Level 1-10):**
- Rod: Common
- Locations: Ocean Zone A, River Zone A
- Goals: Learn mechanics, catch 25 fish
- Income: 50-200 IRF/hour
- Focus: Tutorial quests, index discovery

**Mid Game (Level 11-30):**
- Rod: Rare → Epic
- Locations: All Zones A-B unlocked
- Goals: Complete 50-fish quest, unlock new areas
- Income: 500-1,000 IRF/hour
- Focus: Rare fish hunting, familiar feeding

**Late Game (Level 31-50):**
- Rod: Legendary
- Locations: All Zones A-C, some D zones
- Goals: Legendary fish catches, index 75% complete
- Income: 2,000-5,000 IRF/hour
- Focus: Trophy hunting, trading market

**End Game (Level 50+):**
- Rod: Mythic/Special
- Locations: All zones unlocked
- Goals: 100% index completion, mythic fish
- Income: 10,000+ IRF/hour
- Focus: Treasure hunting, market dominance

### 9.2 Economic Balance

**Fish Market Dynamics:**
- Common fish: Oversupplied, low value (good for beginners)
- Rare fish: Steady demand for familiar food
- Epic+ fish: High trade value, collection demand
- Mythic fish: Extreme rarity, prestige items

**Price Stability:**
- NPC vendors buy at 50% market value (price floor)
- Player trading typically 70-100% market value
- Rare fish in high demand can exceed market value
- Event fish spike in price after event ends

### 9.3 Time Investment vs Reward

**Average Catch Rates:**
- Beginner: 4-6 fish/hour (learning curve)
- Intermediate: 15-20 fish/hour
- Advanced: 25-35 fish/hour
- Expert: 40+ fish/hour (optimized)

**Treasure Time:**
- Average time to Small Treasure: 50 catches
- Average time to Large Treasure: 200 catches
- Average time to Legendary Treasure: 1,000 catches
- Average time to Mythic Treasure: 2,000 catches (with luck)

---

## 10. Technical Implementation

### 10.1 Fishing System Architecture

```lua
FishingSystem = {
    ActiveSessions = {}, -- Player → Session data
    FishDatabase = {}, -- All fish definitions
    LocationData = {}, -- Zone spawn tables
    WeatherSystem = nil, -- Reference to weather controller
}

FishingSession = {
    Player = Player,
    Rod = ItemInstance,
    Location = "Ocean_Zone_A",
    CastTime = tick(),
    BiteTime = nil,
    CurrentFish = nil,
    MinigameActive = false,
}
```

### 10.2 Catch Determination Logic

```lua
function DetermineCatch(player, location, weather, time)
    local rod = GetEquippedRod(player)
    local luckBonus = CalculateTotalLuck(player)
    
    -- Get location fish table
    local fishTable = LocationData[location].FishList
    
    -- Filter by rod rarity (can only catch up to rod tier)
    local validFish = FilterByRarity(fishTable, rod.Rarity)
    
    -- Filter by time/weather requirements
    validFish = FilterByConditions(validFish, weather, time)
    
    -- Check for treasure first (small chance)
    if CheckTreasureDrop(luckBonus) then
        return GenerateTreasure(luckBonus)
    end
    
    -- Roll for fish
    local rolledFish = WeightedRandom(validFish, luckBonus)
    
    return rolledFish
end
```

### 10.3 Mini-Game Controller

```lua
function RunFishingMinigame(player, fish)
    local minigame = CreateMinigameInstance(player, fish)
    
    -- Initialize
    minigame.Tension = 0
    minigame.FishStamina = fish.StaminaMax
    minigame.IndicatorPosition = 0
    minigame.IndicatorDirection = 1
    minigame.StartTime = tick()
    
    -- Update loop
    while minigame.Active do
        wait(0.05) -- 20 FPS update
        
        -- Move indicator
        minigame.IndicatorPosition += minigame.IndicatorDirection * fish.Speed
        
        -- Bounce at edges
        if minigame.IndicatorPosition >= 100 then
            minigame.IndicatorDirection = -1
        elseif minigame.IndicatorPosition <= 0 then
            minigame.IndicatorDirection = 1
        end
        
        -- Check player input
        if PlayerHolding(player, "Space") then
            local zone = GetTensionZone(minigame.IndicatorPosition)
            
            if zone == "Green" then
                minigame.FishStamina -= 2
                minigame.Tension += 0.5
            elseif zone == "Yellow" then
                minigame.FishStamina -= 1
                minigame.Tension += 1.5
            elseif zone == "Orange" then
                minigame.FishStamina -= 0.5
                minigame.Tension += 3
            elseif zone == "Red" then
                minigame.Tension += 5
            end
        else
            minigame.Tension = math.max(0, minigame.Tension - 1)
        end
        
        -- Check win/loss
        if minigame.FishStamina <= 0 then
            return SUCCESS(fish)
        end
        
        if minigame.Tension >= 100 then
            return FAILURE("Line broke!")
        end
        
        if tick() - minigame.StartTime > 30 then
            return FAILURE("Fish got away!")
        end
        
        UpdateMinigameUI(minigame)
    end
end
```

### 10.4 Performance Optimization

**Bobber Physics:**
- Use simplified buoyancy simulation
- Limited particle effects (10-15 particles max)
- LOD for distant players' fishing animations
- Disable bobber render beyond 50 studs

**Database Efficiency:**
- Cache fish spawn tables per location
- Precompute weighted random tables
- Index fish by rarity for fast filtering
- Lazy-load fish models (only when caught)

**Network Optimization:**
- Server authoritative for all catch rolls
- Client prediction for bobber casting
- Batch update UI every 0.1s during minigame
- Compress fish data (ID + stats only)

---

## Implementation Checklist

### Phase 1: Core Mechanics
- [ ] Fishing rod models (all rarities)
- [ ] Fish 3D models (at least 20 species)
- [ ] Bobber physics system
- [ ] Casting animation
- [ ] Mini-game UI and logic
- [ ] Basic catch/fail feedback

### Phase 2: Content
- [ ] All 8 fishing locations (models)
- [ ] Complete fish database (50+ species)
- [ ] Fish index UI
- [ ] Weather integration
- [ ] Time of day system
- [ ] Treasure chest system

### Phase 3: Polish
- [ ] Water shader effects
- [ ] Fish jumping animations
- [ ] Sound design (casting, reeling, catches)
- [ ] UI animations
- [ ] Rod enhancement system
- [ ] Robux shop skins

### Phase 4: Balance
- [ ] Playtesting catch rates
- [ ] Economy balancing (fish prices)
- [ ] Mini-game difficulty tuning
- [ ] Progression pacing
- [ ] Performance optimization

---

**Fishing System - End of Document**

*Next System Documentation: [GDD_Systems_Farming.md](GDD_Systems_Farming.md)*
