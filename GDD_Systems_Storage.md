# IRIFA: Realms of Harvest & Adventure
## Game Design Document - Storage & Inventory System

---

### Document Information
**Document Type:** System Design  
**System:** Inventory & Storage Management  
**Version:** 1.0  
**Last Updated:** February 9, 2026  
**Status:** Implementation Ready

---

## Table of Contents
1. [Overview](#1-overview)
2. [Player Inventory](#2-player-inventory)
3. [Storage Systems](#3-storage-systems)
4. [Sorting & Organization](#4-sorting--organization)
5. [Item Types & Stacking](#5-item-types--stacking)
6. [Quick Access Systems](#6-quick-access-systems)
7. [System Integration](#7-system-integration)
8. [Inventory Upgrades](#8-inventory-upgrades)
9. [Technical Implementation](#9-technical-implementation)
10. [UI/UX Design](#10-uiux-design)

---

## 1. Overview

### 1.1 System Purpose

**Why storage matters:**
- Players accumulate items from ALL systems
- Mining = ores, gems (24+ types)
- Farming = crops, seeds (26+ types)
- Fishing = fish, bait (32+ types)
- Combat = equipment, loot (100+ types)
- Taming = food, familiar items
- Crafting = materials, recipes

**Without proper storage:** Frustration, inventory management mini-game (bad!)

### 1.2 Design Philosophy

**INTERCONNECTED STORAGE:**
- Each system needs dedicated storage
- Materials stored separately from equipment
- Fast access from anywhere (not just town)
- Automated organization options
- Progression = more storage space

### 1.3 Storage Hierarchy

```
Player Inventory (Personal, 50-100 slots)
    ↓
Backpack (Quick access, 20-40 slots)
    ↓
Bank Vault (Town, unlimited* slots)
    ↓
Private Island Storage (Home base, unlimited*)
    ↓
Material Bank (Crafting materials only, auto-access)
    ↓
Familiar Barn (Creature storage, 20-100 capacity)
```

*Unlimited with upgrades (reasonable limits for performance)

---

## 2. Player Inventory

### 2.1 Base Inventory

**Starting capacity:** 50 slots

**Item categories in inventory:**
- Equipment (weapons, armor) - 10 slots
- Consumables (potions, food) - 15 slots
- Materials (ores, crops, fish) - 20 slots
- Miscellaneous (quest items, keys) - 5 slots

```lua
PlayerInventory = {
    OwnerId = 12345,
    Capacity = 50,
    CurrentSlots = 38,
    
    Items = {
        {Slot = 1, ItemId = "WPN_IRON_SWORD", Quantity = 1, Data = {...}},
        {Slot = 2, ItemId = "MAT_IRON_ORE", Quantity = 50},
        {Slot = 3, ItemId = "POTION_HEALTH_SMALL", Quantity = 10},
        -- ...
    },
    
    EquippedGear = {
        Weapon = {ItemId = "WPN_IRON_SWORD", Slot = 1},
        Helmet = nil,
        Chestplate = {ItemId = "ARM_IRON_CHEST", Slot = 15},
        Leggings = {ItemId = "ARM_IRON_LEGS", Slot = 16},
        Accessory1 = nil,
        Accessory2 = nil,
        Familiar = {FamiliarId = "FIRE_WOLF_001", Slot = 30}
    }
}
```

### 2.2 Equipment Slots

**Wearable equipment (doesn't take inventory space when equipped):**
- Weapon (1 slot)
- Helmet (1 slot)
- Chestplate (1 slot)
- Leggings (1 slot)
- Accessory 1 (ring/necklace)
- Accessory 2 (ring/necklace)
- Active Familiar (1 creature)
- Mount (if different from familiar)

**Quick-swap system:**
```lua
function InventoryService:QuickSwapWeapon(player, targetSlot)
    local currentWeapon = player.EquippedGear.Weapon
    local newWeapon = player.Inventory.Items[targetSlot]
    
    -- Swap instantly (no animation delay)
    player.EquippedGear.Weapon = newWeapon
    player.Inventory.Items[targetSlot] = currentWeapon
    
    -- Update character model
    CharacterService:UpdateWeaponModel(player, newWeapon)
    
    -- Trigger weapon swap sound
    SoundService:PlaySound(player, "WeaponSwap")
end
```

### 2.3 Inventory Weight System (Optional)

**Lightweight system (doesn't limit slots, affects movement):**

```lua
function InventoryService:CalculateWeight(player)
    local totalWeight = 0
    
    for _, item in ipairs(player.Inventory.Items) do
        local itemData = ItemDatabase[item.ItemId]
        totalWeight = totalWeight + (itemData.Weight * item.Quantity)
    end
    
    return totalWeight
end

function InventoryService:ApplyWeightPenalty(player)
    local weight = CalculateWeight(player)
    local capacity = player.Stats.CarryCapacity or 1000 -- Base 1000
    
    if weight > capacity * 0.8 then
        -- 80-100%: -10% movement speed
        player.Character.Humanoid.WalkSpeed = BASE_WALKSPEED * 0.9
    elseif weight > capacity then
        -- Over 100%: -30% movement speed, cannot run
        player.Character.Humanoid.WalkSpeed = BASE_WALKSPEED * 0.7
    end
end
```

**Weight can be increased:**
- Strength stat (+10 capacity per point)
- Backpack upgrades (+100 capacity each)
- Familiar buff (pack mule familiar +200 capacity)

---

## 3. Storage Systems

### 3.1 Bank Vault (Town Storage)

**Central storage in every town:**

```lua
BankVault = {
    PlayerId = 12345,
    Tabs = {
        {Name = "Equipment", Capacity = 100, Items = {...}},
        {Name = "Materials", Capacity = 200, Items = {...}},
        {Name = "Consumables", Capacity = 100, Items = {...}},
        {Name = "Valuables", Capacity = 50, Items = {...}},
        {Name = "Custom 1", Capacity = 100, Items = {...}}
    },
    TotalCapacity = 550,
    UsedSlots = 342
}
```

**Bank Features:**
- Access from any town (shared across all locations)
- Cannot access during combat
- Can access from Private Island
- Organized by tabs (customizable)
- Search and filter tools

**Bank Upgrades:**
| Tier | Total Slots | Cost |
|------|-------------|------|
| 1 (Free) | 100 | Free |
| 2 | 200 | 5,000 IRF |
| 3 | 400 | 20,000 IRF |
| 4 | 700 | 50,000 IRF |
| 5 | 1,000 | 150,000 IRF |
| 6 (Max) | 2,000 | 500,000 IRF or 2,000 Robux |

### 3.2 Private Island Storage

**Storage Warehouse on Private Island:**

```lua
function WarehouseService:CreateWarehouse(player)
    local warehouse = {
        OwnerId = player.UserId,
        Location = player.IslandId,
        Capacity = 200, -- Base capacity
        
        Sections = {
            Farming = {Capacity = 50, Items = {}},
            Mining = {Capacity = 50, Items = {}},
            Fishing = {Capacity = 50, Items = {}},
            Crafting = {Capacity = 50, Items = {}},
            General = {Capacity = 100, Items = {}}
        },
        
        AutoSort = true,
        AutoDeposit = true -- Automatically store items when on island
    }
    
    return warehouse
end
```

**Warehouse Benefits:**
- Connects to Market Stall (auto-restock)
- Connects to Crafting Stations (auto-pull materials)
- Connects to Farm Plots (store harvests)
- Connects to Familiar Feeding (auto-feed from storage)

**Smart Storage:**
```lua
function WarehouseService:AutoDeposit(player)
    if not IsOnPrivateIsland(player) then return end
    
    local warehouse = GetWarehouse(player.IslandId)
    
    -- Scan inventory for items that should be stored
    for _, item in ipairs(player.Inventory.Items) do
        local itemData = ItemDatabase[item.ItemId]
        
        -- Don't auto-store equipped gear or quest items
        if not IsEquipped(item) and not itemData.QuestItem then
            -- Determine correct section
            local section = DetermineSection(itemData.Category)
            
            -- Move to warehouse
            AddToWarehouse(warehouse, section, item)
            RemoveFromInventory(player, item)
        end
    end
    
    NotificationService:Send(player, "Items auto-deposited to warehouse")
end
```

### 3.3 Material Bank (Crafting System)

**Separate storage just for crafting materials:**

**Purpose:** 
- Doesn't take inventory space
- Automatically accessible when crafting
- Prevents "Where did I put that Iron Ore?" syndrome

```lua
MaterialBank = {
    PlayerId = 12345,
    
    Materials = {
        -- Each material type, unlimited quantity
        ["MAT_IRON_ORE"] = 543,
        ["MAT_COPPER_ORE"] = 892,
        ["MAT_COAL"] = 234,
        ["GEM_RUBY"] = 23,
        -- ... all materials
    },
    
    TotalTypes = 87, -- Different material types stored
    TotalQuantity = 15432 -- Total items
}

function CraftingService:CheckMaterials(player, recipeId)
    local recipe = RecipeDatabase[recipeId]
    
    for _, material in ipairs(recipe.Materials) do
        -- Check inventory first
        local invCount = InventoryService:CountItem(player, material.ItemId)
        
        -- Check material bank second
        local bankCount = MaterialBank[player.UserId][material.ItemId] or 0
        
        local totalCount = invCount + bankCount
        
        if totalCount < material.Quantity then
            return false, "Not enough " .. material.Name
        end
    end
    
    return true
end
```

**Material Bank Access:**
- Unlocked at Level 20
- Costs 10,000 IRF or 400 Robux
- Stores up to 999 of each material type
- Automatically pulls when crafting
- Can manually deposit/withdraw

### 3.4 Familiar Barn

**Storage for tamed creatures:**

See [GDD_Systems_Taming.md](GDD_Systems_Taming.md)

- Base capacity: 20 familiars
- Expandable to 100 familiars
- Display up to 10 on island simultaneously
- Rest when not active (happiness maintenance)

---

## 4. Sorting & Organization

### 4.1 Auto-Sort Functions

**One-click organization:**

```lua
function InventoryService:SortInventory(player, sortMode)
    local items = player.Inventory.Items
    
    if sortMode == "ByType" then
        -- Group by category (Equipment, Materials, Consumables)
        table.sort(items, function(a, b)
            local catA = ItemDatabase[a.ItemId].Category
            local catB = ItemDatabase[b.ItemId].Category
            return catA < catB
        end)
        
    elseif sortMode == "ByRarity" then
        -- Sort by rarity (Common → Mythic)
        table.sort(items, function(a, b)
            return GetRarityValue(a) > GetRarityValue(b)
        end)
        
    elseif sortMode == "ByValue" then
        -- Sort by sell value (expensive first)
        table.sort(items, function(a, b)
            return GetItemValue(a) > GetItemValue(b)
        end)
        
    elseif sortMode == "ByName" then
        -- Alphabetical
        table.sort(items, function(a, b)
            return ItemDatabase[a.ItemId].Name < ItemDatabase[b.ItemId].Name
        end)
    end
    
    -- Reassign slots
    for i, item in ipairs(items) do
        item.Slot = i
    end
    
    -- Update client
    RemoteEvents.InventoryUpdate:FireClient(player, items)
end
```

**Sort options in UI:**
- Sort by Type (default)
- Sort by Rarity
- Sort by Value
- Sort by Name
- Sort by Recently Acquired

### 4.2 Filters

**Show/hide categories:**

```
╔══════════════════════════════════════╗
║  INVENTORY (45/50)                   ║
╠══════════════════════════════════════╣
║  [All] [⚔️Equipment] [📦Materials]    ║
║  [🧪Consumables] [❓Misc]             ║
╠══════════════════════════════════════╣
║  Search: [________________] 🔍       ║
╠══════════════════════════════════════╣
║  [Iron Sword] [Iron Ore x50]         ║
║  [Health Potion x10] [Ruby x5]       ║
║  ...                                 ║
╚══════════════════════════════════════╝
```

### 4.3 Custom Organization

**Player-defined categories:**

```lua
function InventoryService:CreateCustomTab(player, tabName, filter)
    local tab = {
        Name = tabName,
        Filter = filter, -- Lua function that returns true for matching items
        Icon = "Custom",
        Items = {}
    }
    
    -- Example: "Boss Loot" tab
    tab.Filter = function(item)
        return item.Source == "Boss" or item.Rarity >= "Epic"
    end
    
    table.insert(player.CustomTabs, tab)
end
```

**Example custom tabs:**
- "Boss Loot" (Epic+ from dungeons)
- "Trading Stock" (items marked for sale)
- "Crafting Materials" (for current project)
- "Familiar Food" (crops and fish for feeding)

---

## 5. Item Types & Stacking

### 5.1 Stack Sizes

**Different items stack differently:**

| Category | Stack Size | Reason |
|----------|------------|--------|
| Materials (common) | 999 | Bulk resources |
| Materials (rare+) | 100 | Valuable, less common |
| Consumables | 50 | Balance (don't hoard infinite potions) |
| Equipment | 1 | Each has unique stats/durability |
| Quest Items | 1 | Unique items |
| Currency Items | 9,999 | Event tokens, special currencies |

```lua
function InventoryService:CanStack(item1, item2)
    -- Must be same item type
    if item1.ItemId ~= item2.ItemId then
        return false
    end
    
    -- Equipment never stacks (unique stats)
    if item1.Category == "Equipment" then
        return false
    end
    
    -- Check stack limit
    local maxStack = ItemDatabase[item1.ItemId].MaxStack or 1
    if item1.Quantity >= maxStack then
        return false
    end
    
    return true
end
```

### 5.2 Unique Items

**Items that don't stack:**
- All equipment (each has durability, enchantments, quality)
- Familiars (each has unique stats, bond level)
- Quest items (story-specific)
- Player-crafted items (signature items)

### 5.3 Item Binding

**Bind on Pickup (BoP):**
- Cannot trade or sell
- Quest rewards (prevents selling quest progression)
- Achievement rewards

**Bind on Equip (BoE):**
- Can trade until equipped
- Once equipped, becomes bound
- Rare dungeon drops (tradeable to group initially)

```lua
function InventoryService:EquipItem(player, itemSlot)
    local item = player.Inventory.Items[itemSlot]
    
    -- Check if Bind on Equip
    if item.BindType == "BoE" and not item.IsBound then
        -- Show confirmation
        local confirm = PromptBindWarning(player, item)
        if not confirm then return false end
        
        -- Bind item
        item.IsBound = true
        item.BoundTo = player.UserId
    end
    
    -- Equip
    EquipToSlot(player, item)
end
```

---

## 6. Quick Access Systems

### 6.1 Hotbar

**Fast access to consumables and abilities:**

```
Bottom of screen:
┌────┬────┬────┬────┬────┬────┬────┬────┬────┬────┐
│ 1  │ 2  │ 3  │ 4  │ 5  │ 6  │ 7  │ 8  │ 9  │ 0  │
├────┼────┼────┼────┼────┼────┼────┼────┼────┼────┤
│ ❤️ │ 🧪 │ 🍖 │ ⚔️ │ 🐺 │    │    │    │    │    │
│ HP │Str │Buf │Swd │Pet │    │    │    │    │    │
└────┴────┴────┴────┴────┴────┴────┴────┴────┴────┘
```

**Hotbar slots:**
- 10 slots (keyboard 1-0 keys)
- Drag items from inventory
- Right-click item in inventory → "Add to Hotbar"
- Press number key to use/activate

**Auto-Refill:**
```lua
function HotbarService:UseSlot(player, slotNumber)
    local hotbarItem = player.Hotbar[slotNumber]
    
    if not hotbarItem then return end
    
    -- Use item
    UseConsumable(player, hotbarItem.ItemId)
    
    -- Remove from inventory
    InventoryService:RemoveItem(player, hotbarItem.ItemId, 1)
    
    -- Check if hotbar slot empty
    local remaining = InventoryService:CountItem(player, hotbarItem.ItemId)
    if remaining == 0 then
        -- Try to refill from storage
        if player.Settings.AutoRefillHotbar then
            local fromStorage = GetFromWarehouse(player, hotbarItem.ItemId, 10)
            if fromStorage > 0 then
                NotificationService:Send(player, "Hotbar refilled from storage")
            end
        end
    end
end
```

### 6.2 Quick Deposit/Withdraw

**Keyboard shortcuts:**
- **Shift + Click:** Quick deposit to bank
- **Ctrl + Click:** Quick withdraw from bank
- **Alt + Click:** Mark for sale

```lua
function InventoryService:QuickDeposit(player, itemSlot)
    local item = player.Inventory.Items[itemSlot]
    
    -- Check if at bank or on private island
    if not NearBank(player) and not OnPrivateIsland(player) then
        return false, "Not near storage"
    end
    
    -- Deposit entire stack
    local storage = GetAvailableStorage(player)
    AddToStorage(storage, item)
    RemoveFromInventory(player, itemSlot)
    
    -- Play sound
    SoundService:PlaySound(player, "ItemDeposit")
    
    return true
end
```

### 6.3 Loadouts

**Save equipment sets:**

```lua
EquipmentLoadout = {
    Name = "Mining Build",
    Weapon = "TOOL_MITHRIL_PICKAXE",
    Helmet = "ARM_MINING_HELMET",
    Chestplate = "ARM_MINING_CHEST",
    Leggings = "ARM_MINING_LEGS",
    Accessory1 = "ACC_ORE_DETECTION_RING",
    Accessory2 = "ACC_MINING_SPEED_NECKLACE",
    Familiar = "FAMILIAR_MINING_MOLE"
}

function LoadoutService:ApplyLoadout(player, loadoutName)
    local loadout = player.Loadouts[loadoutName]
    
    -- Unequip current gear
    UnequipAll(player)
    
    -- Equip new gear
    for slot, itemId in pairs(loadout) do
        EquipFromInventory(player, itemId, slot)
    end
    
    NotificationService:Send(player, "Loadout equipped: " .. loadoutName)
end
```

**Preset loadouts:**
- Mining Build (pickaxe, mining armor, ore detection)
- Fishing Build (fishing rod, fishing gear, fish finder)
- Combat Build (weapon, armor, combat familiar)
- Farming Build (hoe, farming tools, crop growth boosts)

**Quick-swap:** One button to switch entire outfit

---

## 7. System Integration

### 7.1 Mining → Storage

```lua
-- When mining ore
function MiningService:OnOreMined(player, oreType, quantity)
    -- Try to add to inventory first
    local added = InventoryService:AddItem(player, oreType, quantity)
    
    if not added then
        -- Inventory full - try material bank
        if HasMaterialBank(player) then
            MaterialBank:AddMaterial(player, oreType, quantity)
            NotificationService:Send(player, "Ore sent to Material Bank (inventory full)")
        else
            -- Drop on ground as last resort
            DropItem(player.Position, oreType, quantity)
            NotificationService:Send(player, "Inventory full! Ore dropped on ground.")
        end
    end
end
```

### 7.2 Farming → Storage

```lua
-- When harvesting crops
function FarmingService:HarvestCrop(player, plotId)
    local plot = GetFarmPlot(plotId)
    local harvest = CalculateHarvest(plot)
    
    -- If on private island with warehouse
    if OnPrivateIsland(player) and player.Warehouse.AutoDeposit then
        -- Send directly to warehouse
        AddToWarehouse(player.Warehouse, "Farming", harvest)
        NotificationService:Send(player, string.format("Harvested %dx %s → Warehouse", 
            harvest.Quantity, harvest.Name))
    else
        -- Normal inventory
        InventoryService:AddItem(player, harvest.ItemId, harvest.Quantity)
    end
end
```

### 7.3 Crafting → Storage

```lua
-- When crafting, auto-pull from multiple sources
function CraftingService:GetMaterialsForCraft(player, recipe)
    local materialsNeeded = recipe.Materials
    local materialsGathered = {}
    
    for _, material in ipairs(materialsNeeded) do
        local needed = material.Quantity
        local gathered = 0
        
        -- Priority 1: Inventory
        local fromInv = InventoryService:CountItem(player, material.ItemId)
        local takeFromInv = math.min(fromInv, needed)
        gathered = gathered + takeFromInv
        
        -- Priority 2: Material Bank
        if gathered < needed and HasMaterialBank(player) then
            local fromBank = MaterialBank:GetCount(player, material.ItemId)
            local takeFromBank = math.min(fromBank, needed - gathered)
            gathered = gathered + takeFromBank
        end
        
        -- Priority 3: Warehouse (if on island)
        if gathered < needed and OnPrivateIsland(player) then
            local fromWarehouse = Warehouse:GetCount(player, material.ItemId)
            local takeFromWarehouse = math.min(fromWarehouse, needed - gathered)
            gathered = gathered + takeFromWarehouse
        end
        
        if gathered < needed then
            return false, "Not enough " .. material.Name
        end
        
        table.insert(materialsGathered, {ItemId = material.ItemId, Quantity = gathered})
    end
    
    -- Remove materials from all sources
    for _, material in ipairs(materialsGathered) do
        RemoveFromAllSources(player, material.ItemId, material.Quantity)
    end
    
    return true, materialsGathered
end
```

### 7.4 Trading → Storage

```lua
-- After buying from market
function MarketService:OnPurchaseComplete(buyer, items)
    for _, item in ipairs(items) do
        local added = InventoryService:AddItem(buyer, item.ItemId, item.Quantity)
        
        if not added then
            -- Send to mail system
            MailService:SendItem(buyer.UserId, item, "Market Purchase")
            NotificationService:Send(buyer, "Purchase sent to mail (inventory full)")
        end
    end
end
```

---

## 8. Inventory Upgrades

### 8.1 Backpack Upgrades

**Increase carrying capacity:**

| Tier | Slots | Cost |
|------|-------|------|
| 1 (Default) | 50 | Free |
| 2 | 60 | 2,000 IRF |
| 3 | 75 | 8,000 IRF |
| 4 | 100 | 25,000 IRF |
| 5 | 150 | 80,000 IRF or 800 Robux |

**Purchased from:** Bag Merchant NPC in towns

### 8.2 Organization Tools

**Premium features (Robux):**

**Auto-Sort Pro (200 Robux):**
- Automatic sorting on pickup
- Custom rules (e.g., "Always sort ores to top")
- Persistent settings

**Material Vacuum (400 Robux):**
- Automatically picks up loot within 20m radius
- Brings items to you (no need to walk over)
- Works for party members too

**Infinite Durability Bag (800 Robux):**
- Items in bag don't degrade
- Good for storing equipment long-term
- 20 special slots

---

## 9. Technical Implementation

### 9.1 Data Structure

```lua
-- Player Inventory (DataStore)
PlayerInventoryData = {
    PlayerId = 12345,
    InventorySlots = 50,
    
    Items = {
        {
            Slot = 1,
            ItemId = "WPN_IRON_SWORD",
            Quantity = 1,
            ItemData = {
                Durability = 80,
                MaxDurability = 100,
                Quality = "Good",
                Enchantments = {"FireDamage_10"},
                CraftedBy = "PlayerName",
                IsBound = false
            }
        },
        {
            Slot = 2,
            ItemId = "MAT_IRON_ORE",
            Quantity = 50
        }
        -- ...
    },
    
    EquippedGear = {...},
    Hotbar = {...},
    Loadouts = {...}
}
```

### 9.2 Optimization

**Inventory updates are expensive - optimize:**

```lua
-- Don't send full inventory every change
-- Send delta updates
function InventoryService:SendInventoryDelta(player, changedSlots)
    local delta = {}
    
    for _, slot in ipairs(changedSlots) do
        delta[slot] = player.Inventory.Items[slot]
    end
    
    RemoteEvents.InventoryDelta:FireClient(player, delta)
end

-- Batch updates during combat
local PendingUpdates = {}

function InventoryService:QueueUpdate(player, slot)
    if not PendingUpdates[player.UserId] then
        PendingUpdates[player.UserId] = {}
    end
    
    table.insert(PendingUpdates[player.UserId], slot)
end

-- Flush every second
RunService.Heartbeat:Connect(function()
    wait(1)
    
    for playerId, slots in pairs(PendingUpdates) do
        local player = Players:GetPlayerByUserId(playerId)
        if player then
            SendInventoryDelta(player, slots)
        end
    end
    
    PendingUpdates = {}
end)
```

### 9.3 Saving & Loading

```lua
function InventoryService:SaveInventory(player)
    local data = {
        Items = SerializeItems(player.Inventory.Items),
        EquippedGear = SerializeEquipment(player.EquippedGear),
        Hotbar = SerializeHotbar(player.Hotbar),
        Capacity = player.InventoryCapacity
    }
    
    local success, err = pcall(function()
        InventoryDataStore:SetAsync("Inventory_" .. player.UserId, data)
    end)
    
    if not success then
        warn("Failed to save inventory:", err)
        -- Queue for retry
    end
end

-- Auto-save every 5 minutes
game.Players.PlayerAdded:Connect(function(player)
    while player.Parent do
        wait(300) -- 5 minutes
        InventoryService:SaveInventory(player)
    end
end)

-- Save on leave
game.Players.PlayerRemoving:Connect(function(player)
    InventoryService:SaveInventory(player)
end)
```

---

## 10. UI/UX Design

### 10.1 Inventory Window

```
╔════════════════════════════════════════════════════════════╗
║  INVENTORY (45/50)                    [Sort ▼] [Filter ▼]  ║
╠════════════════════════════════════════════════════════════╣
║ ┌──────────────────────────┐  ┌──────────────────────────┐ ║
║ │ EQUIPPED GEAR            │  │ INVENTORY                │ ║
║ │                          │  │                          │ ║
║ │  [Helmet]                │  │ [Iron Ore x50]           │ ║
║ │  [Chestplate]            │  │ [Health Pot x10]         │ ║
║ │  [Leggings]              │  │ [Ruby x5]                │ ║
║ │  [Weapon: Iron Sword]    │  │ [Wooden Planks x30]      │ ║
║ │  [Accessory 1]           │  │ [Coal x20]               │ ║
║ │  [Accessory 2]           │  │ ...                      │ ║
║ │  [Familiar: Fire Wolf]   │  │ ...                      │ ║
║ │                          │  │ ...                      │ ║
║ └──────────────────────────┘  └──────────────────────────┘ ║
║                                                            ║
║ Selected: Iron Ore x50                                     ║
║ Value: 500 IRF (10 IRF each)                               ║
║ [Use] [Drop] [Sell to NPC] [List on Market]                ║
╚════════════════════════════════════════════════════════════╝
```

### 10.2 Drag & Drop

```lua
-- Drag and drop items
function InventoryUI:OnItemDragged(draggedItem, targetSlot)
    local player = LocalPlayer
    
    if targetSlot.Type == "InventorySlot" then
        -- Swap items
        RemoteEvents.SwapItems:FireServer(draggedItem.Slot, targetSlot.Slot)
        
    elseif targetSlot.Type == "EquipmentSlot" then
        -- Equip item
        RemoteEvents.EquipItem:FireServer(draggedItem.Slot, targetSlot.SlotType)
        
    elseif targetSlot.Type == "HotbarSlot" then
        -- Add to hotbar
        RemoteEvents.SetHotbar:FireServer(draggedItem.ItemId, targetSlot.SlotNumber)
        
    elseif targetSlot.Type == "TrashBin" then
        -- Delete item (with confirmation)
        ConfirmDelete(draggedItem)
    end
end
```

---

## Implementation Checklist

### Phase 1: Core System (Month 3)
- [ ] Basic inventory (50 slots)
- [ ] Equipment slots
- [ ] Item stacking logic
- [ ] Save/load system
- [ ] Basic UI (grid view)

### Phase 2: Storage (Month 4)
- [ ] Bank vault (town storage)
- [ ] Private island warehouse
- [ ] Material bank (crafting)
- [ ] Auto-deposit/withdraw
- [ ] Storage tabs and organization

### Phase 3: Quality of Life (Month 5)
- [ ] Hotbar system (10 slots)
- [ ] Auto-sort functions
- [ ] Search and filters
- [ ] Quick actions (Shift+Click)
- [ ] Drag-and-drop UI

### Phase 4: Advanced Features (Month 6)
- [ ] Equipment loadouts
- [ ] Custom tabs
- [ ] Material vacuum (premium)
- [ ] Auto-refill hotbar
- [ ] Weight system (optional)

### Phase 5: Integration (Month 7)
- [ ] Connect to all systems (Mining, Farming, etc.)
- [ ] Market integration (auto-list)
- [ ] Crafting material pull
- [ ] Mail system for overflow
- [ ] Performance optimization

---

## Related Documentation
- All system documents - Items generated
- [GDD_Systems_Trading.md](GDD_Systems_Trading.md) - Selling from inventory
- [GDD_Systems_Crafting.md](GDD_Systems_Crafting.md) - Material storage
- [Database_*.md](Database_*.md) - All items that need storage

---

**Document End - Storage & Inventory System**  
*Seamless organization that connects every game system*
