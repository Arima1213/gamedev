# MAP DESIGN DOCUMENT
## MAP 05: OCEAN ZONES

---

### Document Information
**Map Name:** Ocean Zones (Azure Waters)  
**Map ID:** MAP_OCEAN_ZONES  
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
**Primary Role:** Fishing hub, water exploration, and Water Heart Gem theme zone

**Key Functions:**
- Complete fishing progression system (beginner to expert)
- 4 distinct ocean zones with escalating difficulty
- Water-based familiar taming (dolphins, turtles, penguins)
- Underwater exploration areas
- Marina's primary domain (extends from Town Hub docks)
- Boat travel mechanics
- Treasure hunting and diving
- Water Heart Gem story connection

**Design Philosophy:**
*"The Azure Waters should feel vast, mysterious, and rewarding. From the safe beaches where children play to the deep trenches where legendary fish swim, every fisher should find their perfect spot. The ocean gives generously to those who respect it."*

### 1.2 Map Statistics
- **Total Size:** 1200×1200 studs (largest map, mostly water)
- **4 Sub-Zones:** Each with distinct characteristics
- **Player Capacity:** 40 players (distributed across zones)
- **Biome:** Ocean, beaches, tropical islands
- **Danger Level:** Varies (1/10 to 7/10 by zone)
- **Recommended Levels:** Zone A (All), B (10+), C (20+), D (30+)
- **Respawn Points:** Each zone has dock/beach spawn

### 1.3 Zone Overview

**Zone A: Starter Beach**
- Beginner fishing
- Tutorial area
- Safe, shallow water
- Levels: All

**Zone B: Rocky Coast**
- Intermediate fishing
- Rock formations, tide pools
- Some danger (crabs)
- Levels: 10+

**Zone C: Deep Sea Port**
- Advanced fishing
- Harbor town, ships
- Deeper water, sharks
- Levels: 20+

**Zone D: Tropical Reef**
- Expert fishing
- Beautiful coral reefs
- Exotic creatures
- Levels: 30+

### 1.4 Connections

**Accessible From:**
- Town Hub (Fishing Docks - Ocean Zone A directly)
- Portal Plaza (Ocean Portal - to Zone C)

**Internal Travel:**
- Walk along coastline (Zones A → B)
- Boat rental (Zones B → C → D)
- Swimming (short distances only)

**Connects To:**
- Town Hub (seamless from Zone A)
- Mysterious Lake (hidden underwater cave - quest unlock)

---

## 2. Visual Design & Atmosphere

### 2.1 Overall Aesthetic
**Theme:** Beautiful tropical ocean with depth variety

**Visual Style:**
- Clear blue/turquoise water (shallow)
- Deep blue/dark navy (deep water)
- White sand beaches with palm trees
- Rocky cliffs with waves crashing
- Coral reefs (vibrant colors)
- Wooden docks and piers
- Ships and boats (various sizes)
- Seagulls, dolphins, fish jumping

**Color Palette:**
- **Primary:** Azure blue, turquoise
- **Secondary:** White (sand/foam), brown (wood/rocks)
- **Accents:** Coral colors (pink, orange, purple)
- **Sky:** Clear blue to sunset orange

### 2.2 Atmosphere by Zone

**Zone A (Starter Beach):**
- Bright, cheerful, safe
- Children NPCs playing
- Gentle waves
- Tropical paradise vibe

**Zone B (Rocky Coast):**
- Dramatic, adventurous
- Waves crashing on rocks
- Tide pools with creatures
- Exploration feeling

**Zone C (Deep Sea Port):**
- Busy, commercial
- Harbor atmosphere
- Ships coming and going
- Industrial but charming

**Zone D (Tropical Reef):**
- Exotic, breathtaking
- Underwater beauty visible
- Paradise found
- Endgame reward zone

### 2.3 Time of Day Effects

**Sunrise (5-7 AM):**
- Pink/orange sky reflecting on water
- Most beautiful time
- Fish more active
- Perfect for fishing

**Day (7 AM - 6 PM):**
- Bright sunlight, sparkling water
- Clear visibility underwater
- Warm, inviting
- Best for diving/exploration

**Sunset (6-8 PM):**
- Golden hour on ocean
- Romantic atmosphere
- Silhouettes of ships
- Screenshot paradise

**Night (8 PM - 5 AM):**
- Moonlight on waves (silver path)
- Bioluminescent plankton glowing
- Mysterious, beautiful
- Special night fish spawn
- Starfish visible in shallows

### 2.4 Weather Variations

**Clear (60%):**
- Default beautiful weather
- Best visibility
- Normal fishing rates

**Cloudy (20%):**
- Overcast but calm
- Diffused lighting
- Moody atmosphere
- Legendary fish rate +10%

**Rain (10%):**
- Gentle rain on water
- Ripple effects
- Cozy fishing feeling
- All fish rates +15%

**Storm (5%):**
- Heavy rain, waves
- Lightning over ocean
- Dramatic and dangerous
- Legendary/Mythic fish rate +50%
- Best fishing time for experts
- Zone A players advised to take shelter

**Fog (5%):**
- Mysterious, reduced visibility
- Treasure chests spawn more
- Eerie but safe
- Special event fish

---

## 3. Layout & Landmarks

### 3.1 Map Layout Overview

