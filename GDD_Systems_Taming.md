# IRIFA: Realms of Harvest & Adventure
## Game Design Document - Taming & Familiar System

---

### Document Information
**Document Type:** System Design  
**System:** Taming & Familiar System  
**Version:** 1.0  
**Last Updated:** February 8, 2026  
**Status:** Implementation Ready

---

## Table of Contents
1. [Overview](#1-overview)
2. [Taming Mechanics](#2-taming-mechanics)
3. [Familiar Types](#3-familiar-types)
4. [Familiar Stats & Leveling](#4-familiar-stats--leveling)
5. [Familiar Abilities](#5-familiar-abilities)
6. [Feeding & Care System](#6-feeding--care-system)
7. [Familiar Combat](#7-familiar-combat)
8. [Breeding System](#8-breeding-system)
9. [Habitat & Housing](#9-habitat--housing)
10. [Technical Implementation](#10-technical-implementation)

---

## 1. Overview

### 1.1 System Purpose
The Taming system allows players to:
- Capture and befriend creatures from the world
- Raise familiars as companions
- Gain combat and utility bonuses
- Collect rare and legendary creatures
- Breed familiars for better stats
- Showcase collections on Private Island

### 1.2 Core Design Pillars
- **Collection:** Pokémon-style catching and collecting
- **Bonding:** Relationship building through care
- **Utility:** Passive bonuses and active abilities
- **Progression:** Level up familiars alongside player
- **Social:** Trading and showcasing collections

### 1.3 Familiar Categories
- **Combat Familiars:** Fight alongside player
- **Passive Familiars:** Provide stat buffs
- **Utility Familiars:** Gathering/farming bonuses
- **Mount Familiars:** Faster travel
- **Decorative Familiars:** Aesthetic companions

---

## 2. Taming Mechanics

### 2.1 Taming Process

#### Step 1: Encounter Wild Creature
Wild creatures spawn in specific zones:
- Forest: Rabbits, Deer, Foxes, Bears
- Ocean: Dolphins, Sea Turtles, Penguins
- Mountains: Eagles, Mountain Goats, Snow Leopards
- Volcanic: Fire Salamanders, Phoenix Chicks (rare)
- Mysterious zones: Dragons, Unicorns, Void Creatures

#### Step 2: Weaken the Creature
Combat phase:
- Reduce creature HP to <30% (not kill)
- Use special "Taming" weapons (non-lethal damage)
- Avoid overkill or creature dies permanently

#### Step 3: Taming Attempt
```lua
function TamingService:AttemptTame(player, creature)
    local success = false
    local baseChance = creature.BaseTameChance -- 10-80% depending on rarity
    
    -- Modifiers
    local hpModifier = (1 - creature.Health / creature.MaxHealth) * 50 -- Lower HP = higher chance
    local foodModifier = 0
    
    -- Check if player is holding preferred food
    local heldItem = player.Character:FindFirstChild("HeldItem")
    if heldItem and heldItem.Value == creature.PreferredFood then
        foodModifier = 30 -- +30% with correct food
    end
    
    -- Player taming level bonus
    local skillBonus = player.TamingLevel * 0.5 -- +0.5% per level
    
    -- Calculate final chance
    local finalChance = baseChance + hpModifier + foodModifier + skillBonus
    finalChance = math.min(finalChance, 95) -- Cap at 95%
    
    -- Roll
    local roll = math.random(1, 100)
    if roll <= finalChance then
        success = true
        -- Award familiar
        FamiliarService:AwardFamiliar(player, creature.FamiliarId)
        creature:Destroy()
        
        -- XP for taming skill
        player.TamingXP = player.TamingXP + creature.TamingXPReward
    else
        -- Failure - creature escapes or becomes aggressive
        if math.random() > 0.5 then
            creature.Aggressive = true -- Attacks player
        else
            creature:Escape() -- Runs away at high speed
        end
    end
    
    return success, finalChance
end
```

#### Taming Tools

**Taming Net**
- **Cost:** 50 IRF
- **Effect:** +10% tame chance, slows creature
- **Uses:** 10 attempts

**Soothing Flute**
- **Cost:** 500 IRF
- **Effect:** +20% tame chance, calms aggressive creatures
- **Uses:** 20 attempts
- **Cooldown:** 30 seconds between uses

**Master Ball (Robux)**
- **Cost:** 100 Robux
- **Effect:** 100% capture rate (any creature, any HP)
- **Uses:** 1 use, consumed on use
- **Limitation:** Cannot be used on Legendary/Mythic creatures

### 2.2 Taming Difficulty by Rarity

| Rarity | Base Tame Chance | HP Threshold | Preferred Food Required? |
|--------|------------------|--------------|--------------------------|
| Common | 60% | <50% HP | No |
| Rare | 40% | <30% HP | Recommended (+30%) |
| Epic | 20% | <20% HP | Yes (needed) |
| Legendary | 10% | <15% HP | Yes + Special conditions |
| Mythic | 5% | <10% HP | Yes + Quest completion |

### 2.3 Special Taming Conditions

#### Legendary Creatures
Require specific conditions beyond HP:

**Unicorn (Legendary)**
- HP: <15%
- Food: Crystal Carrot
- Condition: Must be full moon (in-game night)
- Location: Mysterious Lake
- Time: Only spawns at night
- Purity: Player must have no active combat kills from last 30 minutes

**Phoenix (Legendary)**
- HP: <10%
- Food: Phoenix Pepper
- Condition: Must survive Inferno attack (iframe dodge)
- Location: Volcanic Core
- Achievement: "Flame Tamer" required

**Baby Dragon (Mythic)**
- HP: Cannot damage (peaceful creature)
- Food: Dragon Heart Gem (from Elder Dragon boss)
- Condition: Complete "Dragon Whisperer" quest chain
- Location: Dragon's Nest (post-raid unlock)
- Limit: 1 per player (account-wide)

---

## 3. Familiar Types

### 3.1 Common Familiars

#### Rabbit
- **Rarity:** Common
- **Type:** Passive
- **Taming Location:** Forest, Plains
- **Preferred Food:** Carrot
- **Base Stats:** HP 100, No combat
- **Passive Bonus:** +5% Farming Speed
- **Appearance:** Brown or white fur, floppy ears
- **Personality:** Timid, hops around player

#### Blue Bird
- **Rarity:** Common
- **Type:** Utility
- **Taming Location:** Forest, Town
- **Preferred Food:** Seeds
- **Base Stats:** HP 80, No combat
- **Utility Ability:** **Item Fetcher** - Retrieves dropped items within 20m
- **Appearance:** Bright blue feathers, small
- **Personality:** Cheerful, chirps frequently

---

### 3.2 Rare Familiars

#### Fox
- **Rarity:** Rare
- **Type:** Combat
- **Taming Location:** Forest (night spawns)
- **Preferred Food:** Raw Meat, Fish
- **Base Stats:** HP 500, Attack 40, Defense 20
- **Combat Ability:** **Quick Strike** - Fast attack with 20% crit chance
- **Passive Bonus:** +10% Movement Speed
- **Appearance:** Orange fur with white tail tip
- **Personality:** Playful, cunning

#### Sea Turtle
- **Rarity:** Rare
- **Type:** Mount + Passive
- **Taming Location:** Ocean beaches
- **Preferred Food:** Fish, Seaweed
- **Base Stats:** HP 800, Defense 50
- **Mount Ability:** Swim speed +50% in water
- **Passive Bonus:** +20% Fishing Success Rate
- **Appearance:** Green shell, flippers
- **Personality:** Calm, slow on land

---

### 3.3 Epic Familiars

#### Fire Wolf
- **Rarity:** Epic
- **Type:** Combat
- **Taming Location:** Volcanic Zone
- **Preferred Food:** Flame Sword (crafted meat dish)
- **Base Stats:** HP 2,000, Attack 120, Defense 60
- **Combat Ability:** **Flame Bite** - Deals fire damage + burn (50 DPS for 5 sec)
- **Passive Bonus:** +15% Fire Damage, +50 Fire Resistance
- **Appearance:** Red-orange fur with flame particles
- **Personality:** Fierce, loyal
- **Special:** Immune to lava damage

#### Crystal Golem
- **Rarity:** Epic
- **Type:** Combat (Tank)
- **Taming Location:** Crystal Cavern
- **Preferred Food:** Amethyst Crystals
- **Base Stats:** HP 5,000, Attack 80, Defense 150
- **Combat Ability:** **Crystal Shield** - Absorbs 500 damage for player (30 sec cooldown)
- **Passive Bonus:** +100 Defense, +20% Physical Resistance
- **Appearance:** Crystalline body, glowing core
- **Personality:** Protective, slow-moving

---

### 3.4 Legendary Familiars

#### Unicorn
- **Rarity:** Legendary
- **Type:** Mount + Healer
- **Taming Location:** Mysterious Lake (full moon)
- **Preferred Food:** Crystal Carrot, Moonberry
- **Base Stats:** HP 3,000, Magic 200
- **Mount Ability:** Run speed +100%, can jump 3× higher
- **Combat Ability:** **Healing Aura** - Heals player 100 HP/sec in 10m radius
- **Passive Bonus:** +50% Healing received, +100 Magic Power
- **Appearance:** Pure white horse, spiraling horn, rainbow mane
- **Personality:** Majestic, gentle
- **Special:** Glows at night, leaves sparkle trail

#### Phoenix
- **Rarity:** Legendary
- **Type:** Combat (Glass Cannon)
- **Taming Location:** Volcanic Core peak
- **Preferred Food:** Phoenix Pepper
- **Base Stats:** HP 2,500, Attack 250, Magic 200
- **Combat Ability:** **Inferno Blast** - AoE fire explosion (500 damage, 8m radius, 60 sec cooldown)
- **Passive Bonus:** +50% Fire Damage, +100% Fire Resistance, Immunity to burn
- **Special Ability:** **Rebirth** - If player dies, Phoenix sacrifices itself to revive player at 50% HP (once per day)
- **Appearance:** Flaming bird with red-gold feathers, fire particle trail
- **Personality:** Noble, protective
- **Respawn:** Phoenix respawns after 24 hours if sacrificed

---

### 3.5 Mythic Familiars

#### Baby Dragon
- **Rarity:** Mythic
- **Type:** Combat + Mount (grows over time)
- **Taming Location:** Dragon's Nest (post Elder Dragon raid)
- **Preferred Food:** Dragon Heart Gem (initial), then Epic+ fish/meat
- **Growth Stages:**
  1. **Hatchling (Levels 1-20):** Small, walks beside player
     - HP 1,000, Attack 100
     - Ability: Flame Breath (minor)
  2. **Juvenile (Levels 21-40):** Medium, can be mounted (ground only)
     - HP 5,000, Attack 300
     - Ability: Fire Breath, Wing Buffet
  3. **Adult (Levels 41-60):** Large, flying mount
     - HP 15,000, Attack 800
     - Ability: Dragon Roar (AoE stun), Fire Breath, Flight
- **Ultimate Ability (Adult):** **Dragonfire Barrage** - Aerial bombardment (1,000 damage per fireball, 10 fireballs, 5 min cooldown)
- **Passive Bonus:** +100% Fire Damage, +50% All Stats, Dragon Slayer weapons deal -50% damage to you
- **Appearance:** Scales match element (Red fire, Blue ice, Green nature)
- **Personality:** Starts playful, becomes majestic
- **Special:** Only 1 per account, tradeable as egg only
- **Limit:** Account-bound once hatched

#### Void Sprite
- **Rarity:** Mythic
- **Type:** Combat (Magic DPS)
- **Taming Location:** Void Rifts (random world event)
- **Preferred Food:** Void Crystal shards
- **Base Stats:** HP 3,000, Attack 150, Magic 500
- **Combat Ability:** **Void Bolt** - High magic damage projectile that ignores 50% resistance
- **Special Ability:** **Phase Shift** - Player and familiar become invulnerable for 3 seconds (2 min cooldown)
- **Passive Bonus:** +200 Magic Power, +30% Magic Damage, +25% Cooldown Reduction
- **Appearance:** Small humanoid void entity, purple-black energy, phases in/out
- **Personality:** Mysterious, otherworldly
- **Special:** Can pass through walls, teleports to player if too far

---

## 4. Familiar Stats & Leveling

### 4.1 Familiar Stats

**Core Stats:**
- **HP:** Health points
- **Attack:** Physical damage output (combat familiars)
- **Defense:** Damage reduction
- **Magic:** Magic damage output (magic familiars)
- **Speed:** Movement and attack speed

**Hidden Stats:**
- **Loyalty:** Affects performance (0-100)
- **Happiness:** Affects XP gain rate (0-100)
- **Bond Level:** Relationship tier (1-10)

### 4.2 Leveling System

#### XP Sources
Familiars gain XP from:
- **Following player:** 1 XP per minute (passive gain)
- **Player combat:** 10% of player's XP from kills
- **Familiar combat:** 100% of damage dealt as XP
- **Feeding preferred food:** 50 XP per feeding
- **Playing with familiar:** 100 XP per play session (once per hour)

#### Level Scaling
```lua
function FamiliarService:CalculateStatsForLevel(familiar, level)
    local baseStats = FamiliarData[familiar.FamiliarId].BaseStats
    
    -- Stats increase 5% per level
    local stats = {
        HP = baseStats.HP * (1 + (level - 1) * 0.05),
        Attack = baseStats.Attack * (1 + (level - 1) * 0.05),
        Defense = baseStats.Defense * (1 + (level - 1) * 0.05),
        Magic = baseStats.Magic * (1 + (level - 1) * 0.05),
    }
    
    -- Bond level bonus
    local bondBonus = familiar.BondLevel * 0.02 -- +2% per bond level
    for stat, value in pairs(stats) do
        stats[stat] = value * (1 + bondBonus)
    end
    
    return stats
end
```

#### Level Cap
- Common: Level 30
- Rare: Level 50
- Epic: Level 60
- Legendary: Level 80
- Mythic: Level 100

### 4.3 Bond Level System

Bond increases through:
- Time spent together (1 point per hour)
- Feeding (5 points per feeding)
- Combat together (10 points per dungeon clear)
- Playing (20 points per play session)
- Grooming/care (15 points)

**Bond Milestones:**

| Bond Level | Points Required | Unlock |
|------------|-----------------|--------|
| 1 | 0 | Initial bond |
| 2 | 100 | Nickname unlocked |
| 3 | 300 | +5% stat bonus |
| 4 | 600 | New ability variant |
| 5 | 1,000 | +10% stat bonus |
| 6 | 1,500 | Accessory customization |
| 7 | 2,200 | +15% stat bonus |
| 8 | 3,000 | Ultimate ability unlocked |
| 9 | 4,000 | +20% stat bonus |
| 10 | 5,000 | Max bond - Special title + cosmetic evolution |

---

## 5. Familiar Abilities

### 5.1 Combat Abilities

#### Active Abilities (Player Activated)
Triggered by player pressing familiar ability hotkey:

**Example: Fire Wolf - Flame Bite**
```lua
function FamiliarAbilities.FlameBite(familiar, target)
    -- Damage calculation
    local damage = familiar.Stats.Attack * 1.5
    
    -- Apply damage
    target:TakeDamage(damage, "Fire")
    
    -- Apply burn DoT
    local burnEffect = {
        Damage = 50,
        Duration = 5,
        Interval = 1,
        Type = "Fire"
    }
    StatusEffectService:ApplyEffect(target, burnEffect)
    
    -- Cooldown
    familiar.AbilityCooldown = 15 -- seconds
    
    -- Visual effects
    EffectsService:PlayEffect("FlameBite", familiar.Position, target.Position)
end
```

#### Passive Abilities (Always Active)
Automatically trigger under conditions:

**Example: Phoenix - Rebirth**
```lua
-- Listen for player death
Players.PlayerDied:Connect(function(player)
    local familiar = FamiliarService:GetActiveFamiliar(player)
    
    if familiar and familiar.FamiliarId == "PHOENIX" then
        -- Check if rebirth available (not on cooldown)
        if not familiar.RebirthUsedToday then
            -- Revive player
            player.Character.Humanoid.Health = player.Character.Humanoid.MaxHealth * 0.5
            player.Character.HumanoidRootPart.CFrame = CFrame.new(familiar.Position)
            
            -- Sacrifice phoenix (temporary)
            familiar.RebirthUsedToday = true
            familiar.RespawnAt = os.time() + 86400 -- 24 hours
            familiar:PlayAnimation("Rebirth")
            familiar:Disappear()
            
            -- Notify player
            NotificationService:Send(player, "Your Phoenix sacrificed itself to save you!")
        end
    end
end)
```

### 5.2 Utility Abilities

#### Resource Gathering Boost
**Blue Bird - Item Fetcher**
- Automatically picks up items within 20m
- Brings items to player
- Saves time running around

#### Auto-Sorting
**Packrat (Utility Familiar)**
- Auto-sorts inventory by item type
- Stacks items automatically
- +20 inventory slots

---

## 6. Feeding & Care System

### 6.1 Hunger System

Familiars have a hunger meter (0-100):
- Decreases 1 point per hour (real-time)
- At 0 hunger: Familiar becomes "Starving"
  - -50% stats
  - Unhappy (stops gaining XP)
  - May run away if starving for 24 hours

### 6.2 Food Types & Preferences

#### Universal Foods (Any familiar)
- Fish (Common): +20 hunger
- Meat (Common/Rare): +30 hunger
- Crops: +25 hunger

#### Preferred Foods (Bonus effects)
Feeding preferred food:
- +50 hunger (fills more)
- +10 happiness
- +5 loyalty
- +50 bonus XP

**Example Preferences:**
- Rabbit: Carrots, Lettuce
- Fox: Raw Meat, Rare Fish
- Dragon: Epic+ Fish, Phoenix Pepper
- Unicorn: Crystal Carrot, Moonberry

### 6.3 Care Activities

#### Playing (Once per hour)
Mini-games with familiar:
- Fetch (throw ball, familiar retrieves)
- Hide and Seek
- Obstacle course

Rewards:
- +20 happiness
- +10 bond points
- 100 XP for familiar

#### Grooming (Once per day)
Clean and brush familiar:
- Costs: 100 IRF (brush tool)
- Effect: +30 happiness, +15 bond
- Visual: Familiar sparkles, cleaner appearance

#### Petting (Unlimited)
Simple interaction:
- Free, instant
- +5 happiness per pet (max 3/day)
- Cute animation

---

## 7. Familiar Combat

### 7.1 Combat Modes

#### Passive Mode
- Familiar does not attack
- Follows player, provides passive bonuses only
- Cannot take damage

#### Defensive Mode
- Familiar attacks only if player is attacked
- Stays near player
- Good for tanky familiars

#### Aggressive Mode
- Familiar actively seeks and attacks enemies
- May run ahead of player
- Good for DPS familiars

#### Assist Mode (Smart AI)
- Analyzes situation and chooses best action
- Tanks use defensive, DPS use aggressive
- Healer familiars prioritize healing

### 7.2 Combat AI

```lua
function FamiliarCombatAI:Update(familiar, player)
    local mode = familiar.CombatMode
    
    if mode == "Passive" then
        return -- No combat
    end
    
    -- Find nearby enemies
    local enemies = GetNearbyEnemies(familiar.Position, 30)
    
    if mode == "Defensive" then
        -- Only attack if player is in combat
        if player.InCombat then
            local target = GetClosestEnemy(player.Position, enemies)
            if target then
                familiar:Attack(target)
            end
        end
    elseif mode == "Aggressive" then
        -- Attack nearest enemy always
        local target = GetClosestEnemy(familiar.Position, enemies)
        if target then
            familiar:Attack(target)
        end
    elseif mode == "Assist" then
        -- Smart decision making
        if familiar.Role == "Tank" then
            -- Taunt enemies hitting player
            local threat = GetHighestThreatEnemy(player)
            if threat then
                familiar:Taunt(threat)
            end
        elseif familiar.Role == "Healer" then
            -- Heal player if low HP
            if player.Character.Humanoid.Health < player.Character.Humanoid.MaxHealth * 0.6 then
                familiar:HealPlayer(player)
            end
        else
            -- DPS: Attack player's target
            local target = player.CurrentTarget
            if target then
                familiar:Attack(target)
            end
        end
    end
end
```

### 7.3 Familiar Death & Revival

If familiar HP reaches 0 in combat:
- Familiar "faints" (doesn't die permanently)
- Returns to familiar storage
- Cannot be summoned for 10 minutes
- OR pay 500 IRF to instantly revive
- No XP penalty, just cooldown

Mythic familiars:
- 30-minute cooldown
- 2,000 IRF instant revival cost

---

## 8. Breeding System

### 8.1 Breeding Mechanics

Requires:
- 2 familiars of same species
- Both at max bond level (10)
- Breeding Nest structure (Private Island)
- Breeding Fee: 5,000 IRF

Process:
1. Place 2 familiars in Breeding Nest
2. Wait 24 hours (real-time)
3. Receive Egg item
4. Hatch egg (instant or incubator for better stats)

### 8.2 Offspring Stats

Baby inherits:
- **Species:** Always same as parents
- **Stats:** Average of both parents +/- 10% random
- **Rarity:** Cannot exceed parent rarity
- **Abilities:** Random from parent pool
- **Appearance:** Mix of parent colorations

**Shiny Chance:**
- Normal: 1% chance for Shiny variant (cosmetic)
- With both parents Shiny: 25% chance
- Shiny variants: Special colors, particle effects, +5% stats

### 8.3 Genetic Traits

Some traits can be passed down:
- **Speed Boost:** +10% movement speed (20% inherit chance)
- **Hardy:** +20% HP (15% inherit chance)
- **Aggressive:** +15% Attack (20% inherit chance)
- **Gentle:** +10% XP gain (10% inherit chance)

Perfect breeding (both parents with desired trait):
- 50% chance to inherit
- 5% chance to get enhanced version (+50% effect)

---

## 9. Habitat & Housing

### 9.1 Familiar Storage

**Familiar Barn (Private Island)**
- Free structure, unlocked at Level 10
- Stores up to 20 familiars
- Familiars rest here when not active
- Can interact with stored familiars

**Expanded Storage:**
- +10 slots: 5,000 IRF or 200 Robux
- +20 slots: 10,000 IRF or 400 Robux
- Max: 100 familiars

### 9.2 Habitat Customization

Players can build habitats on Private Island:

**Forest Habitat**
- Cost: 10,000 IRF
- Suitable for: Rabbits, Foxes, Birds
- Bonus: +10% happiness for forest creatures
- Features: Trees, grass, rocks

**Aquatic Habitat**
- Cost: 15,000 IRF
- Suitable for: Sea Turtles, Dolphins, Water creatures
- Bonus: +15% happiness for water creatures
- Features: Pond, waterfall

**Volcanic Habitat**
- Cost: 25,000 IRF
- Suitable for: Fire creatures, Phoenix
- Bonus: +20% happiness for fire creatures
- Features: Lava pool, obsidian rocks

### 9.3 Display & Showcasing

**Familiar Showcase Stand**
- Displays one familiar as decoration
- Visitors can view and inspect
- Shows stats, level, bond
- Earns "likes" from visitors (social currency)

---

## 10. Technical Implementation

### 10.1 Data Structure

```lua
-- Familiar Instance
FamiliarInstance = {
    InstanceId = "UUID", -- Unique ID for this familiar
    OwnerId = 12345, -- Player UserId
    FamiliarId = "FIRE_WOLF", -- Type
    
    -- Stats
    Level = 25,
    XP = 5432,
    HP = 2000,
    MaxHP = 2500,
    Attack = 150,
    Defense = 75,
    Magic = 50,
    
    -- Status
    Hunger = 85,
    Happiness = 90,
    Loyalty = 95,
    BondLevel = 6,
    BondPoints = 1650,
    
    -- Customization
    Nickname = "Blaze",
    IsShiny = false,
    Accessories = {"RED_COLLAR", "FIRE_WINGS"},
    
    -- Abilities
    Abilities = {
        "FLAME_BITE",
        "FIRE_DASH"
    },
    AbilityCooldowns = {},
    
    -- Breeding
    CanBreed = true,
    BreedCount = 2,
    
    -- Metadata
    CaughtAt = 1707350400,
    CaughtLocation = "Volcanic_Core",
    PlayTime = 86400 -- seconds
}
```

### 10.2 Saving & Loading

```lua
function FamiliarDataService:SaveFamiliar(familiar)
    local data = {
        InstanceId = familiar.InstanceId,
        FamiliarId = familiar.FamiliarId,
        Level = familiar.Level,
        XP = familiar.XP,
        BondLevel = familiar.BondLevel,
        BondPoints = familiar.BondPoints,
        Nickname = familiar.Nickname,
        -- ... all stats
    }
    
    FamiliarDataStore:SetAsync(familiar.InstanceId, data)
end

function FamiliarDataService:LoadFamiliar(instanceId)
    local data = FamiliarDataStore:GetAsync(instanceId)
    
    if data then
        local familiar = FamiliarService:CreateFamiliarInstance(data)
        return familiar
    end
    
    return nil
end
```

### 10.3 Network Optimization

Familiar sync uses StreamingEnabled:
- Only sync active familiar's data
- Stored familiars: Metadata only (no 3D model)
- Update positions every 0.1 seconds
- Batch ability calls with RemoteEvents

---

## Implementation Checklist

### Phase 1: Core Taming (Month 4)
- [ ] Taming mechanics (HP threshold, success calculation)
- [ ] 10 common/rare familiars
- [ ] Basic familiar following AI
- [ ] Feeding system
- [ ] Familiar storage UI

### Phase 2: Combat & Abilities (Month 5)
- [ ] Combat familiar AI (modes)
- [ ] 5 combat abilities implementation
- [ ] Passive bonus system
- [ ] Familiar leveling and stats
- [ ] Bond level system

### Phase 3: Advanced Features (Month 6)
- [ ] Legendary/Mythic familiars
- [ ] Breeding system
- [ ] Habitat customization
- [ ] Shiny variants
- [ ] Care activities (playing, grooming)

### Phase 4: Polish (Month 7)
- [ ] Mount system integration
- [ ] Familiar achievements
- [ ] Trading system
- [ ] Showcase features
- [ ] Balance tuning

---

## Related Documentation
- [Database_Crops.md](Database_Crops.md) - Familiar food sources
- [Database_Fish.md](Database_Fish.md) - Familiar food sources
- [GDD_Systems_PrivateIsland.md](GDD_Systems_PrivateIsland.md) - Habitat placement
- [GDD_Systems_Combat.md](GDD_Systems_Combat.md) - Combat integration

---

**Document End - Taming & Familiar System Design**  
*A comprehensive creature collection and companion system*
