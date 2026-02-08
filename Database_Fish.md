# Item Database
## Fish Species Catalog

---

### Document Information
**Database Type:** Fish Species  
**Version:** 1.0  
**Last Updated:** February 8, 2026  
**Maintainer:** Content Team

---

## Usage Instructions

**For Designers:**
- Add new fish entries using the template below
- Ensure all required fields are filled
- Balance catch rates with rarity tiers
- Coordinate with economy team for pricing

**For Developers:**
- Parse this file to generate in-game data
- Use FishID as unique identifier
- Validate all numerical values
- Check location references exist

---

## Fish Entry Template

```
FishID: FISH_XXX
Name: Fish Display Name
Rarity: Common/Rare/Epic/Legendary/Mythic/Special
Location: Ocean/River Zone X
Catch Rate: X%
Time: Any/Day/Night
Weather: Any/Clear/Rain/Storm
Season: All/Event Name
Size Range: Min-Max kg
Sell Value (NPC): X IRF
Stamina (Mini-game): X HP
Index Number: #XXX
Description: "Flavor text describing the fish."
Uses: Familiar food, Trading, etc.
Special Notes: Any unique properties
```

---

## Ocean Fish

### Common Tier (Grey)

#### FISH_001: Cod
- **FishID:** FISH_001
- **Name:** Cod
- **Rarity:** Common
- **Location:** Ocean Zone A (Starter Beach)
- **Catch Rate:** 40%
- **Time:** Any
- **Weather:** Any
- **Season:** All
- **Size Range:** 0.5-2.0 kg
- **Sell Value:** 10 IRF
- **Stamina:** 30 HP
- **Index Number:** #001
- **Description:** "A common saltwater fish found near beaches. Popular among beginner anglers."
- **Uses:** Common familiar food, basic trading

#### FISH_002: Mackerel
- **FishID:** FISH_002
- **Name:** Mackerel
- **Rarity:** Common
- **Location:** Ocean Zone A, B
- **Catch Rate:** 35%
- **Time:** Any
- **Weather:** Any
- **Season:** All
- **Size Range:** 0.3-1.0 kg
- **Sell Value:** 8 IRF
- **Stamina:** 25 HP
- **Index Number:** #002
- **Description:** "A small, silvery fish known for its speed. Often caught in schools."
- **Uses:** Common familiar food, bulk trading

#### FISH_003: Sardine
- **FishID:** FISH_003
- **Name:** Sardine
- **Rarity:** Common
- **Location:** Ocean Zone A
- **Catch Rate:** 45%
- **Time:** Any
- **Weather:** Any
- **Season:** All
- **Size Range:** 0.1-0.5 kg
- **Sell Value:** 5 IRF
- **Stamina:** 20 HP
- **Index Number:** #003
- **Description:** "Tiny fish that travel in massive schools. Easy to catch but low value."
- **Uses:** Cheapest familiar food

#### FISH_004: Anchovy
- **FishID:** FISH_004
- **Name:** Anchovy
- **Rarity:** Common
- **Location:** Ocean Zone B (Rocky Coast)
- **Catch Rate:** 40%
- **Time:** Any
- **Weather:** Any
- **Season:** All
- **Size Range:** 0.1-0.4 kg
- **Sell Value:** 5 IRF
- **Stamina:** 20 HP
- **Index Number:** #004
- **Description:** "Small saltwater fish with a distinctive flavor. Often preserved in salt."
- **Uses:** Cooking ingredient (future), familiar food

---

### Rare Tier (Blue)

#### FISH_005: Sea Bass
- **FishID:** FISH_005
- **Name:** Sea Bass
- **Rarity:** Rare
- **Location:** Ocean Zone A, B
- **Catch Rate:** 20%
- **Time:** Day
- **Weather:** Clear
- **Season:** All
- **Size Range:** 2.0-5.0 kg
- **Sell Value:** 50 IRF
- **Stamina:** 60 HP
- **Index Number:** #005
- **Description:** "A prized catch among fishermen. Its firm white flesh is highly valued."
- **Uses:** Rare familiar food, profitable trading

#### FISH_006: Tuna
- **FishID:** FISH_006
- **Name:** Tuna
- **Rarity:** Rare
- **Location:** Ocean Zone B, C
- **Catch Rate:** 15%
- **Time:** Any
- **Weather:** Any
- **Season:** All
- **Size Range:** 5.0-15.0 kg
- **Sell Value:** 80 IRF
- **Stamina:** 80 HP
- **Index Number:** #006
- **Description:** "A powerful ocean fish known for its speed and strength. Puts up a good fight!"
- **Uses:** High-quality familiar food, trading

