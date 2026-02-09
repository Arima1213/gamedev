# MAP DESIGN DOCUMENT
## MAP 02: STARTER PLAINS

---

### Document Information
**Map Name:** Starter Plains (Harmony Fields)  
**Map ID:** MAP_STARTER_PLAINS  
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
**Primary Role:** Beginner combat training zone and tutorial area

**Key Functions:**
- First combat experience for new players
- Low-level monster farming (Levels 1-5)
- Safe progression before entering dungeons
- Tutorial quest completion area
- Wild familiar introduction
- Seamless connection to Town Hub

**Design Philosophy:**
*"Starter Plains is where adventurers are born. It should feel safe enough to experiment, but challenging enough to teach combat basics. The open fields give new players confidence, and the gentle difficulty curve ensures nobody feels overwhelmed."*

### 1.2 Map Statistics
- **Size:** 600×600 studs (large, open area)
- **Player Capacity:** 30 players (lower density for learning)
- **Biome:** Temperate grasslands, rolling hills
- **Danger Level:** 1/10 (Very Low - Beginner)
- **Recommended Level:** 1-5
- **Average Session Time:** 15-30 minutes (first visit)
- **Respawn Point:** Town Hub (on death)

### 1.3 Level Progression
**Entry Level:** 1 (fresh spawns)  
**Exit Level:** 5 (ready for Forest or first dungeon)

**Progression Path:**
1. Level 1-2: Fight Green Slimes near town
2. Level 3-4: Challenge Gray Wolves in mid-plains
3. Level 5: Defeat Alpha Slime (mini-boss) or enter first dungeon

### 1.4 Connections
**Accessible From:**
- **Town Hub** (North) - Seamless walking transition
- **Private Island Portal** (Return to Town, then here)

**Connects To:**
- **Town Hub** (North) - Walk back anytime
- **Forest Edge** (East) - Natural transition at Level 5+
- **Mountain Path** (West) - Visible but blocked until Level 10
- **River Path** (South) - Leads to River Zone fishing area

---

## 2. Visual Design & Atmosphere

### 2.1 Overall Aesthetic
**Theme:** Peaceful grasslands with subtle danger

**Visual Style:**
- Rolling green hills (gentle slopes)
- Wildflowers scattered throughout (yellows, whites, purples)
- Tall grass swaying in breeze
- Dirt paths worn by travelers
- Wooden fences (decorative boundaries)
- Occasional trees (shade spots)
- Clear blue sky (optimistic)
- Distant mountains visible (future content tease)

**Color Palette:**
- **Primary:** Vibrant green (grass)
- **Secondary:** Blue (sky), yellow (flowers)
- **Accents:** Brown (dirt paths), white (clouds)
- **Mood:** Bright, cheerful, non-threatening

**Artistic References:**
- Breath of the Wild (Hyrule Field openness)
- Genshin Impact (Mondstadt plains beauty)
- Studio Ghibli (peaceful countryside)

### 2.2 Atmosphere by Time

**Morning (6 AM - 12 PM):**
- Dew on grass (particle effect)
- Sunrise colors fading to blue
- Birds chirping actively
- Slimes most active
- Fresh, energetic feeling

**Afternoon (12 PM - 6 PM):**
- Bright sunlight
- Long shadows from trees
- Warm, sleepy atmosphere
- Wolves napping under trees (less aggressive)
- Butterflies flying

**Evening (6 PM - 8 PM):**
- Golden hour lighting (beautiful)
- Orange/pink sky
- Wolves becoming more active
- Romantic, peaceful feeling
- Best screenshot time

**Night (8 PM - 6 AM):**
- Moon illumination
- Fireflies appear (particle effects)
- Wolves howling (audio cue)
- Slightly more dangerous (wolves attack first)
- Mysterious but safe

### 2.3 Weather Effects

**Clear (70%):**
- Default beautiful weather
- Full visibility
- Normal monster behavior

**Light Rain (15%):**
- Gentle rain particles
- Grass looks wetter (darker green)
- Rainbow occasionally visible
- Slimes spawn rate +20%
- Cozy atmosphere

**Windy (10%):**
- Grass sways dramatically
- Leaves blowing
- Slight screen shake
- Wolf spawn rate +10%

**Storm (5%):**
- Heavy rain, lightning
- Thunder sounds
- Dramatic atmosphere
- Players take shelter under trees
- Rare fish appear in river

### 2.4 Audio Design

**Ambient Sounds:**
- Wind rustling grass (constant, subtle)
- Bird songs (varies by time)
- Distant town bells (from Town Hub)
- Creek flowing (near river)
- Insect buzzing (afternoon)
- Wolf howls (night, distant)

**Music Themes:**
- **Exploration Theme:** Light, adventurous (flutes, strings)
- **Combat Theme:** Simple percussion when engaging monsters
- **Victory Jingle:** Quick 3-second tune after defeating monster

**Dynamic Audio:**
- Music fades when near Town Hub (town music takes over)
- Combat music triggers when damaged
- Peaceful music during non-combat

---

## 3. Layout & Landmarks

### 3.1 Map Layout Overview

