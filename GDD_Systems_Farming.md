# Game Design Document
## Farming System

---

### Document Information
**System Name:** Farming System  
**Document Version:** 1.0  
**Last Updated:** February 8, 2026  
**Owner:** Systems Design Team  
**Status:** Ready for Implementation

---

## Table of Contents
1. [System Overview](#system-overview)
2. [Core Mechanics](#core-mechanics)
3. [Seed System](#seed-system)
4. [Farm Plot Management](#farm-plot-management)
5. [Growth & Watering](#growth--watering)
6. [Harvest Quality System](#harvest-quality-system)
7. [Fertilizer & Enhancements](#fertilizer--enhancements)
8. [Sprinkler Automation](#sprinkler-automation)
9. [Economic Integration](#economic-integration)
10. [Technical Implementation](#technical-implementation)

---

## 1. System Overview

### Purpose
The Farming System provides a passive income and progression mechanic where players plant, nurture, and harvest crops. It serves as a reliable income source and supplies materials for creature taming and trading.

### Design Goals
- **Passive Progression**: Allows players to earn while offline
- **Strategic Planning**: Crop selection impacts income efficiency
- **Quality Gameplay**: Skill expression through quality optimization
- **Economic Balance**: Stable income without market flooding
- **Expansion Incentive**: Growth creates monetization opportunity

### Player Value Proposition
*"Farming offers reliable passive income with optimization depth, allowing strategic players to maximize profits through quality management and efficient crop selection."*

---

## 2. Core Mechanics

### 2.1 Location Requirements

**Private Island Only:**
- Farming ONLY accessible in player's private island
- No public farming areas (prevents griefing)
- Owner-only access (friends can visit but not farm)
- Secure personal space

**Farm Plot Zones:**
- Designated areas within private island
- Can be placed freely after purchase
- Must be on flat terrain
- Cannot overlap with decorations/buildings

### 2.2 Farm Plot Structure

**Plot Capacity:**
- 1 plot = 5 seed slots
- Starting plots: 2 (free at tutorial)
- Maximum plots: 10 (requires expansions)
- Each slot holds 1 plant

**Plot Layout:**
```
┌─────────────────────────────────┐
│  FARM PLOT #1                   │
│  ┌───┬───┬───┬───┬───┐          │
│  │ 🌱│ 🌱│ 🌱│ 🌱│ 🌱│          │
│  │ 1 │ 2 │ 3 │ 4 │ 5 │          │
│  └───┴───┴───┴───┴───┘          │
│  [Watered: ✓] [Ready: 0/5]      │
└─────────────────────────────────┘
```

### 2.3 Farming Cycle Flow

```
1. Purchase/Obtain Seeds
   ↓
2. Select Empty Farm Plot Slot
   ↓
3. Plant Seed (instant)
   ↓
4. Water Daily (required for growth)
   ↓
5. Wait for Growth Period
   ↓
6. Harvest When Ready
   ↓
7. Quality Determined (based on care)
   ↓
8. Sell to NPC or Trade
   ↓
9. Repeat or Plant New Crop
```

---

## 3. Seed System

### 3.1 Seed Types

**Single-Harvest Seeds:**
- Plant once, harvest once
- Plant disappears after harvest
- Higher base value per harvest
- Best for rare/valuable crops

**Multi-Harvest Seeds:**
- Plant once, harvest multiple times
- Plant persists after first harvest
- Lower value per harvest
- Better long-term efficiency
- Harvest interval: Every 2-3 days after maturity

### 3.2 Seed Rarity Tiers

| Rarity | Growth Time | Sell Value | Profit/Day | Harvest Type |
|--------|-------------|------------|------------|--------------|
| **Common** | 2-3 days | 10-15 IRF | ~5-7 IRF | Both types |
| **Rare** | 4-5 days | 25-50 IRF | ~6-12 IRF | Both types |
| **Epic** | 7-10 days | 120-200 IRF | ~15-28 IRF | Single only |
| **Legendary** | 14-21 days | 800-1,500 IRF | ~40-107 IRF | Single only |
| **Mythic** | 21-30 days | 3,000-5,000 IRF | ~100-238 IRF | Single only |
| **Special** | Event-based | Variable | High | Event-specific |

### 3.3 Seed Acquisition Methods

**1. NPC Farmer Shop (Common Seeds)**
- Always available
- Predictable inventory
- Low cost (50-200 IRF per seed)
- Unlimited quantity
- Best for beginners

**2. Game Shop (Rare-Mythic Seeds, Robux)**
- Premium convenience
- Instant access to rare varieties
- Tradeable to F2P players
- Pricing: 50-1,000 Robux depending on rarity

**3. Traveling Merchant (All Rarities, Limited)**
- Appears every 6 hours (in-game time)
- Limited stock (resets daily)
- Competitive pricing
- Rare seeds at reasonable IRF cost
- Stock limits prevent hoarding:
  - Common: 20 seeds available
  - Rare: 10 seeds available
  - Epic: 5 seeds available
  - Legendary: 2 seeds available
  - Mythic: 1 seed available

**4. Dungeon Drops (Common-Mythic)**
- Monsters drop seed pouches
- Drop rate scales with rarity:
  - Common: 15% from any monster
  - Rare: 8% from rare+ monsters
  - Epic: 3% from epic+ monsters
  - Legendary: 1% from legendary+ monsters
  - Mythic: 0.3% from bosses only
- Encourages dungeon exploration
- Luck stat increases drop rates

**5. Event Quests (Special Seeds)**
- Exclusive to seasonal events
- Quest completion rewards
- Event shop purchases
- Cannot obtain outside event period
- High collectible value

### 3.4 Seed Visual Identifiers

**Common Seeds (Grey):**
- Plain brown/grey texture
- No particle effects
- Simple plant model

**Rare Seeds (Blue):**
- Blue-tinted packaging
- Faint sparkle on plant
- Slightly larger plant model

**Epic Seeds (Purple):**
- Purple glow on seed packet
- Purple particles when growing
- Distinctive plant shape

**Legendary Seeds (Gold):**
- Golden shimmer effect
- Bright gold particles
- Majestic plant appearance
- Glowing at night

**Mythic Seeds (Red/Crimson):**
- Intense red glow
- Crimson particles constantly
- Animated plant (sways, pulses)
- Light source (illuminates area)

**Special Seeds (Rainbow):**
- Rainbow shimmer effect
- Multi-colored particles
- Unique themed appearance
- Animated special effects
- Seasonal decorations (e.g., snowflakes for winter)

---

## 4. Farm Plot Management

### 4.1 Plot Expansion System

**Starting Configuration:**
- 2 free plots (10 total slots)
- Unlocked during tutorial
- Fixed locations initially

**Expansion Costs:**

| Expansion | Total Plots | Cost (IRF) | Cost (Robux) | Cumulative Cost IRF |
|-----------|-------------|------------|--------------|---------------------|
| None | 2 plots | Free | Free | 0 |
| +1 | 3 plots | 5,000 IRF | 100 Robux | 5,000 |
| +1 | 4 plots | 15,000 IRF | 200 Robux | 20,000 |
| +1 | 5 plots | 35,000 IRF | 350 Robux | 55,000 |
| +1 | 6 plots | 70,000 IRF | 500 Robux | 125,000 |
| +1 | 7 plots | 150,000 IRF | 700 Robux | 275,000 |
| +1 | 8 plots | 300,000 IRF | 1,000 Robux | 575,000 |
| +1 | 9 plots | 500,000 IRF | 1,500 Robux | 1,075,000 |
| +1 | 10 plots (MAX) | 1,000,000 IRF | 2,500 Robux | 2,075,000 |

**Expansion Rules:**
- Cannot skip tiers (must buy sequentially)
- IRF or Robux payment (player choice)
- Permanent upgrade (account-bound)
- New plots placed by player in private island
- Placement restrictions: Flat ground, no overlaps

### 4.2 Plot Customization

**Plot Appearance:**
- Default: Wooden border, dirt texture
- Cosmetic upgrades available (Robux):
  - Stone border (200 Robux)
  - Golden border (500 Robux)
  - Crystal border (800 Robux)
  - Seasonal themes (300 Robux each)

**Plot Arrangement:**
- Free placement mode in private island
- Drag-and-drop interface
- Snap-to-grid option
- Rotation support (0°, 90°, 180°, 270°)
- Can rearrange anytime (no cost)

---

## 5. Growth & Watering

### 5.1 Growth Mechanics

**Growth Timer:**
- Starts immediately after planting
- Pauses if not watered daily
- Real-time based (continues when offline)
- Visual stages show progress

**Growth Stages:**

```
Stage 1: Seed (0-20% growth)
  🌰 Small mound visible

Stage 2: Sprout (20-40% growth)
  🌱 Small green shoot

Stage 3: Growing (40-70% growth)
  🌿 Plant taking shape, larger

Stage 4: Mature (70-99% growth)
  🌾 Full-size plant, not ready

Stage 5: Harvestable (100% growth)
  ✨🌾✨ Glowing effect, sparkles
```

**Growth Rate Formula:**
```
Daily Growth = (100% / Growth Time in Days) × Watered Multiplier
Watered Multiplier = 1.0 if watered today, 0.0 if not watered
```

**Example:**
- Wheat: 2-day growth
- Daily growth: 50% per day (if watered)
- Day 1: Plant + Water = 50% growth
- Day 2: Water = 100% growth = Harvestable

### 5.2 Watering System

**Watering Requirements:**
- Must water every in-game day
- In-game day = Real-time 24 hours
- Watering window: Any time during the day
- Missing watering = growth pauses

**Watering Process:**

```
1. Player approaches farm plot
   ↓
2. Interaction prompt: [E] Water All
   ↓
3. Watering animation plays (2 seconds)
   ↓
4. All 5 plants in plot watered
   ↓
5. Visual indicator: Wet soil, droplets
   ↓
6. Checkmark appears: "Watered ✓"
```

**Watering Tools:**
- No tool required (default hand-watering)
- Quick action (press E once per plot)
- Can water all plots in <1 minute
- Animation skippable

**Watering Status UI:**
```
┌─────────────────────────────────┐
│  FARM STATUS                    │
│  ─────────────────────────      │
│  Plot 1: ✓ Watered today        │
│  Plot 2: ✓ Watered today        │
│  Plot 3: ✗ Needs watering!      │
│  Plot 4: ✓ Watered today        │
│  ─────────────────────────      │
│  [Water All Plots] (Hotkey: W)  │
└─────────────────────────────────┘
```

### 5.3 Weather Bonuses

**Rain Effect:**
- Auto-waters all plants (no manual watering needed)
- +10% harvest quality chance
- +5% growth speed
- Visual: Rain particles, wet ground

**Clear Weather:**
- Standard growth
- Manual watering required
- No bonuses

**Storm:**
- Auto-waters (like rain)
- +15% harvest quality chance
- Risk: 5% chance plants damaged (quality reduced)

---

## 6. Harvest Quality System

### 6.1 Quality Tiers

**Quality Levels:**

| Quality | Icon | Sell Price Multiplier | Visual Effect |
|---------|------|----------------------|---------------|
| **Poor** | None | 0.5× | Wilted appearance |
| **Decent** | ⚪ Silver | 1.0× (base) | Normal appearance |
| **Good** | 🟡 Gold | 1.5× | Slight glow |
| **Very Good** | 🟣 Purple | 2.0× | Purple shimmer |
| **Perfect** | 🌈 Rainbow | 3.0× | Rainbow aura, sparkles |

**Quality Impact:**
- Poor quality: Plant looks unhealthy, brown edges
- Decent quality: Standard healthy plant
- Good+ quality: Vibrant colors, particle effects
- Perfect quality: Glowing, animated, prestigious

### 6.2 Quality Determination

**Quality Roll (At Harvest):**

Base quality determined by formula:
```
Quality Chance = Base Chance + Fertilizer Bonus + Pet Buff + Weather Bonus

Roll 1d100:
  1-30: Poor
  31-60: Decent
  61-80: Good
  81-95: Very Good
  96-100: Perfect
```

**Improving Quality Chances:**

**1. Fertilizer Use (Guaranteed Quality):**
- Apply fertilizer BEFORE planting
- Fertilizer determines minimum quality
- 100% guarantee of chosen tier
- One-time use per seed

**Fertilizer Types:**

| Fertilizer | Guaranteed Quality | Cost (Robux) | Effect |
|------------|-------------------|--------------|--------|
| Basic | Decent (Silver) | 10 Robux | 1.0× price |
| Quality | Good (Gold) | 50 Robux | 1.5× price |
| Premium | Very Good (Purple) | 150 Robux | 2.0× price |
| Master's | Perfect (Rainbow) | 500 Robux | 3.0× price |

**2. Pet/Familiar Buffs:**
- Passive familiars increase quality chance
- Herbivore familiars provide farming buffs
- Buff ranges: +5% to +25% quality chance
- Stacks with other bonuses

**Example Pet Buffs:**
- Common Herbivore: +5% quality chance
- Rare Herbivore: +10% quality chance
- Epic Herbivore: +15% quality chance
- Legendary Herbivore: +20% quality chance
- Mythic Herbivore: +25% quality chance

**3. Weather Effects:**
- Rain: +10% quality chance
- Storm: +15% quality chance
- Clear: No bonus

**Quality Calculation Example:**
```
Player grows Wheat (Rare):
- Base quality roll: 1d100
- Applied Quality Fertilizer: +guaranteed Good (gold)
- Legendary Pet equipped: +20% chance for Very Good
- Raining: +10% chance bonus

Result: Minimum Good quality, high chance for Very Good
```

---

## 7. Fertilizer & Enhancements

### 7.1 Fertilizer System

**Application Timing:**
- MUST apply before planting seed
- Cannot apply to already-planted crops
- One-time effect (doesn't persist)
- Fertilizer consumed on use

**Application Process:**
```
1. Select empty farm plot slot
   ↓
2. Choose "Plant with Fertilizer"
   ↓
3. Select fertilizer type from inventory
   ↓
4. Select seed to plant
   ↓
5. Seed planted with guaranteed quality
```

**Fertilizer Purchase:**
- Available in Game Shop (Robux only)
- Sold in bundles for discount:
  - 1× Fertilizer: Full price
  - 5× Bundle: -10% discount
  - 10× Bundle: -20% discount
  - 50× Bundle: -30% discount

**Strategic Use:**
- Reserve premium fertilizer for legendary+ seeds
- Use basic fertilizer for common crops
- Calculate ROI before applying

**ROI Examples:**
```
Wheat (Common, 2-day growth, 10 IRF base):
- No fertilizer: 10 IRF
- Quality Fertilizer (50 Robux): 15 IRF
- Loss: Not worth it

Dragon Fruit (Legendary, 14-day growth, 800 IRF base):
- No fertilizer: 800 IRF (average)
- Premium Fertilizer (150 Robux): 1,600 IRF
- Gain: +800 IRF = Worth it
```

### 7.2 Growth Speed Enhancements

**Coming in Future Update:**
- Growth speed fertilizers
- Reduction: 10%-50% growth time
- Separate from quality fertilizers
- Stackable with quality bonuses

---

## 8. Sprinkler Automation

### 8.1 Sprinkler System

**Auto-Watering Device:**
- Purchased from Game Shop (Robux only)
- One-time purchase: 400 Robux
- Permanent upgrade (account-wide)
- Applies to ALL farm plots

**Functionality:**
- Automatically waters all plants daily
- Triggers at daily reset (server time)
- No player action required
- Visual: Sprinklers appear on plots

**Sprinkler Benefits:**
- Eliminates daily watering chore
- Never miss a watering day
- Frees time for other activities
- Quality of life improvement

**Sprinkler Limitations:**
- Does NOT improve growth speed
- Does NOT improve quality
- Only replaces manual watering
- Cannot be disabled once purchased

### 8.2 Visual Design

**Sprinkler Appearance:**
- Small device in corner of each plot
- Animates during watering (morning reset)
- Water particles spray across plot
- Subtle design (doesn't obstruct view)

**Cosmetic Sprinkler Skins (Future):**
- Golden Sprinkler (300 Robux)
- Crystal Sprinkler (500 Robux)
- Seasonal themed (300 Robux each)
- Purely cosmetic (no stat changes)

---

## 9. Economic Integration

### 9.1 Selling Crops

**NPC Farmer (Guaranteed Sale):**
- Always available
- Buys at 100% base price (quality multiplied)
- Instant transaction
- No listing fees
- Best for immediate cash

**Global Trading Board:**
- List for player-to-player sales
- Set own price (usually higher than NPC)
- 10% sale fee applies
- High-quality crops sell for premium
- Best for profit maximization

**Player Direct Trading:**
- Trade crops for items/currency
- No fees
- Negotiable prices
- Social interaction

### 9.2 Profit Analysis

**Crop Profitability Comparison:**

| Crop | Rarity | Growth Time | Base Value | Daily Profit | Best Strategy |
|------|--------|-------------|------------|--------------|---------------|
| Wheat | Common | 2 days | 10 IRF | 5 IRF/day | Volume farming |
| Corn | Common | 3 days | 15 IRF | 5 IRF/day | Beginner-friendly |
| Tomato | Rare (Multi) | 4 days, 3× harvest | 25 IRF/harvest | 18.75 IRF/day | Long-term passive |
| Strawberry | Rare (Multi) | 5 days, 4× harvest | 30 IRF/harvest | 24 IRF/day | Best multi-harvest |
| Melon | Epic | 7 days | 120 IRF | 17.1 IRF/day | Mid-tier value |
| Dragon Fruit | Legendary | 14 days | 800 IRF | 57.1 IRF/day | High quality + fertilizer |
| Starfruit | Mythic | 21 days | 3,000 IRF | 142.8 IRF/day | End-game, require care |

**Optimization Tips:**
- Multi-harvest crops better for lazy farming
- Single-harvest crops better with quality focus
- Mix crop types for diversified income
- Use fertilizer on legendary+ only

### 9.3 Material Uses

**Crops as Taming Food:**
- Herbivore familiars eat crops
- Higher rarity = more taming success
- Quality improves taming chance
- Alternative to selling

**Crops in Crafting (Future):**
- Some recipes require crops
- Decorations use plant materials
- Potions/consumables from crops

---

## 10. Technical Implementation

### 10.1 Data Structure

```lua
FarmPlot = {
    PlotID = 1,
    OwnerUserID = 123456789,
    Position = Vector3.new(0, 0, 0),
    Rotation = 0,
    Slots = {
        {
            SlotIndex = 1,
            SeedID = "SEED_WHEAT",
            PlantedAt = 1707350400, -- Unix timestamp
            LastWatered = 1707350400,
            GrowthProgress = 0.45, -- 45%
            FertilizerApplied = nil, -- or FertilizerID
            QualityRoll = nil, -- Determined at harvest
        },
        {SlotIndex = 2, SeedID = nil}, -- Empty
        {SlotIndex = 3, SeedID = nil},
        {SlotIndex = 4, SeedID = nil},
        {SlotIndex = 5, SeedID = nil},
    },
    LastChecked = 1707350400,
}
```

### 10.2 Growth Calculation

```lua
function FarmingSystem:UpdateGrowth(plot)
    local now = tick()
    local timeSinceLastCheck = now - plot.LastChecked
    local daysPassed = timeSinceLastCheck / 86400 -- seconds in day
    
    for _, slot in ipairs(plot.Slots) do
        if slot.SeedID then
            local seedData = SeedDatabase[slot.SeedID]
            local dailyGrowth = 1.0 / seedData.GrowthDays
            
            -- Check if watered today
            local lastWateredDay = math.floor(slot.LastWatered / 86400)
            local currentDay = math.floor(now / 86400)
            
            if lastWateredDay == currentDay or HasSprinkler(plot.OwnerUserID) then
                -- Grow
                slot.GrowthProgress += dailyGrowth * daysPassed
                slot.GrowthProgress = math.min(slot.GrowthProgress, 1.0)
            end
            
            -- Weather bonus
            if IsRaining() then
                slot.GrowthProgress += dailyGrowth * 0.05 * daysPassed
            end
        end
    end
    
    plot.LastChecked = now
end
```

### 10.3 Harvest Quality Roll

```lua
function FarmingSystem:HarvestPlant(player, plot, slotIndex)
    local slot = plot.Slots[slotIndex]
    
    if slot.GrowthProgress < 1.0 then
        return false, "Plant not ready"
    end
    
    -- Check for guaranteed quality from fertilizer
    if slot.FertilizerApplied then
        local fertilizer = FertilizerDatabase[slot.FertilizerApplied]
        slot.QualityRoll = fertilizer.GuaranteedQuality
    else
        -- Random quality roll
        local qualityChance = 0
        
        -- Add pet buff
        local petBonus = GetFarmingPetBonus(player)
        qualityChance += petBonus
        
        -- Add weather buff
        if IsRaining() then
            qualityChance += 10
        elseif IsStorm() then
            qualityChance += 15
        end
        
        -- Roll quality
        local roll = math.random(1, 100)
        
        if roll <= 30 then
            slot.QualityRoll = "Poor"
        elseif roll <= 60 then
            slot.QualityRoll = "Decent"
        elseif roll <= 80 + qualityChance then
            slot.QualityRoll = "Good"
        elseif roll <= 95 + qualityChance then
            slot.QualityRoll = "VeryGood"
        else
            slot.QualityRoll = "Perfect"
        end
    end
    
    -- Calculate value
    local seedData = SeedDatabase[slot.SeedID]
    local qualityMultiplier = QualityMultipliers[slot.QualityRoll]
    local finalValue = seedData.BaseValue * qualityMultiplier
    
    -- Add to inventory
    InventorySystem:AddItem(player, slot.SeedID.."_HARVESTED", 1, {
        Quality = slot.QualityRoll,
        Value = finalValue
    })
    
    -- Handle multi-harvest
    if seedData.IsMultiHarvest then
        -- Reset for next harvest
        slot.GrowthProgress = 0.7 -- Start at 70% for faster reharvest
        slot.LastWatered = tick()
    else
        -- Clear slot
        slot.SeedID = nil
        slot.PlantedAt = nil
        slot.GrowthProgress = 0
    end
    
    return true, finalValue, slot.QualityRoll
end
```

### 10.4 Sprinkler System

```lua
function FarmingSystem:DailyReset()
    -- Runs at server time 00:00
    
    for _, player in ipairs(Players:GetPlayers()) do
        local hasSprinkler = DataManager:GetPlayerData(player).HasSprinkler
        
        if hasSprinkler then
            local plots = self:GetPlayerPlots(player)
            
            for _, plot in ipairs(plots) do
                for _, slot in ipairs(plot.Slots) do
                    if slot.SeedID then
                        slot.LastWatered = tick()
                    end
                end
            end
            
            -- Visual effect
            self:PlaySprinklerAnimation(player)
        end
    end
end
```

### 10.5 Performance Optimization

**Plot Rendering:**
- Only render plants within 100 studs of player
- Use LOD models for distant plots
- Instance particle effects (pooling)
- Update growth visuals every 5 seconds (not every frame)

**Data Saving:**
- Save plot data on player leave
- Auto-save every 5 minutes
- Batch save multiple plots together
- Compress empty slots (don't store)

**Network Optimization:**
- Server calculates all growth (no client trust)
- Send growth updates only when player views plots
- Batch watering requests (water all plots at once)

---

## Implementation Checklist

### Phase 1: Core Mechanics
- [ ] Farm plot models (basic, customizable)
- [ ] Seed planting system
- [ ] Growth calculation logic
- [ ] Watering interaction
- [ ] Harvest system
- [ ] Basic crop models (10 varieties)

### Phase 2: Quality System
- [ ] Quality determination algorithm
- [ ] Fertilizer application system
- [ ] Pet buff integration
- [ ] Weather effects integration
- [ ] Visual quality indicators
- [ ] Quality-based pricing

### Phase 3: Expansion
- [ ] Plot expansion purchasing
- [ ] Plot placement system
- [ ] Sprinkler automation
- [ ] Multi-harvest mechanics
- [ ] Traveling merchant integration
- [ ] Dungeon seed drops

### Phase 4: Polish
- [ ] Growth stage animations
- [ ] Particle effects (watering, harvesting)
- [ ] Sound effects (planting, watering, harvesting)
- [ ] UI for farm management
- [ ] Seasonal crop variants
- [ ] Cosmetic customizations

---

**Farming System - End of Document**

*Related Documentation: [GDD_Economy.md](GDD_Economy.md), [GDD_Systems_Taming.md](GDD_Systems_Taming.md)*

*Crop Database: [Database_Crops.md](Database_Crops.md)*