#### FISH_007: Snapper
- **FishID:** FISH_007
- **Name:** Red Snapper
- **Rarity:** Rare
- **Location:** Ocean Zone B
- **Catch Rate:** 18%
- **Time:** Day
- **Weather:** Clear/Rain
- **Season:** All
- **Size Range:** 1.0-4.0 kg
- **Sell Value:** 60 IRF
- **Stamina:** 70 HP
- **Index Number:** #007
- **Description:** "Recognizable by its distinctive red color. A delicacy in many cultures."
- **Uses:** Rare familiar food, trading

#### FISH_008: Grouper
- **FishID:** FISH_008
- **Name:** Grouper
- **Rarity:** Rare
- **Location:** Ocean Zone C (Deep Sea)
- **Catch Rate:** 12%
- **Time:** Any
- **Weather:** Any
- **Season:** All
- **Size Range:** 3.0-10.0 kg
- **Sell Value:** 90 IRF
- **Stamina:** 85 HP
- **Index Number:** #008
- **Description:** "A bottom-dwelling fish found in deeper waters. Slow but powerful."
- **Uses:** Quality familiar food, trading

---

### Epic Tier (Purple)

#### FISH_009: Swordfish
- **FishID:** FISH_009
- **Name:** Swordfish
- **Rarity:** Epic
- **Location:** Ocean Zone B, C
- **Catch Rate:** 8%
- **Time:** Day
- **Weather:** Clear
- **Season:** All
- **Size Range:** 20.0-50.0 kg
- **Sell Value:** 300 IRF
- **Stamina:** 150 HP
- **Index Number:** #009
- **Description:** "Named for its long, pointed bill. An apex predator of the ocean."
- **Uses:** Epic familiar food, high-value trading, crafting material

#### FISH_010: Marlin
- **FishID:** FISH_010
- **Name:** Marlin
- **Rarity:** Epic
- **Location:** Ocean Zone C
- **Catch Rate:** 6%
- **Time:** Day
- **Weather:** Clear
- **Season:** All
- **Size Range:** 30.0-80.0 kg
- **Sell Value:** 400 IRF
- **Stamina:** 180 HP
- **Index Number:** #010
- **Description:** "The ultimate trophy fish. Known for its acrobatic leaps when hooked."
- **Uses:** Epic familiar food, prestigious trading

#### FISH_011: Mahi-Mahi
- **FishID:** FISH_011
- **Name:** Mahi-Mahi
- **Rarity:** Epic
- **Location:** Ocean Zone C, D
- **Catch Rate:** 7%
- **Time:** Any
- **Weather:** Any
- **Season:** All
- **Size Range:** 5.0-15.0 kg
- **Sell Value:** 250 IRF
- **Stamina:** 120 HP
- **Index Number:** #011
- **Description:** "Also known as dolphinfish. Vibrant colors fade quickly after catching."
- **Uses:** Epic familiar food, trading

#### FISH_012: Reef Shark
- **FishID:** FISH_012
- **Name:** Reef Shark
- **Rarity:** Epic
- **Location:** Ocean Zone D (Tropical Reef)
- **Catch Rate:** 5%
- **Time:** Any
- **Weather:** Any
- **Season:** All
- **Size Range:** 15.0-40.0 kg
- **Sell Value:** 450 IRF
- **Stamina:** 200 HP
- **Index Number:** #012
- **Description:** "A small shark species. Requires skill and courage to land!"
- **Uses:** Epic familiar food, crafting (shark teeth), trading

---

### Legendary Tier (Gold)

#### FISH_013: Blue Marlin
- **FishID:** FISH_013
- **Name:** Blue Marlin
- **Rarity:** Legendary
- **Location:** Ocean Zone C (Deep Sea Port)
- **Catch Rate:** 3%
- **Time:** Day
- **Weather:** Clear
- **Season:** All
- **Size Range:** 100.0-200.0 kg
- **Sell Value:** 1,500 IRF
- **Stamina:** 300 HP
- **Index Number:** #013
- **Description:** "The king of marlins. A legendary catch that proves your fishing mastery."
- **Uses:** Legendary familiar food, trophy display, high-end trading

