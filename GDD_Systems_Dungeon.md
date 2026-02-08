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

## 2. Dungeon Types

### 2.1 Solo Dungeons (1 player)

#### The Abandoned Mine (Level 5-10)
**Theme:** Tutorial dungeon, mining theme  
**Length:** 10-15 minutes  
**Layout:** Linear path with 2 side rooms  
**Enemies:** Slimes, Bats, Cave Spiders (Common)  
**Miniboss:** Giant Slime King (Mid-dungeon)  
**Boss:** Corrupted Mining Golem  
**Unique Mechanic:** Collapsing tunnels (time pressure in final room)  
**Rewards:**
- Common/Rare equipment (Level 5-10)
- Mining materials (Copper, Iron, Coal)
- 500-1,000 IRF
- Achievement: "First Delve"

#### The Haunted Crypt (Level 15-20)
**Theme:** Undead/Horror theme  
**Length:** 15-20 minutes  
**Layout:** Multiple branching paths, secret rooms  
**Enemies:** Skeletons, Zombies, Ghosts  
**Miniboss:** Crypt Guardian (blocks main path)  
**Boss:** Lich Lord  
**Unique Mechanic:** Light/Dark - torches control ghost visibility  
**Rewards:**
- Rare/Epic equipment (Level 15-20)
- Dark essence crafting materials
- 2,000-4,000 IRF
- Achievement: "Crypt Raider"

---

### 2.2 Party Dungeons (2-5 players)

#### Goblin Fortress (Level 10-15)
**Theme:** Goblin raid, siege warfare  
**Recommended Party:** 3-5 players  
**Length:** 20-30 minutes  
**Layout:** Fortress with walls, towers, throne room  
**Stages:**
1. Breach outer walls (destroy gates)
2. Clear courtyard (wave defense)
3. Ascend throne room tower
4. Boss fight: Goblin King

**Enemies:** 
- Goblin Scouts, Warriors, Archers
- Goblin Shamans (healers)
- War Wolves (pets)

**Mechanics:**
- **Gate Destruction:** Must break down fortified gates
- **Wave Defense:** Survive goblin counterattacks
- **Adds Management:** Boss summons reinforcements

**Rewards:**
- Rare/Epic equipment (Level 10-15)
- Goblin crafting materials
- 3,000-6,000 IRF (split among party)
- Achievement: "Goblin Slayer"

#### Crystal Cavern (Level 25-30)
**Theme:** Crystal/magic theme, puzzle elements  
**Recommended Party:** 4-5 players  
**Length:** 30-45 minutes  
**Layout:** Open cavern with platforms, crystal formations  
**Stages:**
1. Navigate crystal maze (puzzle)
2. Activate power crystals (coordination mechanic)
3. Clear elemental guardians
4. Boss fight: Ancient Crystal Guardian

**Enemies:**
- Crystal Elementals
- Animated Crystals
- Crystal Spiders

**Mechanics:**
- **Crystal Puzzle:** Match colors to open paths
- **Shield Mechanic:** Destroy crystals to damage boss
- **Platform Navigation:** Avoid falling into void

**Rewards:**
- Epic equipment (Level 25-30)
- Crystals (Amethyst, Diamond, rare gems)
- 10,000-20,000 IRF
- Legendary Geode (30% chance)
- Achievement: "Crystal Champion"

---

### 2.3 Raid Dungeons (5-10 players)

#### Dragon's Lair (Level 40-45)
**Theme:** Dragon's mountain lair  
**Recommended Party:** 8-10 players  
**Length:** 60-90 minutes  
**Layout:** Massive multi-room dungeon
- Dragon hoard room
- Lava chambers
- Dragon's nest
- Final arena

**Stages:**
1. Clear dragon whelps and drakes
2. Survive lava room hazards
3. Defend against dragon air raids
4. Boss fight: Elder Dragon (multi-phase)

**Enemies:**
- Dragon Whelps (juvenile dragons)
- Fire Elementals
- Dragon-worshipping cultists
- Elite Drake (miniboss)

**Mechanics:**
- **Tank Requirements:** Heavy armor needed for dragon attacks
- **DPS Check:** Burn phases must complete in time
- **Healer Coordination:** Group healing essential
- **Environmental Hazards:** Lava flows, falling rocks

**Raid Boss:** Ignis the Elder Dragon (See Database_Monsters.md MON_012)

**Rewards (per player):**
- Legendary equipment (Level 40-45)
- Dragon materials (Scale, Heart Gem 30% chance)
- 50,000-100,000 IRF
- Mythic Geode (20% chance)
- Dragon Mount Egg (5% chance)
- Achievement: "Dragon Slayer"
- Title: "Dragonbane"

---

### 2.4 Event Dungeons (Limited Time)

#### Halloween: Pumpkin Patch of Terror
**Theme:** Spooky Halloween  
**Availability:** October 1-31  
**Level:** Scales 15-50 (enters at your level)  
**Recommended Party:** 3-5 players  
**Length:** 25-35 minutes

**Enemies:**
- Possessed Pumpkins
- Ghost Pumpkin Fiends
- Skeleton Warriors (Halloween themed)
- Haunted Scarecrows

**Boss:** The Pumpkin King (giant jack-o'-lantern boss)

**Mechanics:**
- **Trick or Treat Chests:** Random good/bad effects
- **Candy Collection:** Currency for event shop
- **Costume Buff:** Wearing Halloween cosmetics = stat boost

**Rewards:**
- Halloween Tokens (event currency)
- Ghost Pumpkin Seeds
- Exclusive Halloween cosmetics
- Special titles
- Halloween mount (rare drop)

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
