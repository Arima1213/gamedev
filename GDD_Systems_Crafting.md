# IRIFA: Realms of Harvest & Adventure
## Game Design Document - Crafting System

---

### Document Information
**Document Type:** System Design  
**System:** Crafting & Recipe System  
**Version:** 1.0  
**Last Updated:** February 8, 2026  
**Status:** Implementation Ready

---

## Table of Contents
1. [Overview](#1-overview)
2. [Crafting Stations](#2-crafting-stations)
3. [Crafting NPCs](#3-crafting-npcs)
4. [Recipe System](#4-recipe-system)
5. [Material Categories](#5-material-categories)
6. [Equipment Crafting](#6-equipment-crafting)
7. [Consumable Crafting](#7-consumable-crafting)
8. [Enhancement & Upgrades](#8-enhancement--upgrades)
9. [Blueprint Acquisition](#9-blueprint-acquisition)
10. [Technical Implementation](#10-technical-implementation)

---

## 1. Overview

### 1.1 System Purpose
The Crafting system allows players to:
- Create weapons and armor from materials
- Craft consumables (potions, food buffs)
- Upgrade existing equipment
- Produce decorative items
- Convert materials into useful goods

### 1.2 Core Design Pillars
- **Specialization:** Multiple crafting professions
- **Progression:** Unlock better recipes through leveling
- **Economy:** Player-driven crafting market
- **Resource Management:** Strategic material gathering
- **Quality Tiers:** Variable crafting outcomes

### 1.3 Crafting Professions

Players can learn all professions but specialize in one:

| Profession | Focus | Max Level |
|------------|-------|-----------|
| Blacksmithing | Weapons, Armor, Tools | 100 |
| Alchemy | Potions, Elixirs, Buffs | 100 |
| Cooking | Food, Familiar feed | 100 |
| Tailoring | Light armor, Bags, Accessories | 100 |
| Jewelcrafting | Rings, Necklaces, Enchants | 100 |
| Engineering | Gadgets, Mounts, Automation | 100 |

**Specialization Bonus (Level 50+):**
- Chosen profession: Craft speed +50%, quality +10%
- Other professions: Normal speed and quality
- Can change specialization once per month (5,000 IRF fee)

---

## 2. Crafting Stations

### 2.1 Basic Stations (Town)

#### Blacksmith Forge
**Location:** Every town  
**NPCs:** Blacksmith Master NPC  
**Access:** Free for all players  
**Crafting:**
- Basic weapons (Common/Rare)
- Basic armor (Common/Rare)
- Tools (pickaxes, axes, nets)
- Repair services

**Forge Tiers:**
- Tier 1 (Town Forge): Common/Rare recipes
- Tier 2 (Master Forge): Epic recipes (unlock at Blacksmithing 50)
- Tier 3 (Legendary Forge): Legendary recipes (unlock at Blacksmithing 80)

#### Alchemy Station
**Location:** Towns, Wizard Tower  
**NPCs:** Alchemist NPC  
**Access:** Free  
**Crafting:**
- Health potions
- Mana potions
- Status effect cures
- Buff elixirs

**Equipment Needed:**
- Brewing Stand (can place on Private Island for 2,000 IRF)
- Alembic (advanced station, 10,000 IRF)

#### Cooking Pot
**Location:** Towns, Private Island  
**NPCs:** Chef NPC  
**Access:** Free in town, 1,000 IRF for private cooking pot  
**Crafting:**
- Food buffs (+HP, +Stats)
- Familiar feed (premium quality)
- Feast items (party buffs)

---

### 2.2 Advanced Stations (Private Island)

Players can purchase and place these on their Private Island:

#### Personal Forge
- **Cost:** 15,000 IRF or 500 Robux
- **Benefit:** Craft at home, no queue waiting
- **Upgrades:**
  - Enchanted Forge (+20% craft speed): +10,000 IRF
  - Master's Forge (Epic recipes): +25,000 IRF

#### Enchanting Table
- **Cost:** 20,000 IRF or 600 Robux
- **Purpose:** Add enchantments to equipment
- **Requires:** Jewelcrafting 30+

#### Workshop (Engineering)
- **Cost:** 18,000 IRF
- **Purpose:** Craft gadgets, automation items
- **Features:** Blueprint storage, schematic board

---

### 2.3 Special Stations

#### Dragon Forge
**Location:** Unlocked after defeating Elder Dragon  
**Access:** Requires Dragon Slayer achievement  
**Crafting:** Dragon-tier equipment  
**Cost:** 50,000 IRF to unlock access

#### Void Forge
**Location:** Secret area (Void Rift events)  
**Access:** Rare random spawns  
**Crafting:** Void-tier Mythic equipment  
**Unique:** Only available during world events

---

## 3. Crafting NPCs

### 3.1 Blacksmith NPCs

#### Beginner Blacksmith (Level 1-30)
**Name:** Hammerhand Hugo  
**Location:** Starting Town  
**Services:**
- Teaches basic blacksmithing
- Sells Common/Rare recipes
- Repairs equipment (5% durability cost in IRF)
- Quest: "Your First Sword" (tutorial)

**Dialogue:**
> "Ah, a new smith! Let me show you the basics. First rule: never skip the tempering!"

#### Master Blacksmith (Level 30-80)
**Name:** Master Ironforge  
**Location:** Central City  
**Services:**
- Teaches advanced blacksmithing
- Sells Epic recipes (5,000-20,000 IRF each)
- Upgrades equipment to next tier
- Quest Chain: "Forging Legends" (5 quests, rewards Legendary recipe)

#### Legendary Smith (Level 80-100)
**Name:** Titanforge the Eternal  
**Location:** Mountain Peak (secret location)  
**Services:**
- Teaches Legendary crafting
- Sells Legendary recipes (50,000+ IRF each)
- Commissions custom equipment (high cost)
- Quest: "The Pinnacle of Craftsmanship"

---

### 3.2 Alchemist NPCs

#### Novice Alchemist
**Name:** Penny Potionmaker  
**Location:** Starting Town  
**Sells:**
- Basic potion recipes
- Alchemy ingredients (herb seeds)

#### Master Alchemist
**Name:** Professor Elixir  
**Location:** Wizard Tower  
**Sells:**
- Advanced buff potions
- Transmutation recipes (convert materials)

---

### 3.3 Chef NPCs

#### Village Cook
**Name:** Granny Goodtaste  
**Location:** Town Square  
**Sells:**
- Basic food recipes
- Cooking utensils

#### Gourmet Chef
**Name:** Chef Ramsay (NPC easter egg)  
**Location:** Luxury Restaurant (City)  
**Services:**
- Teaches gourmet recipes (+30% buff effectiveness)
- Quality assessment ("This fish is RAW!")
- Competition events

---

## 4. Recipe System

### 4.1 Recipe Structure

```lua
-- Example Recipe: Iron Sword
IronSwordRecipe = {
    RecipeId = "REC_IRON_SWORD",
    Name = "Iron Sword",
    Category = "Blacksmithing",
    Tier = "Rare",
    RequiredLevel = 10, -- Blacksmithing level
    
    Materials = {
        {ItemId = "IRON_ORE", Quantity = 20},
        {ItemId = "COAL", Quantity = 10},
        {ItemId = "WOOD", Quantity = 5}, -- Handle
        {ItemId = "LEATHER", Quantity = 3} -- Grip
    },
    
    CraftingStation = "BLACKSMITH_FORGE",
    CraftTime = 30, -- seconds
    CraftCost = 500, -- IRF fee
    
    Output = {
        ItemId = "WPN_IRON_SWORD",
        MinQuantity = 1,
        MaxQuantity = 1,
        QualityVariance = true -- Can produce Normal/Good/Great quality
    },
    
    XPReward = 100, -- Blacksmithing XP
    UnlockRequirement = "BLACKSMITH_LEVEL_10",
    RecipeSource = "Blacksmith NPC",
    RecipeCost = 1000 -- To purchase recipe
}
```

### 4.2 Recipe Acquisition Methods

#### Purchase from NPCs
- Most common method
- Costs scale with recipe tier
- Common: 100-500 IRF
- Rare: 1,000-5,000 IRF
- Epic: 10,000-50,000 IRF
- Legendary: 100,000+ IRF

#### Loot Drops
- Recipe Scrolls drop from bosses (10-30% chance)
- Dungeon chests (5-15% chance for rare recipes)
- World bosses (guaranteed Legendary recipe)

#### Quest Rewards
- Complete NPC quest chains
- Profession-specific quests
- "Master Craftsman" achievement line

#### Discovery System
- Experiment with materials at crafting station
- Random combinations have 1% chance to discover recipe
- Discovered recipes are account-bound (can't trade)
- Example: Combining Phoenix Pepper + Steel might discover "Flame Sword"

---

## 5. Material Categories

### 5.1 Metals (Blacksmithing)

#### Raw Ores
Mined from rocks (see Database_Minerals.md):
- Copper Ore
- Iron Ore
- Gold Ore
- Mithril Ore
- Adamantite Ore

#### Ingots (Processed)
Smelt ores at forge:
- 5 Copper Ore + 1 Coal = 1 Copper Ingot
- 5 Iron Ore + 2 Coal = 1 Iron Ingot
- 5 Gold Ore + 3 Coal = 1 Gold Ingot

#### Alloys (Advanced)
Combine multiple metals:
- Bronze: 2 Copper + 1 Tin
- Steel: 3 Iron + 2 Coal
- Mithril Alloy: 1 Mithril + 2 Silver

### 5.2 Cloth & Leather (Tailoring)

#### Cloth Sources
- Cotton: Harvest from cotton plants (farming)
- Silk: Drop from spiders
- Enchanted Silk: Magic infusion of silk

#### Leather Sources
- Raw Leather: Drop from animals (wolves, bears)
- Cured Leather: Process raw leather (10 Raw = 1 Cured)
- Dragon Leather: From dragons (rare)

### 5.3 Gems & Crystals (Jewelcrafting)

From mining (see Database_Minerals.md):
- Common: Ruby, Sapphire, Emerald
- Rare: Diamond, Amethyst
- Legendary: Star Sapphire, Black Diamond
- Mythic: Celestium Crystal, Void Crystal

**Processing:**
- Cut Gem: 1 Raw Gem = 1 Cut Gem (increases value 3×)
- Polished Gem: 1 Cut Gem + 1 Polish Powder = 1 Polished (5× value)

### 5.4 Herbs & Reagents (Alchemy)

#### Herbs (Gather from wild)
- Common: Mint, Basil, Thyme
- Rare: Celestial Sage, Moonflower
- Epic: Phoenix Herb, Void Blossom

#### Special Reagents
- Slime Gel: From slimes
- Spider Venom: From spiders
- Dragon Blood: From dragons (extremely rare)
- Void Essence: From void creatures

---

## 6. Equipment Crafting

### 6.1 Weapon Crafting Process

```lua
function CraftingService:CraftWeapon(player, recipeId)
    local recipe = RecipeDatabase[recipeId]
    
    -- Validate
    if not ValidateCraft(player, recipe) then
        return false, "Requirements not met"
    end
    
    -- Consume materials
    for _, material in ipairs(recipe.Materials) do
        InventoryService:RemoveItem(player, material.ItemId, material.Quantity)
    end
    
    -- Deduct crafting cost
    CurrencyService:RemoveCurrency(player, recipe.CraftCost)
    
    -- Start crafting (timed)
    local craftData = {
        PlayerId = player.UserId,
        RecipeId = recipeId,
        StartTime = os.time(),
        Duration = recipe.CraftTime,
        Station = recipe.CraftingStation
    }
    
    ActiveCrafts[player.UserId] = craftData
    
    -- Wait for completion
    task.wait(recipe.CraftTime)
    
    -- Determine quality
    local quality = DetermineQuality(player, recipe)
    
    -- Generate item
    local weapon = ItemService:CreateItem(recipe.Output.ItemId, {
        Quality = quality,
        CraftedBy = player.Name,
        CraftDate = os.date("%Y-%m-%d"),
        Stats = CalculateCraftedStats(recipe, quality, player)
    })
    
    -- Award item
    InventoryService:AddItem(player, weapon)
    
    -- Grant XP
    ProfessionService:AddXP(player, recipe.Category, recipe.XPReward)
    
    return true, weapon
end

function DetermineQuality(player, recipe)
    local skillLevel = player.Professions[recipe.Category].Level
    local baseQuality = 0.5 -- 50% chance for Normal
    
    -- Skill bonus: +0.5% per level
    local skillBonus = skillLevel * 0.005
    
    -- Specialization bonus
    if player.Specialization == recipe.Category then
        skillBonus = skillBonus + 0.1 -- +10%
    end
    
    -- Calculate final quality roll
    local roll = math.random()
    local adjustedRoll = roll + skillBonus
    
    if adjustedRoll >= 0.95 then
        return "Perfect" -- 3× stats
    elseif adjustedRoll >= 0.85 then
        return "Great" -- 2× stats
    elseif adjustedRoll >= 0.60 then
        return "Good" -- 1.5× stats
    else
        return "Normal" -- 1× stats
    end
end
```

### 6.2 Quality Tiers

Crafted equipment can have quality modifiers:

| Quality | Stat Multiplier | Sell Value | Craft Chance |
|---------|-----------------|------------|--------------|
| Poor | 0.5× | 0.5× | N/A (only from failures) |
| Normal | 1.0× | 1.0× | 40% base |
| Good | 1.5× | 2.0× | 35% base |
| Great | 2.0× | 4.0× | 15% base |
| Perfect | 3.0× | 10.0× | 5% base |

**Increasing Quality Chance:**
- Higher profession level (+0.5% per level)
- Specialization bonus (+10%)
- Using premium crafting station (+5%)
- Rare crafting boosters (+20%, consumable)

### 6.3 Signature Items

At max profession level (100), craftsmen can add signature:
- "Crafted by [PlayerName]"
- +5% bonus stats
- Special cosmetic glow
- Cannot be mass-produced (1 per day limit)
- High value in trading market

---

## 7. Consumable Crafting

### 7.1 Potion Recipes

#### Health Potion (Small)
**Profession:** Alchemy Level 1  
**Materials:**
- 3 Red Herbs
- 1 Water Bottle (buy from NPC, 5 IRF)
**Output:** Heals 100 HP instantly  
**Craft Time:** 5 seconds  
**XP:** 10

#### Health Potion (Medium)
**Profession:** Alchemy Level 20  
**Materials:**
- 5 Red Herbs
- 2 Honey
- 1 Purified Water (10 IRF)
**Output:** Heals 300 HP instantly  
**Craft Time:** 10 seconds  
**XP:** 50

#### Health Potion (Large)
**Profession:** Alchemy Level 40  
**Materials:**
- 10 Red Herbs
- 5 Honey
- 1 Crystal Water (50 IRF)
- 1 Essence of Life (rare drop)
**Output:** Heals 1,000 HP instantly  
**Craft Time:** 20 seconds  
**XP:** 150

#### Buff Potions

**Strength Elixir**
- Materials: 5 Bear Meat, 3 Iron Ore (crushed), 1 Alcohol
- Effect: +30% Attack Damage for 10 minutes
- Level: Alchemy 25

**Speed Tonic**
- Materials: 5 Rabbit Foot, 5 Wind Essence, 1 Alcohol
- Effect: +40% Movement Speed for 10 minutes
- Level: Alchemy 30

**Resistance Brew**
- Materials: 10 Obsidian Dust, 5 Dragon Scale Powder, 1 Rare Herb
- Effect: +50% All Resistances for 15 minutes
- Level: Alchemy 60

---

### 7.2 Food Recipes

#### Grilled Fish
**Profession:** Cooking Level 5  
**Materials:**
- 1 Any Fish
- 1 Salt
- 1 Lemon
**Effect:** +50 HP, +10% Fishing Success (30 min)  
**Craft Time:** 10 seconds

#### Dragon Steak
**Profession:** Cooking Level 80  
**Materials:**
- 1 Dragon Meat (boss drop)
- 5 Phoenix Pepper
- 3 Rare Spices
- 1 Premium Oil
**Effect:** +500 HP, +50% Fire Damage, +30% Attack (1 hour)  
**Craft Time:** 60 seconds  
**XP:** 500

#### Feast Platter (Party Buff)
**Profession:** Cooking Level 90  
**Materials:**
- 10 Various Meats
- 10 Various Fish
- 20 Various Crops
- 5 Gourmet Spices
**Effect:** All party members get +20% All Stats (2 hours)  
**Craft Time:** 5 minutes  
**XP:** 1,000  
**Special:** Can be placed on table, feeds 10 players

---

## 8. Enhancement & Upgrades

### 8.1 Equipment Enhancement

Players can enhance existing equipment at Enchanting Table:

#### Sharpening (Weapons)
- **Materials:** 10 Whetstones (buy 100 IRF each)
- **Effect:** +10% damage temporarily (1 hour)
- **Max:** Can stack 3 times (+30% max)

#### Fortification (Armor)
- **Materials:** 10 Reinforcement Plates
- **Effect:** +10% defense temporarily (1 hour)

#### Enchanting (Permanent)
**Example: Flame Enchantment**
- **Materials:**
  - 1 Epic+ Weapon
  - 10 Fire Essence
  - 5 Ruby (cut)
  - 1 Enchantment Scroll
- **Effect:** Adds fire damage (permanently)
- **Visual:** Weapon glows with flames
- **Cost:** 10,000 IRF + materials

**Enchantment Slots:**
- Common: 0 slots
- Rare: 1 slot
- Epic: 2 slots
- Legendary: 3 slots
- Mythic: 5 slots

### 8.2 Tier Upgrading

Upgrade equipment to next rarity tier:

**Rare → Epic Upgrade**
- **Requirements:**
  - Rare equipment at max durability
  - 50 of corresponding materials (Iron for iron sword)
  - 10 Epic Geodes
  - 20,000 IRF
- **Process:**
  - Take to Master Blacksmith
  - 24-hour upgrade time (or instant for 200 Robux)
  - Success rate: 80%
  - Failure: Equipment downgraded to Common (ouch!)

**Epic → Legendary Upgrade**
- **Requirements:**
  - Epic equipment
  - 100 epic materials
  - 20 Legendary Geodes
  - 100,000 IRF
- **Success Rate:** 50%
- **Failure:** Equipment destroyed (harsh!)

**Insurance System:**
- Buy "Safety Scroll" for 50 Robux
- If upgrade fails, equipment returned undamaged
- Scroll consumed on use

---

## 9. Blueprint Acquisition

### 9.1 Engineering Blueprints

Special crafting category for gadgets:

#### Automatons
**Mining Bot Blueprint**
- **Level:** Engineering 50
- **Acquisition:** Complete "Automated Mining" quest
- **Craft Materials:**
  - 100 Iron Ingots
  - 50 Copper Wiring
  - 20 Gears (crafted)
  - 10 Power Cores (rare)
- **Function:** Automatically mines in designated area
- **Output:** 50 ore per hour (must refuel)

#### Mounts
**Mechanical Horse Blueprint**
- **Level:** Engineering 60
- **Acquisition:** Purchase from Engineer NPC (50,000 IRF)
- **Craft Materials:**
  - 200 Steel Plates
  - 100 Gears
  - 50 Leather (saddle)
  - 1 Engine Core (epic drop)
- **Function:** Mount with +80% movement speed
- **Special:** Never gets tired (unlike creature mounts)

---

## 10. Technical Implementation

### 10.1 Crafting Queue System

```lua
-- Crafting Queue (allows crafting while doing other activities)
local CraftQueue = {}

function CraftingService:AddToQueue(player, recipeId, quantity)
    if not CraftQueue[player.UserId] then
        CraftQueue[player.UserId] = {}
    end
    
    local recipe = RecipeDatabase[recipeId]
    local craftJob = {
        RecipeId = recipeId,
        Quantity = quantity,
        StartTime = os.time(),
        EndTime = os.time() + (recipe.CraftTime * quantity),
        Status = "InProgress"
    }
    
    table.insert(CraftQueue[player.UserId], craftJob)
    
    -- Process queue
    task.spawn(function()
        ProcessCraftQueue(player)
    end)
end

function ProcessCraftQueue(player)
    local queue = CraftQueue[player.UserId]
    
    while #queue > 0 do
        local currentJob = queue[1]
        local timeLeft = currentJob.EndTime - os.time()
        
        if timeLeft > 0 then
            task.wait(timeLeft)
        end
        
        -- Complete craft
        local recipe = RecipeDatabase[currentJob.RecipeId]
        for i = 1, currentJob.Quantity do
            CraftingService:CompleteCraft(player, recipe)
        end
        
        -- Remove from queue
        table.remove(queue, 1)
        
        -- Notify player
        NotificationService:Send(player, "Crafting complete: " .. recipe.Name)
    end
end
```

### 10.2 Material Storage Optimization

```lua
-- Material Bank (special storage for crafting materials)
function CraftingService:GetMaterialCount(player, materialId)
    -- Check inventory
    local invCount = InventoryService:CountItem(player, materialId)
    
    -- Check material bank (doesn't take inventory space)
    local bankCount = MaterialBankService:GetCount(player, materialId) or 0
    
    return invCount + bankCount
end

-- Material Bank upgrade: 200 Robux or 20,000 IRF
-- Stores 1,000 of each crafting material
-- Accessible from any crafting station
```

---

## Implementation Checklist

### Phase 1: Core System (Month 4)
- [ ] Basic crafting stations (Forge, Alchemy, Cooking)
- [ ] 50 common/rare recipes (weapons, armor, potions)
- [ ] Crafting UI (material list, progress bar)
- [ ] Quality system implementation
- [ ] Material gathering integration

### Phase 2: Professions (Month 5)
- [ ] 6 profession tracks with leveling
- [ ] NPC craftsmen (quest givers)
- [ ] Recipe acquisition (purchase, drops, quests)
- [ ] Crafting queue system
- [ ] Material bank storage

### Phase 3: Advanced Crafting (Month 6)
- [ ] Enhancement & enchanting system
- [ ] Tier upgrade mechanics
- [ ] Engineering profession (gadgets, mounts)
- [ ] Epic/Legendary recipes (50 additional)
- [ ] Signature item system

### Phase 4: Economy Integration (Month 7)
- [ ] Player trading of crafted items
- [ ] Auction house listings
- [ ] Commission system (craft for others)
- [ ] Crafting leaderboards
- [ ] Seasonal crafting events

---

## Related Documentation
- [Database_Minerals.md](Database_Minerals.md) - Crafting materials from mining
- [Database_Crops.md](Database_Crops.md) - Cooking ingredients
- [Database_Weapons.md](Database_Weapons.md) - Craftable weapons reference
- [Database_Armor.md](Database_Armor.md) - Craftable armor reference
- [GDD_Economy.md](GDD_Economy.md) - Crafting economy balance

---

**Document End - Crafting System Design**  
*A deep crafting system that rewards specialization and experimentation*