```
                    [Town Hub Docks]
                            |
                    [OCEAN ZONE A]
                    [Starter Beach]
                       /        \
            [Boardwalk]        [Lighthouse]
                  |                  |
          [OCEAN ZONE B]        [Tide Pools]
          [Rocky Coast]              |
                  |            [Sea Cave]
            [Cliff Overlook]        |
                  |          [OCEAN ZONE C]
            [Harbor Town]     [Deep Sea Port]
                  |                  |
            [Ship Docks]      [Diving Platform]
                  |                  |
            [Boat Launch]────────────┘
                  |
          [OCEAN ZONE D]
          [Tropical Reef]
                  |
        [Coral Gardens]───[Sunken Temple]
```

---

## 3.2 OCEAN ZONE A: STARTER BEACH

### 3.2.1 Zone Overview
**Coordinates:** (0, 0, 0) - Starting ocean area  
**Size:** 300×300 studs  
**Depth:** 0-15 studs (shallow)  
**Danger Level:** 1/10 (Safe)  
**Recommended Level:** All levels

**Description:**
The safest and most accessible ocean area, directly connected to Town Hub fishing docks. A beautiful white sand beach with gentle waves, perfect for new anglers. Palm trees provide shade, beach umbrellas dot the sand, and children NPCs build sandcastles. The water is crystal clear and shallow enough to wade safely.

### 3.2.2 Landmarks in Zone A

#### MAIN BEACH
**Description:** Wide sandy beach (100 studs across)

**Visual Elements:**
- **White Sand:** Pristine, footprints appear
- **Palm Trees:** (12) Providing shade spots
- **Beach Umbrellas:** (6) Colorful, player can sit under
- **Beach Chairs:** (12) Lounging spots
- **Sandcastles:** Built by NPC children (decorative)
- **Volleyball Net:** Decorative, future mini-game hint
- **Beach Towels:** Scattered (players building them)
- **Picnic Areas:** Blankets with baskets

**NPCs:**
- **Generic Beach-Goers:** (8-10) Walking, sitting, playing
- **Children NPCs:** (4-5) Building sandcastles, playing in waves
- **Lifeguard NPC:** Sitting on tower, gives safety tips

