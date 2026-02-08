# IRIFA: Realms of Harvest & Adventure
## Database - Crafting Recipes Catalog

---

### Document Information
**Document Type:** Database Reference  
**Category:** Crafting & Recipes  
**Version:** 1.0  
**Last Updated:** February 9, 2026  
**Total Recipes:** 85+ recipes across all professions

---

## Table of Contents
1. [Database Overview](#database-overview)
2. [Blacksmithing Recipes](#blacksmithing-recipes)
3. [Fishing Rod Crafting](#fishing-rod-crafting)
4. [Farming Tools](#farming-tools)
5. [Weapon Recipes](#weapon-recipes)
6. [Armor Recipes](#armor-recipes)
7. [Decoration Crafting](#decoration-crafting)
8. [Recipe Discovery System](#recipe-discovery-system)
9. [Usage Guidelines](#usage-guidelines)

---

## Database Overview

### Recipe Structure
Each recipe contains:
- **RecipeID:** Unique identifier
- **Name:** Display name
- **Category:** Profession type
- **Station:** Where to craft (NPC or structure)
- **Materials:** Required items + quantities
- **Output:** Result item(s)
- **Rarity:** Crafted item rarity
- **Craft Time:** Duration in seconds
- **Unlock Requirements:** Level, quest, or discovery
- **XP Reward:** Proficiency XP gained

### Crafting Categories
1. **Blacksmithing:** Tools, weapons, armor (metal-based)
2. **Fishing Rod Crafting:** Fishing rods and equipment
3. **Farming Tools:** Hoes, watering cans, scythes
4. **Workshop:** Decorations, furniture, island structures
5. **Cooking:** Food items (future expansion)
6. **Alchemy:** Potions and buffs (future expansion)

### Material Types
- **Base Materials:** Wood, Stone, Iron Ingot (always needed)
- **Mineral Materials:** Ores and gems
- **Monster Materials:** Drops from creatures
- **Organic Materials:** Crops, fish, wood
- **Special Materials:** Event or rare drops

---

## Blacksmithing Recipes

### Basic Mining Tools

#### 1. Wooden Pickaxe
**RecipeID:** RECIPE_TOOL_WOOD_PICKAXE  
**Rarity:** Common  
**Station:** Blacksmith NPC

**Materials:**
- Wood x10
- Stone x5

**Output:** Wooden Pickaxe x1  
**Stats:** Mining Speed: 1.0 (base), Durability: 100

**Unlock:** Level 1 (starter recipe)  
**Craft Time:** 5 seconds  
**XP Reward:** 10 Blacksmithing XP

---

#### 2. Stone Pickaxe
**RecipeID:** RECIPE_TOOL_STONE_PICKAXE  
**Rarity:** Common  
**Station:** Blacksmith NPC

**Materials:**
- Wood x15
- Stone x20
- Iron Ore x5

**Output:** Stone Pickaxe x1  
**Stats:** Mining Speed: 1.3, Durability: 250

**Unlock:** Level 5 or Mine 100 ore  
**Craft Time:** 10 seconds  
**XP Reward:** 25 Blacksmithing XP

---

#### 3. Iron Pickaxe
**RecipeID:** RECIPE_TOOL_IRON_PICKAXE  
**Rarity:** Rare  
**Station:** Blacksmith NPC

**Materials:**
- Wood x10
- Iron Ingot x15
- Stone x10

**Output:** Iron Pickaxe x1  
**Stats:** Mining Speed: 1.6, Durability: 500

**Unlock:** Level 10, Quest "Forging Ahead"  
**Craft Time:** 30 seconds  
**XP Reward:** 50 Blacksmithing XP

---

#### 4. Steel Pickaxe
**RecipeID:** RECIPE_TOOL_STEEL_PICKAXE  
**Rarity:** Rare  
**Station:** Blacksmith NPC

**Materials:**
- Oak Wood x15
- Steel Ingot x20
- Iron Ingot x10

**Output:** Steel Pickaxe x1  
**Stats:** Mining Speed: 1.9, Durability: 1,000

**Unlock:** Level 20, Craft 50 items  
**Craft Time:** 60 seconds  
**XP Reward:** 100 Blacksmithing XP

---

#### 5. Mithril Pickaxe
**RecipeID:** RECIPE_TOOL_MITHRIL_PICKAXE  
**Rarity:** Epic  
**Station:** Blacksmith NPC

**Materials:**
- Mahogany Wood x20
- Mithril Ingot x30
- Ruby x5

**Output:** Mithril Pickaxe x1  
**Stats:** Mining Speed: 2.3, Durability: 2,500  
**Special Effect:** +10% Rare Ore Chance

**Unlock:** Level 35, Mining Proficiency 40  
**Craft Time:** 120 seconds  
**XP Reward:** 250 Blacksmithing XP

---

#### 6. Adamantite Pickaxe
**RecipeID:** RECIPE_TOOL_ADAMANTITE_PICKAXE  
**Rarity:** Epic  
**Station:** Blacksmith NPC

**Materials:**
- Ancient Wood x25
- Adamantite Ingot x40
- Diamond x10
- Obsidian x15

**Output:** Adamantite Pickaxe x1  
**Stats:** Mining Speed: 2.7, Durability: 5,000  
**Special Effects:**
- +15% Rare Ore Chance
- +10% Geode Find Rate

**Unlock:** Level 50, Mining Proficiency 60  
**Craft Time:** 180 seconds  
**XP Reward:** 500 Blacksmithing XP

---

#### 7. Dragon Pickaxe
**RecipeID:** RECIPE_TOOL_DRAGON_PICKAXE  
**Rarity:** Legendary  
**Station:** Blacksmith NPC

**Materials:**
- Dragon Scale x50
- Dragon Bone x30
- Mythril Ingot x50
- Dragon Heart Gem x5

**Output:** Dragon Pickaxe x1  
**Stats:** Mining Speed: 3.2, Durability: 10,000  
**Special Effects:**
- +25% Rare Ore Chance
- +20% Geode Find Rate
- +50% Mythic Material Chance
- Fire Aura (visual)

**Unlock:** Level 70, Defeat Elder Dragon, Mining Proficiency 80  
**Craft Time:** 300 seconds  
**XP Reward:** 1,000 Blacksmithing XP

---

### Ingot Processing

#### 8. Iron Ingot
**RecipeID:** RECIPE_MATERIAL_IRON_INGOT  
**Rarity:** Common  
**Station:** Blacksmith Furnace

**Materials:**
- Iron Ore x5
- Coal x1

**Output:** Iron Ingot x1  
**Craft Time:** 10 seconds  
**XP Reward:** 5 Blacksmithing XP

---

#### 9. Steel Ingot
**RecipeID:** RECIPE_MATERIAL_STEEL_INGOT  
**Rarity:** Rare  
**Station:** Blacksmith Furnace

**Materials:**
- Iron Ingot x3
- Carbon x2
- Coal x2

**Output:** Steel Ingot x1  
**Craft Time:** 20 seconds  
**XP Reward:** 15 Blacksmithing XP

---

#### 10. Mithril Ingot
**RecipeID:** RECIPE_MATERIAL_MITHRIL_INGOT  
**Rarity:** Epic  
**Station:** Blacksmith Furnace

**Materials:**
- Mithril Ore x10
- Ruby Dust x3
- Ancient Coal x5

**Output:** Mithril Ingot x1  
**Craft Time:** 45 seconds  
**XP Reward:** 40 Blacksmithing XP

---

#### 11. Adamantite Ingot
**RecipeID:** RECIPE_MATERIAL_ADAMANTITE_INGOT  
**Rarity:** Epic  
**Station:** Blacksmith Furnace

**Materials:**
- Adamantite Ore x15
- Diamond Dust x5
- Volcanic Coal x8

**Output:** Adamantite Ingot x1  
**Craft Time:** 60 seconds  
**XP Reward:** 80 Blacksmithing XP

---

## Weapon Recipes

### Swords

#### 12. Iron Sword
**RecipeID:** RECIPE_WEAPON_IRON_SWORD  
**Rarity:** Rare  
**Station:** Blacksmith NPC

**Materials:**
- Iron Ingot x10
- Oak Wood x5
- Leather x3

**Output:** Iron Sword x1  
**Stats:** Damage: 35, Attack Speed: 1.2, Durability: 800

**Unlock:** Level 10, Quest "First Blade"  
**Craft Time:** 60 seconds  
**XP Reward:** 80 Blacksmithing XP

---

#### 13. Steel Longsword
**RecipeID:** RECIPE_WEAPON_STEEL_LONGSWORD  
**Rarity:** Rare  
**Station:** Blacksmith NPC

**Materials:**
- Steel Ingot x15
- Mahogany Wood x8
- Iron Ingot x5
- Monster Claw x3

**Output:** Steel Longsword x1  
**Stats:** Damage: 60, Attack Speed: 1.1, Durability: 1,500  
**Effect:** +5% Critical Chance

**Unlock:** Level 25, Craft 10 weapons  
**Craft Time:** 90 seconds  
**XP Reward:** 150 Blacksmithing XP

---

#### 14. Flame Blade
**RecipeID:** RECIPE_WEAPON_FLAME_BLADE  
**Rarity:** Epic  
**Station:** Blacksmith NPC

**Materials:**
- Mithril Ingot x20
- Fire Crystal x10
- Phoenix Feather x5
- Ruby x8

**Output:** Flame Blade x1  
**Stats:** Damage: 120 (80 physical + 40 fire), Attack Speed: 1.3, Durability: 3,000  
**Effects:**
- +50% Fire Damage
- Burn enemies on hit (20 DPS, 5 sec)
- Fire trail visual

**Unlock:** Level 45, Defeat Fire Golem Boss, Blacksmithing Proficiency 50  
**Craft Time:** 180 seconds  
**XP Reward:** 400 Blacksmithing XP

---

#### 15. Dragon Slayer Greatsword
**RecipeID:** RECIPE_WEAPON_DRAGON_SLAYER  
**Rarity:** Legendary  
**Station:** Blacksmith NPC

**Materials:**
- Dragon Scale x80
- Dragon Bone x50
- Adamantite Ingot x60
- Dragon Heart Gem x10
- Obsidian x40

**Output:** Dragon Slayer Greatsword x1  
**Stats:** Damage: 300, Attack Speed: 0.8, Durability: 10,000  
**Effects:**
- +100% Damage vs Dragon-type enemies
- +20% Critical Chance
- +50% Critical Damage
- Dragon Roar on critical (AoE stun)
- Legendary Glow visual

**Unlock:** Level 80, Defeat Elder Dragon 5 times, Blacksmithing Proficiency 90  
**Craft Time:** 600 seconds  
**XP Reward:** 2,000 Blacksmithing XP

---

### Spears

#### 16. Iron Spear
**RecipeID:** RECIPE_WEAPON_IRON_SPEAR  
**Rarity:** Rare  
**Station:** Blacksmith NPC

**Materials:**
- Iron Ingot x8
- Oak Wood x12
- Rope x5

**Output:** Iron Spear x1  
**Stats:** Damage: 30, Attack Speed: 1.5, Range: 3m, Durability: 600

**Unlock:** Level 12  
**Craft Time:** 45 seconds  
**XP Reward:** 60 Blacksmithing XP

---

#### 17. Trident of the Tides
**RecipeID:** RECIPE_WEAPON_TRIDENT  
**Rarity:** Epic  
**Station:** Blacksmith NPC

**Materials:**
- Mithril Ingot x25
- Ocean Pearl x15
- Leviathan Scale x10
- Sapphire x10

**Output:** Trident of the Tides x1  
**Stats:** Damage: 100 (70 physical + 30 water), Attack Speed: 1.4, Range: 3.5m, Durability: 4,000  
**Effects:**
- +100% Damage underwater
- Shoot water projectiles
- Swim speed +50%
- Water breathing

**Unlock:** Level 55, Defeat Leviathan Boss  
**Craft Time:** 240 seconds  
**XP Reward:** 600 Blacksmithing XP

---

### Axes

#### 18. Iron Battleaxe
**RecipeID:** RECIPE_WEAPON_IRON_AXE  
**Rarity:** Rare  
**Station:** Blacksmith NPC

**Materials:**
- Iron Ingot x12
- Oak Wood x8
- Stone x10

**Output:** Iron Battleaxe x1  
**Stats:** Damage: 50, Attack Speed: 0.9, Durability: 900  
**Effect:** +10% Damage vs trees (also chops trees faster)

**Unlock:** Level 15  
**Craft Time:** 60 seconds  
**XP Reward:** 70 Blacksmithing XP

---

### Bows

#### 19. Longbow
**RecipeID:** RECIPE_WEAPON_LONGBOW  
**Rarity:** Rare  
**Station:** Workshop NPC

**Materials:**
- Yew Wood x20
- Spider Silk x15
- Iron Ingot x5

**Output:** Longbow x1  
**Stats:** Damage: 40, Attack Speed: 0.8, Range: 30m, Durability: 1,000

**Unlock:** Level 20  
**Craft Time:** 90 seconds  
**XP Reward:** 120 Crafting XP

---

#### 20. Shadow Crossbow
**RecipeID:** RECIPE_WEAPON_SHADOW_CROSSBOW  
**Rarity:** Epic  
**Station:** Workshop NPC

**Materials:**
- Ancient Wood x30
- Shadow Essence x20
- Steel Ingot x25
- Void Crystal x5

**Output:** Shadow Crossbow x1  
**Stats:** Damage: 80, Attack Speed: 1.0, Range: 40m, Durability: 2,500  
**Effects:**
- Piercing shots (hits multiple enemies)
- +20% Critical Chance at night
- Invisible arrows

**Unlock:** Level 50, Defeat Shadow Beast  
**Craft Time:** 180 seconds  
**XP Reward:** 450 Crafting XP

---

## Armor Recipes

### Helmets

#### 21. Iron Helmet
**RecipeID:** RECIPE_ARMOR_IRON_HELMET  
**Rarity:** Rare  
**Station:** Blacksmith NPC

**Materials:**
- Iron Ingot x8
- Leather x5

**Output:** Iron Helmet x1  
**Stats:** Defense: 15, HP: +50, Durability: 800

**Unlock:** Level 10  
**Craft Time:** 45 seconds  
**XP Reward:** 60 Blacksmithing XP

---

#### 22. Steel Helmet
**RecipeID:** RECIPE_ARMOR_STEEL_HELMET  
**Rarity:** Rare  
**Station:** Blacksmith NPC

**Materials:**
- Steel Ingot x12
- Reinforced Leather x8
- Iron Ingot x5

**Output:** Steel Helmet x1  
**Stats:** Defense: 30, HP: +100, Durability: 1,500

**Unlock:** Level 20  
**Craft Time:** 60 seconds  
**XP Reward:** 100 Blacksmithing XP

---

#### 23. Dragon Helm
**RecipeID:** RECIPE_ARMOR_DRAGON_HELM  
**Rarity:** Legendary  
**Station:** Blacksmith NPC

**Materials:**
- Dragon Scale x30
- Dragon Bone x20
- Adamantite Ingot x25
- Ruby x10

**Output:** Dragon Helm x1  
**Stats:** Defense: 100, HP: +500, Fire Resistance: +50%, Durability: 8,000  
**Effects:**
- +10% Critical Chance
- +15% Fire Damage
- Dragon horns visual

**Unlock:** Level 70, Defeat Elder Dragon  
**Craft Time:** 300 seconds  
**XP Reward:** 1,200 Blacksmithing XP

---

### Chestplates

#### 24. Iron Chestplate
**RecipeID:** RECIPE_ARMOR_IRON_CHEST  
**Rarity:** Rare  
**Station:** Blacksmith NPC

**Materials:**
- Iron Ingot x15
- Leather x10
- Cloth x5

**Output:** Iron Chestplate x1  
**Stats:** Defense: 30, HP: +100, Durability: 1,000

**Unlock:** Level 10  
**Craft Time:** 90 seconds  
**XP Reward:** 100 Blacksmithing XP

---

#### 25. Mithril Chestplate
**RecipeID:** RECIPE_ARMOR_MITHRIL_CHEST  
**Rarity:** Epic  
**Station:** Blacksmith NPC

**Materials:**
- Mithril Ingot x30
- Dragon Leather x15
- Ruby x8
- Iron Ingot x10

**Output:** Mithril Chestplate x1  
**Stats:** Defense: 80, HP: +300, Durability: 4,000  
**Effect:** +10% Defense

**Unlock:** Level 40, Blacksmithing Proficiency 40  
**Craft Time:** 180 seconds  
**XP Reward:** 400 Blacksmithing XP

---

### Full Armor Sets

#### 26. Dragon Armor Set (5 pieces)
**Set Includes:**
- Dragon Helm
- Dragon Chestplate
- Dragon Leggings
- Dragon Boots
- Dragon Gauntlets

**Set Bonus (2 pieces):** +100 HP, +10% Fire Resistance  
**Set Bonus (3 pieces):** +200 HP, +20% Fire Resistance, +10% Attack  
**Set Bonus (5 pieces - FULL SET):**
- +500 HP
- +50% Fire Resistance
- +25% Attack
- +25% Defense
- Dragon Wings (glide ability)
- Dragon Breath attack (cooldown ability)

**Total Materials for Full Set:**
- Dragon Scale x250
- Dragon Bone x150
- Adamantite Ingot x200
- Dragon Heart Gem x30
- Ruby x50
- Obsidian x100

**Total Craft Time:** ~25 minutes  
**Total XP:** 8,000 Blacksmithing XP

---

## Fishing Rod Crafting

#### 27. Bamboo Fishing Rod
**RecipeID:** RECIPE_TOOL_BAMBOO_ROD  
**Rarity:** Common  
**Station:** Fisherman NPC

**Materials:**
- Bamboo x10
- String x5
- Iron Hook x1

**Output:** Bamboo Fishing Rod x1  
**Stats:** Catch Speed: 1.2, Rare Fish Chance: +0%, Durability: 200

**Unlock:** Level 1 (starter)  
**Craft Time:** 10 seconds  
**XP Reward:** 10 Fishing XP

---

#### 28. Oak Fishing Rod
**RecipeID:** RECIPE_TOOL_OAK_ROD  
**Rarity:** Rare  
**Station:** Fisherman NPC

**Materials:**
- Oak Wood x15
- Spider Silk x10
- Steel Hook x1
- Reel x1

**Output:** Oak Fishing Rod x1  
**Stats:** Catch Speed: 1.5, Rare Fish Chance: +5%, Durability: 600

**Unlock:** Level 10, Quest "Angler's Progress"  
**Craft Time:** 30 seconds  
**XP Reward:** 50 Fishing XP

---

#### 29. Enchanted Fishing Rod
**RecipeID:** RECIPE_TOOL_ENCHANTED_ROD  
**Rarity:** Epic  
**Station:** Fisherman NPC

**Materials:**
- Mahogany Wood x25
- Magical Thread x15
- Mithril Hook x1
- Precision Reel x1
- Sapphire x5

**Output:** Enchanted Fishing Rod x1  
**Stats:** Catch Speed: 2.0, Rare Fish Chance: +15%, Durability: 2,000  
**Effect:** Glowing lure attracts fish faster

**Unlock:** Level 40, Fishing Proficiency 40  
**Craft Time:** 120 seconds  
**XP Reward:** 300 Fishing XP

---

#### 30. Leviathan's Rod
**RecipeID:** RECIPE_TOOL_LEVIATHAN_ROD  
**Rarity:** Legendary  
**Station:** Fisherman NPC

**Materials:**
- Ancient Wood x40
- Leviathan Scale x30
- Mythril Hook x1
- Ocean Pearl x20
- Diamond x10

**Output:** Leviathan's Rod x1  
**Stats:** Catch Speed: 2.8, Rare Fish Chance: +30%, Durability: 8,000  
**Effects:**
- Can catch Mythic fish
- +50% catch rate in storms
- Never breaks line
- Water walking (walk on water surface)
- Oceanic Glow visual

**Unlock:** Level 70, Defeat Leviathan, Fishing Proficiency 90  
**Craft Time:** 360 seconds  
**XP Reward:** 1,500 Fishing XP

---

## Farming Tools

#### 31. Wooden Hoe
**RecipeID:** RECIPE_TOOL_WOOD_HOE  
**Rarity:** Common  
**Station:** Farmer NPC

**Materials:**
- Wood x8
- Stone x5

**Output:** Wooden Hoe x1  
**Stats:** Tilling Speed: 1.0, Durability: 100

**Unlock:** Level 1 (starter)  
**Craft Time:** 5 seconds  
**XP Reward:** 5 Farming XP

---

#### 32. Iron Hoe
**RecipeID:** RECIPE_TOOL_IRON_HOE  
**Rarity:** Rare  
**Station:** Farmer NPC

**Materials:**
- Oak Wood x10
- Iron Ingot x12

**Output:** Iron Hoe x1  
**Stats:** Tilling Speed: 1.5, Durability: 500  
**Effect:** Can till 3×3 area

**Unlock:** Level 15  
**Craft Time:** 30 seconds  
**XP Reward:** 40 Farming XP

---

#### 33. Watering Can
**RecipeID:** RECIPE_TOOL_WATERING_CAN  
**Rarity:** Common  
**Station:** Farmer NPC

**Materials:**
- Iron Ingot x8
- Leather x5

**Output:** Watering Can x1  
**Stats:** Waters 1 plant at a time, Capacity: 20 uses

**Unlock:** Level 5  
**Craft Time:** 20 seconds  
**XP Reward:** 15 Farming XP

---

#### 34. Golden Watering Can
**RecipeID:** RECIPE_TOOL_GOLD_WATERING_CAN  
**Rarity:** Epic  
**Station:** Farmer NPC

**Materials:**
- Gold Ingot x20
- Mithril Ingot x10
- Sapphire x5

**Output:** Golden Watering Can x1  
**Stats:** Waters 3×3 area, Capacity: 100 uses  
**Effect:** +10% Perfect Crop Chance when used

**Unlock:** Level 45, Farming Proficiency 50  
**Craft Time:** 150 seconds  
**XP Reward:** 300 Farming XP

---

#### 35. Scythe
**RecipeID:** RECIPE_TOOL_SCYTHE  
**Rarity:** Rare  
**Station:** Farmer NPC

**Materials:**
- Steel Ingot x15
- Mahogany Wood x10
- Iron Ingot x5

**Output:** Scythe x1  
**Stats:** Harvest Speed: 2.0, Durability: 1,200  
**Effect:** Harvests 3×3 area instantly

**Unlock:** Level 25, Quest "Efficient Harvester"  
**Craft Time:** 60 seconds  
**XP Reward:** 100 Farming XP

---

## Decoration Crafting

#### 36. Wooden Chair
**RecipeID:** RECIPE_DECO_WOOD_CHAIR  
**Rarity:** Common  
**Station:** Workshop NPC

**Materials:**
- Wood x10

**Output:** Wooden Chair x1  
**Aesthetic Score:** +5

**Unlock:** Level 5  
**Craft Time:** 15 seconds  
**XP Reward:** 10 Crafting XP

---

#### 37. Stone Fountain
**RecipeID:** RECIPE_DECO_FOUNTAIN  
**Rarity:** Rare  
**Station:** Workshop NPC

**Materials:**
- Stone x50
- Iron Ingot x15
- Water Crystal x5

**Output:** Stone Fountain x1  
**Aesthetic Score:** +50  
**Effect:** Animated water

**Unlock:** Level 20  
**Craft Time:** 120 seconds  
**XP Reward:** 150 Crafting XP

---

#### 38. Crystal Statue
**RecipeID:** RECIPE_DECO_CRYSTAL_STATUE  
**Rarity:** Epic  
**Station:** Workshop NPC

**Materials:**
- Crystal x100
- Diamond x20
- Mithril Ingot x30

**Output:** Crystal Statue x1  
**Aesthetic Score:** +200  
**Effect:** Glowing particle effects

**Unlock:** Level 50, Place 100 decorations  
**Craft Time:** 300 seconds  
**XP Reward:** 500 Crafting XP

---

#### 39. Dragon Monument
**RecipeID:** RECIPE_DECO_DRAGON_MONUMENT  
**Rarity:** Legendary  
**Station:** Workshop NPC

**Materials:**
- Dragon Scale x200
- Dragon Bone x100
- Obsidian x300
- Dragon Heart Gem x20

**Output:** Dragon Monument x1 (large structure)  
**Aesthetic Score:** +1,000  
**Effects:**
- Dragon statue with glowing eyes
- Fire particle effects
- +5% All Stats in radius (island buff)

**Unlock:** Level 80, Defeat Elder Dragon 10 times  
**Craft Time:** 600 seconds  
**XP Reward:** 3,000 Crafting XP

---

## Recipe Discovery System

### How to Unlock Recipes

#### 1. Automatic Level Unlocks
- Level 1-10: Basic recipes
- Level 11-30: Intermediate recipes
- Level 31-60: Advanced recipes
- Level 61+: Legendary recipes

#### 2. Quest Rewards
- Complete NPC quest chains
- Story progression
- Special challenges

#### 3. Discovery System
**Experimentation:**
Players can place materials in crafting interface and "experiment" to discover new recipes.

```lua
function DiscoveryService:AttemptRecipeDiscovery(player, materials)
    -- Check if materials match any undiscovered recipe
    for recipeId, recipeData in pairs(RecipeDatabase) do
        if not player.KnownRecipes[recipeId] then
            if CheckMaterialsMatch(materials, recipeData.Materials) then
                -- Discovery success!
                player.KnownRecipes[recipeId] = true
                AwardDiscoveryBonus(player, recipeData)
                return true, recipeId
            end
        end
    end
    
    -- Discovery failed, lose 50% of materials
    return false
end
```

**Discovery Examples:**
- Combine Iron Ingot + Ruby + Fire Crystal = Discover Flame Blade recipe
- Mix Leviathan Scale + Ocean Pearl + Mithril = Discover Trident recipe
- Experiment with Dragon materials = Discover Dragon equipment

#### 4. Boss Drops
- Defeat bosses to get recipe scrolls
- Legendary bosses drop legendary recipes
- One-time drop per boss

#### 5. Merchant Purchase
- Traveling Merchant sells random recipes
- Limited stock
- High IRF cost

---

## Special Recipe Features

### Quality System
Some recipes can produce higher quality outputs:

**Quality Tiers:**
- Normal: 100% base stats
- Good: 110% base stats (+10% materials consumed)
- Excellent: 125% base stats (+25% materials consumed)
- Perfect: 150% base stats (+50% materials consumed)

**Quality influenced by:**
- Crafting Proficiency level
- Using perfect quality materials
- Luck stat
- Familiar buffs

### Material Efficiency
At high Crafting Proficiency:
- Level 50: 10% chance to save materials
- Level 75: 20% chance to save materials
- Level 100: 30% chance to save materials

### Batch Crafting
For consumables and common items:
- Craft multiple at once
- Speeds up process
- Requires sufficient materials
- Higher proficiency = faster batch crafting

---

## Usage Guidelines

### For Designers
- Balance material costs vs item power
- Ensure progression curve (low → high tier)
- Create clear upgrade paths
- Make discovery rewarding

### For Developers
- Use RecipeID for crafting system logic
- Check unlock requirements before showing recipe
- Implement crafting time with progress bar
- Handle material consumption server-side

### For Content Updates
**Adding New Recipe Checklist:**
1. [ ] Assign unique RecipeID
2. [ ] Determine rarity tier
3. [ ] Define material requirements
4. [ ] Set output item and stats
5. [ ] Choose unlock method
6. [ ] Balance craft time
7. [ ] Set XP reward
8. [ ] Test material economy impact
9. [ ] Create crafting animation (if special)
10. [ ] Update recipe book UI

---

## Recipe Balance Sheet

### Material Value Reference
| Material | IRF Value | Rarity | Gathering Time |
|----------|-----------|--------|----------------|
| Wood | 5 | Common | 2 sec/unit |
| Stone | 3 | Common | 3 sec/unit |
| Iron Ore | 20 | Common | 10 sec/unit |
| Iron Ingot | 100 | Common | 20 sec/unit |
| Steel Ingot | 300 | Rare | 40 sec/unit |
| Mithril Ingot | 1,000 | Epic | 90 sec/unit |
| Adamantite Ingot | 3,000 | Epic | 150 sec/unit |
| Dragon Scale | 5,000 | Legendary | Boss drop |
| Dragon Heart Gem | 50,000 | Legendary | Rare boss drop |

### Crafting Time Guidelines
- Common tools: 5-30 seconds
- Rare equipment: 30-120 seconds
- Epic equipment: 120-300 seconds
- Legendary equipment: 300-600 seconds
- Large structures: 600+ seconds

---

## Future Recipe Expansions

### Planned Additions (v2.0)
- [ ] Cooking recipes (food buffs)
- [ ] Alchemy recipes (potions)
- [ ] Jewelry crafting (accessories)
- [ ] Furniture set recipes
- [ ] Vehicle crafting (boats, carts)
- [ ] Familiar equipment (saddles, armor)

### Event Recipes
- Seasonal exclusive recipes
- Holiday-themed items
- Limited-time collaboration recipes

---

**Document End - Crafting Recipes Database**  
*Craft your destiny!*
