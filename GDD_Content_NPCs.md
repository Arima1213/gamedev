# IRIFA: Realms of Harvest & Adventure
## Game Design Document - NPC Content

---

### Document Information
**Document Type:** Content Design  
**Category:** Characters & Dialogue  
**Version:** 1.0  
**Last Updated:** February 9, 2026  
**Total NPCs:** 12 core NPCs + 5 special NPCs

---

## Table of Contents
1. [NPC System Overview](#1-npc-system-overview)
2. [Core NPCs](#2-core-npcs)
3. [Special NPCs](#3-special-npcs)
4. [Dialogue System](#4-dialogue-system)
5. [Quest Integration](#5-quest-integration)
6. [Relationship System](#6-relationship-system)
7. [Technical Implementation](#7-technical-implementation)

---

## 1. NPC System Overview

### 1.1 NPC Purpose

NPCs serve multiple functions:
- **Tutorial Guides:** Teach game systems
- **Vendors:** Sell items and equipment
- **Crafters:** Provide crafting services
- **Quest Givers:** Advance story and progression
- **World Building:** Add personality and lore

### 1.2 NPC Design Principles

**Memorable Personalities:**
- Each NPC has distinct personality
- Unique speaking style
- Memorable visual design
- Clear role in the world

**Functional Clarity:**
- Players instantly understand NPC's purpose
- Consistent location and availability
- Clear UI indicators for services

**Progressive Dialogue:**
- Dialogue changes based on player progress
- NPCs remember player achievements
- Build relationships over time

---

## 2. Core NPCs

### 2.1 Mayor Theodore "Theo" Brightwood

**NPCID:** NPC_MAYOR  
**Role:** Tutorial Guide, Town Leader  
**Location:** Town Hall (daytime), Town Square (rotates)  
**Availability:** Always available

**Visual Design:**
- Middle-aged human male, friendly face
- Brown beard, warm smile
- Fancy suit with gold trim
- Mayor's sash across chest
- Top hat (occasionally)

**Personality:**
- Warm and welcoming
- Father-figure energy
- Slightly forgetful but wise
- Tells stories about "the old days"
- Genuinely cares about town and newcomers

**Voice/Speaking Style:**
*"Ah, welcome welcome! Another fine day in our humble town!"*  
*"Back in my day, we had to mine with our BARE HANDS! ...Well, not really, but it felt like it!"*  
*"You remind me of myself when I was young... full of potential and slightly confused!"*

**Services:**
- Main story quest giver
- Tutorial quests
- General information
- Town announcements

**Quest Chain: "Welcome to IRIFA"**

**Quest 1: A New Beginning**
- Objective: Talk to Mayor, receive tour of town
- Reward: 500 IRF, Town Map

*"Welcome to our little paradise! I'm Mayor Brightwood, but everyone calls me Theo. Let me show you around!"*

**Quest 2: Meeting the Locals**
- Objective: Visit Blacksmith, Farmer, Fisherman
- Reward: Starter tool set

*"The folks here are the best you'll ever meet. Go introduce yourself - they love new faces!"*

**Quest 3: Your Own Slice of Paradise**
- Objective: Visit Private Island for first time
- Reward: 1,000 IRF, 5 Potato Seeds

*"Every resident gets their own island! It's not much at first, but with hard work, you'll turn it into something spectacular!"*

**Dialogue Progression:**

**First Meeting:**
*"Ah, a new face! Welcome to our town! I'm Mayor Brightwood. You must be tired from your journey. Let me help you get settled in!"*

**After Tutorial:**
*"Look at you, already fitting in! The townspeople have been talking about your hard work. Keep it up!"*

**Mid Game:**
*"I've been hearing impressive things about you! You've caught some rare fish, defeated dungeon monsters, AND your island is looking beautiful? Color me impressed!"*

**Late Game:**
*"You've become a legend around here, you know. Remember when you first arrived, looking confused? Look at you now - a true master adventurer!"*

**Endgame:**
*"I knew from the moment you arrived that you were special. You've not just survived here - you've THRIVED. This town is lucky to have you!"*

---

### 2.2 Gruff "Hammer" Ironforge

**NPCID:** NPC_BLACKSMITH  
**Role:** Blacksmith, Weapon/Tool Crafter  
**Location:** Blacksmith Forge (south of Town Square)  
**Availability:** 6 AM - 10 PM (game time)

**Visual Design:**
- Muscular dwarf male, massive arms
- Thick red beard with singed tips
- Leather apron covered in soot
- Safety goggles on forehead
- Hammer on belt (always)
- Covered in soot and ash

**Personality:**
- Gruff exterior, heart of gold
- Takes pride in his craft
- Perfectionist
- Speaks bluntly
- Respects hard work
- Softens up after earning his respect

**Voice/Speaking Style:**
*"Hmph. Another greenhorn. Well, don't expect me to do the work FOR you!"*  
*"You want quality? Then bring me QUALITY materials. Simple as that."*  
*"...Fine work on that last commission. You're learning. Don't let it go to your head."*

**Services:**
- Craft weapons and tools
- Smelt ore into ingots
- Enhance equipment
- Upgrade tool stats
- Break open geodes
- Sell basic tools

**Shop Inventory:**
| Item | Price (IRF) | Stock |
|------|-------------|-------|
| Wooden Pickaxe | 500 | Infinite |
| Stone Pickaxe | 2,000 | Infinite |
| Iron Ore | 100 | 50/day |
| Coal | 50 | 100/day |
| Repair Kit | 200 | Infinite |

**Quest Chain: "Forging Ahead"**

**Quest 1: First Forging**
- Objective: Craft Iron Pickaxe
- Reward: Blacksmithing XP, Iron Sword

*"If you're gonna survive in those dungeons, you'll need proper equipment. Bring me these materials, and I'll show you how it's done."*

**Quest 2: Geode Mystery**
- Objective: Bring 10 geodes to crack open
- Reward: 2,000 IRF, Rare mineral guaranteed

*"Hmm, interesting. These geodes... there's something special inside. Let's crack 'em open and see what fortune brings."*

**Quest 3: Master's Challenge**
- Objective: Craft a Legendary weapon
- Reward: Master Blacksmith title, 20% discount

*"You've come far. But can you handle a TRUE challenge? Craft me a legendary weapon, and I'll acknowledge you as an equal."*

**Dialogue Progression:**

**First Meeting:**
*"Hmph. New in town? Well, if you need tools or weapons, you've come to the right place. But I don't do charity - bring materials and coin."*

**Low Friendship:**
*"Again? Fine, what do you need this time? Make it quick, I've got work to do."*

**Medium Friendship:**
*"Oh, it's you. Actually... your last order came out pretty good. You brought quality materials. Keep that up."*

**High Friendship:**
*"Ah, my favorite customer! You know, you remind me of myself when I was younger. Same dedication to the craft. What can I make for you today?"*

**Max Friendship:**
*"You've earned my respect, friend. Not many can say that. Here, I've been working on something special for you... [gives unique item]"*

**Special Dialogue - Dragon Materials:**
*"Wait... is this... DRAGON SCALE?! By the forge! I never thought I'd get to work with this in my lifetime! Let me show you what a master can truly create!"*

---

### 2.3 Marina Seafoam

**NPCID:** NPC_FISHERMAN  
**Role:** Fishing Instructor, Rod Merchant  
**Location:** Fishing Docks (east waterfront)  
**Availability:** 5 AM - 8 PM (game time)

**Visual Design:**
- Young adult female human, athletic build
- Long teal-colored hair in ponytail
- Freckles across nose
- Wears fishing vest covered in lures
- Rubber boots
- Straw hat
- Always has fishing rod in hand

**Personality:**
- Cheerful and optimistic
- Patient teacher
- Loves the ocean
- Storyteller (fish tales)
- Competitive (fishing contests)
- Environmental advocate

**Voice/Speaking Style:**
*"The ocean is calling! Can you hear it?"*  
*"Every fish has a story. Want to hear about the one that got away? ...Wait, no, I CAUGHT that one!"*  
*"Patience is key! Unless it's a legendary fish, then you PULL LIKE YOUR LIFE DEPENDS ON IT!"*

**Services:**
- Sell fishing rods and equipment
- Craft fishing rods
- Teach fishing techniques
- Buy fish from players
- Host fishing contests
- Fish identification

**Shop Inventory:**
| Item | Price (IRF) | Stock |
|------|-------------|-------|
| Bamboo Rod | 300 | Infinite |
| Oak Rod | 5,000 | 5/day |
| Bait | 10 | 500/day |
| Fishing Line | 50 | 100/day |
| Tackle Box Expansion | 10,000 | 1/player |

**Quest Chain: "Angler's Journey"**

**Quest 1: First Catch**
- Objective: Catch 5 any fish
- Reward: 300 IRF, Better fishing rod

*"Welcome to the water! Here, take this rod - it's a bit worn, but it'll get you started. Come back when you've caught your first few fish!"*

**Quest 2: The Rare Ones**
- Objective: Catch 1 Rare fish
- Reward: 1,500 IRF, Fishing XP boost

*"Good work! But ANY fish can catch common ones. Let's see if you can land something... special. Try fishing during different weather!"*

**Quest 3: Storm Fishing**
- Objective: Catch fish during a storm
- Reward: Enchanted Fishing Rod recipe

*"You want to know a secret? The BEST fish come out during storms! Dangerous? Sure. Worth it? ABSOLUTELY!"*

**Quest 4: Leviathan Legend**
- Objective: Catch the Leviathan Eel (Mythic)
- Reward: 50,000 IRF, Master Angler title

*"There's a legend... a fish so massive, so rare, that most fishermen think it's just a story. But I KNOW it's real. And I think YOU can catch it."*

**Dialogue Progression:**

**First Meeting:**
*"Hey there! I'm Marina! You look like you could use some fresh air and a fishing rod! Want me to teach you?"*

**After First Catch:**
*"YES! I knew you had it in you! That feeling when the line tugs? That's MAGIC, friend!"*

**Mid Game:**
*"Wow, your fishing index is filling up nicely! Have you tried night fishing yet? Completely different experience!"*

**After Catching Legendary Fish:**
*"NO WAY. YOU CAUGHT A LEGENDARY?! I've been fishing for YEARS and... okay, okay, I'm not jealous. Much. Tell me EVERYTHING!"*

**Max Friendship:**
*"You know what? You're not just a great angler - you're a great friend. This spot on the dock? It's yours anytime. We'll watch the sunset together."*

**Special Events - Fishing Contest:**
*"ATTENTION ANGLERS! The Annual Grand Fishing Contest starts in 1 hour! Biggest fish wins LEGENDARY PRIZES! You IN?!"*

---

### 2.4 Grandma Rose Bloomfield

**NPCID:** NPC_FARMER  
**Role:** Farming Instructor, Seed Merchant  
**Location:** Farm Shop (north of Town Square)  
**Availability:** 6 AM - 6 PM (game time)

**Visual Design:**
- Elderly human female, gentle appearance
- Silver hair in bun
- Round glasses
- Floral dress with apron
- Straw hat with flowers
- Basket of produce
- Always smiling

**Personality:**
- Motherly and nurturing
- Wise life advice giver
- Loves plants like children
- Bakes cookies for everyone
- Tells farming wisdom
- Surprisingly strong for her age

**Voice/Speaking Style:**
*"Oh dearie, you look thin! Have you been eating properly? Here, take some fresh vegetables!"*  
*"Patience and love - that's the secret to beautiful crops. Well, and water. Don't forget to water!"*  
*"In my day, we walked uphill BOTH ways to water our crops! These young folks with their sprinklers..."*

**Services:**
- Sell seeds and farming tools
- Buy crops from players
- Teach farming basics
- Craft farming equipment
- Offer farming wisdom
- Sell fertilizer

**Shop Inventory:**
| Item | Price (IRF) | Stock |
|------|-------------|-------|
| Potato Seeds | 20 | 500/day |
| Carrot Seeds | 30 | 500/day |
| Wheat Seeds | 25 | 500/day |
| Rare Seeds | 500-2,000 | 50/day |
| Fertilizer | 100 | 200/day |
| Watering Can | 800 | Infinite |
| Garden Plot Expansion | 5,000 | Per player |

**Quest Chain: "Green Thumb"**

**Quest 1: First Harvest**
- Objective: Plant and harvest 10 crops
- Reward: 500 IRF, 20 assorted seeds

*"Welcome, dear! Ready to learn about farming? It's quite simple - plant seeds, water them, and watch them grow! Come back when you've harvested your first crops!"*

**Quest 2: Perfect Quality**
- Objective: Grow 5 Perfect quality crops
- Reward: Greenhouse blueprint, fertilizer

*"Good crops are nice, but PERFECT crops? That's where the real magic happens! Use this fertilizer and care for your plants with love!"*

**Quest 3: Master Farmer**
- Objective: Grow one of each crop type
- Reward: Master Farmer title, rare seed bundle

*"You've proven yourself to be a true farmer, dear. I'm so proud! Here, these seeds are from my personal collection. Plant them with care!"*

**Dialogue Progression:**

**First Meeting:**
*"Oh my! A new gardener! How wonderful! Come in, come in! Would you like some fresh cookies? I baked them this morning!"*

**After First Harvest:**
*"Look at you! Your first harvest! *wipes tear* They grow up so fast... the CROPS, I mean! Well, you too, dear!"*

**Mid Game:**
*"Your island farm is beautiful, dear! I visited yesterday - oh, don't look so surprised, we farmers like to check on our students! Keep up the excellent work!"*

**During Rain:**
*"Isn't the rain wonderful? Your crops must be so happy! This is perfect growing weather!"*

**Max Friendship:**
*"You've become like family to me, dear. Here, take this [rare item]. It belonged to my late husband - he was a master farmer too. He'd want you to have it."*

**Grandma Rose's Random Wisdom:**
- *"A crop rushed is a crop wasted. Patience, dear!"*
- *"Talk to your plants! They can't understand you, but YOU'LL feel better!"*
- *"The best fertilizer is a farmer's shadow on the crops - meaning, spend time caring for them!"*

---

### 2.5 Captain Zara Quickblade

**NPCID:** NPC_GUILD_MASTER  
**Role:** Guild Master, Combat Instructor  
**Location:** Adventurer's Guild Hall  
**Availability:** Always available

**Visual Design:**
- Adult female human, strong build
- Short dark hair, scar over left eye
- Wears adventurer's armor (brown leather)
- Sword on hip
- Cape with guild emblem
- Confident posture

**Personality:**
- No-nonsense leader
- Respects strength and skill
- Strategic thinker
- Protective of guild members
- Has seen things™
- Secretly soft for rookies

**Voice/Speaking Style:**
*"You want to join the guild? Prove you're worth my time."*  
*"Good form! You've got potential. Keep training."*  
*"The dungeon isn't a playground. Go in prepared, or don't go in at all."*

**Services:**
- Register players for dungeon access
- Sell combat equipment
- Give combat quests
- Buy monster materials
- Provide dungeon information
- Track monster kills

**Shop Inventory:**
| Item | Price (IRF) | Stock |
|------|-------------|-------|
| Healing Potion | 100 | 500/day |
| Mana Potion | 150 | 500/day |
| Antidote | 50 | 200/day |
| Dungeon Key | 1,000 | 10/day |
| Raid Token | 5,000 | 5/day |

**Quest Chain: "Path of the Warrior"**

**Quest 1: Guild Registration**
- Objective: Defeat 10 slimes in dungeon
- Reward: Dungeon access, 1,000 IRF

*"So you want to be an adventurer? First lesson: prove you can handle yourself. Clear out some slimes, then we'll talk."*

**Quest 2: Monster Hunter**
- Objective: Defeat 5 different monster types
- Reward: 5,000 IRF, Basic combat gear

*"Not bad for a rookie. But slimes are child's play. Show me you can adapt to different enemies."*

**Quest 3: Boss Challenge**
- Objective: Defeat any dungeon boss
- Reward: 10,000 IRF, Raid access

*"A TRUE warrior faces the biggest threats head-on. Go defeat a boss. Solo or with party - your choice. Just GET IT DONE."*

**Quest 4: Nightmare Mode**
- Objective: Complete Nightmare dungeon
- Reward: Master Warrior title, Legendary weapon

*"You've come far. But there's one final test - Nightmare difficulty. Only the elite survive. Are you elite?"*

**Dialogue Progression:**

**First Meeting:**
*"You're the new blood? Hmm. You look... fragile. But appearances can deceive. Want to register as an adventurer?"*

**After First Dungeon:**
*"So you survived. Good. Too many rookies rush in and get themselves killed. At least you used your brain."*

**Mid Game:**
*"The veterans have been talking about you. They're impressed. That's rare. Keep it up."*

**After Boss Kill:**
*"You took down [Boss Name]? Solo? ...I may have underestimated you. Welcome to the elite, adventurer."*

**Max Friendship:**
*"You know... when you first walked in here, I thought you'd wash out in a week. I'm glad I was wrong. You're one of the best. Don't let it go to your head... but between us? I'm proud of you."*

**Combat Tips:**
- *"Always watch their attack patterns. Every monster has a tell."*
- *"Healing potions are cheaper than respawn penalties. Use them."*
- *"Party composition matters. Don't bring three mages to a magic-resistant boss."*

---

### 2.6 Jasper "Jaz" Tinkerton

**NPCID:** NPC_WORKSHOP  
**Role:** Decorator, Builder, Craftsman  
**Location:** Workshop (west side of town)  
**Availability:** 8 AM - 8 PM (game time)

**Visual Design:**
- Young adult male human, lanky build
- Messy brown hair, paint splatter
- Tool belt with hammers and wrenches
- Goggles on head
- Colorful shirt (paint-stained)
- Pencil behind ear
- Always sketching

**Personality:**
- Creative and artistic
- Enthusiastic about design
- Gets distracted easily
- Talks fast when excited
- Perfectionist with decorations
- Friendly rivalry with Blacksmith

**Voice/Speaking Style:**
*"OH OH OH! I just had the BEST idea for your island! Picture this..."*  
*"Beauty is in the details! This vase goes HERE, not THERE! Trust me!"*  
*"Function AND form! Why choose when you can have BOTH?!"*

**Services:**
- Sell decorations and furniture
- Craft decoration items
- Build island structures
- Design consulting
- Storage chest crafting
- Aesthetic advice

**Shop Inventory:**
| Item | Price (IRF) | Stock |
|------|-------------|-------|
| Wooden Chair | 200 | 100/day |
| Table | 300 | 100/day |
| Lamp | 500 | 50/day |
| Storage Chest | 2,000 | 20/day |
| Decorative Flowers | 100 | 200/day |

**Quest Chain: "Island Paradise"**

**Quest 1: First Decoration**
- Objective: Place 10 decorations on island
- Reward: 1,000 IRF, Decoration bundle

*"An empty island is a SAD island! Let's fix that! Start with basics - chairs, tables, flowers. Make it YOURS!"*

**Quest 2: Aesthetic Vision**
- Objective: Reach 1,000 aesthetic score
- Reward: Rare decoration blueprint

*"Good start! But we can do better! Here's a secret - themed decorations give bonus points! Create a cohesive design!"*

**Quest 3: Island Showcase**
- Objective: Get 100 island visits with positive ratings
- Reward: Master Decorator title, Legendary furniture

*"Your island is GORGEOUS! Let's show it off! Open it to visitors and blow their minds with your design skills!"*

**Dialogue Progression:**

**First Meeting:**
*"Welcome to my workshop! You here for decorations? Oh, you NEED decorations! Everyone does! Let me show you what I've got!"*

**After First Purchase:**
*"Great choice! That piece really ties the room together! Come back if you need more!"*

**Mid Game:**
*"I visited your island yesterday and WOW! The way you arranged those statues? *chef's kiss* Magnificent!"*

**High Aesthetic Score:**
*"Your island is trending on the leaderboards! People are visiting just to get inspiration! You're basically famous now!"*

**Max Friendship:**
*"You know what? You're not just a customer - you're an ARTIST! Here, I've been working on this custom piece just for you. It's one-of-a-kind!"*

**Easter Egg Dialogue:**
*"You know Gruff, the Blacksmith? Great guy, terrible decorating sense. He hung a HORSESHOE above his door. A HORSESHOE! I mean, it's traditional, but WHERE'S THE CREATIVITY?!"*

---

### 2.7 Elder Willow Moonwhisper

**NPCID:** NPC_CREATURE_MASTER  
**Role:** Taming Expert, Familiar Specialist  
**Location:** Creature Sanctuary (north forest)  
**Availability:** Always available

**Visual Design:**
- Elderly female elf, graceful
- Long silver hair to waist
- Robes with leaf patterns
- Staff with glowing crystal
- Animals always around her
- Gentle, ethereal glow

**Personality:**
- Calm and wise
- Speaks to animals
- Cryptic advice giver
- Deep connection to nature
- Patient teacher
- Protector of creatures

**Voice/Speaking Style:**
*"The creatures speak... if you know how to listen."*  
*"Strength is not dominance. True power comes from the bond between hearts."*  
*"Every creature has a soul. Treat them with respect, and they will return it tenfold."*

**Services:**
- Teach taming basics
- Sell creature food
- Familiar storage (boarding)
- Breeding services
- Creature healing
- Bond level information

**Shop Inventory:**
| Item | Price (IRF) | Stock |
|------|-------------|-------|
| Generic Pet Food | 50 | 1,000/day |
| Premium Pet Food | 200 | 500/day |
| Taming Treat | 500 | 100/day |
| Familiar Barn Expansion | 10,000 | Per player |
| Revival Crystal | 1,000 | 50/day |

**Quest Chain: "Beast Whisperer"**

**Quest 1: First Friend**
- Objective: Tame any creature
- Reward: 1,000 IRF, Pet food bundle

*"To understand creatures, you must first open your heart. Go into the world, find a creature that calls to you, and form a bond."*

**Quest 2: Diverse Bonds**
- Objective: Tame 5 different creature types
- Reward: Breeding system unlock

*"Each creature is unique, with their own needs and personalities. Learn to understand them all."*

**Quest 3: Legendary Bond**
- Objective: Tame a Legendary creature
- Reward: Beast Master title, Unicorn hint

*"Legendary creatures... they test not just your skill, but your soul. Are you pure of heart? We shall see."*

**Dialogue Progression:**

**First Meeting:**
*"Welcome, young one. The forest whispered of your coming. You seek to bond with creatures, yes? Come, I shall teach you."*

**After First Tame:**
*"Ah, I sense a new bond has formed. Cherish it. The creature has given you its trust - a precious gift."*

**Mid Game:**
*"Your familiar grows strong. But remember - strength without wisdom is merely chaos. Train both body and mind."*

**After Taming Legendary:**
*"I felt it... the moment you bonded with [Creature Name]. Such connections are rare. You have been blessed."*

**Max Friendship:**
*"You have become a true Beast Whisperer. The creatures of this world recognize you as kin. This is my highest honor to bestow."*

**Cryptic Hints:**
- *"The purest creature appears only under the moon's full gaze..."* (Unicorn hint)
- *"Fire and fury rise from volcanic peaks..."* (Phoenix hint)
- *"Storms hide treasures for those brave enough to seek..."* (Storm Hawk hint)

---

## 3. Special NPCs

### 3.1 Cornelius the Traveling Merchant

**NPCID:** NPC_MERCHANT_TRAVELING  
**Role:** Rare Item Vendor  
**Location:** Random (rotates between 5 town locations)  
**Availability:** 2 hours every 6 hours (real time)

**Visual Design:**
- Middle-aged human male, jovial
- Colorful merchant outfit
- Large backpack filled with goods
- Feathered hat
- Gold tooth
- Donkey companion

**Personality:**
- Energetic salesman
- Mysterious origins
- "Special deals just for you!"
- Knows everyone's business
- Comic relief character

**Voice/Speaking Style:**
*"STEP RIGHT UP! I've got items you WON'T BELIEVE!"*  
*"This? Oh, I got it from a place I can't tell you about. Trade secrets, you understand!"*  
*"For YOU? Special discount! Only 50,000 IRF! (That's actually the regular price...)"*

**Services:**
- Sell rare seeds
- Sell limited stock items
- Sell recipes
- Buy rare items at premium
- Event items (seasonal)

**Shop Inventory (Random Stock):**
- Epic Seeds (3-5 types, 10 stock each)
- Legendary Seeds (1-2 types, 5 stock each)
- Rare Decorations (5 types, limited)
- Recipe Scrolls (random)
- Special Materials (event-based)

**Dialogue:**

**Arrival Announcement (Server-Wide):**
*"ATTENTION CITIZENS! Cornelius the Traveling Merchant has arrived in Town Square! Limited time, LIMITED STOCK!"*

**First Encounter:**
*"Ah, a new face! Perfect! You look like someone who appreciates QUALITY! Come, look at my wares!"*

**After Purchase:**
*"Excellent choice! You have good taste! Come back next time I'm in town!"*

**Leaving Announcement:**
*"Well folks, my donkey is getting restless! Time to move on! See you next time!"*

---

### 3.2 Shadow the Information Broker

**NPCID:** NPC_SHADOW  
**Role:** Secrets & Tips Vendor  
**Location:** Dark alley behind Inn  
**Availability:** Night only (8 PM - 6 AM game time)

**Visual Design:**
- Figure in dark cloak (gender ambiguous)
- Hood covers most of face
- Glowing eyes visible
- Mysterious aura
- Appears in shadows

**Personality:**
- Mysterious and cryptic
- Knows everything (somehow)
- Speaks in riddles (sometimes)
- Morally grey
- Prices information

**Voice/Speaking Style:**
*"Information has value. What do you seek to know?"*  
*"For the right price, I can tell you where the rarest fish swims..."*  
*"Secrets are currency. And business is... good."*

**Services:**
- Sell location hints for rare spawns
- Reveal boss weak points
- Forecast rare events
- Track player statistics
- Reveal hidden quests

**Information Prices:**
| Information Type | Price (IRF) |
|------------------|-------------|
| Rare Fish Location | 5,000 |
| Boss Weakness | 10,000 |
| Legendary Spawn Time | 25,000 |
| Hidden Quest Location | 15,000 |
| Player Statistics | Free |

**Dialogue:**

**First Meeting:**
*"You found me. Clever. Most don't notice this alley. You seek knowledge, yes? Everything has a price."*

**Buying Information:**
*"Ah, interested in [item/boss]? Very well. Pay, and I shall reveal what you wish to know."*

**After Purchase:**
*"Use this knowledge wisely. Or don't. The outcome matters not to me."*

**Easter Egg:**
*"How do I know these things? *chuckles* A good information broker never reveals their sources."*

---

### 3.3 Professor Archimedes Cogsworth

**NPCID:** NPC_RESEARCHER  
**Role:** Index & Collection Tracker  
**Location:** Museum/Library  
**Availability:** Always available

**Visual Design:**
- Elderly human male, scholarly
- Lab coat, messy white hair
- Thick glasses
- Notebook always in hand
- Magnifying glass
- Ink stains on fingers

**Personality:**
- Obsessed with cataloging
- Excited by discoveries
- Absentminded professor
- Rewards completionists
- Loves sharing facts

**Voice/Speaking Style:**
*"Fascinating! Simply FASCINATING! A new species for my records!"*  
*"Did you know that the Golden Carp only spawns during full moon? REMARKABLE!"*  
*"Hmm? Oh sorry, I was lost in my research. What can I do for you?"*

**Services:**
- Track collection indexes
- Reward completion milestones
- Provide creature/fish facts
- Offer discovery bonuses
- Display collections

**Completion Rewards:**
- 25% Fish Index: 5,000 IRF + Rare Rod
- 50% Fish Index: 15,000 IRF + Epic Rod
- 100% Fish Index: Master Angler Title + Legendary Rod

**Dialogue:**

**First Meeting:**
*"Welcome to my research facility! I've dedicated my life to cataloging every creature, plant, and mineral in IRIFA! Care to help?"*

**After New Discovery:**
*"Oh my! You've discovered something I haven't cataloged yet! Hold still, I must document this! *frantically scribbles*"*

**Nearing Completion:**
*"You're so close to completing the [Fish/Creature] index! Only [X] more to go! The academic community will be THRILLED!"*

**100% Completion:**
*"YOU DID IT! COMPLETE COLLECTION! This is... this is a momentous occasion! *wipes tear* I'm so proud! Here, take this reward! You've earned it!"*

---

### 3.4 Ghost NPC (Easter Egg)

**NPCID:** NPC_GHOST  
**Role:** Easter Egg/Rare Encounter  
**Location:** Random spawn (graveyards, caves)  
**Availability:** Night, Full Moon (rare spawn)

**Visual Design:**
- Translucent white figure
- Phases in and out
- Glowing blue aura
- Sad expression
- Old-fashioned clothing

**Personality:**
- Lonely spirit
- Seeks help/completion
- Rewards kindness
- Lore connection

**Services:**
- Give ultra-rare items
- Unlock secret quests
- Provide lore

**Dialogue:**
*"You... you can see me? It's been so long since anyone could..."*  
*"I've been waiting... for someone pure of heart... please, help me..."*  
*"Thank you... *fades away peacefully* ...may fortune smile upon you..."*

---

### 3.5 Mysterious Hooded Figure (Late Game)

**NPCID:** NPC_VOID_HERALD  
**Role:** Endgame Content Unlock  
**Location:** Appears after level 80  
**Availability:** Random encounters

**Visual Design:**
- Dark purple/black robes
- Hood hides face
- Void energy particles
- Ominous presence
- Floats slightly

**Personality:**
- Ominous and cryptic
- Challenges player
- Tests worthiness
- Gates endgame content

**Dialogue:**
*"You have grown strong... but are you strong enough for what lies beyond?"*  
*"The Void beckons. Will you answer?"*  
*"Interesting... you do not fear me. Perhaps you ARE ready..."*

---

## 4. Dialogue System

### 4.1 Dialogue Structure

```lua
DialogueData = {
    DialogueId = "MAYOR_WELCOME_001",
    NPCId = "NPC_MAYOR",
    Conditions = {
        FirstMeeting = true,
        Level = {Min = 1, Max = 5}
    },
    Text = "Ah, welcome welcome! Another fine day in our humble town!",
    Choices = {
        {
            Text = "Tell me about this place",
            NextDialogue = "MAYOR_ABOUT_TOWN"
        },
        {
            Text = "What should I do first?",
            NextDialogue = "MAYOR_TUTORIAL_HINT"
        },
        {
            Text = "Goodbye",
            Action = "CloseDialogue"
        }
    }
}
```

### 4.2 Dynamic Dialogue

Dialogue changes based on:
- **Player Level:** Different responses for beginners vs veterans
- **Quest Progress:** NPCs acknowledge completed quests
- **Achievements:** Special dialogue for major milestones
- **Friendship Level:** Closer relationships unlock new dialogue
- **Time/Weather:** Contextual comments
- **Events:** Seasonal/event-specific dialogue
- **Inventory:** React to rare items player carries

---

## 5. Quest Integration

NPCs give three types of quests:

**Main Story Quests:**
- Progress through game narrative
- Unlock major systems
- Cannot skip (but can delay)

**Side Quests:**
- Optional, repeatable
- Build friendship
- Rewards tailored to NPC specialty

**Daily/Weekly Quests:**
- Simple objectives
- Encourage regular engagement
- Rotate randomly

---

## 6. Relationship System

### 6.1 Friendship Levels

Each NPC has friendship (0-10,000 points):

| Level | Points | Title | Benefits |
|-------|--------|-------|----------|
| 0 | 0-999 | Stranger | Normal shop prices |
| 1 | 1,000-1,999 | Acquaintance | -5% shop prices |
| 2 | 2,000-3,999 | Friend | -10% prices, dialogue unlocks |
| 3 | 4,000-6,999 | Good Friend | -15% prices, special quests |
| 4 | 7,000-9,999 | Best Friend | -20% prices, rare items |
| 5 | 10,000+ | Soulmate | -25% prices, unique rewards |

### 6.2 Increasing Friendship

- Talk daily: +10 points
- Complete quests: +50-500 points
- Give gifts: +20-200 points (based on item)
- Buy from shop: +5 points per transaction

### 6.3 Favorite Gifts

| NPC | Loved Gifts | Hated Gifts |
|-----|-------------|-------------|
| Mayor | Gold items, Decorations | Trash, Junk |
| Blacksmith | Rare ores, Gems | Flowers, Food |
| Marina | Legendary fish, Pearls | Meat, Fire items |
| Grandma Rose | Flowers, Perfect crops | Weapons, Monsters |
| Captain Zara | Weapons, Boss items | Flowers, Cute items |
| Jasper | Art supplies, Decorations | Weapons, Dirt |
| Elder Willow | Nature items, Creatures | Metal, Technology |

---

## 7. Technical Implementation

### 7.1 NPC Spawn System

```lua
function NPCService:SpawnNPC(npcId, location)
    local npcData = NPCDatabase[npcId]
    
    -- Check availability conditions
    if not CheckNPCAvailable(npcData) then
        return nil
    end
    
    -- Create NPC model
    local npcModel = ReplicatedStorage.NPCs[npcId]:Clone()
    npcModel.Parent = workspace.NPCs
    npcModel:SetPrimaryPartCFrame(location)
    
    -- Setup interaction
    SetupNPCInteraction(npcModel, npcData)
    
    -- Setup dialogue
    SetupDialogueSystem(npcModel, npcData.DialogueTree)
    
    return npcModel
end
```

### 7.2 Dialogue System

```lua
function DialogueService:StartConversation(player, npcId)
    local npcData = NPCDatabase[npcId]
    local playerData = GetPlayerData(player)
    
    -- Get appropriate dialogue based on conditions
    local dialogue = GetDialogue(npcData, playerData)
    
    -- Show dialogue UI
    FireClient(player, "ShowDialogueUI", {
        NPCName = npcData.Name,
        Text = dialogue.Text,
        Choices = dialogue.Choices,
        Portrait = npcData.Portrait
    })
    
    -- Track interaction
    playerData.NPCFriendship[npcId] = (playerData.NPCFriendship[npcId] or 0) + 10
end
```

---

## Implementation Checklist

### Phase 1: Core NPCs (Month 2-3)
- [ ] Create Mayor NPC (tutorial)
- [ ] Create Blacksmith NPC (crafting)
- [ ] Create Marina NPC (fishing)
- [ ] Create Grandma Rose NPC (farming)
- [ ] Create Captain Zara NPC (combat)
- [ ] Basic dialogue system
- [ ] Shop interfaces

### Phase 2: Expansion (Month 4-5)
- [ ] Create Workshop NPC (decorations)
- [ ] Create Elder Willow NPC (taming)
- [ ] Friendship system
- [ ] Dynamic dialogue
- [ ] Gift system

### Phase 3: Special NPCs (Month 6-7)
- [ ] Traveling Merchant spawn system
- [ ] Shadow information broker
- [ ] Professor Archimedes
- [ ] Rare encounter NPCs

### Phase 4: Polish (Month 8+)
- [ ] Voice acting (optional)
- [ ] Facial animations
- [ ] Gesture animations
- [ ] Seasonal dialogue updates
- [ ] Event-specific NPCs

---

## Related Documentation
- [GDD_Progression.md](GDD_Progression.md) - Quest integration
- [GDD_Content_Story.md](GDD_Content_Story.md) - Main narrative
- [GDD_Systems_Trading.md](GDD_Systems_Trading.md) - Shop systems

---

**Document End - NPC Content**  
*Every character tells a story*
