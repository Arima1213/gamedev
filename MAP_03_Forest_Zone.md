# MAP DESIGN DOCUMENT
## MAP 03: FOREST ZONE

---

### Document Information
**Map Name:** Forest Zone (Whispering Woods)  
**Map ID:** MAP_FOREST_ZONE  
**Version:** 1.0  
**Last Updated:** February 9, 2026  
**Designer:** Systems Design Team  
**Status:** Ready for Implementation

---

## Table of Contents
1. [Map Overview](#map-overview)
2. [Visual Design & Atmosphere](#visual-design--atmosphere)
3. [Layout & Landmarks](#layout--landmarks)
4. [NPC Locations & Details](#npc-locations--details)
5. [Monster Distribution](#monster-distribution)
6. [Fishing Areas](#fishing-areas)
7. [Wild Familiar Spawns](#wild-familiar-spawns)
8. [Resource Nodes](#resource-nodes)
9. [Story Integration](#story-integration)
10. [Hidden Secrets & Easter Eggs](#hidden-secrets--easter-eggs)
11. [Loading & Transitions](#loading--transitions)
12. [Technical Implementation](#technical-implementation)

---

## 1. Map Overview

### 1.1 Purpose & Function
**Primary Role:** Mid-level exploration zone, taming hub, and Nature Heart Gem story location

**Key Functions:**
- Core taming tutorial and familiar gameplay
- Mid-level combat progression (Levels 8-15)
- Nature-themed exploration and secrets
- Goblin Camp and Forest Outposts (combat clusters)
- Access to forest stream fishing (River Zone B)
- Pathway to Mountain Region (via forest pass)

**Design Philosophy:**
*"The Whispering Woods should feel alive. It's a place where nature is both welcoming and dangerous—friendly creatures roam in the sunlit glades, while deeper shadows hide goblins and corrupted beasts."*

### 1.2 Map Statistics
- **Size:** 700×700 studs (dense, multi-layered)
- **Player Capacity:** 30-40 players
- **Biome:** Dense woodland, temperate forest
- **Danger Level:** 4/10 (Mid-level)
- **Recommended Level:** 8-15
- **Respawn Point:** Town Hub (default), Forest Entrance (unlocked at Level 10)

### 1.3 Connections
**Accessible From:**
- Starter Plains (Forest Edge)
- Town Hub (north path via Sanctuary Entrance)

**Connects To:**
- Mountain Region (Northwest pass, Level 15+)
- Goblin Fortress Dungeon entrance (hidden grove)
- Deep Forest (internal)
- Mysterious Lake (quest unlock path, later)

---

## 2. Visual Design & Atmosphere

### 2.1 Overall Aesthetic
**Theme:** Enchanted forest with layered depth

**Visual Style:**
- Dense canopy overhead (sunbeams through leaves)
- Moss-covered trees and rocks
- Soft mist in low-lying areas
- Bioluminescent plants in deeper forest
- Winding dirt paths and wooden bridges
- Tree roots forming natural arches
- Wildlife sounds and rustling leaves

**Color Palette:**
- **Primary:** Deep greens and rich browns
- **Secondary:** Gold sunlight, blue shadows
- **Accents:** Purple glow (Void corruption hints)

### 2.2 Atmosphere by Time

**Morning:**
- Misty ground fog
- Birds active
- Soft sun rays

**Afternoon:**
- Bright but filtered light
- Warm, peaceful
- Creatures most active

**Evening:**
- Golden glow through canopy
- Shadows lengthen
- Goblins become more active

**Night:**
- Bioluminescent plants glow
- Fireflies appear
- Wolves and goblins patrol aggressively
- Mysterious, magical atmosphere

---

## 3. Layout & Landmarks

### 3.1 Map Layout Overview

```
           [Mountain Pass]
                 |
     [Goblin Outpost]---[Deep Forest]
          |                 |
[Forest Stream]---[Sanctuary Grove]---[Forest Edge]
          |                 |
     [Hunter's Trail]   [Ancient Shrine]
          |                 |
     [Goblin Camp]-----[Hidden Grove]
```

### 3.2 Detailed Landmark Descriptions

---

#### 3.2.1 FOREST EDGE (Entrance)
**Description:** Transition from plains to dense forest. Sign warns of higher danger.
- Soft barrier: “Level 8+ Recommended”
- Clear trail leading into woods
- NPC hint signposts

---

#### 3.2.2 SANCTUARY GROVE (Elder Willow)
**Description:** A peaceful, glowing grove where Elder Willow teaches taming.
- Large ancient tree at center
- Soft green glow, gentle wind chimes
- Friendly animals roaming freely
- Healing aura (slow HP regen)

**NPC:** Elder Willow Moonwhisper (Creature Master)

---

#### 3.2.3 FOREST STREAM (River Zone B)
**Description:** Clear stream with wooden bridge and fishing spots.
- River Zone B access
- Scenic fishing area
- Waterfall nearby

---

#### 3.2.4 DEEP FOREST
**Description:** Darker, denser region. Bears and stronger monsters spawn here.
- Reduced visibility
- Bioluminescent mushrooms
- Higher loot chance

---

#### 3.2.5 GOBLIN CAMP
**Description:** Crude goblin settlement with tents and bonfires.
- Goblin Scout & Warrior spawns
- Lootable crates
- Fire pits with goblin chatter

---

#### 3.2.6 GOBLIN OUTPOSTS
**Description:** Smaller fortified areas with patrols.
- Barricades, lookout towers
- Good for ambush encounters

---

#### 3.2.7 HUNTER’S TRAIL
**Description:** Long winding path used by hunters and travelers.
- Leads to mountain pass
- Occasional NPC hunter sightings (event)

---

#### 3.2.8 ANCIENT SHRINE (Nature Fragment)
**Description:** Hidden shrine where Nature Heart Gem fragment is found.
- Stone altar, glowing vines
- Quest instance for Chapter 4

---

#### 3.2.9 HIDDEN GROVE (Dungeon Entrance)
**Description:** Secret clearing with overgrown stone door.
- Goblin Fortress dungeon entrance
- Unlocks after Chapter 2

---

#### 3.2.10 MOUNTAIN PASS (Exit)
**Description:** Narrow trail leading to Mountain Region.
- Level 15+ recommended
- Steeper terrain, rockier ground

---

## 4. NPC Locations & Details

### 4.1 Core NPCs
| NPC Name | NPC ID | Location | Services | Availability |
|----------|---------|----------|----------|--------------|
| **Elder Willow Moonwhisper** | NPC_CREATURE_MASTER | Sanctuary Grove | Taming, Breeding, Familiar Care | Always |

### 4.2 Event/Temporary NPCs
- **Hunter NPC (random):** Offers hunting quests, appears on Hunter’s Trail
- **Lost Child NPC (event):** Rescue quest in Forest Edge

---

## 5. Monster Distribution

### 5.1 Common Monsters
- **Gray Wolf (MON_002):** Forest Edge, Trails
- **Goblin Scout (MON_003):** Goblin Camp, Forest
- **Forest Bear (MON_004):** Deep Forest
- **Goblin Warrior (MON_005):** Goblin Camp, Outposts

### 5.2 Spawn Zones
| Zone | Monsters | Density |
|------|----------|---------|
| Forest Edge | Wolves, Goblin Scouts | Medium |
| Sanctuary Grove | None (safe) | None |
| Forest Stream | Wolves (low) | Low |
| Deep Forest | Bears, Goblins | High |
| Goblin Camp | Scouts, Warriors | Very High |
| Outposts | Warriors | Medium |

---

## 6. Fishing Areas

### 6.1 River Zone B (Forest Stream)
- **Location:** Forest Stream landmark
- **Fish:** Trout, Catfish (common), Pike/Bass (rare), King Salmon/Sturgeon (epic)
- **Special:** Increased fish quality during rain

---

## 7. Wild Familiar Spawns

### 7.1 Common Familiars
- **Rabbit** (Forest Edge)
- **Fox** (Forest Edge / Trails)
- **Deer** (Sanctuary Grove outskirts)

### 7.2 Rare Familiars
- **Bear Cub** (Deep Forest, dawn/dusk)
- **Owl** (Night only, forest canopy)

### 7.3 Legendary Familiar
- **Unicorn (Legendary)**
  - **Spawn:** Mysterious Lake (quest unlock)
  - **Conditions:** Full moon, Crystal Carrot, no recent combat kills

---

## 8. Resource Nodes

### 8.1 Gatherables
- **Herbs:** Healing herb, stamina herb (common)
- **Mushrooms:** Luminescent mushrooms (rare)
- **Wood Nodes:** Softwood logs (basic crafting)

### 8.2 Chests
- **Hidden forest chests:** 3 active at a time
- **Loot:** Potions, IRF, rare seeds

---

## 9. Story Integration

### Chapter 4: Bonds of Nature
- Meet Elder Willow at Sanctuary Grove
- Tame first familiar
- Quest leads to Ancient Shrine
- Nature Heart Gem fragment obtained
- Corrupted Alpha Wolf boss fight (Deep Forest)

---

## 10. Hidden Secrets & Easter Eggs

### 10.1 Secret: Singing Tree
- Tree hums at night
- Sit under it to gain +5% EXP buff for 30 minutes

### 10.2 Secret: Goblin Treasure
- Hidden chest behind Goblin Camp tent
- Requires stealth (no combat for 1 minute)

### 10.3 Easter Egg: Firefly Swarm
- Trigger by walking through Deep Forest at midnight
- Fireflies form Heart Gem symbol

---

## 11. Loading & Transitions

- **From Starter Plains:** Seamless transition
- **To Mountain Region:** Brief load (2-3 sec)
- **To Goblin Fortress Dungeon:** Portal load instance
- **To Mysterious Lake:** Quest unlock portal

---

## 12. Technical Implementation

- **StreamingEnabled:** true
- **Zone-based spawns** to reduce server load
- **Safe Zone:** Sanctuary Grove (no combat)
- **NPC AI** reduced complexity to save resources

---

**END OF DOCUMENT**
