# IRIFA: Realms of Harvest & Adventure
## Game Design Document - Weather & Time System

---

### Document Information
**Document Type:** System Design  
**System:** Weather, Day/Night Cycle, Seasonal Events  
**Version:** 1.0  
**Last Updated:** February 9, 2026  
**Status:** Implementation Ready

---

## Table of Contents
1. [Overview](#1-overview)
2. [Day/Night Cycle](#2-daynight-cycle)
3. [Weather System](#3-weather-system)
4. [Seasonal Calendar](#4-seasonal-calendar)
5. [Gameplay Effects](#5-gameplay-effects)
6. [System Integration](#6-system-integration)
7. [Visual Effects](#7-visual-effects)
8. [Player Interaction](#8-player-interaction)
9. [Technical Implementation](#9-technical-implementation)
10. [Balance & Design](#10-balance--design)

---

## 1. Overview

### 1.1 System Purpose

**Why weather & time matter:**
- Creates **dynamic world** that changes constantly
- **Different content** available at different times
- **Strategic depth:** Plan activities around conditions
- **Immersion:** Living, breathing world
- **Forces system interaction:** Can't just mine 24/7

### 1.2 Core Design Philosophy

**INTERCONNECTED GAMEPLAY:**
- **Mining:** Night spawns rare ores in deep caves
- **Fishing:** Specific fish only appear in rain/night
- **Farming:** Crops grow faster in certain weather
- **Combat:** Nighttime spawns stronger enemies (risk/reward)
- **Taming:** Rare creatures only spawn under special conditions
- **Events:** Seasonal activities rotate

**Players must adapt** to the world, not ignore it.

### 1.3 Time Scale

**Real-time to game-time conversion:**
- 1 real hour = 1 game day (24 game hours)
- 1 real minute = 24 game minutes
- Full day/night cycle: 60 real minutes

**Breakdown:**
- 00:00-06:00 (Night): 15 real minutes
- 06:00-12:00 (Morning): 15 real minutes
- 12:00-18:00 (Afternoon): 15 real minutes
- 18:00-24:00 (Evening): 15 real minutes

---

## 2. Day/Night Cycle

### 2.1 Time Phases

#### Night (00:00 - 06:00)
**Visual:**
- Dark skies, moon visible
- Stars twinkling
- Reduced ambient light
- Player needs torch/light source

**Gameplay Effects:**
- **Mining:** +20% rare ore spawn rate in caves
- **Fishing:** Night fish species appear
- **Combat:** Nighttime enemies spawn (Undead, Ghosts)
- **Taming:** Nocturnal creatures available (Owls, Bats, Wolves)
- **Dungeons:** Haunted Crypt only accessible at night

**Special Spawns:**
- Shadow Slime (only night, drops Void Essence)
- Night Wolf (rare, high XP)
- Ghost NPC (sells exclusive night items)

#### Dawn (06:00 - 08:00)
**Visual:**
- Sun rising, orange/pink skies
- Fog in valleys
- Beautiful screenshot opportunity

**Gameplay Effects:**
- Transition period
- Both day and night creatures briefly available
- **Farming:** +50% growth speed for 2 game hours (speed boost)

#### Day (08:00 - 18:00)
**Visual:**
- Bright sunny skies
- Clear visibility
- Dynamic clouds

**Gameplay Effects:**
- **Mining:** Standard spawn rates
- **Fishing:** Daytime fish species
- **Combat:** Standard enemies
- **Farming:** Normal growth
- **Taming:** Diurnal creatures (most common types)

**Special Events:**
- Traveling Merchant (appears 12:00-14:00, rare items)
- Fishing Tournament (Sundays 12:00-16:00)

#### Dusk (18:00 - 20:00)
**Visual:**
- Sun setting, purple/orange sky
- Long shadows
- Transition lighting

**Gameplay Effects:**
- Transition period
- **Taming:** Crepuscular creatures (Deer, Rabbits more active)

#### Evening (20:00 - 24:00)
**Visual:**
- Darkening sky
- Moon rising
- Streetlights in towns turn on

**Gameplay Effects:**
- Gradual transition to night mechanics
- Some night creatures start spawning

### 2.2 Moon Phases

**8-day cycle (8 real hours):**

| Phase | Days | Special Effects |
|-------|------|-----------------|
| New Moon | 0-1 | Darkest night, +30% enemy damage, Ghost spawns increased |
| Waxing Crescent | 1-2 | Transition |
| First Quarter | 2-3 | Balanced |
| Waxing Gibbous | 3-4 | Transition |
| Full Moon | 4-5 | **Brightest night, Werewolf spawns, Unicorn can be tamed** |
| Waning Gibbous | 5-6 | Transition |
| Last Quarter | 6-7 | Balanced |
| Waning Crescent | 7-8 | Transition |

**Full Moon Events:**
- **Werewolf Outbreak:** Elite enemies spawn in forests
- **Unicorn Taming:** Only available during full moon
- **Moonflower Blooming:** Rare herb only harvested at full moon
- **+50% Fishing luck** at night during full moon

```lua
function TimeService:GetMoonPhase()
    local daysSinceEpoch = math.floor(os.time() / 28800) -- 8 hours per cycle
    local phaseIndex = daysSinceEpoch % 8
    
    local phases = {
        "New Moon",
        "Waxing Crescent",
        "First Quarter",
        "Waxing Gibbous",
        "Full Moon",
        "Waning Gibbous",
        "Last Quarter",
        "Waning Crescent"
    }
    
    return phases[phaseIndex + 1]
end
```

---

## 3. Weather System

### 3.1 Weather Types

#### Clear (60% chance)
**Visual:**
- Blue skies, white clouds
- Sun shining
- No weather effects

**Gameplay:**
- Standard conditions
- No bonuses or penalties

#### Cloudy (20% chance)
**Visual:**
- Overcast skies
- Gray clouds
- Slightly dimmer lighting

**Gameplay:**
- **Farming:** Crops don't need watering (clouds provide moisture)
- **Fishing:** +10% catch rate (fish more active)

#### Rain (15% chance)
**Visual:**
- Rainfall particles
- Wet ground reflections
- Thunder sounds (no lightning yet)
- Puddles form

**Gameplay:**
- **Farming:** Automatically waters all crops (+100% growth)
- **Fishing:** +30% catch rate, rain-exclusive fish spawn
- **Mining:** Caves become muddy (-10% movement speed in caves)
- **Combat:** Burn effects last 50% longer due to moisture
- **Taming:** Amphibious creatures spawn (Frogs, Salamanders)

**Rain-Exclusive Content:**
- **Leviathan Eel:** Mythic fish (only during storms in ocean)
- **Rain Slime:** Drops purified water
- **Singing Frog:** Rare familiar (only spawns in rain)

#### Storm (3% chance, only during rain)
**Visual:**
- Heavy rainfall
- Lightning strikes (visual + sound)
- Dark skies
- Strong wind particle effects

**Gameplay:**
- **All rain effects amplified**
- **Fishing:** +50% catch rate, Leviathan Eel spawns
- **Combat:** Lightning strikes randomly deal 200 damage to enemies (dangerous for players too!)
- **Dungeons:** Storm-themed dungeon accessible
- **Taming:** Storm creatures (Lightning Elemental, Storm Hawk)

**Dangers:**
- Lightning can strike players in open areas (wear rubber armor!)
- Reduced visibility
- High winds slow movement -15%

#### Snow (2% chance, winter season only)
**Visual:**
- Snowfall particles
- Snow accumulation on ground
- Frozen water surfaces
- Frost on trees

**Gameplay:**
- **Farming:** Crops stop growing (frozen)
- **Fishing:** Ice fishing holes spawn, winter fish available
- **Mining:** Ice caves become accessible
- **Combat:** Burn effects reduced by 30%, freeze effects last 50% longer
- **Taming:** Arctic creatures (Snow Leopard, Penguin, Ice Fox)

**Snow-Exclusive Content:**
- **Winter Ice Salmon:** Event fish (high value)
- **Frost Wyrm:** Rare dragon-type familiar
- **Ice Geodes:** Special geodes with bonus gems

### 3.2 Weather Transitions

**Weather changes every 2-4 hours (real-time):**

```lua
function WeatherService:UpdateWeather()
    local currentWeather = GetCurrentWeather()
    local nextWeather = RollNextWeather(currentWeather)
    
    -- Transition period (5 minutes)
    TransitionWeather(currentWeather, nextWeather, 300)
    
    -- Update gameplay effects
    ApplyWeatherEffects(nextWeather)
    
    -- Notify players
    if nextWeather == "Storm" or nextWeather == "Snow" then
        NotificationService:BroadcastAll(nextWeather .. " incoming!")
    end
end

function RollNextWeather(current)
    -- Weather probabilities
    local weights = {
        Clear = 60,
        Cloudy = 20,
        Rain = 15,
        Storm = 3, -- Only if currently raining
        Snow = 2   -- Only in winter
    }
    
    -- Adjust based on season
    local season = TimeService:GetCurrentSeason()
    if season == "Winter" then
        weights.Snow = 15
        weights.Rain = 5
    elseif season == "Summer" then
        weights.Clear = 70
        weights.Rain = 10
    end
    
    -- Storm can only follow rain
    if current ~= "Rain" then
        weights.Storm = 0
    end
    
    return WeightedRandom(weights)
end
```

### 3.3 Forecast System

**Players can check upcoming weather:**

```
╔══════════════════════════════════════╗
║          WEATHER FORECAST            ║
╠══════════════════════════════════════╣
║  Current: ☀️ Clear                   ║
║  Time: 14:30 (Afternoon)             ║
║  Moon: 🌕 Full Moon                  ║
║                                      ║
║  Next 24 Hours:                      ║
║  18:00 - ☁️ Cloudy                   ║
║  22:00 - 🌧️ Rain                     ║
║  02:00 - ☀️ Clear                    ║
║                                      ║
║  Special: Full Moon tonight!         ║
║  (Unicorn taming available)          ║
╚══════════════════════════════════════╝
```

**Forecast Accuracy:**
- Short-term (6 hours): 90% accurate
- Medium-term (12 hours): 70% accurate
- Long-term (24 hours): 50% accurate

**Forecast Item:**
- **Weather Crystal:** Craftable item (500 IRF)
- Opens forecast UI anytime
- Helps plan activities

---

## 4. Seasonal Calendar

### 4.1 Four Seasons

**Each season: 7 real days (1 week)**

#### Spring (Weeks 1, 5, 9...)
**Theme:** Growth, renewal, flowers

**Visual:**
- Green grass, flowers blooming
- Light rain common
- Cherry blossom trees (decorative)

**Gameplay Effects:**
- **Farming:** All crops grow +20% faster
- **Fishing:** Spring fish spawn (Trout, Salmon)
- **Taming:** Baby animals spawn (high demand)
- **Combat:** Fewer aggressive enemies

**Special Events:**
- **Spring Festival (First week):**
  - Flower collecting event
  - Planting competition
  - Rewards: Rare seeds, Flower Crown cosmetic

#### Summer (Weeks 2, 6, 10...)
**Theme:** Heat, abundance, adventure

**Visual:**
- Bright sunny skies
- Longer days (day lasts 20 min, night 10 min)
- Heat haze effects

**Gameplay Effects:**
- **Farming:** Crops need more watering (2× frequency)
- **Fishing:** Summer fish (Tuna, Marlin)
- **Mining:** Volcanic zone becomes more accessible
- **Combat:** Desert enemies more active

**Special Events:**
- **Summer Beach Party (Mid-season):**
  - Beach activities
  - Surfing mini-game
  - Rewards: Beach decorations, Surfboard mount

#### Autumn/Fall (Weeks 3, 7, 11...)
**Theme:** Harvest, preparation, change

**Visual:**
- Orange/red leaves on trees
- Falling leaves particles
- Golden lighting

**Gameplay Effects:**
- **Farming:** Harvest yields +30% (harvest season!)
- **Fishing:** Autumn fish (Pike, Bass)
- **Taming:** Squirrels, Foxes more common
- **Combat:** Standard enemy spawns

**Special Events:**
- **Harvest Festival (Mid-season):**
  - Crop selling competition (best profit)
  - Cooking contest
  - Rewards: Golden Pumpkin decoration, Scarecrow familiar

#### Winter (Weeks 4, 8, 12...)
**Theme:** Cold, survival, magic

**Visual:**
- Snow-covered landscape
- Ice on water
- Shorter days (day 10 min, night 20 min)
- Northern lights at night

**Gameplay Effects:**
- **Farming:** Outdoor crops don't grow (need greenhouse)
- **Fishing:** Ice fishing, winter fish (Ice Salmon)
- **Mining:** Ice caves unlock (rare crystals)
- **Combat:** Ice enemies, winter wolves

**Special Events:**
- **Winter Solstice (End of season):**
  - Snow sculpture contest
  - Ice dungeon opens
  - Rewards: Frost Wyrm egg, Snow Castle decoration

### 4.2 Year-Round Calendar

```lua
SeasonCalendar = {
    -- Week 1
    {Season = "Spring", Events = {"Spring Festival"}},
    -- Week 2
    {Season = "Summer", Events = {}},
    -- Week 3
    {Season = "Autumn", Events = {}},
    -- Week 4
    {Season = "Winter", Events = {"Winter Solstice"}},
    -- Week 5
    {Season = "Spring", Events = {}},
    -- ... repeats
}

function TimeService:GetCurrentSeason()
    local weeksSinceEpoch = math.floor(os.time() / 604800) -- 7 days
    local seasonIndex = (weeksSinceEpoch % 4) + 1
    
    local seasons = {"Spring", "Summer", "Autumn", "Winter"}
    return seasons[seasonIndex]
end
```

---

## 5. Gameplay Effects

### 5.1 Mining System Integration

**Time-based ore spawns:**

```lua
function MiningService:GetOreSpawnWeight(oreType, timeOfDay, weather)
    local baseWeight = OreDatabase[oreType].SpawnWeight
    local modifier = 1.0
    
    -- Night bonus for rare ores
    if timeOfDay == "Night" and OreDatabase[oreType].Rarity >= "Epic" then
        modifier = modifier * 1.2 -- +20%
    end
    
    -- Deep cave bonus at night
    if timeOfDay == "Night" and IsInDeepCave() then
        modifier = modifier * 1.3 -- Additional +30%
    end
    
    -- Rain penalty in caves (muddy)
    if weather == "Rain" then
        modifier = modifier * 0.9 -- -10% mining speed
    end
    
    return baseWeight * modifier
end
```

**Example:**
- **Dragon Heart Gem** (Mythic):
  - Day spawn rate: 0.1%
  - Night spawn rate: 0.13% (+30%)
  - Full Moon night: 0.15% (+50%)

### 5.2 Fishing System Integration

**Fish availability table:**

| Fish | Time | Weather | Season |
|------|------|---------|--------|
| Common Cod | Any | Any | Any |
| Night Squid | Night | Any | Any |
| Storm Eel | Any | Storm | Any |
| Ice Salmon | Any | Snow | Winter |
| Cherry Salmon | Day | Clear | Spring |
| Summer Tuna | Day | Clear | Summer |

```lua
function FishingService:CanFishSpawn(fishId)
    local fishData = FishDatabase[fishId]
    local currentTime = TimeService:GetTimeOfDay()
    local currentWeather = WeatherService:GetCurrentWeather()
    local currentSeason = TimeService:GetCurrentSeason()
    
    -- Check time requirement
    if fishData.TimeRequirement and fishData.TimeRequirement ~= currentTime then
        return false
    end
    
    -- Check weather requirement
    if fishData.WeatherRequirement and fishData.WeatherRequirement ~= currentWeather then
        return false
    end
    
    -- Check season requirement
    if fishData.SeasonRequirement and fishData.SeasonRequirement ~= currentSeason then
        return false
    end
    
    return true
end
```

### 5.3 Farming System Integration

**Crop growth modifiers:**

```lua
function FarmingService:CalculateGrowthSpeed(plotId)
    local baseSpeed = 1.0
    local weather = WeatherService:GetCurrentWeather()
    local season = TimeService:GetCurrentSeason()
    local timeOfDay = TimeService:GetTimeOfDay()
    
    -- Season bonuses
    if season == "Spring" then
        baseSpeed = baseSpeed * 1.2 -- +20%
    elseif season == "Autumn" then
        baseSpeed = baseSpeed * 1.1 -- +10%
    elseif season == "Winter" then
        -- Outdoor crops stop growing
        if not HasGreenhouse(plotId) then
            return 0 -- No growth
        end
    end
    
    -- Weather bonuses
    if weather == "Rain" then
        baseSpeed = baseSpeed * 2.0 -- +100% (rain waters and fertilizes)
    elseif weather == "Cloudy" then
        baseSpeed = baseSpeed * 1.1 -- +10%
    end
    
    -- Dawn bonus (morning dew)
    if timeOfDay == "Dawn" then
        baseSpeed = baseSpeed * 1.5 -- +50% for 2 hours
    end
    
    return baseSpeed
end
```

**Example: Dragon Fruit**
- Base growth: 12 hours
- Spring bonus: 10 hours (-20%)
- Spring + Rain: 5 hours (-58%)
- Spring + Rain + Dawn: 3.3 hours (-72.5%)

**Strategic planning:** Plant before rain for fast growth!

### 5.4 Combat System Integration

**Enemy spawn variations:**

```lua
function CombatService:GetNightSpawnTable()
    local enemies = {
        -- Day enemies still spawn but reduced
        {EnemyId = "GOBLIN_SCOUT", SpawnWeight = 20}, -- Reduced from 40
        
        -- Night-exclusive enemies
        {EnemyId = "NIGHT_WOLF", SpawnWeight = 30},
        {EnemyId = "SHADOW_SLIME", SpawnWeight = 25},
        {EnemyId = "UNDEAD_SKELETON", SpawnWeight = 20},
        {EnemyId = "GHOST", SpawnWeight = 5}
    }
    
    -- Full moon: Add werewolves
    if TimeService:GetMoonPhase() == "Full Moon" then
        table.insert(enemies, {EnemyId = "WEREWOLF", SpawnWeight = 10})
    end
    
    return enemies
end
```

**Night combat rewards:**
- +20% XP (risk/reward)
- +10% IRF drops
- Night-exclusive loot (Shadow Essence, Ghost Ectoplasm)

### 5.5 Taming System Integration

**Creature spawn conditions:**

```lua
CreatureSpawnConditions = {
    UNICORN = {
        Time = "Night",
        Weather = "Clear",
        MoonPhase = "Full Moon",
        Location = "Mysterious Lake",
        SpawnChance = 5 -- 5% when all conditions met
    },
    
    PHOENIX = {
        Time = "Day",
        Weather = "Clear",
        Season = "Summer",
        Location = "Volcanic Core",
        SpawnChance = 3
    },
    
    STORM_HAWK = {
        Time = "Any",
        Weather = "Storm",
        Location = "Mountain Peak",
        SpawnChance = 10
    },
    
    SNOW_LEOPARD = {
        Time = "Any",
        Weather = "Snow",
        Season = "Winter",
        Location = "Mountain Region",
        SpawnChance = 8
    }
}
```

**Players must track weather/time to find rare creatures!**

---

## 6. System Integration

### 6.1 Interconnection Map

```
Weather/Time System (Core)
    ↓
┌─────────────┼─────────────┬────────────┬────────────┐
│             │             │            │            │
Mining      Fishing      Farming     Combat      Taming
│             │             │            │            │
├─Night: Rare ore     ├─Rain: More fish  ├─Night enemies  ├─Time-specific
├─Weather affects    ├─Storm: Mythic    ├─Buff/debuff    │  spawns
│  cave conditions    │  fish            │  by weather    ├─Moon phase
│                     ├─Season fish      │                │  affects rarity
└─────────────┴─────────────┴────────────┴────────────┘
                           ↓
                    Dungeon Access
                    (Night dungeons, Storm dungeons)
                           ↓
                      Private Island
                      (Weather affects visitors)
                           ↓
                         Trading
                      (Demand for seasonal items)
```

### 6.2 Progression Loop

**Forcing system interaction:**

**Example player journey:**
```
Day 1 (Morning, Clear):
- Mine ores during day
- Sell ores for IRF
- Buy fishing rod

Day 1 (Afternoon, Rain starts):
- Can't mine efficiently (muddy caves)
- Switch to fishing (+30% catch rate)
- Catch rare rain fish
- Sell for high profit

Day 1 (Night, Clear, Full Moon):
- Farm monsters for XP (+20% night bonus)
- Find Unicorn at lake (full moon spawn)
- Attempt taming

Day 2 (Morning, Clear):
- Harvest crops (grew during night + dawn boost)
- Cook food buffs
- Prepare for dungeon run
```

**Players optimize based on conditions, not just grind one activity!**

---

## 7. Visual Effects

### 7.1 Lighting System

**Dynamic lighting based on time:**

```lua
function LightingService:UpdateLighting(timeOfDay)
    local Lighting = game:GetService("Lighting")
    
    if timeOfDay == "Night" then
        Lighting.Brightness = 1
        Lighting.OutdoorAmbient = Color3.fromRGB(50, 50, 80)
        Lighting.ClockTime = 0 -- Midnight
        
    elseif timeOfDay == "Dawn" then
        Lighting.Brightness = 1.5
        Lighting.OutdoorAmbient = Color3.fromRGB(255, 200, 150)
        Lighting.ClockTime = 6
        
    elseif timeOfDay == "Day" then
        Lighting.Brightness = 2
        Lighting.OutdoorAmbient = Color3.fromRGB(150, 150, 150)
        Lighting.ClockTime = 12
        
    elseif timeOfDay == "Dusk" then
        Lighting.Brightness = 1.5
        Lighting.OutdoorAmbient = Color3.fromRGB(200, 150, 200)
        Lighting.ClockTime = 18
    end
end
```

### 7.2 Weather Particles

**Particle emitters for weather:**

```lua
function WeatherService:SpawnWeatherParticles(weatherType)
    if weatherType == "Rain" then
        local rainEmitter = ReplicatedStorage.WeatherEffects.Rain:Clone()
        rainEmitter.Parent = workspace
        rainEmitter.Position = Vector3.new(0, 500, 0) -- Sky
        
    elseif weatherType == "Snow" then
        local snowEmitter = ReplicatedStorage.WeatherEffects.Snow:Clone()
        snowEmitter.Parent = workspace
        snowEmitter.Rate = 50 -- Snowflakes per second
        
    elseif weatherType == "Storm" then
        -- Rain + Lightning
        SpawnWeatherParticles("Rain")
        SpawnLightningEffects()
    end
end

function SpawnLightningEffects()
    while WeatherService:GetCurrentWeather() == "Storm" do
        wait(math.random(5, 15)) -- Random lightning
        
        -- Flash
        game.Lighting.Brightness = 3
        wait(0.1)
        game.Lighting.Brightness = 1
        
        -- Thunder sound
        SoundService:PlayGlobalSound("Thunder")
        
        -- Damage random outdoor enemy
        local enemy = GetRandomOutdoorEnemy()
        if enemy then
            enemy:TakeDamage(200, "Lightning")
        end
    end
end
```

### 7.3 Seasonal Decorations

**World changes with seasons:**

```lua
function SeasonService:ApplySeasonalChanges(season)
    if season == "Spring" then
        -- Add flowers
        for _, flowerSpawn in ipairs(workspace.FlowerSpawns:GetChildren()) do
            local flower = ReplicatedStorage.Decorations.Flower:Clone()
            flower.Parent = flowerSpawn
        end
        
        -- Cherry blossoms
        for _, tree in ipairs(workspace.Trees:GetChildren()) do
            if tree.TreeType == "Cherry" then
                tree.Leaves.Color = Color3.fromRGB(255, 200, 200)
            end
        end
        
    elseif season == "Autumn" then
        -- Orange leaves
        for _, tree in ipairs(workspace.Trees:GetChildren()) do
            tree.Leaves.Color = Color3.fromRGB(255, 150, 50)
        end
        
        -- Falling leaves particles
        for _, tree in ipairs(workspace.Trees:GetChildren()) do
            local leaves = ReplicatedStorage.Particles.FallingLeaves:Clone()
            leaves.Parent = tree
        end
        
    elseif season == "Winter" then
        -- Snow on ground
        workspace.Terrain.Decoration = Enum.Decoration.Snow
        
        -- Freeze water
        for _, water in ipairs(workspace.Water:GetChildren()) do
            water.Material = Enum.Material.Ice
        end
    end
end
```

---

## 8. Player Interaction

### 8.1 Time Control (Private Island Only)

**Players can change time on their Private Island:**

```lua
function IslandService:ChangeIslandTime(islandId, desiredTime)
    local island = GetIsland(islandId)
    
    -- Only owner can change time
    if island.OwnerId ~= player.UserId then
        return false, "Only island owner can change time"
    end
    
    -- Costs IRF (prevents abuse)
    local cost = 1000
    if CurrencyService:GetBalance(player) < cost then
        return false, "Not enough IRF"
    end
    
    CurrencyService:RemoveCurrency(player, cost)
    
    -- Change island time (doesn't affect main world)
    island.CustomTime = desiredTime
    UpdateIslandLighting(island)
    
    return true
end
```

**Use cases:**
- Take screenshots during golden hour
- Farm at optimal time (dawn growth boost)
- Show off island at different times to visitors

### 8.2 Weather Prediction Tools

**Craftable items for weather info:**

**Weather Vane (Decoration):**
- Cost: 2,000 IRF
- Place on Private Island
- Shows current wind direction and upcoming weather

**Barometer (Tool):**
- Cost: 5,000 IRF
- Hold in hand to open forecast
- Shows 24-hour prediction

**Meteorologist NPC:**
- Located in town
- Free forecast service
- Sells weather prediction items

---

## 9. Technical Implementation

### 9.1 Time System

```lua
-- Server-side time manager
local TimeService = {}

local TIME_SCALE = 24 -- 1 real min = 24 game mins
local DAY_LENGTH = 3600 -- 1 hour in seconds

function TimeService:Init()
    self.StartTime = os.time()
    self.CurrentTime = 0
    
    -- Update every second
    game:GetService("RunService").Heartbeat:Connect(function(dt)
        self:Update(dt)
    end)
end

function TimeService:Update(deltaTime)
    -- Calculate elapsed game time
    local realElapsed = os.time() - self.StartTime
    self.CurrentTime = (realElapsed * TIME_SCALE) % (DAY_LENGTH * TIME_SCALE)
    
    -- Convert to hours (0-24)
    local gameHour = math.floor(self.CurrentTime / 3600) % 24
    
    -- Update lighting
    LightingService:SetTimeOfDay(gameHour)
    
    -- Broadcast to clients
    if gameHour ~= self.LastBroadcastHour then
        RemoteEvents.TimeUpdate:FireAllClients(gameHour)
        self.LastBroadcastHour = gameHour
    end
end

function TimeService:GetTimeOfDay()
    local hour = math.floor(self.CurrentTime / 3600) % 24
    
    if hour >= 0 and hour < 6 then
        return "Night"
    elseif hour >= 6 and hour < 8 then
        return "Dawn"
    elseif hour >= 8 and hour < 18 then
        return "Day"
    elseif hour >= 18 and hour < 20 then
        return "Dusk"
    else
        return "Evening"
    end
end

return TimeService
```

### 9.2 Weather System

```lua
local WeatherService = {}

local WEATHER_DURATION_MIN = 7200 -- 2 hours
local WEATHER_DURATION_MAX = 14400 -- 4 hours

function WeatherService:Init()
    self.CurrentWeather = "Clear"
    self.NextWeatherChange = os.time() + math.random(WEATHER_DURATION_MIN, WEATHER_DURATION_MAX)
    
    -- Check for weather changes
    spawn(function()
        while true do
            wait(60) -- Check every minute
            self:CheckWeatherChange()
        end
    end)
end

function WeatherService:CheckWeatherChange()
    if os.time() >= self.NextWeatherChange then
        self:ChangeWeather()
    end
end

function WeatherService:ChangeWeather()
    local newWeather = self:RollNextWeather()
    
    -- Notify players
    NotificationService:BroadcastAll("Weather changing to: " .. newWeather)
    
    -- Transition (5 minute fade)
    self:TransitionWeather(self.CurrentWeather, newWeather, 300)
    
    self.CurrentWeather = newWeather
    self.NextWeatherChange = os.time() + math.random(WEATHER_DURATION_MIN, WEATHER_DURATION_MAX)
    
    -- Broadcast
    RemoteEvents.WeatherUpdate:FireAllClients(newWeather)
end

return WeatherService
```

---

## 10. Balance & Design

### 10.1 Activity Distribution

**Goal: Players engage with different systems at different times**

| Time/Weather | Primary Activity | Secondary Activity |
|--------------|------------------|-------------------|
| Day/Clear | Mining, Farming | Combat (standard) |
| Day/Rain | Fishing | Farming (automated watering) |
| Night/Clear | Combat (XP farm) | Mining (rare ores) |
| Night/Rain | Fishing (rare fish) | Taming (amphibious) |
| Storm | Fishing (mythic) | Dungeon (storm instance) |
| Full Moon | Taming (unicorn) | Combat (werewolves) |

### 10.2 Seasonal Economy

**Market demand fluctuates:**

```lua
function TradingService:GetSeasonalPriceModifier(itemId)
    local season = TimeService:GetCurrentSeason()
    local itemData = ItemDatabase[itemId]
    
    if itemData.Category == "Crop" then
        if season == "Autumn" then
            return 1.5 -- Harvest season, more supply, but high demand
        elseif season == "Winter" then
            return 2.0 -- Scarcity, prices double
        end
    elseif itemData.Category == "Fish" then
        if itemData.SeasonExclusive == season then
            return 0.8 -- Current season fish more common
        else
            return 1.5 -- Out of season fish rare
        end
    end
    
    return 1.0
end
```

**Smart trading:** Buy winter crops in autumn (cheap), sell in spring (expensive)

---

## Implementation Checklist

### Phase 1: Core Time System (Month 2)
- [ ] Day/night cycle (60-minute loop)
- [ ] Dynamic lighting
- [ ] Time-of-day detection
- [ ] Moon phase system
- [ ] Client-server time sync

### Phase 2: Weather System (Month 3)
- [ ] 5 weather types (Clear, Cloudy, Rain, Storm, Snow)
- [ ] Weather transitions
- [ ] Particle effects (rain, snow)
- [ ] Weather change timing
- [ ] Forecast system

### Phase 3: Seasonal System (Month 4)
- [ ] 4 seasons (7-day cycles)
- [ ] Seasonal visual changes
- [ ] Seasonal events
- [ ] Season-exclusive content
- [ ] Calendar UI

### Phase 4: Gameplay Integration (Month 5)
- [ ] Mining time/weather effects
- [ ] Fishing conditions
- [ ] Farming growth modifiers
- [ ] Combat spawn variations
- [ ] Taming spawn conditions

### Phase 5: Polish & Balance (Month 6)
- [ ] Advanced lighting (volumetric)
- [ ] Lightning strikes (storms)
- [ ] Aurora borealis (winter nights)
- [ ] Private island time control
- [ ] Economic balancing

---

## Related Documentation
- [GDD_Systems_Mining.md](GDD_Systems_Mining.md) - Time affects ore spawns
- [GDD_Systems_Fishing.md](GDD_Systems_Fishing.md) - Weather/time fish spawns
- [GDD_Systems_Farming.md](GDD_Systems_Farming.md) - Growth speed modifiers
- [GDD_Systems_Combat.md](GDD_Systems_Combat.md) - Night enemy spawns
- [GDD_Systems_Taming.md](GDD_Systems_Taming.md) - Creature spawn conditions

---

**Document End - Weather & Time System**  
*A living world that forces players to adapt and engage with all systems*
