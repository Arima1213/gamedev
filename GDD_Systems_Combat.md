# Game Design Document
## Combat System

---

### Document Information
**System Name:** Combat System  
**Document Version:** 1.0  
**Last Updated:** February 8, 2026  
**Owner:** Combat Design Team  
**Status:** Ready for Implementation

---

## Table of Contents
1. [System Overview](#system-overview)
2. [Player Stats](#player-stats)
3. [Combat Mechanics](#combat-mechanics)
4. [Weapon System](#weapon-system)
5. [Armor System](#armor-system)
6. [Enemy AI](#enemy-ai)
7. [Damage Calculation](#damage-calculation)
8. [Special Effects](#special-effects)
9. [Boss Encounters](#boss-encounters)
10. [Technical Implementation](#technical-implementation)

---

## 1. System Overview

### Purpose
The Combat System provides engaging dungeon exploration with risk-reward dynamics. Players fight monsters to obtain materials for crafting while protecting themselves during mining operations.

### Design Goals
- **Accessible Depth**: Easy to learn, hard to master
- **Build Variety**: Multiple viable equipment combinations
- **Skill Expression**: Dodge timing and ability management
- **Risk Management**: Balance aggression with survival
- **Progression Clarity**: Clear path to power increases

### Player Value Proposition
*"Combat provides thrilling action gameplay with meaningful progression through equipment, offering both challenge and reward for skilled players."*

---

## 2. Player Stats

### 2.1 Core Stats

**Health Points (HP):**
- Base HP: 2,000 (Level 1)
- HP per level: +100
- Armor bonus: +HP from armor pieces
- Display: Current/Max (e.g., 1,650/2,000)
- Regeneration: 1% per second out of combat (3 sec delay)

**Attack Damage:**
- Base Damage: 20 (fixed, all players)
- Weapon Damage: Added from equipped weapon
- Total Attack = Base Damage + Weapon Damage + Armor Bonuses
- Example: 20 (base) + 150 (sword) + 30 (armor) = 200 total

**Armor (Damage Reduction):**
- Each armor point reduces incoming damage by 1
- Obtained from armor equipment only
- Example: 50 armor = reduces 100 damage to 50 damage
- No diminishing returns (linear reduction)
- Cannot reduce damage below 1

**Attack Speed:**
- Base: 1.0 (one attack per second)
- Weapon modifier: Scales with weapon type
  - Dagger: 1.5× (fast)
  - Sword: 1.0× (balanced)
  - Greatsword: 0.7× (slow, high damage)
  - Spear: 1.1× (moderate)
- Attack Speed affects DPS calculation

**Critical Chance:**
- Base: 5% (all players)
- Equipment bonus: +% from weapons/armor
- Maximum: 75% (cap to prevent guaranteed crits)
- Roll per attack (independent)

**Critical Damage:**
- Base: 100% (double damage on crit)
- Equipment bonus: +% from weapons/armor
- Critical Hit = Attack Damage × (1 + Critical Damage %)
- Example: 200 damage, 150% crit damage = 200 + (200 × 1.5) = 500 damage

**Luck:**
- Affects drop rates from monsters
- No combat effectiveness impact
- See [GDD_Luck_System.md](GDD_Luck_System.md) for details

### 2.2 Stat Scaling

**Level Progression:**
```
Level 1: Base stats
Level 10: equipment slots unlocked
Level 20: rare equipment accessible
Level 35: epic equipment unlocked
Level 50: legendary equipment unlocked
Level 80: mythic equipment unlocked
```

**Equipment Contribution:**
- Equipment provides 70% of player power
- Base stats provide 30%
- End-game total attack: 20 (base) + 500 (equipment) = 520 damage
- End-game total HP: 7,000 (base+levels) + 3,000 (armor) = 10,000 HP

---

## 3. Combat Mechanics

### 3.1 Basic Combat Actions

**Light Attack:**
- Input: Left Mouse Click / [E] key
- Damage: 100% weapon damage
- Speed: Based on weapon attack speed
- Stamina: No cost
- Can be chained into combos

**Heavy Attack:**
- Input: Hold Left Mouse (1 second) / [R] key
- Damage: 200% weapon damage
- Speed: 2× slower than light attack
- Stamina: 25% max stamina
- Cannot be cancelled once started
- Knockback effect on enemies

**Dodge Roll:**
- Input: [Space] + direction key
- Invincibility: 0.3 seconds (I-frames)
- Cooldown: 1.5 seconds
- Stamina: 30% max stamina
- Distance: 5 studs in chosen direction
- Can dodge through attacks

**Block (Shield Only):**
- Input: Hold Right Mouse / [Q] key
- Damage Reduction: 50% + shield bonus
- Stamina Drain: 10% per hit blocked
- Movement: Reduced to 50% speed while blocking
- Cannot attack while blocking
- Perfect Block (within 0.2s of hit): 100% reduction + counter opportunity

### 3.2 Stamina System

**Stamina Pool:**
- Max Stamina: 100 (all players)
- Regeneration: 20 stamina/second (out of combat)
- Regeneration: 10 stamina/second (in combat)
- Actions consume stamina (dodge, heavy attack, blocking)

**Stamina Management:**
- Running out of stamina = cannot dodge (vulnerable)
- Strategic resource management
- Encourages attack-defense rhythm
- No stamina = heavy attacks disabled

### 3.3 Combo System

**Light Attack Chains:**
```
Attack 1 → Attack 2 → Attack 3 (Finisher)
   ↓         ↓           ↓
  100%      110%       150% damage

Timing Window: 0.5 seconds between attacks
```

**Combo Bonuses:**
- 3-hit combo: Finisher deals 150% damage
- 5-hit combo: +10% damage for 5 seconds
- 10-hit combo: Next attack guaranteed critical

**Combo Reset:**
- Taking damage resets combo
- Missing attack resets combo
- 2 seconds without attacking resets combo

### 3.4 Combat States

**Normal State:**
- Full movement speed (16 studs/second)
- All actions available
- Stamina regenerates normally

**Combat State (Enemy Aggro):**
- Triggered when enemy targets player
- Stamina regeneration reduced to 50%
- Cannot open menus (except quick-access)
- Background music changes to combat theme

**Stunned State:**
- Triggered by heavy enemy attacks
- Duration: 1-3 seconds (depends on attack)
- Cannot move or attack
- Can be dodged with proper timing

**Invulnerable State:**
- During dodge roll I-frames (0.3s)
- After being hit (0.5s mercy invincibility)
- Respawn protection (5 seconds)
- Visual: Character flashes white

---

## 4. Weapon System

### 4.1 Weapon Types

**Swords (Balanced):**
- Attack Speed: 1.0×
- Range: Medium (5 studs)
- Damage: Balanced
- Special: Combo-focused
- Best for: General combat

**Greatswords (Heavy):**
- Attack Speed: 0.7×
- Range: Long (7 studs)
- Damage: High (+30% per hit)
- Special: Knockback on all attacks
- Best for: Slow, powerful hits

**Daggers (Fast):**
- Attack Speed: 1.5×
- Range: Short (3 studs)
- Damage: Low (-20% per hit)
- Special: Guaranteed crit on backstab
- Best for: Hit-and-run tactics

**Spears (Tactical):**
- Attack Speed: 1.1×
- Range: Very Long (9 studs)
- Damage: Moderate
- Special: Can hit multiple enemies in line
- Best for: Safe distance combat

**Hammers (Stagger):**
- Attack Speed: 0.6×
- Range: Medium (5 studs)
- Damage: Very High (+50% per hit)
- Special: Stuns enemies on heavy attack
- Best for: Breaking enemy defense

### 4.2 Weapon Rarity Scaling

| Rarity | Base Damage | Attack Speed Bonus | Special Effects | Crafting Cost |
|--------|-------------|-------------------|-----------------|---------------|
| **Common** | 50 | 0% | None | 200 IRF |
| **Rare** | 100 | +5% | 1 random stat +5% | 1,000 IRF |
| **Epic** | 200 | +10% | 2 stats +8%, unique passive | 5,000 IRF |
| **Legendary** | 350 | +15% | 3 stats +12%, powerful passive | 25,000 IRF |
| **Mythic** | 500 | +20% | 4 stats +15%, legendary passive | 100,000 IRF |
| **Special** | 600 | +25% | All stats +20%, 2 unique passives | Event/Quest |

**Unique Passives (Epic+):**
- **Flame Enchant**: 15% chance to burn (DoT: 5% damage/sec for 5s)
- **Ice Shard**: 10% chance to slow enemy (50% speed for 3s)
- **Lightning Strike**: 8% chance to chain to nearby enemies (50% damage)
- **Life Steal**: Heal 5% of damage dealt
- **Critical Master**: +15% critical damage
- **Berserker**: +2% damage per 10% HP missing (max +20%)

**Special Event Weapons:**
- Unique appearance (themed to event)
- Cannot be crafted normally
- High trade value
- Often have 2 unique passives

### 4.3 Weapon Enhancement

**Enhancement Levels: +1 to +5**

| Level | Damage Bonus | Stat Bonus | Cost (IRF) | Materials |
|-------|--------------|------------|------------|-----------|
| Base | 0% | 0% | N/A | N/A |
| +1 | +10% | +5% | 1,000 | 10× Enhancement Crystals |
| +2 | +20% | +10% | 3,000 | 20× Enhancement Crystals |
| +3 | +30% | +15% | 7,500 | 40× Enhancement Crystals |
| +4 | +40% | +20% | 15,000 | 80× Enhancement Crystals |
| +5 | +50% | +25% | 30,000 | 160× Enhancement Crystals |

**Enhancement Rules:**
- Cannot skip levels (must go +1→+2→+3, etc.)
- Enhancement persists (permanent)
- Visual: Weapon glows brighter per level
- Failure chance: NONE (always succeeds)
- Cost increases per rarity of base weapon

---

## 5. Armor System

### 5.1 Armor Pieces

**Armor Slots:**
1. **Helmet**: +HP, +Armor, +Special Stat
2. **Chest Armor**: +HP (highest), +Armor (highest), +Special Stat
3. **Leg Armor**: +HP, +Armor, +Special Stat

**No gloves/boots** (simplified system)

### 5.2 Armor Set Bonuses

**Wearing Full Set (3/3 pieces same rarity):**
- +15% to all stats from armor
- Set bonus effect activates
- Visual: Matching appearance, set aura

**Example Set Bonuses:**
- **Knight Set (Epic)**: +200 HP, +10% damage reduction
- **Assassin Set (Epic)**: +15% critical chance, +20% dodge distance
- **Berserker Set (Legendary)**: +30% damage, -10% defense
- **Tank Set (Legendary)**: +500 HP, enemies deal -15% damage to you
- **Mythic Dragon Set**: +50% all stats, fire aura damages nearby enemies

### 5.3 Armor Rarity Scaling

| Rarity | HP Bonus | Armor Bonus | Special Stat | Cost (Full Set) |
|--------|----------|-------------|--------------|-----------------|
| **Common** | +300 HP | +30 Armor | None | 600 IRF |
| **Rare** | +600 HP | +60 Armor | +5% one stat | 3,000 IRF |
| **Epic** | +1,200 HP | +120 Armor | +10% two stats | 15,000 IRF |
| **Legendary** | +2,000 HP | +200 Armor | +15% three stats | 75,000 IRF |
| **Mythic** | +3,000 HP | +300 Armor | +20% all stats | 300,000 IRF |

### 5.4 Cursed Equipment (Optional)

**Cursed Items:**
- Extremely powerful stats (+50% over normal)
- Negative effect (debuff)
- Cannot be unequipped easily (requires NPC)
- High risk, high reward

**Example Cursed Items:**
- **Cursed Samurai Blade**: +500 damage, -30% defense
- **Cursed Berserker Armor**: +50% HP, take 20% more damage
- **Cursed Lucky Charm**: +100% luck, -50% HP regeneration

---

## 6. Enemy AI

### 6.1 Monster Types

**Melee Enemies:**
- Approach player directly
- Attack when in range (3 studs)
- Telegraphed attacks (windup animation)
- Can be kited with movement

**Ranged Enemies:**
- Maintain distance (15 studs)
- Projectile attacks
- Lower HP than melee
- Backpedal when player approaches

**Elite Enemies (Rare+):**
- Higher stats than common
- Special abilities (AoE, stun, charge)
- Better loot drops
- Unique appearance (glowing)

**Boss Enemies:**
- Massive HP pools
- Multiple attack phases
- Arena-based encounters
- Guaranteed rare loot
- See [Boss Encounters](#9-boss-encounters)

### 6.2 AI Behaviors

**Aggro System:**
- Aggro Range: 20 studs
- Chase Range: 50 studs (before reset)
- De-aggro: Return to spawn if player too far
- Threat: Player with highest damage gets aggro

**Attack Patterns:**
```
Common Enemy:
  1. Light Attack (1s cooldown)
  2. Light Attack
  3. Heavy Attack (3s cooldown)
  Repeat

Rare Enemy:
  1. Light Attack Combo (3 hits)
  2. Special Ability (5s cooldown)
  3. Heavy Attack
  Repeat

Elite/Boss:
  1. Phase-based patterns
  2. Multiple abilities
  3. Enrage at low HP
```

**Telegraphs:**
- All attacks have visible windup (0.5-1.5s)
- Red flash before heavy attacks
- Audio cue before special abilities
- Ground indicator for AoE attacks

### 6.3 Monster Scaling

**Monster Stats by Rarity:**

| Rarity | HP Multiplier | Damage Multiplier | Speed | Abilities |
|--------|---------------|-------------------|-------|-----------|
| **Common** | 1.0× (500 HP) | 1.0× (30 dmg) | Normal | Basic attacks only |
| **Rare** | 2.0× | 1.5× | Normal | 1 special ability |
| **Epic** | 4.0× | 2.0× | Fast | 2 special abilities |
| **Legendary** | 8.0× | 3.0× | Fast | 3 special abilities + passive |
| **Mythic** | 15.0× | 4.0× | Very Fast | 4 abilities + strong passive |

---

## 7. Damage Calculation

### 7.1 Damage Formula

**Outgoing Damage (Player attacking Enemy):**
```
Base Damage = Attack Damage (Base + Weapon + Armor Bonuses)
Critical Roll = Random(1-100) ≤ Critical Chance%
Final Damage = Base Damage × Critical Multiplier (if crit) × Combo Multiplier
Enemy Takes = Final Damage (no armor reduction on monsters)
```

**Incoming Damage (Enemy attacking Player):**
```
Enemy Damage = Enemy Base Damage
Armor Reduction = min(Player Armor, Enemy Damage - 1)
Final Damage = Enemy Damage - Armor Reduction
Player Takes = Final Damage
```

**Examples:**

**Player Attacks Enemy:**
```
Player Attack: 200 (base 20 + weapon 150 + armor 30)
Critical Chance: 25%
Critical Damage: 150%
Roll: 18 (critical hit!)

Damage = 200 × 2.5 (150% = +150% of base) = 500 damage
Enemy HP: 1000 → 500
```

**Enemy Attacks Player:**
```
Enemy Damage: 120
Player Armor: 80

Damage Reduction = 80
Final Damage = 120 - 80 = 40 damage
Player HP: 2000 → 1960
```

### 7.2 Damage Types (Future Expansion)

**Planned Damage Types:**
- Physical: Standard attacks
- Fire: DoT effects, high burst
- Ice: Slow effects, control
- Lightning: Chain damage, fast
- Poison: Strong DoT, weaker burst

**Elemental Advantages:**
- Fire beats Ice
- Ice beats Lightning
- Lightning beats Fire
- Create build diversity

---

## 8. Special Effects

### 8.1 Status Effects

**Burn (DoT):**
- Duration: 5 seconds
- Damage: 5% of initial hit per second
- Stacks: No (refreshes duration)
- Source: Fire weapons, fire enemies

**Slow:**
- Duration: 3 seconds
- Effect: -50% movement speed
- Stacks: No
- Source: Ice weapons, ice enemies

**Stun:**
- Duration: 1-2 seconds
- Effect: Cannot move or attack
- Stacks: No (extends duration)
- Source: Heavy attacks, hammer weapons

**Poison:**
- Duration: 10 seconds
- Damage: 3% of max HP per second
- Stacks: Yes (up to 3 stacks)
- Source: Poison weapons, toxic enemies

**Bleed:**
- Duration: 8 seconds
- Damage: 2% of initial hit per second
- Stacks: Yes (up to 5 stacks)
- Source: Dagger attacks, critical hits

### 8.2 Buff Effects

**Attack Boost:**
- Duration: 10-30 seconds
- Effect: +10-50% attack damage
- Source: Potions, familiars, equipment passives

**Defense Boost:**
- Duration: 10-30 seconds
- Effect: +10-50% armor
- Source: Potions, shield abilities

**Speed Boost:**
- Duration: 5-15 seconds
- Effect: +20-50% movement speed
- Source: Potions, dodge upgrades

**Invincibility:**
- Duration: 1-3 seconds
- Effect: Immune to damage
- Source: Special abilities, rare equipment

---

## 9. Boss Encounters

### 9.1 Boss Types

**Normal Boss (Weekly Spawn):**
- HP: 50,000+
- Players: 1-10 recommended
- Duration: 10-15 minutes
- Loot: Guaranteed epic+ materials

**Elite Boss (Event Boss):**
- HP: 150,000+
- Players: 5-10 required
- Duration: 20-30 minutes
- Loot: Guaranteed legendary+ materials

**World Boss (Special Event):**
- HP: 500,000+
- Players: 10+ server-wide effort
- Duration: 30+ minutes
- Loot: Mythic materials, exclusive rewards

### 9.2 Boss Mechanics

**Phase System:**
```
Phase 1 (100-66% HP):
  - Basic attack patterns
  - Introduces mechanics
  
Phase 2 (66-33% HP):
  - New abilities unlocked
  - Increased aggression
  - Environmental hazards
  
Phase 3 (33-0% HP):
  - Enrage mode
  - All abilities available
  - Desperation attacks
  - Time limit pressure
```

**Example Boss: Forest Guardian**
```
Phase 1:
  - Melee swipes
  - Ground pound (AoE)
  - Summons 2 adds every 30s
  
Phase 2:
  - Vine entangle (root players)
  - Poison cloud (DoT zones)
  - Charges across arena
  
Phase 3:
  - Enrage (+50% damage)
  - Rapid summons (4 adds every 15s)
  - Ultimate: Arena-wide AoE (must hide behind pillars)
```

### 9.3 Boss Loot

**Guaranteed Drops:**
- Epic+ materials: 100% chance
- Legendary materials: 50% chance
- Mythic materials: 10% chance
- Boss-specific crafting material: 100% chance

**Bonus Loot (Per Player):**
- Participation reward: 5,000-15,000 IRF
- MVP bonus (most damage): +5,000 IRF
- First-time completion: Exclusive title + decoration

---

## 10. Technical Implementation

### 10.1 Combat System Architecture

```lua
CombatSystem = {
    ActiveCombats = {}, -- Player → Combat session
    RegisteredEnemies = {},
    DamageQueue = {},
}

function CombatSystem:ProcessAttack(attacker, target, attackType)
    -- Calculate base damage
    local baseDamage = self:GetAttackDamage(attacker, attackType)
    
    -- Roll for critical
    local isCrit = math.random(1, 100) <= attacker.Stats.CriticalChance
    local critMultiplier = isCrit and (1 + attacker.Stats.CriticalDamage / 100) or 1
    
    -- Apply combo bonus
    local comboMultiplier = self:GetComboMultiplier(attacker)
    
    -- Calculate final damage
    local finalDamage = baseDamage * critMultiplier * comboMultiplier
    
    -- Apply damage to target
    if target:IsA("Player") then
        finalDamage = self:ApplyArmorReduction(finalDamage, target)
    end
    
    target.Health -= finalDamage
    
    -- Visual feedback
    self:ShowDamageNumber(target, finalDamage, isCrit)
    self:PlayHitEffect(target)
    
    -- Update combo
    if attacker:IsA("Player") then
        self:UpdateCombo(attacker)
    end
    
    return finalDamage
end
```

### 10.2 Enemy AI Controller

```lua
function EnemyAI:Update(enemy, deltaTime)
    local target = self:GetTarget(enemy)
    
    if not target then
        self:IdleState(enemy)
        return
    end
    
    local distance = (enemy.Position - target.Position).Magnitude
    
    -- State machine
    if distance > enemy.AggroRange then
        self:ResetToSpawn(enemy)
    elseif distance > enemy.AttackRange then
        self:ChaseState(enemy, target)
    else
        self:AttackState(enemy, target)
    end
    
    -- Ability cooldowns
    self:UpdateCooldowns(enemy, deltaTime)
end

function EnemyAI:AttackState(enemy, target)
    -- Face target
    enemy:LookAt(target.Position)
    
    -- Choose attack based on cooldowns
    local availableAttacks = self:GetAvailableAttacks(enemy)
    local chosenAttack = availableAttacks[math.random(#availableAttacks)]
    
    -- Execute attack
    self:ExecuteAttack(enemy, target, chosenAttack)
end
```

### 10.3 Boss Phase System

```lua
BossSystem = {}

function BossSystem:UpdateBossPhase(boss)
    local hpPercent = boss.Health / boss.MaxHealth
    
    if hpPercent <= 0.33 and boss.Phase < 3 then
        self:EnterPhase(boss, 3)
    elseif hpPercent <= 0.66 and boss.Phase < 2 then
        self:EnterPhase(boss, 2)
    end
end

function BossSystem:EnterPhase(boss, phaseNumber)
    boss.Phase = phaseNumber
    
    -- Phase transition animation
    self:PlayPhaseTransition(boss)
    
    -- Unlock new abilities
    local phaseAbilities = boss.PhaseAbilities[phaseNumber]
    for _, ability in ipairs(phaseAbilities) do
        table.insert(boss.AvailableAbilities, ability)
    end
    
    -- Apply phase buffs
    if phaseNumber == 3 then
        boss.Damage *= 1.5 -- Enrage
        boss.Speed *= 1.2
    end
    
    -- Announce phase change
    self:AnnouncePhase(boss, phaseNumber)
end
```

---

## Implementation Checklist

### Phase 1: Core Combat
- [ ] Basic melee combat
- [ ] Damage calculation system
- [ ] Player stats system
- [ ] Health and stamina bars
- [ ] Hit detection and feedback
- [ ] Weapon switching

### Phase 2: Enemy AI
- [ ] Enemy pathfinding
- [ ] Basic AI state machine
- [ ] Attack patterns (3 types)
- [ ] Aggro system
- [ ] Monster spawning
- [ ] Death and loot drops

### Phase 3: Advanced Systems
- [ ] Critical hit system
- [ ] Combo system
- [ ] Dodge roll with I-frames
- [ ] Armor damage reduction
- [ ] Status effects (burn, slow, stun)
- [ ] Equipment stat bonuses

### Phase 4: Boss Content
- [ ] Boss AI (phase system)
- [ ] Boss arena design
- [ ] Special boss abilities
- [ ] Boss loot tables
- [ ] Victory conditions
- [ ] Leaderboards

### Phase 5: Polish
- [ ] Combat animations (all weapon types)
- [ ] Visual effects (hits, crits, abilities)
- [ ] Sound design (combat audio)
- [ ] UI polish (damage numbers, health bars)
- [ ] Balance testing
- [ ] Accessibility options (difficulty settings)

---

**Combat System - End of Document**

*Related Documentation: [GDD_Systems_Dungeon.md](GDD_Systems_Dungeon.md), [Database_Weapons.md](Database_Weapons.md), [Database_Armor.md](Database_Armor.md), [Database_Monsters.md](Database_Monsters.md)*
