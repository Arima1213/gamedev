# IRIFA: Realms of Harvest & Adventure
## Reference Document - Status Effects & Modifiers

---

### Document Information
**Document Type:** Technical Reference  
**Category:** Game Mechanics  
**Version:** 1.0  
**Last Updated:** February 9, 2026  
**Purpose:** Complete reference for all buffs, debuffs, and stat modifiers in the game

---

## Table of Contents
1. [Overview](#1-overview)
2. [Player Stats Reference](#2-player-stats-reference)
3. [Combat Status Effects](#3-combat-status-effects)
4. [Buff Effects](#4-buff-effects)
5. [Debuff Effects](#5-debuff-effects)
6. [Environmental Effects](#6-environmental-effects)
7. [Proficiency Modifiers](#7-proficiency-modifiers)
8. [Duration Types](#8-duration-types)
9. [Stacking Rules](#9-stacking-rules)
10. [Implementation Guide](#10-implementation-guide)

---

## 1. Overview

### 1.1 Purpose
This document serves as the **master reference** for all status effects, buffs, debuffs, and stat modifiers that can affect players, familiars, and enemies in IRIFA.

### 1.2 Usage
**For Designers:** Use this reference when creating items, abilities, or game mechanics
**For Developers:** Implement these effects with standardized names and values
**For Balance Team:** Understand all modifier sources for balancing

### 1.3 Effect Categories
- **Combat Effects:** Stun, slow, damage over time
- **Stat Buffs:** Increase player stats temporarily
- **Stat Debuffs:** Decrease player stats temporarily
- **Environmental Effects:** Weather, biome-specific
- **Proficiency Modifiers:** Increase gathering/crafting efficiency
- **Passive Bonuses:** Permanent effects from equipment/familiars

---

## 2. Player Stats Reference

### 2.1 Core Combat Stats

#### Health Points (HP)
**Base Value:** 2,000 at Level 1, +100 per level
**Can be Modified By:**
- Equipment: +HP from armor
- Food buffs: Temporary HP increase
- Familiar bonuses: Passive HP boost
- Healing effects: Restore HP over time

**Formula:** `Current HP / Max HP`

---

#### Attack Damage
**Base Value:** 50 at Level 1, +5 per level
**Can be Modified By:**
- Weapon damage: Primary source
- Equipment bonuses: +Attack from armor/accessories
- Buff potions: Temporary attack increase
- Familiar bonuses: Passive damage boost
- Critical hits: 150-300% damage multiplier

**Usage:** Base damage for all physical attacks

---

#### Defense
**Base Value:** 10 at Level 1, +2 per level
**Can be Modified By:**
- Armor pieces: Primary defense source
- Buff potions: Temporary defense increase
- Familiar bonuses: Passive defense boost
- Debuffs: Armor reduction effects

**Formula for Damage Reduction:** `Damage Taken = Base Damage × (100 / (100 + Defense))`
- 100 Defense = 50% damage reduction
- 200 Defense = 66% damage reduction
- 400 Defense = 80% damage reduction

---

#### Critical Chance
**Base Value:** 5%
**Can be Modified By:**
- Equipment bonuses: +Crit% from weapons/armor
- Buff potions: Temporary crit increase
- Familiar bonuses: Passive crit boost
- Skills: Combat proficiency increases crit

**Cap:** 75% maximum (cannot exceed)

---

#### Critical Damage
**Base Value:** 150% (1.5× normal damage)
**Can be Modified By:**
- Equipment bonuses: +Crit Damage%
- Buff potions: Temporary multiplier increase
- Familiar bonuses: Passive crit damage boost

**Cap:** 300% maximum (3× normal damage)

---

### 2.2 Movement & Speed Stats

#### Movement Speed
**Base Value:** 16 studs/second (Roblox standard)
**Can be Modified By:**
- Equipment weight: Heavy armor = slower
- Buff potions: Speed boost
- Familiar bonuses: +Movement Speed%
- Status effects: Slow, sprint, frozen
- Mounts: 150-200% speed increase

**Effects:**
- **Sprint Buff:** +50% movement speed (temporary)
- **Slow Debuff:** -30% to -50% movement speed
- **Frozen:** 0% movement speed (cannot move)
- **Mount:** +50% to +100% depending on mount type

**Minimum:** 50% of base speed (cannot go below 8 studs/sec)
**Maximum:** 300% of base speed (48 studs/sec with mount)

---

#### Attack Speed
**Base Value:** 1.0 attacks per second (varies by weapon type)
**Can be Modified By:**
- Weapon type: Fast (1.5/sec), Normal (1.0/sec), Slow (0.7/sec)
- Equipment bonuses: +Attack Speed%
- Buff potions: Haste effect
- Debuffs: Fatigue, slow

**Effects:**
- **Haste Buff:** +20% to +50% attack speed
- **Fatigue Debuff:** -30% attack speed

**Minimum:** 50% of base speed
**Maximum:** 200% of base speed

---

### 2.3 Proficiency Stats

#### Gathering Speed
**Base Value:** 1.0× (100%)
**Affects:** Mining, Fishing, Farming, Harvesting speed
**Can be Modified By:**
- Tool quality: Better tools = faster gathering
- Familiar bonuses: +Gathering Speed%
- Buff potions: Efficiency boost
- Proficiency level: Higher level = faster

**Effects:**
- **+10% Gathering Speed:** Reduces action time by 10%
- **+50% Gathering Speed:** Reduces action time by 50%

**Example:** Mining a rock takes 5 seconds base
- With +20% gathering speed: 5 / 1.2 = 4.17 seconds
- With +50% gathering speed: 5 / 1.5 = 3.33 seconds

---

#### Drop Rate / Luck
**Base Value:** 0% (no bonus)
**Affects:** Rare item drops, quality chances
**Can be Modified By:**
- Equipment bonuses: +Luck
- Familiar bonuses: +Drop Rate%
- Buff potions: Fortune effect
- Weather: Full moon = +10% luck
- Events: Special events = +Luck

**Effects:**
- **+10% Luck:** Increases rare drop chance by 10%
- **+50% Luck:** Significantly increases rare drops

**Example:** Legendary fish has 2% base catch rate
- With +50% luck: 2% × 1.5 = 3% catch rate

---

#### Experience Gain
**Base Value:** 100% (1.0×)
**Affects:** XP earned from all activities
**Can be Modified By:**
- VIP Pass: +25% XP
- Familiar bonuses: +XP%
- Buff potions: Experience boost
- Events: Double XP weekends

**Effects:**
- **+25% XP:** Earn 125 XP instead of 100 XP
- **+100% XP (Double XP):** Earn 200 XP instead of 100 XP

**Stacking:** All XP bonuses are multiplicative
- Example: +25% VIP + +10% Familiar + 2× Event = 100 × 1.25 × 1.1 × 2 = 275 XP

---

## 3. Combat Status Effects

### 3.1 Crowd Control (Hard CC)

#### Stun
**Description:** Player/enemy cannot move, attack, or use abilities
**Duration:** 1-5 seconds (typical: 2 seconds)
**Visual:** Stars spinning above head
**Can Affect:** Players, Enemies
**Sources:**
- Boss abilities
- Golem slam attacks
- Crystal Golem familiar ability
- Certain weapon special abilities

**Implementation:**
```lua
StatusEffect.Stun = {
    Name = "Stunned",
    Type = "HardCC",
    Duration = 2, -- seconds
    Effects = {
        MovementSpeed = 0, -- Cannot move
        AttackSpeed = 0, -- Cannot attack
        AbilitiesDisabled = true
    },
    Visual = "StunStars" -- Particle effect
}
```

---

#### Freeze / Frozen
**Description:** Player/enemy frozen in ice, cannot move or attack
**Duration:** 2-4 seconds
**Visual:** Ice block encasing character
**Can Affect:** Players, Enemies
**Sources:**
- Ice Fox familiar ability
- Frost Wyrm familiar breath attack
- Winter event boss attacks
- Certain weapons

**Implementation:**
```lua
StatusEffect.Frozen = {
    Name = "Frozen",
    Type = "HardCC",
    Duration = 3, -- seconds
    Effects = {
        MovementSpeed = 0,
        AttackSpeed = 0,
        DefenseModifier = 1.2 -- Takes 20% more damage
    },
    Visual = "IceBlock"
}
```

---

#### Knockback
**Description:** Player/enemy pushed back forcefully
**Duration:** 0.5-1 second (short duration)
**Distance:** 5-15 studs
**Can Affect:** Players, Enemies
**Sources:**
- Heavy weapon attacks (hammers)
- Boss charge attacks
- Explosions
- Storm Hawk familiar wing attack

**Implementation:**
```lua
StatusEffect.Knockback = {
    Name = "Knocked Back",
    Type = "Displacement",
    Duration = 0.8,
    Distance = 10, -- studs
    CanCancelActions = true -- Interrupts current action
}
```

---

### 3.2 Movement Impairing (Soft CC)

#### Slow
**Description:** Reduces movement and attack speed
**Duration:** 3-10 seconds
**Intensity:** -30% to -50% speed reduction
**Can Affect:** Players, Enemies
**Visual:** Blue aura/particles
**Sources:**
- Ice Fox familiar frost bite
- Frost Wyrm blizzard
- Certain enemy abilities
- Trap effects

**Implementation:**
```lua
StatusEffect.Slow = {
    Name = "Slowed",
    Type = "SoftCC",
    Duration = 5,
    Effects = {
        MovementSpeedModifier = 0.7, -- 30% slower
        AttackSpeedModifier = 0.8 -- 20% slower
    },
    Visual = "SlowAura",
    Stacks = false -- Does not stack with itself
}
```

---

#### Root / Entangle
**Description:** Player/enemy cannot move but can still attack
**Duration:** 2-5 seconds
**Can Affect:** Players, Enemies
**Visual:** Vines/roots wrapping legs
**Sources:**
- Nature-based attacks
- Trap abilities
- Certain boss mechanics

**Implementation:**
```lua
StatusEffect.Root = {
    Name = "Rooted",
    Type = "SoftCC",
    Duration = 3,
    Effects = {
        MovementSpeed = 0, -- Cannot move
        AttackSpeed = 1.0, -- Can still attack
        CanUseAbilities = true
    },
    Visual = "VineWrap"
}
```

---

### 3.3 Damage Over Time (DoT)

#### Burn
**Description:** Takes fire damage over time
**Duration:** 5-10 seconds
**Damage:** 20-100 damage per tick (1 second intervals)
**Can Affect:** Players, Enemies
**Visual:** Fire particles on character
**Sources:**
- Fire Wolf familiar flame bite
- Phoenix familiar attacks
- Volcanic hazards
- Fire-based weapon abilities

**Implementation:**
```lua
StatusEffect.Burn = {
    Name = "Burning",
    Type = "DoT",
    Duration = 5,
    DamagePerTick = 50,
    TickInterval = 1, -- seconds
    TotalDamage = 250, -- 50 × 5 ticks
    Visual = "FireParticles",
    Stacks = true, -- Can have multiple burn stacks
    MaxStacks = 3
}
```

**Resistance:** Heat Resistance reduces burn damage and duration

---

#### Poison
**Description:** Takes poison damage over time, reduces healing
**Duration:** 10-15 seconds
**Damage:** 15-50 damage per tick (2 second intervals)
**Can Affect:** Players, Enemies
**Visual:** Green poison cloud around character
**Sources:**
- Poison dart traps
- Certain enemy attacks
- Poisoned weapons (future)

**Implementation:**
```lua
StatusEffect.Poison = {
    Name = "Poisoned",
    Type = "DoT",
    Duration = 10,
    DamagePerTick = 30,
    TickInterval = 2,
    TotalDamage = 150,
    Effects = {
        HealingReceivedModifier = 0.5 -- 50% less healing
    },
    Visual = "PoisonCloud",
    Stacks = true,
    MaxStacks = 5
}
```

---

#### Bleed
**Description:** Takes physical damage over time from wounds
**Duration:** 6-12 seconds
**Damage:** 25-80 damage per tick (1 second intervals)
**Can Affect:** Players, Enemies
**Visual:** Blood drops
**Sources:**
- Critical hits from sharp weapons
- Certain enemy claw attacks
- Bleed-enchanted weapons

**Implementation:**
```lua
StatusEffect.Bleed = {
    Name = "Bleeding",
    Type = "DoT",
    Duration = 8,
    DamagePerTick = 40,
    TickInterval = 1,
    TotalDamage = 320,
    Effects = {
        MovementSpeedModifier = 0.9 -- 10% slower
    },
    Visual = "BloodDrops",
    Stacks = true,
    MaxStacks = 3,
    RemoveOnHeal = true -- Healing removes bleed
}
```

---

## 4. Buff Effects

### 4.1 Combat Buffs

#### Attack Boost
**Description:** Increases attack damage
**Duration:** 30 seconds - 5 minutes
**Intensity:** +10% to +50% attack damage
**Sources:**
- Food buffs
- Potions
- Familiar passive bonuses
- Equipment set bonuses

**Implementation:**
```lua
StatusEffect.AttackBoost = {
    Name = "Attack Boost",
    Type = "Buff",
    Duration = 60, -- seconds
    Effects = {
        AttackModifier = 1.25 -- 25% more damage
    },
    Visual = "RedAuraUp",
    Icon = "IconAttackUp",
    Stacks = false -- Only highest buff applies
}
```

---

#### Defense Boost
**Description:** Increases defense/damage reduction
**Duration:** 30 seconds - 5 minutes
**Intensity:** +10% to +50% defense
**Sources:**
- Food buffs
- Potions
- Familiar passive bonuses
- Defensive abilities

**Implementation:**
```lua
StatusEffect.DefenseBoost = {
    Name = "Defense Boost",
    Type = "Buff",
    Duration = 60,
    Effects = {
        DefenseModifier = 1.3 -- 30% more defense
    },
    Visual = "BlueShield",
    Icon = "IconDefenseUp",
    Stacks = false
}
```

---

#### Critical Strike Chance Boost
**Description:** Increases critical hit chance
**Duration:** 30 seconds - 2 minutes
**Intensity:** +5% to +25% crit chance
**Sources:**
- Food buffs
- Potions
- Temporary abilities

**Implementation:**
```lua
StatusEffect.CritBoost = {
    Name = "Critical Focus",
    Type = "Buff",
    Duration = 45,
    Effects = {
        CritChanceBonus = 15 -- +15% crit chance
    },
    Visual = "GoldenGlow",
    Icon = "IconCritUp"
}
```

---

#### Haste
**Description:** Increases attack speed and movement speed
**Duration:** 20-60 seconds
**Intensity:** +15% to +50% speed
**Sources:**
- Potions
- Abilities
- Equipment set bonuses

**Implementation:**
```lua
StatusEffect.Haste = {
    Name = "Haste",
    Type = "Buff",
    Duration = 30,
    Effects = {
        AttackSpeedModifier = 1.3, -- 30% faster attacks
        MovementSpeedModifier = 1.2 -- 20% faster movement
    },
    Visual = "SpeedLines",
    Icon = "IconHaste"
}
```

---

#### Regeneration
**Description:** Restores HP over time
**Duration:** 10-60 seconds
**Healing:** 50-200 HP per tick (2-3 second intervals)
**Sources:**
- Food buffs
- Healing potions
- Unicorn familiar aura
- Resting in safe zones

**Implementation:**
```lua
StatusEffect.Regeneration = {
    Name = "Regeneration",
    Type = "HoT", -- Heal over Time
    Duration = 30,
    HealPerTick = 100,
    TickInterval = 3,
    TotalHealing = 1000, -- 100 × 10 ticks
    Visual = "GreenHeartbeat",
    Icon = "IconRegen",
    Stacks = true,
    MaxStacks = 2
}
```

---

### 4.2 Gathering & Proficiency Buffs

#### Gathering Speed Boost
**Description:** Increases mining, fishing, farming speed
**Duration:** 5-30 minutes
**Intensity:** +10% to +50% gathering speed
**Sources:**
- Food buffs
- Familiar passive bonuses
- Tool enchantments
- Proficiency level bonuses

**Implementation:**
```lua
StatusEffect.GatheringSpeed = {
    Name = "Efficient Gathering",
    Type = "Buff",
    Duration = 600, -- 10 minutes
    Effects = {
        MiningSpeedModifier = 1.25, -- 25% faster
        FishingSpeedModifier = 1.25,
        FarmingSpeedModifier = 1.25
    },
    Icon = "IconGatherSpeed"
}
```

---

#### Luck / Fortune
**Description:** Increases rare drop chances and quality
**Duration:** 10-60 minutes
**Intensity:** +10% to +50% luck
**Sources:**
- Food buffs
- Potions (2× Luck Potion)
- Familiar passive bonuses
- Full moon event
- Equipment bonuses

**Implementation:**
```lua
StatusEffect.Luck = {
    Name = "Fortune",
    Type = "Buff",
    Duration = 1800, -- 30 minutes
    Effects = {
        LuckModifier = 1.3, -- 30% better luck
        RareDropChanceBonus = 0.3, -- +30% rare drops
        QualityChanceBonus = 0.2 -- +20% perfect quality
    },
    Visual = "GoldenSparkles",
    Icon = "IconLuck",
    Stacks = true -- Multiple sources multiply
}
```

---

#### Experience Boost
**Description:** Increases XP gain from all activities
**Duration:** 30 minutes - 24 hours
**Intensity:** +25% to +200% XP
**Sources:**
- VIP Pass (+25% permanent)
- 2× XP events (+100%)
- 2× XP potions (purchased or earned)
- Familiar bonuses
- Equipment bonuses

**Implementation:**
```lua
StatusEffect.XPBoost = {
    Name = "Experience Boost",
    Type = "Buff",
    Duration = 3600, -- 1 hour
    Effects = {
        XPModifier = 2.0 -- Double XP
    },
    Icon = "IconXPBoost",
    Stacks = true -- All bonuses multiply
}
```

---

### 4.3 Utility Buffs

#### Night Vision
**Description:** See better in darkness
**Duration:** Permanent (while familiar equipped) or 5-10 minutes (potion)
**Sources:**
- Bat familiar
- Owl familiar
- Night vision potions

**Implementation:**
```lua
StatusEffect.NightVision = {
    Name = "Night Vision",
    Type = "Utility",
    Duration = -1, -- Permanent (familiar-based)
    Effects = {
        BrightnessBoost = 2.0, -- 2× brightness at night
        ViewDistance = 1.5 -- See 50% farther
    },
    Visual = "GlowingEyes"
}
```

---

#### Water Breathing
**Description:** Breathe underwater indefinitely
**Duration:** Permanent (mount) or 5-10 minutes (potion)
**Sources:**
- Sea Turtle mount
- Water breathing potions

**Implementation:**
```lua
StatusEffect.WaterBreathing = {
    Name = "Water Breathing",
    Type = "Utility",
    Duration = -1,
    Effects = {
        OxygenUnlimited = true,
        SwimSpeedModifier = 1.5 -- 50% faster swimming
    }
}
```

---

#### Sprint
**Description:** Temporary speed burst
**Duration:** 5-10 seconds
**Cooldown:** 30 seconds
**Sources:**
- Player ability (sprint key)
- Certain equipment
- Potions

**Implementation:**
```lua
StatusEffect.Sprint = {
    Name = "Sprinting",
    Type = "Utility",
    Duration = 5,
    Effects = {
        MovementSpeedModifier = 1.5 -- 50% faster
    },
    Cooldown = 30,
    StaminaCost = 20 -- Drains stamina
}
```

---

## 5. Debuff Effects

### 5.1 Combat Debuffs

#### Weakness
**Description:** Reduces attack damage
**Duration:** 10-30 seconds
**Intensity:** -20% to -50% attack reduction
**Sources:**
- Enemy curse abilities
- Certain boss attacks

**Implementation:**
```lua
StatusEffect.Weakness = {
    Name = "Weakened",
    Type = "Debuff",
    Duration = 15,
    Effects = {
        AttackModifier = 0.7 -- 30% less damage
    },
    Visual = "GrayAuraDown",
    Icon = "IconWeakness"
}
```

---

#### Armor Break
**Description:** Reduces defense
**Duration:** 5-20 seconds
**Intensity:** -20% to -50% defense reduction
**Sources:**
- Heavy enemy attacks
- Armor-piercing abilities
- Boss mechanics

**Implementation:**
```lua
StatusEffect.ArmorBreak = {
    Name = "Armor Broken",
    Type = "Debuff",
    Duration = 10,
    Effects = {
        DefenseModifier = 0.5 -- 50% less defense
    },
    Visual = "CrackedArmor",
    Icon = "IconArmorBreak"
}
```

---

#### Blind
**Description:** Reduces vision range and accuracy
**Duration:** 3-8 seconds
**Effects:** Cannot see enemies clearly, -50% accuracy
**Sources:**
- Flash bomb attacks
- Certain enemy abilities
- Environmental hazards

**Implementation:**
```lua
StatusEffect.Blind = {
    Name = "Blinded",
    Type = "Debuff",
    Duration = 5,
    Effects = {
        ViewDistance = 0.3, -- 70% reduced vision
        AccuracyModifier = 0.5 -- 50% miss chance
    },
    Visual = "BlackScreen" -- Dark overlay
}
```

---

#### Fatigue / Exhaustion
**Description:** Reduces attack speed and stamina regeneration
**Duration:** 20-60 seconds
**Sources:**
- Overexertion
- Boss drain abilities
- Starvation (low hunger)

**Implementation:**
```lua
StatusEffect.Fatigue = {
    Name = "Exhausted",
    Type = "Debuff",
    Duration = 30,
    Effects = {
        AttackSpeedModifier = 0.7, -- 30% slower attacks
        StaminaRegenModifier = 0.5, -- 50% slower stamina regen
        MovementSpeedModifier = 0.9 -- 10% slower movement
    },
    Visual = "PantingBreath",
    Icon = "IconFatigue"
}
```

---

### 5.2 Environmental Debuffs

#### Cold / Hypothermia
**Description:** Takes cold damage over time, slowed movement
**Duration:** Persistent (while in cold area without protection)
**Damage:** 10-50 damage per tick (3 second intervals)
**Sources:**
- Ice biome without cold resistance
- Winter weather without proper gear
- Snow areas

**Implementation:**
```lua
StatusEffect.Cold = {
    Name = "Cold",
    Type = "Environmental",
    Duration = -1, -- Persistent in cold areas
    DamagePerTick = 20,
    TickInterval = 3,
    Effects = {
        MovementSpeedModifier = 0.8, -- 20% slower
        AttackSpeedModifier = 0.9 -- 10% slower
    },
    Visual = "ShiveringEffect",
    Icon = "IconCold",
    Resistance = "ColdResistance" -- Negated by cold resistance
}
```

---

#### Heat Exhaustion
**Description:** Takes heat damage, reduced stamina
**Duration:** Persistent (while in hot area without protection)
**Damage:** 10-50 damage per tick
**Sources:**
- Volcanic biome without heat resistance
- Desert areas
- Near lava

**Implementation:**
```lua
StatusEffect.HeatExhaustion = {
    Name = "Heat Exhaustion",
    Type = "Environmental",
    Duration = -1,
    DamagePerTick = 25,
    TickInterval = 3,
    Effects = {
        StaminaDrainRate = 2.0, -- 2× stamina drain
        MovementSpeedModifier = 0.85 -- 15% slower
    },
    Visual = "SweatDrops",
    Icon = "IconHeat",
    Resistance = "HeatResistance"
}
```

---

#### Drowning
**Description:** Takes damage while underwater without oxygen
**Duration:** Persistent (while underwater without air)
**Damage:** 50-100 damage per tick (1 second intervals)
**Sources:**
- Staying underwater too long
- Oxygen runs out

**Implementation:**
```lua
StatusEffect.Drowning = {
    Name = "Drowning",
    Type = "Environmental",
    Duration = -1,
    DamagePerTick = 75,
    TickInterval = 1,
    Visual = "BubblesGasping",
    Icon = "IconDrowning",
    Resistance = "WaterBreathing" -- Negated by water breathing
}
```

---

## 6. Environmental Effects

### 6.1 Weather Modifiers

#### Rain Bonus
**Description:** Increases fishing catch rate and crop growth
**Duration:** While raining (10-30 minutes game time)
**Effects:**
- **Fishing:** +30% catch rate
- **Farming:** 2× crop growth speed
**Implementation:**
```lua
EnvironmentModifier.Rain = {
    Name = "Rainy Weather",
    Type = "Weather",
    Effects = {
        FishingCatchRateBonus = 0.3,
        CropGrowthRateModifier = 2.0
    }
}
```

---

#### Night Bonus
**Description:** Increases rare ore spawns and combat XP
**Duration:** Night time (20 minutes game time)
**Effects:**
- **Mining:** +30% rare ore spawn rate
- **Combat:** +20% XP gain
- **Taming:** Legendary creatures may spawn
**Implementation:**
```lua
EnvironmentModifier.Night = {
    Name = "Nighttime",
    Type = "TimeOfDay",
    Effects = {
        RareOreSpawnBonus = 0.3,
        CombatXPModifier = 1.2,
        LegendaryCreatureSpawn = true
    }
}
```

---

#### Full Moon Bonus
**Description:** Increases luck and legendary creature spawns
**Duration:** Full moon phase (1 night per 8-day cycle)
**Effects:**
- **Luck:** +10% to all luck-based rolls
- **Taming:** Unicorn can spawn
- **Fishing:** Rare fish spawn rate increased
**Implementation:**
```lua
EnvironmentModifier.FullMoon = {
    Name = "Full Moon",
    Type = "MoonPhase",
    Effects = {
        LuckBonus = 0.1,
        UnicornSpawnEnabled = true,
        RareFishSpawnBonus = 0.25
    }
}
```

---

### 6.2 Biome Effects

#### Volcanic Heat
**Description:** Persistent heat damage in volcanic areas
**Mitigation:** Heat resistance equipment or Fire Wolf familiar
**See:** Heat Exhaustion status effect above

---

#### Arctic Cold
**Description:** Persistent cold damage in ice biome
**Mitigation:** Cold resistance equipment or Ice Fox familiar
**See:** Cold status effect above

---

## 7. Proficiency Modifiers

### 7.1 Mining Proficiency Bonuses

**Level 10:** +5% mining speed
**Level 25:** +10% rare ore chance, unlock gold pickaxe
**Level 50:** +15% mining speed, +5% geode chance
**Level 75:** +20% rare ore chance, unlock diamond pickaxe
**Level 100:** +25% mining speed, +15% rare ore chance, unlock mythril pickaxe

---

### 7.2 Fishing Proficiency Bonuses

**Level 10:** +5% catch rate
**Level 25:** +10% rare fish chance, unlock better rod
**Level 50:** +15% catch rate, mini-game timer +2 seconds
**Level 75:** +20% rare fish chance, unlock legendary rod
**Level 100:** +25% catch rate, +25% rare fish chance

---

### 7.3 Combat Proficiency Bonuses

**Level 10:** +2% critical chance
**Level 25:** +5% damage, +3% critical chance
**Level 50:** +10% damage, +5% critical chance, +10% critical damage
**Level 75:** +15% damage, +7% critical chance
**Level 100:** +20% damage, +10% critical chance, +25% critical damage

---

## 8. Duration Types

### 8.1 Duration Categories

**Instant:** Immediate effect, no duration (e.g., heal, damage)
**Short:** 1-10 seconds (stuns, knockbacks)
**Medium:** 10-60 seconds (combat buffs)
**Long:** 1-30 minutes (food buffs, potions)
**Persistent:** Lasts until condition ends (weather, biome, equipment)
**Permanent:** Lasts forever until removed (passive bonuses)

---

## 9. Stacking Rules

### 9.1 Buff Stacking

**Same Source, Same Type:** Does NOT stack (only highest applies)
- Example: Two attack boost potions = only strongest counts

**Different Sources:** DOES stack (multiplicative)
- Example: Attack boost potion + familiar bonus + equipment = all apply
- Formula: `FinalDamage = BaseDamage × (1 + Buff1) × (1 + Buff2) × (1 + Buff3)`

**DoT Stacking:** DOES stack (additive)
- Example: 3 burn stacks = 3× damage per tick
- Usually capped at 3-5 stacks maximum

---

## 10. Implementation Guide

### 10.1 Lua Status Effect System

```lua
-- Status Effect Manager
StatusEffectService = {}
StatusEffectService.ActiveEffects = {} -- [Player] = {EffectID, ...}

function StatusEffectService:ApplyEffect(target, effectData)
    local effect = {
        Name = effectData.Name,
        Type = effectData.Type,
        Duration = effectData.Duration,
        StartTime = os.time(),
        Effects = effectData.Effects,
        Visual = effectData.Visual,
        Icon = effectData.Icon
    }
    
    -- Check stacking rules
    if not effectData.Stacks then
        -- Remove existing effect of same type
        self:RemoveEffectByName(target, effectData.Name)
    end
    
    -- Apply stat modifiers
    for stat, modifier in pairs(effectData.Effects) do
        if stat == "AttackModifier" then
            target.Stats.Attack = target.Stats.BaseAttack * modifier
        elseif stat == "DefenseModifier" then
            target.Stats.Defense = target.Stats.BaseDefense * modifier
        elseif stat == "MovementSpeedModifier" then
            target.Character.Humanoid.WalkSpeed = 16 * modifier
        -- ... other stat modifications
        end
    end
    
    -- Start visual effects
    if effectData.Visual then
        self:PlayVisualEffect(target, effectData.Visual)
    end
    
    -- Add to active effects
    table.insert(self.ActiveEffects[target], effect)
    
    -- Schedule removal
    if effectData.Duration > 0 then
        task.delay(effectData.Duration, function()
            self:RemoveEffect(target, effect)
        end)
    end
    
    return effect
end

function StatusEffectService:RemoveEffect(target, effect)
    -- Remove stat modifiers
    -- Stop visual effects
    -- Remove from active effects table
end

function StatusEffectService:UpdateEffects()
    -- Called every frame or second
    -- Update DoT/HoT ticks
    -- Check duration expiration
    -- Update UI displays
end
```

---

### 10.2 Naming Conventions

**For Designers:**
- Use descriptive names: "Attack Boost" not "Buff1"
- Include intensity in name: "Minor Speed Boost" vs "Major Speed Boost"
- Be consistent with terminology

**For Developers:**
- Use EffectID constants: `StatusEffect.Stun`, `StatusEffect.AttackBoost`
- Prefix with type: `Buff_AttackBoost`, `Debuff_Weakness`, `DoT_Burn`

---

### 10.3 Balance Guidelines

**Stuns:**
- Keep short (1-3 seconds on players)
- Longer on minions (2-5 seconds)
- Very long on bosses makes them trivial (use resistance)

**DoT Effects:**
- Total damage should be 50-80% of instant damage spell
- Example: Instant 500 damage vs. 400 damage over 8 seconds

**Movement Speed:**
- Never reduce below 50% of base speed (too frustrating)
- Never increase above 300% (breaks navigation, hard to control)

**Buffs:**
- Keep combat buffs short (30-60 seconds)
- Gathering buffs can be longer (5-30 minutes)
- Never make buffs mandatory for progression

---

## Quick Reference Table

### Common Effect Values

| Effect | Weak | Moderate | Strong | Very Strong |
|--------|------|----------|--------|-------------|
| **Attack Boost** | +10% | +25% | +40% | +60% |
| **Defense Boost** | +10% | +25% | +40% | +60% |
| **Speed Boost** | +10% | +25% | +40% | +60% |
| **Slow Debuff** | -20% | -35% | -50% | -70% |
| **Burn DoT** | 20/tick | 50/tick | 100/tick | 200/tick |
| **Stun Duration** | 1 sec | 2 sec | 3 sec | 5 sec |
| **Luck Bonus** | +10% | +25% | +50% | +100% |
| **XP Bonus** | +10% | +25% | +50% | +100% |

---

## Related Documentation
- [GDD_Systems_Combat.md](GDD_Systems_Combat.md) - Combat system details
- [Database_Weapons.md](Database_Weapons.md) - Weapon special effects
- [Database_Armor.md](Database_Armor.md) - Armor set bonuses
- [Database_Familiars.md](Database_Familiars.md) - Familiar passive bonuses
- [GDD_Systems_Weather.md](GDD_Systems_Weather.md) - Environmental effects

---

**Document End - Status Effects & Modifiers Reference**  
*Your complete guide to all buffs, debuffs, and stat modifications in IRIFA*