#### FISH_014: Giant Tuna
- **FishID:** FISH_014
- **Name:** Giant Bluefin Tuna
- **Rarity:** Legendary
- **Location:** Ocean Zone C
- **Catch Rate:** 2.5%
- **Time:** Any
- **Weather:** Any
- **Season:** All
- **Size Range:** 150.0-300.0 kg
- **Sell Value:** 2,000 IRF
- **Stamina:** 350 HP
- **Index Number:** #014
- **Description:** "An enormous tuna of legendary proportions. Worth a fortune at market."
- **Uses:** Legendary familiar food, trading, prestige

#### FISH_015: Manta Ray
- **FishID:** FISH_015
- **Name:** Oceanic Manta Ray
- **Rarity:** Legendary
- **Location:** Ocean Zone D (Tropical Reef)
- **Catch Rate:** 2%
- **Time:** Any
- **Weather:** Clear
- **Season:** All
- **Size Range:** 200.0-500.0 kg
- **Sell Value:** 2,500 IRF
- **Stamina:** 400 HP
- **Index Number:** #015
- **Description:** "Graceful giant of the sea. Catching one is considered incredibly lucky."
- **Uses:** Legendary familiar food, rare crafting material

---

### Mythic Tier (Red)

#### FISH_016: Celestial Jellyfish
- **FishID:** FISH_016
- **Name:** Celestial Jellyfish
- **Rarity:** Mythic
- **Location:** Ocean Zone D (Tropical Reef)
- **Catch Rate:** 0.5%
- **Time:** Night
- **Weather:** Clear
- **Season:** All
- **Size Range:** N/A (ethereal)
- **Sell Value:** 10,000 IRF
- **Stamina:** 500 HP
- **Index Number:** #016
- **Description:** "A mystical creature that glows with otherworldly light. Some say it's not entirely of this world."
- **Uses:** Mythic familiar food, rare alchemy ingredient, prestigious trading
- **Special Notes:** Glows in dark, particle effects, very difficult mini-game

#### FISH_017: Leviathan Eel
- **FishID:** FISH_017
- **Name:** Leviathan Eel
- **Rarity:** Mythic
- **Location:** Ocean Zone C (Deep Sea)
- **Catch Rate:** 0.3%
- **Time:** Any
- **Weather:** Storm only
- **Season:** All
- **Size Range:** ??? (unmeasurable)
- **Sell Value:** 15,000 IRF
- **Stamina:** 600 HP
- **Index Number:** #017
- **Description:** "An ancient sea serpent of legend. Appears only during the fiercest storms."
- **Uses:** Mythic familiar food, legendary crafting material, ultimate trophy
- **Special Notes:** Storm-exclusive, extremely difficult, requires high-end equipment

---

## River Fish

### Common Tier (Grey)

#### FISH_018: Trout
- **FishID:** FISH_018
- **Name:** Rainbow Trout
- **Rarity:** Common
- **Location:** River Zone A (Town River)
- **Catch Rate:** 40%
- **Time:** Any
- **Weather:** Any
- **Season:** All
- **Size Range:** 0.5-2.0 kg
- **Sell Value:** 12 IRF
- **Stamina:** 35 HP
- **Index Number:** #018
- **Description:** "A beautiful freshwater fish with rainbow-colored sides. Popular with anglers."
- **Uses:** Common familiar food, trading

#### FISH_019: Carp
- **FishID:** FISH_019
- **Name:** Common Carp
- **Rarity:** Common
- **Location:** River Zone A, B
- **Catch Rate:** 35%
- **Time:** Any
- **Weather:** Any
- **Season:** All
- **Size Range:** 1.0-5.0 kg
- **Sell Value:** 15 IRF
- **Stamina:** 50 HP
- **Index Number:** #019
- **Description:** "A hardy fish found in calm waters. Known for its distinctive whiskers."
- **Uses:** Common familiar food, trading

#### FISH_020: Minnow
- **FishID:** FISH_020
- **Name:** Minnow
- **Rarity:** Common
- **Location:** River Zone A
- **Catch Rate:** 50%
- **Time:** Any
- **Weather:** Any
- **Season:** All
- **Size Range:** 0.1-0.3 kg
- **Sell Value:** 3 IRF
- **Stamina:** 15 HP
- **Index Number:** #020
- **Description:** "Tiny river fish. Often used as bait, but makes decent familiar food in bulk."
- **Uses:** Basic familiar food, bulk trading

---

### Rare Tier (Blue)

