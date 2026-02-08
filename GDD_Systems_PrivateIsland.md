# IRIFA: Realms of Harvest & Adventure
## Game Design Document - Private Island System

---

### Document Information
**Document Type:** System Design  
**System:** Private Island & Housing  
**Version:** 1.0  
**Last Updated:** February 8, 2026  
**Status:** Implementation Ready

---

## Table of Contents
1. [Overview](#1-overview)
2. [Island Types & Expansion](#2-island-types--expansion)
3. [Building System](#3-building-system)
4. [Decoration & Aesthetics](#4-decoration--aesthetics)
5. [Functional Structures](#5-functional-structures)
6. [Aesthetic Score System](#6-aesthetic-score-system)
7. [Visitor System](#7-visitor-system)
8. [Island Activities](#8-island-activities)
9. [Permissions & Privacy](#9-permissions--privacy)
10. [Technical Implementation](#10-technical-implementation)

---

## 1. Overview

### 1.1 System Purpose
Private Island provides players with:
- Personal customizable space
- Housing for farming, crafting, familiars
- Creative expression through building
- Social hub for visitors
- Prestige through aesthetic scores
- Passive income from visitors

### 1.2 Core Design Pillars
- **Personalization:** Unique player expression
- **Functionality:** Not just decoration, actual utility
- **Progression:** Unlock and expand over time
- **Social:** Showcase to community
- **Economy:** Market for decorations and blueprints

### 1.3 Island Acquisition

#### Starting Island (Free)
- **Size:** 50×50 studs (small)
- **Unlocked:** Complete tutorial (Level 5)
- **Features:**
  - Basic house (1 room)
  - 5 farm plots
  - Familiar barn (20 capacity)
  - Teleport waypoint

#### Island Location
- Instanced zone (separate from main world)
- Access via:
  - Teleport from any waypoint
  - "Home" button in menu
  - Direct visit from friend list

---

## 2. Island Types & Expansion

### 2.1 Island Biomes

Players choose island biome (visual theme):

#### Tropical Island (Default)
- **Theme:** Beach, palm trees, ocean view
- **Weather:** Sunny, occasional rain
- **Unique Decor:** Tiki torches, beach chairs, surf boards

#### Forest Island
- **Cost:** 10,000 IRF or 300 Robux
- **Theme:** Dense forest, streams, woodland
- **Weather:** Misty mornings, clear days
- **Unique Decor:** Tree houses, wooden bridges, campfires

#### Mountain Peak Island
- **Cost:** 15,000 IRF or 400 Robux
- **Theme:** Rocky cliffs, waterfalls, caves
- **Weather:** Variable, snow possible
- **Unique Decor:** Stone walls, mining outposts, cable cars

#### Desert Oasis Island
- **Cost:** 12,000 IRF or 350 Robux
- **Theme:** Sand dunes, oasis pool, pyramids
- **Weather:** Hot, clear, sandstorms (rare)
- **Unique Decor:** Egyptian statues, cacti, palm oasis

#### Mystical Island
- **Cost:** 25,000 IRF or 800 Robux
- **Theme:** Floating crystals, magical effects, ethereal
- **Weather:** Aurora skies, magical mist
- **Unique Decor:** Arcane symbols, floating platforms, magic crystals

**Biome Switching:**
- Can change biome once per month
- Cost: 5,000 IRF or 200 Robux
- All placed decorations remain

### 2.2 Island Expansion Tiers

| Tier | Size | Farm Plots | Cost | Level Req |
|------|------|------------|------|-----------|
| 1 | 50×50 | 5 | Free | 5 |
| 2 | 75×75 | 10 | 10,000 IRF | 15 |
| 3 | 100×100 | 20 | 30,000 IRF | 25 |
| 4 | 150×150 | 40 | 80,000 IRF | 35 |
| 5 | 200×200 | 60 | 200,000 IRF | 45 |
| 6 (Max) | 300×300 | 100 | 500,000 IRF or 2,000 Robux | 50 |

**Expansion Benefits:**
- More space for decorations
- Additional farm plots
- Unlock special structure slots
- Higher visitor capacity

---

## 3. Building System

### 3.1 Building Mode

#### Accessing Build Mode
- Press "B" key or click "Edit Island" button
- Enters free-cam mode with placement UI
- Pauses time, weather effects

#### Placement Mechanics
```lua
function BuildingService:PlaceObject(player, objectId, position, rotation)
    local objectData = DecorationDatabase[objectId]
    
    -- Validate ownership
    if not PlayerDataService:OwnsItem(player, objectId) then
        return false, "You don't own this decoration"
    end
    
    -- Check build limit
    local currentObjects = IslandService:GetObjectCount(player.IslandId)
    local maxObjects = GetMaxObjectsForTier(player.IslandTier)
    
    if currentObjects >= maxObjects then
        return false, "Object limit reached. Upgrade island to place more."
    end
    
    -- Collision check
    if CheckCollision(position, objectData.Size) then
        return false, "Cannot place here - overlapping with another object"
    end
    
    -- Grid snapping (optional)
    if player.Settings.GridSnap then
        position = SnapToGrid(position, 2) -- 2 stud grid
    end
    
    -- Create instance
    local instance = {
        InstanceId = HttpService:GenerateGUID(false),
        ObjectId = objectId,
        Position = position,
        Rotation = rotation,
        PlacedAt = os.time()
    }
    
    -- Save to island data
    IslandService:AddObject(player.IslandId, instance)
    
    -- Spawn in world
    SpawnDecorationModel(player.IslandId, instance)
    
    return true
end
```

#### Grid System
- **Free Placement:** Place anywhere (advanced users)
- **Grid Snapping:** Snap to 2-stud grid (easier alignment)
- **Rotation:** 45° increments or free rotation
- **Height:** Adjustable elevation (0-20 studs)

### 3.2 Object Limits

| Island Tier | Max Objects | Max Structures | Max Familiars Displayed |
|-------------|-------------|----------------|-------------------------|
| 1 | 50 | 5 | 5 |
| 2 | 100 | 10 | 10 |
| 3 | 200 | 15 | 15 |
| 4 | 400 | 20 | 20 |
| 5 | 700 | 30 | 30 |
| 6 | 1,000 | 50 | 50 |

**Object Limit Expansion:**
- +100 objects: 1,000 IRF or 50 Robux
- Max 2,000 objects total (performance limit)

---

## 4. Decoration & Aesthetics

### 4.1 Decoration Categories

#### Furniture (Indoor)

**Seating:**
- Wooden Chair: 100 IRF
- Luxury Armchair: 2,000 IRF
- Throne: 50,000 IRF (prestige item)

**Tables:**
- Simple Table: 150 IRF
- Dining Table: 1,000 IRF
- Enchanted Workbench: 5,000 IRF

**Storage:**
- Small Chest: 500 IRF (+10 storage slots)
- Large Wardrobe: 3,000 IRF (+30 storage slots)
- Vault: 25,000 IRF (+100 storage, secure)

**Lighting:**
- Torch: 50 IRF
- Chandelier: 5,000 IRF
- Crystal Lamp: 10,000 IRF (magical glow)

#### Outdoor Decorations

**Nature:**
- Flower Pots: 100 IRF each
- Trees: 500-2,000 IRF (various types)
- Bushes: 200 IRF
- Rocks: 300 IRF

**Pathways:**
- Stone Path (per tile): 50 IRF
- Brick Path: 100 IRF
- Magical Path: 500 IRF (glows at night)

**Water Features:**
- Fountain: 10,000 IRF (aesthetic score bonus)
- Pond: 5,000 IRF (can place fish)
- Waterfall: 20,000 IRF (premium)

**Lighting:**
- Lamp Post: 500 IRF
- Garden Lights: 300 IRF
- Fairy Lights: 1,000 IRF (string lights)

#### Premium Decorations (Robux)

**Animated Decorations:**
- Animated Dragon Statue: 400 Robux (breathes fire every 30 sec)
- Dancing Fountain: 300 Robux (water choreography)
- Floating Crystal: 250 Robux (orbits slowly)

**Particle Effect Decorations:**
- Rainbow Generator: 500 Robux (creates rainbow)
- Firework Launcher: 400 Robux (shoots fireworks)
- Sparkle Tree: 350 Robux (sparkles constantly)

### 4.2 Limited Edition Decorations

#### Seasonal Items

**Winter Event:**
- Snowman: 500 Event Tokens
- Ice Sculpture: 1,000 Event Tokens
- Christmas Tree: 1,500 Event Tokens (lights up at night)

**Halloween Event:**
- Jack-o'-lanterns: 300 Event Tokens
- Haunted Tree: 800 Event Tokens
- Ghost Decoration: 600 Event Tokens (floats and phases)

**Summer Event:**
- Beach Umbrella: 400 Event Tokens
- Surf Board: 500 Event Tokens
- BBQ Grill: 700 Event Tokens

#### Achievement Decorations

Unlock through gameplay:
- **Dragon Slayer Statue:** Defeat Elder Dragon (prestige)
- **Trophy Case:** Collect 100 achievements
- **Golden Fountain:** Earn 1,000,000 IRF total

---

## 5. Functional Structures

### 5.1 Resource Generation

#### Farm Plots
See [GDD_Systems_Farming.md](GDD_Systems_Farming.md)
- Place crops
- Automated watering with sprinklers
- Connect to storage

#### Fishing Dock
- **Cost:** 5,000 IRF
- **Function:** Fish from private island pond
- **Catches:** Lower-tier fish, relaxing activity
- **Bonus:** +10% fishing XP when on island

### 5.2 Crafting Stations

#### Personal Forge (Blacksmithing)
- **Cost:** 15,000 IRF or 500 Robux
- **Function:** Craft equipment at home
- **Benefit:** No queue, instant access
- **Upgrades:** Speed +20% (10,000 IRF)

#### Alchemy Lab
- **Cost:** 12,000 IRF or 400 Robux
- **Function:** Brew potions at home
- **Benefit:** Batch crafting (×5 at once)

#### Cooking Kitchen
- **Cost:** 8,000 IRF or 300 Robux
- **Function:** Cook food, buffs
- **Special:** Can cook for visitors (social activity)

### 5.3 Utility Structures

#### Teleport Waypoint
- **Cost:** 10,000 IRF
- **Function:** Fast travel to any unlocked location
- **Benefit:** Skip walking to island entrance

#### Storage Warehouse
- **Cost:** 20,000 IRF or 600 Robux
- **Function:** +200 inventory storage
- **Upgrades:** Additional +100 per 5,000 IRF

#### Familiar Habitat (Various)
See [GDD_Systems_Taming.md](GDD_Systems_Taming.md)
- Forest Habitat: 10,000 IRF
- Aquatic Habitat: 15,000 IRF
- Volcanic Habitat: 25,000 IRF

#### Market Stall
- **Cost:** 15,000 IRF
- **Function:** Sell items to visitors
- **Revenue:** Automated passive income
- **Stock:** Up to 20 item types, auto-restocks from storage

---

## 6. Aesthetic Score System

### 6.1 Score Calculation

Each island has an Aesthetic Score (0-10,000+):

```lua
function AestheticService:CalculateScore(islandId)
    local island = IslandService:GetIsland(islandId)
    local score = 0
    
    -- Base score from decorations
    for _, object in ipairs(island.Objects) do
        local objectData = DecorationDatabase[object.ObjectId]
        score = score + objectData.AestheticValue
    end
    
    -- Theme coherence bonus
    local themeBonus = CalculateThemeBonus(island)
    score = score * (1 + themeBonus)
    
    -- Variety bonus (different decoration types)
    local varietyBonus = CalculateVarietyBonus(island)
    score = score + varietyBonus
    
    -- Symmetry bonus (balanced placement)
    local symmetryBonus = CalculateSymmetryBonus(island)
    score = score + symmetryBonus
    
    -- Visitor rating bonus
    local visitorBonus = island.AverageVisitorRating * 100
    score = score + visitorBonus
    
    return math.floor(score)
end
```

### 6.2 Aesthetic Tiers & Rewards

| Score Range | Tier | Rewards |
|-------------|------|---------|
| 0-1,000 | Novice | None |
| 1,001-3,000 | Apprentice | Title: "Decorator" |
| 3,001-6,000 | Skilled | Title: "Designer", +5% visitor tips |
| 6,001-10,000 | Master | Title: "Architect", +10% visitor tips, Featured listing |
| 10,001-15,000 | Grandmaster | Title: "Island Artisan", +20% visitor tips, Weekly spotlight |
| 15,000+ | Legendary | Title: "Paradise Creator", +30% visitor tips, Exclusive decoration access |

### 6.3 Featured Islands

Top 10 highest-scoring islands:
- Featured on "Discover Islands" page
- Increased visitor traffic
- Bragging rights
- Special badge on profile

---

## 7. Visitor System

### 7.1 Visiting Mechanics

#### How to Visit
Players can visit islands via:
1. **Friend List:** Click friend → "Visit Island"
2. **Discovery Page:** Browse featured/popular islands
3. **Direct Code:** Enter 6-digit island code
4. **Random Visit:** Teleport to random public island

#### Visitor Limits
- **Private Mode:** 0 visitors (owner only)
- **Friends Only:** Up to 10 friends simultaneously
- **Public Mode:** Up to 30 visitors (scales with island tier)

### 7.2 Visitor Activities

#### Exploration
- Walk around island
- View decorations
- Inspect placed items (see info)
- Take screenshots

#### Social Interaction
- Chat with owner and other visitors
- Emotes and poses
- Trade (if enabled by owner)
- Play mini-games (if available)

#### Economic Interaction
- **Buy from Market Stall:** Purchase items owner is selling
- **Leave Tips:** Donate IRF to island owner (thank you for nice island)
- **Commission Requests:** Request specific crafted items

#### Rating System
After visiting, rate island 1-5 stars:
- 5 stars: Amazing! (+100 aesthetic score)
- 4 stars: Very good (+50)
- 3 stars: Good (+25)
- 2 stars: Okay (+10)
- 1 star: Needs work (+0)

**Abuse Prevention:**
- Can only rate each island once per day
- Ratings from friends count less (prevent farming)
- System detects mass low-rating (trolling protection)

### 7.3 Visitor Benefits for Owner

**Passive Income:**
- Tips: Average 50-200 IRF per satisfied visitor
- Market Sales: Automated income from stall
- Commission Fees: 10% of crafted item value

**Social Currency:**
- Likes: Accumulate likes (similar to followers)
- Featured Chance: High likes = higher discovery placement
- Reputation: "Popular Island" badge at 1,000 likes

---

## 8. Island Activities

### 8.1 Mini-Games

Owners can place mini-game structures:

#### Obstacle Course
- **Cost:** 10,000 IRF
- **Function:** Timed parkour challenge
- **Rewards:** Fastest completion wins daily prize (set by owner)
- **Revenue:** Owner can charge entry fee (100-1,000 IRF)

#### Fishing Tournament
- **Cost:** 5,000 IRF
- **Function:** Compete to catch biggest fish
- **Duration:** Owner sets (15-60 min)
- **Prizes:** Automated prize distribution

#### Scavenger Hunt
- **Cost:** 8,000 IRF
- **Function:** Hide objects, visitors find them
- **Prizes:** Owner-defined rewards

### 8.2 Events & Parties

#### Island Parties
Owner can host events:
- **Party Announcement:** Send to friends
- **Event Duration:** 1-4 hours
- **Special Features:**
  - Music player (choose soundtrack)
  - Fireworks launcher (party effects)
  - Food buffet (place feast, visitors get buffs)
  - Dance floor (social hub)

**Party Benefits:**
- +50% visitor tips during event
- Party achievement progress
- Featured in "Live Events" page

---

## 9. Permissions & Privacy

### 9.1 Permission Tiers

#### Owner (You)
- Full edit access
- Place/remove objects
- Change settings
- Manage visitors

#### Co-Owner (Trusted friends)
- **Max:** 3 co-owners
- Can edit island (place decorations)
- Cannot delete owner's objects
- Cannot change permissions

#### Builder (Limited)
- **Max:** 10 builders
- Can place decorations only
- Cannot delete anything
- Good for collaborative projects

#### Visitor (Public)
- Can walk around
- Can view decorations
- Can interact with mini-games
- Cannot modify anything

### 9.2 Privacy Settings

#### Island Visibility
- **Private:** Only you can visit
- **Friends Only:** Only friends can visit
- **Public:** Anyone can visit
- **Featured:** Public + listed in discovery

#### Advanced Settings
- **Allow Trading:** Visitors can trade with owner
- **Allow Market:** Enable market stall sales
- **Allow PvP:** Enable friendly combat (if both agree)
- **Block List:** Block specific users from visiting

---

## 10. Technical Implementation

### 10.1 Island Data Structure

```lua
IslandData = {
    IslandId = "UUID",
    OwnerId = 12345, -- Player UserId
    Biome = "Tropical",
    Tier = 3,
    Size = {X = 100, Y = 100},
    
    -- Objects placed on island
    Objects = {
        {
            InstanceId = "UUID",
            ObjectId = "FURNITURE_CHAIR_01",
            Position = Vector3.new(50, 0, 50),
            Rotation = CFrame.Angles(0, math.rad(45), 0),
            PlacedAt = 1707350400
        },
        -- ... more objects
    },
    
    -- Structures
    Structures = {
        {StructureId = "FARM_PLOT", Position = Vector3.new(30, 0, 30), Crops = {}},
        {StructureId = "FORGE", Position = Vector3.new(70, 0, 70), Upgrades = {"SPEED_BOOST"}},
    },
    
    -- Settings
    Settings = {
        Visibility = "Public",
        MaxVisitors = 30,
        AllowTrading = true,
        AllowMarket = true,
        GridSnap = true
    },
    
    -- Statistics
    Stats = {
        TotalVisitors = 1543,
        AverageRating = 4.5,
        TotalLikes = 234,
        AestheticScore = 8543
    },
    
    -- Permissions
    Permissions = {
        CoOwners = {67890, 11111},
        Builders = {22222, 33333, 44444},
        BlockedUsers = {99999}
    }
}
```

### 10.2 Instancing & Loading

```lua
function IslandService:LoadIsland(islandId)
    -- Get island data from DataStore
    local islandData = IslandDataStore:GetAsync(islandId)
    
    if not islandData then
        return nil
    end
    
    -- Create island instance (separate server if large party)
    local islandPlace = ReplicatedStorage.IslandTemplates[islandData.Biome]:Clone()
    islandPlace.Parent = workspace.Islands
    
    -- Spawn all objects
    for _, objectInstance in ipairs(islandData.Objects) do
        SpawnObject(islandPlace, objectInstance)
    end
    
    -- Spawn structures
    for _, structure in ipairs(islandData.Structures) do
        SpawnStructure(islandPlace, structure)
    end
    
    return islandPlace
end

function SpawnObject(parent, objectInstance)
    local objectData = DecorationDatabase[objectInstance.ObjectId]
    local model = ReplicatedStorage.Decorations[objectData.ModelName]:Clone()
    
    model:SetPrimaryPartCFrame(CFrame.new(objectInstance.Position) * objectInstance.Rotation)
    model.Parent = parent
    
    -- Metadata
    model:SetAttribute("InstanceId", objectInstance.InstanceId)
    model:SetAttribute("ObjectId", objectInstance.ObjectId)
end
```

### 10.3 Performance Optimization

#### Level of Detail (LOD)
- Objects far from player: Use low-poly models
- Objects near player: Use high-poly models
- Dynamically swap based on distance

#### Culling
- Only render objects in player's view
- Unload distant islands (memory management)

#### Batching
- Group similar decorations into single mesh
- Reduces draw calls significantly

#### Streaming
```lua
-- Stream island content as player explores
function IslandStreamingService:UpdateStreaming(player, islandId)
    local playerPosition = player.Character.HumanoidRootPart.Position
    local island = IslandService:GetIsland(islandId)
    
    for _, object in ipairs(island.Objects) do
        local distance = (object.Position - playerPosition).Magnitude
        
        if distance < STREAM_IN_DISTANCE then
            -- Load object if not already loaded
            if not object.IsLoaded then
                SpawnObject(island.Model, object)
                object.IsLoaded = true
            end
        elseif distance > STREAM_OUT_DISTANCE then
            -- Unload object
            if object.IsLoaded then
                object.Model:Destroy()
                object.IsLoaded = false
            end
        end
    end
end
```

---

## Implementation Checklist

### Phase 1: Basic Housing (Month 5)
- [ ] Island instancing system
- [ ] Basic decoration placement (100 items)
- [ ] Grid snapping and free placement
- [ ] Save/load island data
- [ ] Island UI (edit mode, inventory)

### Phase 2: Functionality (Month 6)
- [ ] Farm plots on island
- [ ] Crafting stations placement
- [ ] Familiar habitats
- [ ] Storage structures
- [ ] Visitor system (friends only)

### Phase 3: Social Features (Month 7)
- [ ] Public visiting
- [ ] Aesthetic score calculation
- [ ] Rating system
- [ ] Discovery page (featured islands)
- [ ] Market stall (player shops)

### Phase 4: Advanced Features (Month 8)
- [ ] Mini-games (obstacle course, scavenger hunt)
- [ ] Island events and parties
- [ ] Co-owner and builder permissions
- [ ] Island biome variants (5 types)
- [ ] Premium decorations (50+ Robux items)

### Phase 5: Polish (Month 9)
- [ ] Performance optimization (LOD, streaming)
- [ ] Seasonal decorations
- [ ] Achievement decorations
- [ ] Leaderboards (top islands)
- [ ] Island customization presets

---

## Related Documentation
- [GDD_Systems_Farming.md](GDD_Systems_Farming.md) - Farm plots on island
- [GDD_Systems_Taming.md](GDD_Systems_Taming.md) - Familiar habitats
- [GDD_Systems_Crafting.md](GDD_Systems_Crafting.md) - Personal crafting stations
- [GDD_Economy.md](GDD_Economy.md) - Island-based economy

---

**Document End - Private Island System Design**  
*Player housing that combines creativity, functionality, and social interaction*