**Functionality:**
- Social gathering
- AFK safe zone
- Rest area between fishing
- Tutorial starting point (Marina's first quest sends here)

---

#### BEGINNER FISHING SPOTS
**Description:** Multiple designated fishing areas

**Spot Locations:**
1. **Dock Extension:** 4 spots (most popular)
2. **Beach Shore:** 6 spots along beach
3. **Rock Outcrop:** 2 spots (scenic)
4. **Pier End:** 2 premium spots

**Total Capacity:** 14 concurrent fishers

**Fish Available:**
| Fish Name | Rarity | Catch Rate | Value |
|-----------|--------|------------|-------|
| Cod | Common | 40% | 50 IRF |
| Mackerel | Common | 35% | 60 IRF |
| Sardine | Common | 15% | 30 IRF |
| Tuna | Rare | 8% | 250 IRF |
| Sea Bass | Rare | 2% | 400 IRF |

**Tutorial Integration:**
- Marina's "First Catch" quest uses these spots
- Clear UI indicators for fishing zones
- Helper tooltips appear

---

#### LIGHTHOUSE
**Coordinates:** (150, 30, 0) - East end of beach

**Description:**
A classic red and white striped lighthouse standing 40 studs tall. Functional, rotating light at night. Can climb internal stairs to observation deck for panoramic ocean view.

**Visual Elements:**
- **Lighthouse Tower:** Red/white stripes, 40 studs
- **Light Room:** Glowing beacon (rotates at night)
- **Keeper's House:** Small attached building
- **Rocky Base:** Built on rock formation
- **Observation Deck:** Walkable platform at top
- **Flag Pole:** Maritime flags

**Interactive:**
- **Climb Stairs:** Internal staircase to top
- **Telescope:** At observation deck (can view all zones)
- **Guest Book:** Sign your name (achievement)

**NPC:**
- **Lighthouse Keeper (Generic):** Old sailor
  - Shares ocean lore
  - *"The lighthouse has guided sailors for generations. Before The Fracture, these waters were peaceful..."*

**Functionality:**
- Navigation landmark (visible from all ocean zones)
- View point for exploration
- Quest objective location
- Achievement spot

---

#### BOARDWALK
**Coordinates:** (-100, 0, 0) - West side of beach

**Description:**
A wooden boardwalk running parallel to beach (80 studs long). Shops, games, and food stalls create a festive atmosphere. String lights overhead (glow at night).

**Visual Elements:**
- **Wooden Planks:** Beach boardwalk style
- **Railings:** White painted wood
- **String Lights:** Overhead, glow at night
- **Stalls:** (5) Various decorative shops
- **Benches:** Seating every 15 studs
- **Trash Bins:** (4) Decorative
- **Flower Pots:** Colorful plants

**Shops/Stalls (Decorative):**
1. **Ice Cream Stand:** Beach themed
2. **Souvenir Shop:** Shells, trinkets
3. **Bait & Tackle:** Backup fishing supplies
4. **Snack Bar:** Food decorations
5. **Boat Rental:** For Zone B+ travel

**NPCs:**
- **Vendor NPCs:** (3) Standing at stalls
- **Tourist NPCs:** (4-6) Walking, shopping
- **Street Performer:** Musician (decorative)

**Functionality:**
- Atmosphere and immersion
- Future event location (festivals)
- Social gathering spot
- Boat rental quest starts here

---

#### SHALLOW WATERS
**Description:** Wadeable water area (0-5 studs deep)

**Visual Elements:**
- **Crystal Clear Water:** Can see sandy bottom
- **Small Fish Schools:** Swimming around (decorative)
- **Starfish:** On sand (can pick up for decoration)
- **Shells:** Collectible (decorative items)
- **Gentle Waves:** Particle effects
- **Foam:** Where waves break on shore

**Activities:**
- **Wade/Swim:** Shallow enough to walk
- **Shell Collecting:** 20 shells spawn, decorative items
- **Starfish Finding:** 5 spawn, rare
- **Splashing:** Particle effects when moving

**Wild Familiars:**
- **Hermit Crab (Common):**
  - Level 1
  - Spawns in shallow water
  - Tamable (60% chance)
  - Bonus: +2% luck
  - Cute pet, follows on beach

---

#### BEACH CAVE
**Coordinates:** (120, 0, -80) - Southeast corner

**Description:**
Small cave accessible only at low tide (time-based). Contains tide pools with unique creatures and hidden treasure chest.

**Tide System:**
- **Low Tide:** 6-9 AM, 6-9 PM (accessible)
- **High Tide:** Other times (blocked by water)

**Interior:**
- **Tide Pools:** (3) With trapped fish and crabs
- **Rock Formations:** Beautiful natural sculptures
- **Hidden Chest:** Spawns rare loot
- **Glow Worms:** Ceiling decoration (bioluminescent)

**Loot:**
- Pearls (rare crafting material)
- Rare fishing lures
- Ocean-themed decorations
- 500-1,000 IRF

**Secret:**
- Hidden passage to underwater cave system (discovered later)

---

### 3.2.3 Zone A Summary

**Safety:** Completely safe, no hostile monsters  
**Purpose:** Tutorial, beginner fishing, social hub  
**Fish Count:** 5 species (common to rare)  
**Unique Feature:** Direct connection to Town Hub  
**Time Investment:** 15-30 minutes for new players

---

## 3.3 OCEAN ZONE B: ROCKY COAST

### 3.3.1 Zone Overview
**Coordinates:** (-200, 0, -200) - Northwest of Zone A  
**Size:** 400×400 studs  
**Depth:** 5-30 studs (varied)  
**Danger Level:** 3/10 (Low-Medium)  
**Recommended Level:** 10+

**Description:**
A dramatic coastline with towering rock formations, crashing waves, and hidden tide pools. The water is rougher here, and the fishing is more challenging but rewarding. Rock climbing opportunities and sea caves to explore. Occasional hostile crabs patrol the rocks.

### 3.3.2 Landmarks in Zone B

#### ROCK FORMATIONS
**Description:** Massive stone pillars rising from ocean

**Visual Elements:**
- **Stone Pillars:** 15-25 studs tall (8 major formations)
- **Natural Arches:** Wave-carved tunnels through rocks
- **Flat Tops:** Climbable, fishing spots on top
- **Barnacles:** Covering lower sections
- **Seaweed:** Hanging from rocks
- **Nesting Birds:** Seagulls on peaks

**Gameplay:**
- **Climbing:** Can scale rocks (stamina drain)
- **Fishing Spots:** Premium locations on flat tops (less crowded)
- **Jumping Points:** Dive into deep water (safe, fun)
- **Exploration:** Multiple paths through arches

---

#### TIDE POOLS
**Description:** Natural pools formed in rocks, teeming with life

**Pools (5 major):**
1. **Hermit Crab Pool:** 20+ crabs visible
2. **Starfish Pool:** 15+ starfish (orange, purple)
3. **Anemone Pool:** Colorful sea anemones
4. **Small Fish Pool:** Minnows trapped at low tide
5. **Mystery Pool:** Rare creatures, changes daily

**Interactive:**
- **Examine Creatures:** Click for information
- **Collect Specimens:** For Professor Archimedes
- **Fishing:** Can fish in pools (unique catches)
- **Familiar Taming:** Hermit crabs here

**Educational:**
- Teaches ocean ecosystem
- Quest objective location
- Relaxing exploration

---

#### CLIFF OVERLOOK
**Coordinates:** (-300, 40, -200) - Highest point in Zone B

**Description:**
A grassy cliff top with breathtaking ocean views. A small stone shelter provides rest. Perfect for screenshots and planning next destination.

**Visual Elements:**
- **Stone Shelter:** Three walls, open to ocean
- **Wooden Bench:** Seating with best view
- **Telescope:** Pay 10 IRF to use (zoom to other zones)
- **Flower Patch:** Wildflowers in grass
- **Path:** Winding trail up from beach
- **Warning Signs:** "Cliff Edge - Stay Back"

**Functionality:**
- **Rest Area:** Full HP/MP regen while sitting
- **Fast Travel Point:** Unlocks after first visit
- **View Point:** Can see Zones A, C, D in distance
- **Quest Objective:** "Reach the Overlook" exploration quest

---

#### FISHING SPOTS (Zone B)
**Description:** More challenging fishing areas

**Spot Types:**
1. **Rock Top Fishing:** (4 spots) Elevated, requires climbing
2. **Arch Fishing:** (3 spots) Inside natural stone arches
3. **Jetty Fishing:** (4 spots) Wooden pier extending into water
4. **Boat Fishing:** (2 spots) Small fishing boats (decorative)

**Total Capacity:** 13 concurrent fishers

**Fish Available:**
| Fish Name | Rarity | Catch Rate | Value | Notes |
|-----------|--------|------------|-------|-------|
| Mackerel | Common | 25% | 60 IRF | Still common |
| Anchovy | Common | 20% | 40 IRF | Bait fish |
| Sea Bass | Rare | 15% | 400 IRF | Better rate |
| Snapper | Rare | 12% | 350 IRF | Rocky waters |
| Swordfish | Epic | 5% | 1,200 IRF | Challenge fish |
| Marlin | Epic | 3% | 1,500 IRF | Fight takes time |

**Difficulty Increase:**
- Fish fight harder (harder to reel)
- Weather affects catch rates more
- Stamina drain from difficult catches
- Better rewards compensate

---

#### SEA CAVES
**Description:** Multiple cave systems in cliff faces

**Cave Types:**

**1. Smuggler's Cave:**
- Hidden entrance behind waterfall
- Old pirate loot (decorative)
- Lootable chest (rare spawn)
- Lore journals (story hints)

**2. Echo Cave:**
- Deep cavern with echo effect
- All sounds reverberate
- Mysterious atmosphere
- Secret fishing spot (unique fish)

**3. Crystal Cave:**
- Walls lined with crystals
- Soft blue glow
- Peaceful meditation spot
- Rare mineral nodes

**Exploration:**
- Requires swimming through underwater entrances
- Breath meter (30 seconds underwater max)
- Rewarding for curious players
- Achievement for finding all three

---

#### MONSTERS IN ZONE B

**Giant Crab (Common Enemy):**
- **Level:** 12
- **HP:** 300
- **Damage:** 15-25
- **Behavior:** Patrols rocks, defends territory
- **Aggro:** Only when approached within 8 studs
- **Drops:** Crab Meat (cooking), Crab Shell (crafting)
- **Spawn Count:** 8-12 active

**Rock Barnacle (Decorative Hazard):**
- Stationary
- Deals 5 damage if touched
- Teaches caution near rocks

---

### 3.3.3 Zone B Summary

**Safety:** Mostly safe, minor crab threats  
**Purpose:** Intermediate fishing, exploration  
**Fish Count:** 6 species (common to epic)  
**Unique Feature:** Rock climbing, cave exploration  
**Time Investment:** 45-60 minutes full exploration

---

## 3.4 OCEAN ZONE C: DEEP SEA PORT

### 3.4.1 Zone Overview
**Coordinates:** (0, 0, -500) - South of Zone A  
**Size:** 500×500 studs  
**Depth:** 15-60 studs (deep)  
**Danger Level:** 5/10 (Medium-High)  
**Recommended Level:** 20+

**Description:**
A bustling harbor town with wooden buildings on stilts, large ships docked at piers, and deep blue water. This is where serious fishermen gather. The port serves as the gateway to Tropical Reef (Zone D) via boat travel. Commercial fishing boats, cargo ships, and naval vessels create an active atmosphere.

### 3.4.2 Landmarks in Zone C

#### HARBOR TOWN
**Description:** Waterfront settlement built on docks and platforms

**Buildings:**

**1. Harbor Master's Office:**
- Two-story building on main dock
- NPC Harbor Master (Generic) inside
- Quest giver for shipping quests
- Map of ocean zones on wall
- Ship schedule board

**2. Fisherman's Market:**
- Open-air market with stalls
- NPCs buying/selling fish
- Player can sell fish here (alternative to Marina)
- Prices vary daily (economy simulation)

**3. Sailor's Rest Inn:**
- Tavern/Inn hybrid
- Generic NPCs drinking, sharing tales
- Rumor board (hints for legendary fish)
- Decorative interior, can sit and socialize

**4. Ship Repair Yard:**
- Dry dock with ship under repair
- Scaffolding, workers (NPC)
- Shows industry of port
- Quest location (help repair ship)

**5. Warehouse District:**
- Storage buildings for cargo
- Crates stacked (parkour opportunity)
- Forklift NPCs moving goods
- Lootable crates (rare spawns)

**Population:**
- 15-20 generic NPCs (sailors, merchants, workers)
- Bustling, lived-in atmosphere
- Dynamic NPC movement (walking between buildings)

---

#### SHIP DOCKS
**Description:** Multiple piers with various vessels

**Ships:**

**1. Fishing Trawler (Large):**
- Commercial fishing vessel
- Can board and explore deck
- Fishing mini-game possibility (future)
- NPC crew working

**2. Cargo Ship (Huge):**
- 3-mast sailing vessel
- Decorative (can't board)
- Sails in/out on schedule (visual spectacle)
- Horn sound when departing

**3. Naval Patrol Ship (Medium):**
- Military-style vessel
- Guards NPC on deck
- Protects from pirates (lore)
- Cannot board (restricted)

**4. Player Rental Boats (Small):**
- 6 small boats available
- Use to travel to Zone D
- Autopilot (click destination)
- 100 IRF fee per trip

**Fishing from Docks:**
- **Deep Water Fishing:** (8 spots)
- Access to deeper fish species
- More challenging catches
- Higher value rewards

---

#### DIVING PLATFORM
**Coordinates:** (100, 0, -500) - East side of port

**Description:**
A specialized platform for deep diving and underwater exploration. Scuba equipment available (decorative), diving instructors, and submersible access.

**Visual Elements:**
- **Wooden Platform:** 30×30 studs
- **Diving Board:** Can jump from (fun)
- **Equipment Rack:** Scuba tanks, fins, masks (decorative)
- **Decompression Chamber:** Small building (decorative)
- **Ladder:** Down to water
- **Depth Markers:** Buoys showing safe zones

**NPCs:**
- **Diving Instructor (Generic):**
  - Teaches diving mechanics
  - "Hold your breath for 30 seconds underwater!"
  - Gives diving tutorial quest

**Underwater Access:**
- Can dive to explore underwater sections
- Breath meter: 30 seconds
- Surface to refill
- Treasure chests on ocean floor (rare)
- Underwater caves entrance

---

#### LIGHTHOUSE RUINS
**Description:** Old abandoned lighthouse on rocky island

**Access:** Small boat or strong swimming

**Visual Elements:**
- **Crumbling Tower:** Partially collapsed
- **Overgrown:** Vines and seaweed
- **Broken Light:** No longer functional
- **Ghost Ship:** Wrecked ship nearby (decorative)

**Exploration:**
- Can climb ruins (dangerous, gaps in floor)
- Hidden chest at top (risk/reward)
- Story lore (journal of old keeper)
- Haunted feeling (spooky music)

**Secret:**
- At midnight, ghost keeper appears (friendly)
- Shares story of The Fracture
- Gives blessing (+5% fishing luck for 24 hours)
- Achievement: "Lighthouse Guardian"

---

#### FISHING SPOTS (Zone C)

**Deep Water Fishing:**

| Fish Name | Rarity | Catch Rate | Value | Notes |
|-----------|--------|------------|-------|-------|
| Tuna | Rare | 15% | 250 IRF | Common here |
| Grouper | Rare | 12% | 350 IRF | Deep water |
| Marlin | Epic | 10% | 1,500 IRF | Strong fighter |
| Mahi-Mahi | Epic | 8% | 1,200 IRF | Fast, colorful |
| Blue Marlin | Legendary | 5% | 5,000 IRF | Trophy fish |
| Giant Tuna | Legendary | 3% | 6,000 IRF | Massive |
| Hammerhead Shark | Epic | 2% | 3,000 IRF | Dangerous |

**Special Mechanics:**
- **Treasure Chests:** 1% chance while fishing
  - Contains rare loot, IRF, equipment
- **Stamina Drain:** Legendary fish drain stamina fast
- **Equipment Breaks:** 5% chance rod breaks on legendary

---

#### UNDERWATER SECTIONS
**Description:** Diveable areas beneath port

**Areas:**

**1. Coral Garden (Preview):**
- Beautiful coral formations
- Tropical fish swimming
- Teaser for Zone D
- Cannot reach (too far)

**2. Shipwreck:**
- Sunken cargo vessel
- Explore interior (breath meter challenge)
- Treasure chests inside (3 spawn points)
- Skeleton decorations (pirates?)

**3. Underwater Cave:**
- Leads to mysterious location
- Breath meter test
- Requires full stamina
- Connects to Mysterious Lake (story quest)

**Hazards:**
- **Breath Timer:** 30 seconds
- **Sharks:** Occasional reef shark (avoidable)
- **Currents:** Push player slightly

---

#### MONSTERS IN ZONE C

**Reef Shark (Uncommon Enemy):**
- **Level:** 22
- **HP:** 800
- **Damage:** 30-50
- **Behavior:** Patrols deep water, aggressive if player swims too deep
- **Aggro:** Attacks swimmers in deep water (>30 studs depth)
- **Drops:** Shark Tooth (rare crafting), Shark Fin (cooking)
- **Spawn Count:** 3-5 active

**Jellyfish (Passive Hazard):**
- **Level:** N/A (not killable)
- **Behavior:** Floats slowly
- **Contact:** 15 damage, poison (10 damage/sec for 5 sec)
- **Avoidable:** Easy to dodge
- **Visual Warning:** Glowing, visible from distance

---

### 3.4.3 Zone C Summary

**Safety:** Moderate danger (sharks in deep water)  
**Purpose:** Advanced fishing, harbor town hub, boat travel  
**Fish Count:** 7 species (rare to legendary)  
**Unique Feature:** Harbor town, underwater diving, boat access  
**Time Investment:** 1-2 hours full exploration

---

## 3.5 OCEAN ZONE D: TROPICAL REEF

### 3.5.1 Zone Overview
**Coordinates:** (300, 0, -800) - Southeast, accessed by boat  
**Size:** 600×600 studs  
**Depth:** 10-80 studs (deepest)  
**Danger Level:** 7/10 (High)  
**Recommended Level:** 30+

**Description:**
A remote tropical paradise with stunning coral reefs, exotic fish, and dangerous predators. The most beautiful and rewarding ocean zone. White sand islands, crystal-clear turquoise water, and vibrant underwater life. This is where expert fishermen seek legendary and mythic catches.

### 3.5.2 Landmarks in Zone D

#### CORAL GARDENS
**Description:** Massive coral reef system, visible underwater

**Visual Elements:**
- **Brain Coral:** Large round formations
- **Staghorn Coral:** Branching structures
- **Fan Coral:** Colorful waving fans
- **Anemones:** With clownfish (decorative)
- **Tropical Fish Schools:** Swimming everywhere
- **Sea Turtles:** Gliding peacefully
- **Rays:** Gliding along bottom

**Colors:**
- Pink, orange, purple, blue, yellow corals
- Most visually stunning area in game
- Screenshot paradise

**Exploration:**
- Snorkeling view (head underwater to see)
- Diving access (30-second breath timer)
- Multiple levels of reef (shallow to deep)
- Hidden caves within coral

**Wild Familiars:**
- **Clownfish (Common):** Level 30, decorative pet
- **Sea Turtle (Rare):** Level 32, tamable, +10% swimming speed
- **Manta Ray (Legendary):** Level 35, rare spawn, +15% water speed

---

#### TROPICAL ISLAND
**Description:** Small sandy island with palm trees

**Visual Elements:**
- **White Sand Beach:** Pristine, untouched
- **Palm Trees:** (8) Providing shade
- **Coconut Trees:** Coconuts hanging (decorative)
- **Bamboo:** Growing in patches
- **Tropical Flowers:** Hibiscus, orchids
- **Hammock:** Between two palms (can sit/rest)
- **Campfire Pit:** Can light for cooking (future feature)

**Functionality:**
- **Rest Area:** Safe zone on island
- **Fishing Spots:** Beach and island perimeter (6 spots)
- **Exploration:** Hidden treasure buried on island (dig mechanic)
- **Screenshot Location:** Beautiful tropical paradise

**Hidden Secret:**
- Dig at marked X (faint mark in sand)
- Treasure chest with legendary loot
- Resets weekly

---

#### DEEP TRENCH
**Description:** Underwater canyon dropping to extreme depths

**Visual Elements:**
- **Dark Depths:** Sunlight doesn't reach bottom
- **Steep Walls:** Canyon sides covered in coral
- **Mysterious Glow:** Bioluminescent creatures at bottom
- **Strong Currents:** Visual water flow
- **Pressure Warning:** UI warns of depth danger

**Depth Levels:**
- **0-20 studs:** Safe, visible
- **20-40 studs:** Dim, cautious
- **40-60 studs:** Dark, dangerous
- **60-80 studs:** Abyssal, extreme danger

**Diving Challenge:**
- Requires stamina management
- Breath timer critical
- Legendary fish spawn at depths
- High risk, high reward

**Hazards:**
- **Pressure Damage:** 10 damage/sec below 60 studs
- **Limited Visibility:** Hard to see at depth
- **Predators:** Hammerhead sharks patrol
- **Disorientation:** Easy to lose direction

---

#### SUNKEN TEMPLE
**Description:** Ancient Harmony civilization ruins underwater

**Visual Elements:**
- **Stone Pillars:** Covered in barnacles
- **Carved Statues:** Ancient guardians
- **Broken Walls:** Overgrown with coral
- **Intact Chamber:** Central room (air pocket)
- **Glowing Runes:** Faint magical energy
- **Artifacts:** Scattered pottery and tools

**Story Integration:**
- Connected to Water Heart Gem
- Quest location (Chapter 2-3)
- Lore about ancient civilization
- Professor Archimedes sends player here

**Exploration:**
- **Air Pocket Chamber:** Can breathe inside
- **Puzzle:** Activate runes in correct order
- **Reward:** Water Fragment (story item)
- **Boss:** Corrupted Guardian (optional, respawns weekly)

**Boss: Coral Guardian (Elite)**
- Level 35
- 8,000 HP
- Water magic attacks
- Drops: Legendary crafting materials, Water-themed equipment
- Achievement: "Temple Raider"

---

#### FISHING SPOTS (Zone D)

**Expert Fishing:**

| Fish Name | Rarity | Catch Rate | Value | Notes |
|-----------|--------|------------|-------|-------|
| Parrotfish | Common | 20% | 150 IRF | Colorful, tropical |
| Clownfish | Common | 15% | 120 IRF | Anemone dwellers |
| Angelfish | Rare | 12% | 500 IRF | Beautiful patterns |
| Butterfly Fish | Rare | 10% | 450 IRF | Delicate, prized |
| Reef Shark | Epic | 8% | 2,000 IRF | Dangerous catch |
| Stingray | Epic | 6% | 2,500 IRF | Requires skill |
| Manta Ray | Legendary | 4% | 8,000 IRF | Massive, rare |
| Celestial Jellyfish | Mythic | 0.5% | 50,000 IRF | Glowing, magical |

**Special Conditions:**
- **Full Moon:** Celestial Jellyfish rate × 5 (2.5%)
- **Storm:** All legendary/mythic rates +50%
- **Night:** Bioluminescent fish spawn (different pool)

**Mythic Fish: Celestial Jellyfish**
- Only spawns in Zone D
- Requires luck +20% minimum
- Glows rainbow colors
- Extremely difficult to reel in (3-minute fight)
- Achievement: "Deep Sea Legend"
- One of rarest catches in game

---

#### VOLCANIC UNDERWATER VENTS
**Description:** Underwater geothermal vents (teaser for Volcanic Region)

**Visual Elements:**
- **Sulfur Vents:** Yellow smoke rising from seafloor
- **Warm Water Currents:** Visible distortion
- **Unique Ecosystem:** Heat-loving creatures
- **Orange Glow:** From thermal energy

**Gameplay:**
- **Danger:** 20 damage/sec if too close to vents
- **Special Fish:** Heat-adapted species (rare)
- **Mineral Deposits:** Can mine (requires diving)
- **Story Connection:** Hints at volcanic power

---

#### PIRATE COVE (Secret Location)
**Description:** Hidden cove accessible through cave system

**Discovery:**
- Swim through underwater cave
- Breath timer challenge
- Secret entrance marked by X on rock

**Interior:**
- **Pirate Ship (Abandoned):** Can board and explore
- **Treasure Room:** Multiple chests (respawn weekly)
- **Skeleton Crew:** Decorative pirate skeletons
- **Pirate Flag:** Can take as decoration
- **Journal:** Story of pirate crew during Fracture

**Loot:**
- Pirate-themed decorations
- Legendary fishing lures
- Rare equipment blueprints
- 10,000-20,000 IRF
- Achievement: "Pirate Hunter"

---

#### MONSTERS IN ZONE D

**Hammerhead Shark (Elite Enemy):**
- **Level:** 35
- **HP:** 2,000
- **Damage:** 60-90
- **Behavior:** Patrols reef, aggressive, fast
- **Aggro:** Attacks on sight in water
- **Drops:** Hammerhead Trophy (legendary), Shark Meat
- **Spawn Count:** 2-3 active

**Barracuda (Aggressive Fish):**
- **Level:** 33
- **HP:** 1,200
- **Damage:** 40-60
- **Behavior:** Fast, ambush attacks
- **Drops:** Barracuda Fang, Fish Meat
- **Spawn Count:** 5-7 active

**Sea Serpent (World Boss - Rare Spawn):**
- **Level:** 40
- **HP:** 15,000
- **Spawn Rate:** 5% chance per day (server-wide)
- **Announcement:** "A massive Sea Serpent has been spotted in the Tropical Reef!"
- **Duration:** 30 minutes
- **Drops:** Serpent Scale (mythic), Legendary equipment, 50,000 IRF
- **Challenge:** Requires party of 5+, boat combat mechanics

---

### 3.5.3 Zone D Summary

**Safety:** High danger (sharks, barracuda, sea serpent)  
**Purpose:** Endgame fishing, exploration, legendary content  
**Fish Count:** 8 species (common to mythic)  
**Unique Feature:** Most beautiful zone, mythic fish, sunken temple  
**Time Investment:** 2-3 hours full exploration

---

## 4. NPC Locations & Details

### 4.1 Core NPCs

**Marina Seafoam (NPC_FISHERMAN)**
- **Primary Location:** Town Hub Fishing Docks (Zone A connection)
- **Secondary Appearance:** Deep Sea Port (rare, weekly visit)
- **Services:** Fishing rods, bait, fish buying, contests, quests
- **Quest Chain:** "Angler's Journey" (4 quests across all zones)

### 4.2 Generic NPCs by Zone

**Zone A (Starter Beach):**
- Beach-goers (10)
- Children (5)
- Lifeguard (1)
- Boardwalk vendors (3)

**Zone B (Rocky Coast):**
- Rock climbers (2)
- Tide pool researchers (1)
- Lighthouse keeper (1)

**Zone C (Deep Sea Port):**
- Harbor master (1)
- Sailors (8)
- Merchants (5)
- Ship crew (6)
- Diving instructor (1)

**Zone D (Tropical Reef):**
- None (remote, uninhabited)

### 4.3 Event NPCs

**Traveling Merchant (Cornelius):**
- Rare spawn at Deep Sea Port marketplace
- Sells exotic fish bait, rare lures

**Pirate Ghost (Secret):**
- Appears in Pirate Cove at midnight
- Shares treasure map (quest)
- Gives pirate-themed rewards

---

## 5. Monster Distribution

### 5.1 Monster Summary by Zone

| Zone | Monsters | Danger | Notes |
|------|----------|--------|-------|
| A: Starter Beach | None | Safe | Tutorial zone |
| B: Rocky Coast | Giant Crabs | Low | Avoidable |
| C: Deep Sea Port | Reef Sharks, Jellyfish | Medium | Water hazards |
| D: Tropical Reef | Hammerhead Sharks, Barracuda, Sea Serpent | High | Combat required |

### 5.2 Monster Behavior

**Water Combat Mechanics:**
- Slower movement in water
- Stamina drains faster
- Swimming affects combat
- Depth matters (pressure damage)

---

## 6. Fishing Areas

### 6.1 Comprehensive Fishing Guide

**Zone A (Beginner):**
- 14 spots
- 5 fish species
- Easiest catches
- Tutorial focus

**Zone B (Intermediate):**
- 13 spots
- 6 fish species
- Moderate difficulty
- Rock top fishing unique

**Zone C (Advanced):**
- 8 spots
- 7 fish species
- Challenging catches
- Treasure chest chance

**Zone D (Expert):**
- 6 spots
- 8 fish species
- Hardest catches
- Mythic fish possible

**Total:** 41 fishing spots across 4 zones

### 6.2 Fishing Progression Curve

**Level 1-10:** Zone A (learn basics)  
**Level 10-20:** Zone B (improve skill)  
**Level 20-30:** Zone C (master techniques)  
**Level 30+:** Zone D (legendary fishing)

---

## 7. Wild Familiar Spawns

### 7.1 Zone A Familiars
- **Hermit Crab:** Common, cute pet
- **Seagull:** Common, decorative

### 7.2 Zone B Familiars
- **Rock Crab:** Common, defensive bonus
- **Pelican:** Rare, fishing luck bonus

### 7.3 Zone C Familiars
- **Dolphin:** Rare, swimming speed boost
- **Penguin:** Rare (ice migration event)

### 7.4 Zone D Familiars
- **Clownfish:** Common, decorative
- **Sea Turtle:** Rare, swimming speed
- **Manta Ray:** Legendary, best water familiar

---

## 8. Resource Nodes

### 8.1 Collectibles

**Shells:** All zones, decorative items  
**Starfish:** Zones A & B, rare decorations  
**Pearls:** Rare drops from diving, crafting  
**Coral Fragments:** Zone D, decorative/crafting  
**Seaweed:** All zones, cooking ingredient

### 8.2 Treasure Chests

**Spawn Locations:**
- Beach caves (Zones A & B)
- Shipwrecks (Zone C)
- Coral caves (Zone D)
- Pirate Cove (Zone D, weekly reset)

**Loot Tables:**
- Common: Potions, IRF (100-500)
- Rare: Fishing lures, decorations, IRF (1,000-3,000)
- Epic: Equipment, blueprints, IRF (5,000-10,000)
- Legendary: Unique items, IRF (20,000+)

---

## 9. Story Integration

### 9.1 Chapter 2: Into the Depths

**Ocean Connection:**
- Marina mentions strange fish behavior
- Void corruption affecting sea creatures
- Quest: Investigate Zone C shipwreck

### 9.2 Chapter 3: Echoes of the Past

**Sunken Temple Quest:**
- Professor Archimedes sends player to Zone D
- Dive to Sunken Temple
- Find Water Heart Fragment
- Fight Coral Guardian
- Learn about ancient civilization

**Key Moments:**
- Discovery of underwater ruins
- Vision of The Fracture (water gem shattering)
- First underwater boss fight

---

## 10. Hidden Secrets & Easter Eggs

### 10.1 Secret: Message in a Bottle

**Location:** Random spawn on any beach

**Trigger:** Find bottle (1 spawns per day, random zone)

**Content:** Message from sailor during Fracture, coordinates to treasure

**Reward:** Follow coordinates, dig up legendary fishing rod

---

### 10.2 Easter Egg: Dolphin Dance

**Location:** Zone C or D

**Trigger:** Swim alongside dolphin familiar for 2 minutes

**Event:** Dolphin does backflips, hearts appear

**Reward:** "Dolphin Whisperer" title, +5% water familiar bond

---

### 10.3 Secret: Lighthouse Ghost

**Location:** Zone B Lighthouse or Zone C Ruins

**Trigger:** Visit at midnight

**Event:** Ghost keeper appears, tells story

**Reward:** +5% fishing luck for 24 hours, "Ghost Friend" achievement

---

### 10.4 Easter Egg: Giant Fish Shadow

**Location:** Zone D, Deep Trench

**Trigger:** Random while fishing (0.1% chance)

**Event:** Massive shadow passes underneath (Leviathan hint)

**Lore:** Teases future mythic fish or boss

---

### 10.5 Secret: Coral Symphony

**Location:** Zone D Coral Gardens

**Trigger:** Touch corals in specific pattern (hint in library)

**Event:** Corals glow and hum musically

**Reward:** "Ocean Musician" title, coral chime decoration

---

### 10.6 Hidden Achievement: Ocean Master

**Requirements:**
- Catch 1 of each fish species (all zones)
- Visit all landmarks in all zones
- Defeat all ocean monsters (shark, barracuda, serpent, guardian)
- Tame all water familiars
- Find all treasure chests (10 total)
- Complete Marina's quest chain

**Rewards:**
- "Ocean Master" title
- 50,000 IRF
- Legendary fishing equipment set
- Boat decoration for private island
- Fast travel to any ocean zone

---

## 11. Loading & Transitions

### 11.1 Zone Transitions

**Zone A ↔ Town Hub:**
- Seamless (no loading)
- Walk from docks

**Zone A → Zone B:**
- Walk along coastline
- Brief fade (1 second)

**Zone B → Zone C:**
- Can walk (long) or use boat
- Boat = loading screen (3 seconds)

**Zone C → Zone D:**
- Boat required (too far to swim)
- Loading screen (4 seconds)
- Ocean journey animation

### 11.2 Loading Screens

**Visuals:**
- Ocean waves animation
- Rotating fish models
- Marina's tips

**Tips:**
- "Storm fishing increases legendary fish spawn rates!"
- "Zone D's Celestial Jellyfish only spawns during full moon!"
- "Diving lets you explore shipwrecks and coral caves!"
- "Feed dolphins to befriend them as familiars!"

---

## 12. Technical Implementation

### 12.1 Water System

**Roblox Terrain Water:**
- Use Terrain water for ocean
- Adjustable depth
- Wave animations
- Transparency gradient by depth

**Swimming Mechanics:**
```lua
function SwimmingService:HandleSwimming(player)
    if InWater(player) then
        player.WalkSpeed = 12 -- Slower in water
        player.JumpPower = 20 -- Lower jumps
        
        -- Breath timer for diving
        if Underwater(player) then
            StartBreathTimer(30) -- 30 seconds
        end
    end
end
```

### 12.2 Fishing System Integration

**Already defined in GDD_Systems_Fishing.md**

**Zone-Specific Additions:**
- Each zone has fish pool table
- Weather modifiers apply
- Depth affects catches

### 12.3 Performance Optimization

**Water Rendering:**
- LOD for distant water
- Particle effects scale with distance
- Fish schools instanced

**Zone Streaming:**
- Load only active zone + adjacent
- Unload distant zones
- Boat travel triggers zone load

---

**END OF DOCUMENT**