#### FISH_021: Salmon
- **FishID:** FISH_021
- **Name:** Salmon
- **Rarity:** Rare
- **Location:** River Zone A, B
- **Catch Rate:** 18%
- **Time:** Day
- **Weather:** Any
- **Season:** All (increased during Autumn event)
- **Size Range:** 3.0-8.0 kg
- **Sell Value:** 70 IRF
- **Stamina:** 90 HP
- **Index Number:** #021
- **Description:** "Known for swimming upstream to spawn. Highly nutritious and flavorful."
- **Uses:** Rare familiar food, trading, event material (Salmon Run)

#### FISH_022: Pike
- **FishID:** FISH_022
- **Name:** Northern Pike
- **Rarity:** Rare
- **Location:** River Zone B (Forest Stream)
- **Catch Rate:** 15%
- **Time:** Any
- **Weather:** Any
- **Season:** All
- **Size Range:** 5.0-15.0 kg
- **Sell Value:** 90 IRF
- **Stamina:** 100 HP
- **Index Number:** #022
- **Description:** "An aggressive predator with sharp teeth. Exciting fight when hooked!"
- **Uses:** Rare familiar food, trading

#### FISH_023: Bass
- **FishID:** FISH_023
- **Name:** Largemouth Bass
- **Rarity:** Rare
- **Location:** River Zone A, B
- **Catch Rate:** 20%
- **Time:** Any
- **Weather:** Any
- **Season:** All
- **Size Range:** 1.0-4.0 kg
- **Sell Value:** 55 IRF
- **Stamina:** 70 HP
- **Index Number:** #023
- **Description:** "A popular sport fish known for its fighting spirit."
- **Uses:** Rare familiar food, trading

---

### Epic Tier (Purple)

#### FISH_024: King Salmon
- **FishID:** FISH_024
- **Name:** King Salmon
- **Rarity:** Epic
- **Location:** River Zone B, C
- **Catch Rate:** 7%
- **Time:** Day
- **Weather:** Rain preferred
- **Season:** All (peak during Autumn)
- **Size Range:** 10.0-25.0 kg
- **Sell Value:** 350 IRF
- **Stamina:** 150 HP
- **Index Number:** #024
- **Description:** "The largest salmon species. A true trophy catch for river anglers."
- **Uses:** Epic familiar food, event trading (high demand in Autumn)

#### FISH_025: Sturgeon
- **FishID:** FISH_025
- **Name:** Sturgeon
- **Rarity:** Epic
- **Location:** River Zone B, C
- **Catch Rate:** 5%
- **Time:** Any
- **Weather:** Any
- **Season:** All
- **Size Range:** 20.0-80.0 kg
- **Sell Value:** 500 IRF
- **Stamina:** 200 HP
- **Index Number:** #025
- **Description:** "An ancient fish species that has remained unchanged for millions of years."
- **Uses:** Epic familiar food, caviar production (future), high-value trading

#### FISH_026: Golden Trout
- **FishID:** FISH_026
- **Name:** Golden Trout
- **Rarity:** Epic
- **Location:** River Zone C (Mountain Rapids)
- **Catch Rate:** 6%
- **Time:** Day
- **Weather:** Clear
- **Season:** All
- **Size Range:** 2.0-6.0 kg
- **Sell Value:** 400 IRF
- **Stamina:** 120 HP
- **Index Number:** #026
- **Description:** "A stunning variant with brilliant golden coloration. Found only in pristine mountain streams."
- **Uses:** Epic familiar food, decorative aquarium fish (future)

---

### Legendary Tier (Gold)

#### FISH_027: Ancient Sturgeon
- **FishID:** FISH_027
- **Name:** Ancient Sturgeon
- **Rarity:** Legendary
- **Location:** River Zone C (Mountain Rapids)
- **Catch Rate:** 2%
- **Time:** Any
- **Weather:** Any
- **Season:** All
- **Size Range:** 100.0-250.0 kg
- **Sell Value:** 2,500 IRF
- **Stamina:** 400 HP
- **Index Number:** #027
- **Description:** "A prehistoric giant that has lived for over a century. Extremely rare."
- **Uses:** Legendary familiar food, premium caviar, prestigious trading