```
                    [TOWN HUB - North]
                            |
                    [South Gate]
                            |
        [Wolf Den]    [Tutorial Field]    [Forest Edge]
            |               |                    |
            |               |                    |
    [Western Hills]---[CENTER PLAINS]---[Slime Pond]
            |               |                    |
            |               |                    |
    [Mountain Path]   [Alpha Glade]      [River Access]
     (Blocked)             |                    |
                           |                    |
                    [Training Dummy Area]   [Fishing Spot]
```

### 3.2 Detailed Landmark Descriptions

---

#### 3.2.1 SOUTH GATE (Transition from Town)
**Coordinates:** (0, 0, 0) - Northern edge of map

**Description:**
A simple wooden arch marking the boundary between Town Hub's safety and the adventure of the plains. Two wooden guard towers flank the path, though no guards are present (peaceful times). A worn dirt path leads south into grasslands.

**Visual Elements:**
- **Wooden Arch:** Simple construction, "Harmony Fields" sign
- **Guard Towers:** (2) Empty but maintained, can climb for view
- **Fence Line:** Wooden fence extends east/west, decorative boundary
- **Flower Gardens:** Planted beds on either side (town's reach)
- **Milestone:** Stone marker "Town Hub - 50m North"

**Functionality:**
- Seamless transition point (no loading)
- New players see this immediately after leaving town
- Orientation point (always know where town is)
- Safe retreat zone (close to town)

**Ambient Details:**
- Town music fades out here
- Plains music fades in
- Last safe zone before monsters

---

#### 3.2.2 TUTORIAL FIELD
**Coordinates:** (0, 0, -80) - Just south of gate

**Description:**
A large, flat grassy area specifically designed for first combat. Green Slimes spawn here frequently but move slowly. This is where Mayor Theo's tutorial quest directs new players. Wooden training dummies stand ready for practice.

**Visual Elements:**
- **Training Dummies:** (5) Wooden targets, can attack
  - Show damage numbers
  - Don't fight back
  - Unlimited HP (for practice)
  - Positioned in line
  
- **Tutorial Markers:** (Holographic arrows)
  - Point to first slime
  - Appear during tutorial quest
  - Disappear after completion
  
- **Picnic Area:** (Decorative)
  - Single tree with shade
  - Blanket and basket (set dressing)
  - Bench for resting
  
- **Sign Post:** "Combat Tutorial Area - New Adventurers Welcome!"

**Monster Spawns:**
- **Green Slimes ONLY:** (10-15 active at once)
- **Spawn Rate:** High (respawn every 30 seconds)
- **Behavior:** Non-aggressive unless attacked
- **Difficulty:** Easiest enemies in game

**Tutorial Integration:**
- Mayor Theo's quest sends players here
- Learn attack, dodge, health management
- First kill = tutorial completion
- Safe area to practice (close to town)

**Player Traffic:**
- Highest new player density
- Veterans pass through quickly
- Often see groups of Level 1s practicing

---

#### 3.2.3 CENTER PLAINS
**Coordinates:** (0, 0, -200) - Central area

**Description:**
The vast heart of Harmony Fields, rolling hills covered in tall grass. Slimes bounce lazily through the area while wolves patrol the perimeter. Wildflowers dot the landscape. Multiple dirt paths cross here, leading to all other landmarks.

**Visual Elements:**
- **Rolling Hills:** Gentle elevation changes (5-10 studs)
- **Tall Grass Patches:** (20% of area)
  - Sway in wind
  - Slightly obscure vision
  - Monsters can hide in them
  
- **Wildflower Fields:** (30% of area)
  - Yellow, purple, white flowers
  - Butterflies flying around
  - Beautiful photo location
  
- **Crossroads:** (Center point)
  - 4 dirt paths intersect
  - Small wooden signpost with directions
  - "Town North, Forest East, Mountain West, River South"
  
- **Scattered Trees:** (8-10 trees)
  - Oak-like, medium size
  - Provide shade (aesthetic)
  - Wolves rest under them during day

**Monster Distribution:**
- **Green Slimes:** 60% (more common)
- **Gray Wolves:** 40% (patrol areas)
- **Mixed groups possible**
- **Spawn zones clearly defined by terrain**

**Functionality:**
- Main leveling area (1-4)
- Natural monster variety
- Multi-path navigation
- Central hub for zone

**Ambient Activity:**
- Birds flying overhead
- Butterflies near flowers
- Wind rustling grass
- Distant wolf howls

---

#### 3.2.4 SLIME POND
**Coordinates:** (120, 0, -200) - East area

**Description:**
A small natural pond surrounded by reeds and mud. Green Slimes spawn here most frequently - this is their "habitat." The pond water is murky from slime residue. Lily pads float on surface.

**Visual Elements:**
- **Pond:** 30 studs diameter, shallow
  - Murky green water
  - Not swimmable (too shallow)
  - Slime particles rising from surface
  
- **Reed Patches:** Around edge
  - Tall cattails
  - Frogs hopping (decorative)
  - Dragonflies
  
- **Mud Banks:** Slippery edges
  - Character leaves footprints
  - Slightly slows movement (-10%)
  
- **Giant Mushrooms:** (3) Oversized decorative
  - Slimes bounce off them
  - Can climb on top (vantage point)

**Monster Spawns:**
- **Green Slimes:** 95% (primary habitat)
- **Spawn Rate:** Very high (slime farming spot)
- **Special:** Alpha Slime (mini-boss) rare spawn here

**Resources:**
- **Water Source:** Can refill water bottles (future feature)
- **Frog Legs:** Rare drop from frogs (cooking material)

**Hidden Feature:**
- Jumping in center of pond at full moon reveals secret achievement
- "Slime Bath" title unlocked (cosmetic)

---

#### 3.2.5 WOLF DEN
**Coordinates:** (-150, 0, -200) - West area

**Description:**
A cluster of large rocks and boulders forming natural caves. This is where Gray Wolves den during the day. More dangerous than other areas due to higher wolf concentration. Bones scattered around entrance.

**Visual Elements:**
- **Boulder Cluster:** 5-6 large rocks
  - Create cave entrances (decorative, not enterable)
  - Shadows make area darker
  - Ominous atmosphere
  
- **Bone Piles:** Scattered around
  - Wolf Fang pickups (respawn daily)
  - Visual warning (danger ahead)
  
- **Dirt Dens:** Holes where wolves emerge
  - Spawn points visible
  - Wolves dig/scratch animations
  
- **Dead Trees:** (3) Leafless, gnarled
  - Contrasts with healthy plains
  - Adds foreboding mood
  
- **Warning Sign:** Wooden sign
  - "Wolf Territory - Caution Advised"
  - Skull symbol

**Monster Spawns:**
- **Gray Wolves:** 90% (den habitat)
- **Spawn Rate:** High, aggressive
- **Pack Behavior:** 2-3 wolves often together
- **Special:** Occasionally "Alpha Wolf" (elite, rare)

**Danger Level:** Highest in zone
- Not recommended for Level 1-2
- Level 3+ preferred
- Good farming spot for wolf materials

**Ambient Audio:**
- Growling
- Howling (more frequent)
- Wind through rocks
- Ominous background music

---

#### 3.2.6 ALPHA GLADE
**Coordinates:** (0, 0, -350) - South-central area

**Description:**
A circular clearing surrounded by ancient standing stones. This is where the Alpha Slime (mini-boss) spawns every 30 minutes. Magical energy lingers here - remnants of ancient Harmony civilization. The grass grows greener here.

**Visual Elements:**
- **Standing Stones:** (7 stones in circle)
  - 10 studs tall each
  - Weathered, moss-covered
  - Faint glowing runes
  - Arranged like Stonehenge
  
- **Central Altar:** Stone platform
  - Alpha Slime spawns here
  - Glows when boss is present
  - Can stand on it when empty
  
- **Pristine Grass:** Unnaturally green
  - Flowers more vibrant
  - Magical shimmer effect
  
- **Light Shafts:** Sun beams through stones
  - Dramatic lighting
  - Particles floating in air

**Boss Encounter:**
- **Alpha Slime** spawns every 30 minutes
  - Server announcement: "The Alpha Slime has appeared!"
  - 5-minute timer (despawns if not killed)
  - Level 5, HP: 500
  - Drops guaranteed rare loot
  
**Loot Rewards:**
- Alpha Slime Core (100%)
- 200-500 IRF
- Rare equipment chance (20%)
- Large EXP reward (500 EXP)

**Functionality:**
- First boss experience for new players
- Timed event (creates gathering)
- Party content (easier with group)
- Repeatable (every 30 min)

**Lore Integration:**
- Ancient site (story hints)
- Professor Archimedes mentions in quest
- Connected to Heart Gem history

---

#### 3.2.7 TRAINING DUMMY AREA
**Coordinates:** (0, 0, -280) - South of center

**Description:**
An abandoned training camp from before The Fracture. Wooden dummies still stand, along with weapon racks and practice targets. NPCs once trained here, now players use it.

**Visual Elements:**
- **Training Dummies:** (12) Various types
  - Standard dummies
  - Moving dummies (swing side to side)
  - Armored dummies (higher HP)
  - Showing wear and age
  
- **Weapon Racks:** Empty but functional
  - Decorative display
  - Hint at history
  
- **Target Range:** Archery targets
  - Bulls-eye painted (faded)
  - Different distances
  
- **Worn Fence:** Perimeter fence
  - Broken sections
  - Overgrown with vines
  
- **Old Campfire:** Ash pile
  - Can sit around
  - Logs for seating

**Functionality:**
- **DPS Testing:** Attack dummies to see damage
- **Skill Practice:** Test combos safely
- **AFK Spot:** Safe from monsters
- **Social Area:** Players gather between fights

**Story Context:**
- Captain Zara mentions this place
- Old Adventurer's Guild training ground
- Abandoned during Fracture chaos
- Players reclaim it

---

#### 3.2.8 RIVER ACCESS
**Coordinates:** (100, 0, -400) - Southeast corner

**Description:**
Where the Town River flows into the plains. A small wooden dock provides fishing access. Gentle current flows south toward ocean. Riverbank covered in smooth stones.

**Visual Elements:**
- **Wooden Dock:** Small, 4-person fishing spot
  - Weathered planks
  - Rope railings
  - Bucket and net decorations
  
- **Riverbank:** Gradual slope to water
  - Smooth river stones
  - Reeds growing
  - Sandy patches
  
- **Willow Tree:** Single large tree
  - Branches hang over water
  - Peaceful atmosphere
  - Shade for anglers
  
- **Stepping Stones:** Cross river (decorative)
  - Can't actually cross (boundary)
  - Visual element

**Fishing Access:**
- **River Zone A Extension:** Same as Town docks
- **Fish Species:** Trout, Carp, Minnow, rare Salmon
- **Less crowded** than Town docks
- **Peaceful fishing spot**

**Ambient Audio:**
- Water flowing (soothing)
- Fish jumping occasionally
- Reeds rustling
- Birds near water

---

#### 3.2.9 FOREST EDGE
**Coordinates:** (200, 0, -200) - East boundary

**Description:**
The grasslands gradually transition to forest here. Trees become denser, grass gives way to ferns. This is the natural boundary leading to Forest Zone (next map). A visible path leads deeper into woods.

**Visual Elements:**
- **Tree Line:** Dense forest begins
  - Oak, birch, pine mix
  - Shadows deepen
  - Canopy visible
  
- **Path Entrance:** Clear trail
  - "Forest Zone Ahead - Level 8+ Recommended" sign
  - Wooden arch marker
  
- **Transition Vegetation:**
  - Grass → Ferns
  - Wildflowers → Forest flowers
  - Open → Enclosed feeling
  
- **Boundary Fence:** Natural barrier
  - Fallen logs
  - Boulder placement
  - Guides players to path

**Functionality:**
- **Level Gate:** Soft barrier
  - Level 5+ can proceed
  - Below Level 5 gets warning
  - Not hard-blocked (player choice)
  
- **Zone Transition:** Seamless or brief load
- **Teaser:** Shows next zone content

**Monster Presence:**
- Occasional Goblin Scout (Level 5)
- Rare deer sighting (can't tame yet)
- Warning for harder content ahead

---

#### 3.2.10 WESTERN HILLS
**Coordinates:** (-150, 0, -300) - West area

**Description:**
Rocky hills with steeper slopes. This area offers higher vantage points overlooking the plains. More challenging terrain with elevation changes.

**Visual Elements:**
- **Rocky Outcrops:** Climbable hills
  - 15-20 studs elevation
  - Best view of entire map
  - Popular screenshot location
  
- **Boulder Fields:** Large rocks scattered
  - Can hide behind (combat tactics)
  - Wolf patrol routes
  
- **Mountain Vista:** View of Mountain Region
  - Teaser of future content
  - Blocked path visible (locked until later)
  
- **Wildflower Slopes:** Hillsides covered in flowers
  - Beautiful during golden hour
  - Butterflies abundant

**Gameplay:**
- **Higher Challenge:** More wolves here
- **Better Loot:** Slightly increased drop rates
- **Exploration:** Rewards venturing off main path
- **Familiar Spawns:** Rabbits occasionally hop by

---

#### 3.2.11 MOUNTAIN PATH (Blocked)
**Coordinates:** (-250, 0, -250) - Northwest corner

**Description:**
A rocky path leading toward Mountain Region, but blocked by a massive boulder. Captain Zara's quest will eventually clear this path at Level 10+.

**Visual Elements:**
- **Massive Boulder:** Blocking path
  - "Unstable - Do Not Enter" sign
  - Cracks visible (will be cleared later)
  
- **Rocky Terrain:** Transition to mountain
  - Gravel path
  - Sparse vegetation
  - Steeper incline
  
- **Warning Signs:** Multiple notices
  - "Road Closed - Guild Orders"
  - "Level 10+ Required"
  
- **Ambient Details:**
  - Distant mountain peaks
  - Eagle flying overhead
  - Wind sounds stronger

**Functionality:**
- **Content Gate:** Prevents early access
- **Future Tease:** Shows progression path
- **Quest Objective:** Chapter 2 clears this

---

## 4. NPC Locations & Details

### 4.1 Core NPCs

**NO PERMANENT NPCs IN STARTER PLAINS**

**Reasoning:**
- Zone is transitional (players come from town)
- All services available in Town Hub (50m north)
- Encourages returning to town (social hub design)

### 4.2 Quest NPCs (Temporary)

**Tutorial Quest Phase:**
- **Mayor Theo** occasionally appears near South Gate
  - Only during tutorial quest
  - Guides player to Tutorial Field
  - Disappears after quest complete

### 4.3 Random Encounter NPCs

**Wandering Merchant (Rare):**
- **Chance:** 5% to spawn per hour
- **Location:** Crossroads in Center Plains
- **Duration:** 10 minutes, then despawns
- **Sells:** Basic potions, bandages (emergency supplies)
- **Dialogue:** *"Ah, an adventurer! Care for some supplies?"*

**Injured Adventurer (Event):**
- **Trigger:** Random world event
- **Location:** Random spot in plains
- **Quest:** Rescue quest (give healing potion)
- **Reward:** Small IRF, friendship with Guild

---

## 5. Monster Distribution

### 5.1 Monster Spawn System

**Total Active Monsters:** 40-50 at any time  
**Respawn Timer:** 30-60 seconds after death  
**Spawn Logic:** Maintains ratio even as players kill

### 5.2 Green Slime (MON_001)

**Spawn Zones:**
- Tutorial Field (highest density)
- Slime Pond (secondary habitat)
- Center Plains (scattered)
- Alpha Glade (near boss area)

**Spawn Distribution:**
- Tutorial Field: 40%
- Slime Pond: 30%
- Center Plains: 25%
- Alpha Glade: 5%

**Stats:**
- **Level:** 1
- **HP:** 50
- **Damage:** 5-8 per hit
- **Attack Speed:** 0.8 hits/sec
- **Movement:** Slow (easy to escape)
- **Aggro Range:** 10 studs
- **Behavior:** Passive until attacked

**Loot Table:**
- Slime Gel (80%) - 1-3 units
- Copper Coin (40%) - 2-5 IRF
- Health Potion (10%) - Small
- EXP: 10

**Spawn Count:** 25-30 active

---

### 5.3 Gray Wolf (MON_002)

**Spawn Zones:**
- Wolf Den (primary habitat)
- Western Hills (patrol routes)
- Center Plains (scattered)
- Night spawns increase (anywhere)

**Spawn Distribution:**
- Wolf Den: 50%
- Western Hills: 30%
- Center Plains: 15%
- Random (night): 5%

**Stats:**
- **Level:** 3
- **HP:** 120
- **Damage:** 10-15 per hit
- **Attack Speed:** 1.2 hits/sec
- **Movement:** Fast (hard to escape)
- **Aggro Range:** 15 studs
- **Behavior:** Aggressive (attacks on sight)

**Special Ability:**
- **Pack Tactics:** +20% damage when another wolf nearby
- **Howl:** Alerts nearby wolves (calls reinforcements)

**Loot Table:**
- Wolf Pelt (70%) - 1-2 units
- Leather (50%) - 1-3 units
- Wolf Fang (30%) - 1 unit
- Raw Meat (60%) - 2-4 units
- Copper/Silver coins (50%) - 5-15 IRF
- EXP: 25

**Spawn Count:** 15-20 active

---

### 5.4 Alpha Slime (Mini-Boss)

**Spawn Location:** Alpha Glade ONLY  
**Spawn Timer:** Every 30 minutes (server-wide)  
**Spawn Announcement:** "The Alpha Slime has appeared in Harmony Fields!"

**Stats:**
- **Level:** 5
- **HP:** 500
- **Damage:** 15-25 per hit
- **Attack Speed:** 1.0 hits/sec
- **Movement:** Normal
- **Size:** 3x larger than normal slime
- **Aggro Range:** 20 studs

**Visual Design:**
- Larger model (3x scale)
- Blue-green color (distinct from normal green)
- Glowing aura particles
- Crown-like protrusion on top

**Abilities:**
- **Bounce Attack:** Jumps high, slam AOE (30 damage, 5m radius)
- **Slime Split:** At 50% HP, spawns 2 normal slimes
- **Acid Spray:** Ranged attack (15 damage, DOT 5/sec for 3 sec)

**Loot Table (Guaranteed):**
- Alpha Slime Core (100%) - 1 unit
- Slime Gel (100%) - 10-15 units
- Rare Crafting Material (30%)
- Equipment drop (20% - Common to Rare tier)
- 200-500 IRF
- EXP: 500

**Encounter Design:**
- Soloable at Level 5 with skill
- Easier with 2-3 players (encourages co-op)
- 5-minute despawn timer
- Repeatable (every 30 min)

---

### 5.5 Alpha Wolf (Rare Elite)

**Spawn Condition:** 5% chance when wolf pack defeated  
**Spawn Location:** Wolf Den area  
**Spawn Announcement:** Local chat notification

**Stats:**
- **Level:** 5
- **HP:** 400
- **Damage:** 20-30 per hit
- **Attack Speed:** 1.3 hits/sec
- **Movement:** Very fast
- **Size:** 1.5x larger than normal wolf

**Visual Design:**
- Larger model
- Darker fur (almost black)
- Red eyes (glowing)
- Scar across face
- Alpha aura effect

**Abilities:**
- **Feral Bite:** Applies bleed (10 damage/sec for 5 sec)
- **Pack Leader:** Summons 2 wolves to assist
- **Howl:** Buffs all nearby wolves +30% damage

**Loot Table:**
- Alpha Wolf Pelt (100%) - Epic crafting material
- Wolf Fang (100%) - 3-5 units
- Rare equipment (40%)
- 100-200 IRF
- EXP: 300

---

### 5.6 Monster Spawn Heat Map

```
[North - South Gate]
         LOW
         
[Tutorial Field]    [Wolf Den]
    HIGH (Slimes)   VERY HIGH (Wolves)
    
[Center Plains]     [Slime Pond]
    MEDIUM (Mixed)  HIGH (Slimes)
    
[Alpha Glade]       [Western Hills]
    BOSS ONLY       MEDIUM (Wolves)
    
[Training Area]     [River Access]
    NONE (Safe)     LOW
```

---

## 6. Fishing Areas

### 6.1 River Access Fishing Spot

**Location:** Southeast corner, wooden dock

**Access:**
- Walk to dock
- Stand in designated fishing spots (2 positions)
- Same as River Zone A

**Fish Species Available:**

| Fish Name | Rarity | Catch Rate | Value | Time Bonus |
|-----------|--------|------------|-------|------------|
| Trout | Common | 35% | 60 IRF | Morning +10% |
| Minnow | Common | 30% | 20 IRF | Anytime |
| Carp | Common | 20% | 80 IRF | Afternoon +10% |
| Catfish | Common | 10% | 100 IRF | Night +15% |
| Salmon | Rare | 5% | 300 IRF | Evening only |

**Advantages Over Town Docks:**
- Less crowded (peaceful)
- Scenic location
- Same fish pool
- Convenient when leveling

**Fishing Quests:**
- Marina's tutorial quest can be completed here
- Counts toward fishing index

---

## 7. Wild Familiar Spawns

### 7.1 Common Familiars

#### Rabbit

**Spawn Locations:**
- Center Plains (near flowers)
- Western Hills (grass patches)
- Slime Pond (edge)

**Spawn Rate:** Common (10-15 active)  
**Spawn Time:** Daytime (6 AM - 6 PM)  
**Level:** 1  
**HP:** 30

**Taming Requirements:**
- Level: 1+
- Method: Weaken to <30% HP
- Food: Carrot (optional, +30% chance)
- Base Tame Chance: 60%

**Tamed Benefits:**
- **Type:** Passive Familiar
- **Bonus:** +2% Movement Speed
- **Appearance:** Brown or white variants
- **Personality:** Timid, hops around

**Loot if Killed:**
- Rabbit Fur (70%) - 1-2 units
- Raw Meat (50%) - 1 unit
- EXP: 5

---

#### Songbird

**Spawn Locations:**
- Trees throughout map
- Flying overhead
- Training Area fence posts

**Spawn Rate:** Common (15-20 active)  
**Spawn Time:** Daytime (5 AM - 8 PM)  
**Level:** 1  
**HP:** 20

**Taming Requirements:**
- Level: 1+
- Method: Weaken to <50% HP (flies, ranged needed)
- Food: Seeds (optional)
- Base Tame Chance: 55%

**Tamed Benefits:**
- **Type:** Decorative Familiar
- **Bonus:** Sings periodically (aesthetic)
- **Appearance:** Blue, red, or yellow variants
- **Personality:** Cheerful, perches on shoulder

**Loot if Killed:**
- Feather (80%) - 2-3 units
- EXP: 5

---

### 7.2 Rare Familiar Spawns

#### Fox

**Spawn Locations:**
- Wolf Den (ironic - hunts nearby)
- Western Hills (dens in rocks)
- Forest Edge (transition zone)

**Spawn Rate:** Uncommon (2-3 active)  
**Spawn Time:** Dawn/Dusk (5-7 AM, 6-8 PM)  
**Level:** 3  
**HP:** 80

**Taming Requirements:**
- Level: 3+
- Method: Weaken to <25% HP
- Food: Raw Meat (required)
- Base Tame Chance: 35%

**Tamed Benefits:**
- **Type:** Utility Familiar
- **Bonus:** +5% Item Drop Rate
- **Appearance:** Red-orange, bushy tail
- **Personality:** Clever, playful

**Loot if Killed:**
- Fox Pelt (60%) - 1 unit (Rare material)
- Fox Tail (30%) - 1 unit (Epic material)
- Raw Meat (70%) - 2-3 units
- EXP: 50

---

### 7.3 Special Encounter

#### Golden Rabbit (Legendary)

**Spawn Condition:** 
- 0.1% chance to spawn instead of normal rabbit
- Full moon night only
- Alpha Glade area

**Spawn Rate:** Extremely Rare  
**Level:** 5  
**HP:** 150

**Visual Design:**
- Golden glowing fur
- Sparkle particles
- Much faster than normal rabbit
- Crown-like ears

**Taming Requirements:**
- Level: 5+
- Method: Reduce to <10% HP (very difficult)
- Food: Golden Carrot (rare item)
- Base Tame Chance: 10%
- **Runs away if not tamed in 60 seconds**

**Tamed Benefits:**
- **Type:** Legendary Passive Familiar
- **Bonus:** +10% Luck, +5% Movement Speed
- **Appearance:** Glowing golden
- **Personality:** Regal, rare flex
- **Achievement:** "Golden Touch" title

**Loot if Killed:**
- Golden Fur (100%) - Legendary material
- Rabbit's Foot (50%) - Epic luck charm
- 1,000 IRF
- EXP: 500

---

## 8. Resource Nodes

### 8.1 Gatherable Items

#### Wildflowers

**Location:** Scattered throughout plains (30% coverage)

**Types:**
- **Sunflowers:** Yellow, tall
- **Lavender:** Purple clusters
- **White Daisies:** Common

**Gathering:**
- Click flower to pick
- No tool required
- Respawn: 5 minutes

**Uses:**
- Decorative (island decoration)
- Crafting (dye materials)
- Cooking (herbal tea recipe)
- Trading (sells for 5 IRF each)

**Spawn Count:** 100+ flowers active

---

#### Wolf Fangs (Ground Pickup)

**Location:** Wolf Den area, scattered on ground

**Appearance:**
- White fang sticking from dirt
- Glowing outline when close
- Respawn: Daily reset

**Gathering:**
- Walk over to auto-collect
- No tool needed

**Uses:**
- Crafting material (weapons)
- Quest item (Gruff's quest)
- Sells for 50 IRF

**Spawn Count:** 5-8 per day

---

#### Smooth River Stones

**Location:** River Access, riverbank

**Gathering:**
- Click stones along bank
- Respawn: 10 minutes

**Uses:**
- Decoration (path stones)
- Crafting (stone tools)
- Trading

**Spawn Count:** 20-30 active

---

### 8.2 Chest Spawns

#### Wooden Crates

**Location:** Random spawns in plains

**Spawn Rate:** 5 active at a time  
**Respawn:** 15 minutes after opened  
**Appearance:** Small wooden box, glowing aura

**Contents (Random):**
- Health Potion (50%)
- Bandages (30%)
- Copper/Silver coins (50-100 IRF)
- Common crafting materials (20%)
- Rare seed (5%)

---

## 9. Story Integration

### 9.1 Chapter 1: A New Beginning

**Quest: "First Steps"**

**Objectives:**
1. Exit Town Hub to Starter Plains
2. Reach Tutorial Field
3. Defeat 5 Green Slimes
4. Return to Mayor Theo

**Key Moments:**
- Player walks through South Gate (first time)
- Tutorial prompts appear
- First combat experience
- Victory feeling (level up to 2)

**Story Context:**
Mayor Theo: *"These fields used to be completely safe. But since The Fracture, even slimes have become aggressive. Show me you can handle yourself out there."*

---

### 9.2 Chapter 2: Into the Depths

**Quest: "Path to Adventure"**

**Objectives:**
1. Reach Level 5 in Starter Plains
2. Defeat Alpha Slime
3. Explore to Forest Edge
4. Report to Captain Zara

**Key Moments:**
- Player masters basic combat
- First boss fight (Alpha Slime)
- Discovery of Alpha Glade (ancient site)
- Professor Archimedes mentions the stones

**Story Context:**
*"The standing stones in Alpha Glade... they're pre-Fracture. The ancient Harmony civilization built them. But for what purpose? The answer lies deeper in the dungeons..."*

---

### 9.3 No Major Story Events

**Reasoning:**
- Starter Plains is tutorial zone
- Story accelerates in dungeons/later zones
- Focus on gameplay learning

---

## 10. Hidden Secrets & Easter Eggs

### 10.1 Secret: The Lonely Tree

**Location:** Exact center of map (0, 0, -200)

**Discovery:**
- Single tree in perfect center
- Sitting under it at sunset triggers dialogue

**Reward:**
- Meditation achievement
- Small HP/MP restore
- Peaceful music plays
- "Moment of Zen" title

**Flavor Text:**
*"You sit beneath the ancient tree and feel connected to IRIFA's heartbeat. For a moment, all worries fade away."*

---

### 10.2 Easter Egg: Wolf Pack Leadership

**Trigger:** Defeat 100 wolves total (tracked stat)

**Event:**
- Next Alpha Wolf spawn addresses player
- Special dialogue: *"You... strong. We respect."*
- Wolf Pack Respect unlock
- Wolves become non-aggressive for 1 hour
- Can walk among them peacefully

**Achievement:** "Wolf Whisperer"

---

### 10.3 Secret: Slime Pond Dive

**Location:** Slime Pond

**Method:**
- Jump in pond during full moon
- Swim to bottom (reach ground)
- Hidden treasure chest appears

**Reward:**
- Slime Crown (cosmetic hat)
- 1,000 IRF
- Rare slime pet egg
- "Slime King/Queen" title

---

### 10.4 Easter Egg: Training Dummy Master

**Location:** Training Dummy Area

**Challenge:**
- Deal 10,000 total damage to dummies
- Special dummy turns gold

**Reward:**
- Golden Sword (cosmetic weapon skin)
- "Dummy Destroyer" title
- Free weapon repair coupon

---

### 10.5 Secret: Flower Field Photo

**Location:** Center Plains, largest flower field

**Trigger:**
- Take screenshot during golden hour
- Game detects camera use in specific area

**Reward:**
- "Photographer" title
- Photo frame decoration
- Small aesthetic score boost

---

### 10.6 Hidden Achievement: Plains Explorer

**Requirements:**
- Visit all 11 landmarks
- Defeat both mini-bosses
- Catch fish at River Access
- Tame at least one familiar
- Find all chest spawns (5)

**Reward:**
- "Plains Master" title
- 5,000 IRF
- Rare equipment piece
- Fast travel unlock to plains

---

## 11. Loading & Transitions

### 11.1 Entering Starter Plains

**From Town Hub:**
- Walk south through South Gate
- **Seamless transition** (no loading screen)
- Music fades from town theme to plains theme
- Gradual visual blend (cobblestone → dirt path)

**From Private Island:**
- Portal to Town Hub first
- Then walk to plains

**From Death:**
- Respawn in Town Hub
- Must walk back

---

### 11.2 Leaving Starter Plains

**To Town Hub:**
- Walk north through South Gate
- Seamless transition
- Safe retreat available anytime

**To Forest Zone:**
- Walk east through Forest Edge
- Brief loading screen (2-3 seconds)
- Level recommendation warning (<8)

**To Private Island:**
- Must return to Town Hub portal first

---

### 11.3 Loading Screen Design

**When Transitioning to/from Plains:**

**Visual:**
- Grassland landscape with wolves/slimes
- Rotating 3D model of Alpha Slime
- Progress bar with grass growth animation

**Tips Displayed:**
- "Green Slimes are weak but plentiful. Great for beginners!"
- "Wolves hunt in packs. Be careful when fighting multiple!"
- "The Alpha Slime spawns every 30 minutes in Alpha Glade"
- "Gather flowers to craft decorations for your island!"
- "Rabbits make great first familiars. Feed them carrots!"

---

## 12. Technical Implementation

### 12.1 Performance Optimization

**Terrain:**
- Use Roblox Terrain system for grass
- LOD for distant hills
- Grass detail reduces at distance

**Monster Management:**
- Max 50 monsters active
- Despawn if no players nearby (100 studs)
- Spawn zones inactive when empty
- Client-side prediction for smooth combat

**Streaming:**
- StreamingEnabled = true
- Priority loading: Center Plains → Landmarks → Edges
- Monsters load before detailed decorations

---

### 12.2 Spawn System

```lua
-- Pseudo-code
local SpawnZones = {
    TutorialField = {
        Monsters = {
            {Type = "GreenSlime", Weight = 100}
        },
        MaxCount = 15,
        RespawnTime = 30
    },
    CenterPlains = {
        Monsters = {
            {Type = "GreenSlime", Weight = 60},
            {Type = "GrayWolf", Weight = 40}
        },
        MaxCount = 20,
        RespawnTime = 45
    },
    -- etc.
}

function MaintainSpawns()
    for zone, data in pairs(SpawnZones) do
        local currentCount = CountMonstersInZone(zone)
        if currentCount < data.MaxCount then
            SpawnMonster(zone, data.Monsters)
        end
    end
end
```

---

### 12.3 Combat System Integration

**Damage Calculations:**
- Server-authoritative (prevent exploits)
- Client prediction for smooth feel
- Validation on hit detection

**Loot Drops:**
- Server-side RNG (anti-exploit)
- Personal loot (dungeon system applies)
- Drop appears for killer + party

**EXP Distribution:**
- Scaled by damage dealt
- Party members share EXP (range 50 studs)
- Bonus for first-time kills

---

### 12.4 Roblox-Specific Implementation

**Workspace Structure:**
```
Workspace
├── StarterPlains (Folder)
│   ├── Terrain (Terrain object)
│   ├── Landmarks (Folder)
│   │   ├── SouthGate (Model)
│   │   ├── TutorialField (Model)
│   │   ├── CenterPlains (Model)
│   │   ├── AlphaGlade (Model)
│   │   └── etc.
│   ├── SpawnZones (Folder)
│   │   ├── SlimeSpawn1 (Part)
│   │   ├── WolfSpawn1 (Part)
│   │   └── etc.
│   ├── Resources (Folder)
│   │   ├── Flowers (Folder)
│   │   ├── Chests (Folder)
│   │   └── etc.
│   └── Boundaries (Folder)
```

**Key Scripts:**
- **MonsterSpawnService:** Handles all spawning
- **CombatService:** Damage, death, loot
- **FamiliarService:** Wild creature management
- **ResourceService:** Flowers, chests, pickups
- **BossService:** Alpha Slime timer & announcement

---

## 13. Balance & Progression

### 13.1 Expected Player Journey

**Level 1:**
- Start at Tutorial Field
- Fight Green Slimes (5-10 minutes)
- Level up to 2
- Learn basic combat

**Level 2-3:**
- Move to Center Plains
- Mix of slimes and wolves
- Practice dodging
- Learn resource management (HP/MP)
- 15-20 minutes

**Level 4:**
- Challenge Wolf Den
- Farm wolf materials
- Prepare for boss
- 10-15 minutes

**Level 5:**
- Defeat Alpha Slime (first boss)
- Feel accomplished
- Ready for dungeons or Forest Zone

**Total Time:** 40-60 minutes (first visit)

---

### 13.2 Loot Progression

**Level 1-2:**
- Common materials (Slime Gel)
- Small IRF amounts (2-5 per kill)
- Basic crafting intro

**Level 3-4:**
- Better materials (Wolf Pelt, Leather)
- Moderate IRF (10-20 per kill)
- Equipment drops (Common tier)

**Level 5:**
- Boss loot (Alpha Slime Core)
- Rare materials possible
- First Rare equipment chance
- Large IRF reward

---

## 14. Changelog & Version History

**Version 1.0 - February 9, 2026**
- Initial comprehensive map design
- Monster distribution defined
- Quest integration complete
- Familiar spawns documented
- Boss mechanics detailed
- Secrets added

---

## 15. Designer Notes

**Design Philosophy:**
Starter Plains exists to teach without overwhelming. Every mechanic introduced here appears in more complex form later. The open fields give new players confidence to explore while the clear danger zones (Wolf Den) teach caution.

**Key Lessons Taught:**
1. Combat basics (attack, dodge, heal)
2. Monster difficulty variation (slimes vs wolves)
3. Resource gathering (materials, IRF)
4. Boss mechanics (Alpha Slime phases)
5. Familiar taming introduction
6. Map exploration rewards

**Tuning Goals:**
- No frustrating deaths (fair difficulty)
- Clear progression (Level 1→5)
- Repeatable content (boss farming)
- Beautiful environment (screenshot worthy)
- Smooth transition to harder content

**Common Player Feedback:**
- "The plains felt safe but exciting"
- "Alpha Slime was my first real challenge"
- "Loved the peaceful fishing spot"
- "Golden Rabbit is my white whale!"

---

**END OF DOCUMENT**