#### FISH_028: Moonlight Koi
- **FishID:** FISH_028
- **Name:** Moonlight Koi
- **Rarity:** Legendary
- **Location:** River Zone D (Mysterious Lake)
- **Catch Rate:** 2.5%
- **Time:** Night (Full Moon increases rate)
- **Weather:** Clear
- **Season:** All
- **Size Range:** 5.0-12.0 kg
- **Sell Value:** 3,000 IRF
- **Stamina:** 350 HP
- **Index Number:** #028
- **Description:** "A mystical koi that glows under moonlight. Brings good fortune to its catcher."
- **Uses:** Legendary familiar food, luck charm (buff item), trading
- **Special Notes:** Glows at night, increased spawn during full moon

---

### Mythic Tier (Red)

#### FISH_029: Phoenix Koi
- **FishID:** FISH_029
- **Name:** Phoenix Koi
- **Rarity:** Mythic
- **Location:** River Zone D (Mysterious Lake)
- **Catch Rate:** 0.8%
- **Time:** Night
- **Weather:** Clear
- **Season:** All
- **Size Range:** 15.0-30.0 kg
- **Sell Value:** 12,000 IRF
- **Stamina:** 550 HP
- **Index Number:** #029
- **Description:** "A legendary koi said to transform into a phoenix. Its scales shimmer with fire."
- **Uses:** Mythic familiar food, ultimate luck charm, legendary crafting
- **Special Notes:** Fire particle effects, extremely difficult mini-game, luck-dependent

#### FISH_030: Dragon Carp
- **FishID:** FISH_030
- **Name:** Dragon Carp
- **Rarity:** Mythic
- **Location:** River Zone D (Mysterious Lake)
- **Catch Rate:** 0.5%
- **Time:** Any
- **Weather:** Rain/Thunderstorm
- **Season:** All
- **Size Range:** 50.0-100.0 kg
- **Sell Value:** 18,000 IRF
- **Stamina:** 650 HP
- **Index Number:** #030
- **Description:** "According to legend, carp that leap over waterfalls transform into dragons. This one is halfway there."
- **Uses:** Mythic familiar food, dragon scale crafting, ultimate trophy
- **Special Notes:** Storm-enhanced spawn, draconic visual effects, hardest freshwater catch

---

## Special/Event Fish

### Winter Event

#### FISH_EVENT_001: Ice Salmon
- **FishID:** FISH_EVENT_001
- **Name:** Frozen Salmon
- **Rarity:** Special (Event)
- **Location:** Winter Ice Lake (Event Zone)
- **Catch Rate:** 15%
- **Time:** Any
- **Weather:** Snow
- **Season:** Winter Event Only
- **Size Range:** 4.0-10.0 kg
- **Sell Value:** 500 IRF
- **Stamina:** 100 HP
- **Index Number:** #E01
- **Description:** "A salmon that has adapted to frozen waters. Its flesh remains unfrozen even in extreme cold."
- **Uses:** Event familiar food, winter decorations, collectible

#### FISH_EVENT_002: Frost Wyrm
- **FishID:** FISH_EVENT_002
- **Name:** Frost Wyrm
- **Rarity:** Special (Event)
- **Location:** Winter Ice Lake
- **Catch Rate:** 2%
- **Time:** Night
- **Weather:** Blizzard
- **Season:** Winter Event Only
- **Size Range:** 80.0-150.0 kg
- **Sell Value:** 20,000 IRF
- **Stamina:** 700 HP
- **Index Number:** #E02
- **Description:** "A mythical ice dragon in eel form. Said to guard ancient treasures beneath the ice."
- **Uses:** Exclusive event familiar, ice crafting material, prestige trophy
- **Special Notes:** Limited-time exclusive, extremely rare, special quest reward

---

## Database Management Notes

### Adding New Fish:
1. Create unique FishID (follow naming convention)
2. Balance catch rate with rarity tier
3. Set appropriate stamina (difficulty)
4. Price based on rarity and time investment
5. Assign unique index number
6. Write compelling description
7. Test in-game before deployment

### Balancing Guidelines:
- Common: 30-50% catch rate
- Rare: 10-20% catch rate
- Epic: 5-10% catch rate
- Legendary: 1-3% catch rate
- Mythic: <1% catch rate
- Special: Event-specific rates

### Version History:
- v1.0 (Feb 8, 2026): Initial database with 30+ fish species
- v1.1 (Planned): Summer event fish additions
- v1.2 (Planned): Mythic tier expansions

---

**Fish Database - End of Document**

*Total Fish Species: 32 (30 permanent + 2 event)*  
*Target Total (Future): 100+ species*
