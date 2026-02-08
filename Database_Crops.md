# Item Database
## Crop & Seed Catalog

---

### Document Information
**Database Type:** Crops & Seeds  
**Version:** 1.0  
**Last Updated:** February 8, 2026  
**Maintainer:** Content Team

---

## Usage Instructions

**For Designers:**
- Add new crop entries using the template provided
- Balance growth times with profit potential
- Ensure rarity tiers align with acquisition difficulty
- Coordinate with economy team for pricing

**For Developers:**
- Parse this file to generate seed/crop data
- Use CropID as unique identifier
- Implement growth timers based on RealTime values
- Validate all numerical ranges

---

## Crop Entry Template

```
CropID: CROP_XXX
Name: Crop Display Name
Rarity: Common/Rare/Epic/Legendary/Mythic/Special
Category: Vegetable/Fruit/Grain/Herb/Flower
Growth Time: X hours (Real Time)
Growth Stages: X stages
Watering Needs: X times during growth
Seasons: All/Spring/Summer/Fall/Winter
Seed Price: X IRF / Y Robux
Base Harvest Value: X IRF (Normal quality)
Quality Multipliers: Poor 0.5×, Normal 1.0×, Good 1.5×, Great 2.0×, Perfect 3.0×
Harvest Quantity: Min-Max items per plant
Seeds per Harvest: X% chance for X-Y seeds
Acquisition: List of methods (Shop/Event/Fishing/etc.)
Fertilizer Compatibility: Basic/Quality/Premium/Perfect
Description: "Flavor text about the crop."
Special Effects: Any unique properties
Familiar Preference: Which familiars prefer this crop
Uses: Food/Trading/Crafting/Decoration
```

---

## Vegetables

### Common Tier (Grey)

#### CROP_001: Potato
- **CropID:** CROP_001
- **Name:** Potato
- **Rarity:** Common
- **Category:** Vegetable
- **Growth Time:** 2 hours (Real Time)
- **Growth Stages:** 4 stages (Seedling → Small Plant → Flowering → Ready)
- **Watering Needs:** 2 times (after stage 1 and 2)
- **Seasons:** All
- **Seed Price:** 5 IRF (Shop)
- **Base Harvest Value:** 15 IRF (Normal quality)
- **Quality Multipliers:** Poor 7.5 IRF, Good 22.5 IRF, Great 30 IRF, Perfect 45 IRF
- **Harvest Quantity:** 1-3 potatoes
- **Seeds per Harvest:** 25% chance for 1-2 seeds
- **Acquisition:** Farming Shop, Tutorial Quest Reward
- **Fertilizer Compatibility:** All types
- **Description:** "A versatile root vegetable. Easy to grow, perfect for beginners."
- **Familiar Preference:** Herbivore familiars (Low preference)
- **Uses:** Common familiar food, bulk trading, cooking (future)

#### CROP_002: Carrot
- **CropID:** CROP_002
- **Name:** Carrot
- **Rarity:** Common
- **Category:** Vegetable
- **Growth Time:** 2.5 hours
- **Growth Stages:** 4 stages
- **Watering Needs:** 2 times
- **Seasons:** All
- **Seed Price:** 6 IRF
- **Base Harvest Value:** 18 IRF
- **Quality Multipliers:** Poor 9 IRF, Good 27 IRF, Great 36 IRF, Perfect 54 IRF
- **Harvest Quantity:** 1-2 carrots
- **Seeds per Harvest:** 20% chance for 1 seed
- **Acquisition:** Farming Shop, Fishing (rare trash drop)
- **Fertilizer Compatibility:** All types
- **Description:** "Crunchy orange root vegetable. Rich in nutrients."
- **Familiar Preference:** Rabbits (High), Herbivores (Medium)
- **Uses:** Familiar food, trading, rabbit taming bait

#### CROP_003: Lettuce
- **CropID:** CROP_003
- **Name:** Lettuce
- **Rarity:** Common
- **Category:** Vegetable
- **Growth Time:** 1.5 hours
- **Growth Stages:** 3 stages
- **Watering Needs:** 2 times
- **Seasons:** All
- **Seed Price:** 4 IRF
- **Base Harvest Value:** 12 IRF
- **Quality Multipliers:** Poor 6 IRF, Good 18 IRF, Great 24 IRF, Perfect 36 IRF
- **Harvest Quantity:** 2-4 leaves
- **Seeds per Harvest:** 30% chance for 1-3 seeds
- **Acquisition:** Farming Shop
- **Fertilizer Compatibility:** All types
- **Description:** "Quick-growing leafy green. Great for fast turnover farming."
- **Familiar Preference:** Herbivores (Medium)
- **Uses:** Familiar food, high-volume trading

#### CROP_004: Tomato
- **CropID:** CROP_004
- **Name:** Tomato
- **Rarity:** Common
- **Category:** Vegetable (botanically a fruit)
- **Growth Time:** 3 hours
- **Growth Stages:** 5 stages (Seedling → Vine → Flowering → Green Fruit → Ripe)
- **Watering Needs:** 3 times
- **Seasons:** All (bonus growth in Summer)
- **Seed Price:** 8 IRF
- **Base Harvest Value:** 22 IRF
- **Quality Multipliers:** Poor 11 IRF, Good 33 IRF, Great 44 IRF, Perfect 66 IRF
- **Harvest Quantity:** 2-5 tomatoes
- **Seeds per Harvest:** 35% chance for 2-4 seeds
- **Acquisition:** Farming Shop, Summer Event bonus
- **Fertilizer Compatibility:** All types
- **Description:** "Juicy red fruit-vegetable. Produces multiple harvests per plant."
- **Familiar Preference:** Omnivores (Medium)
- **Uses:** Familiar food, cooking ingredient, trading

---

### Rare Tier (Blue)

#### CROP_005: Corn
- **CropID:** CROP_005
- **Name:** Corn
- **Rarity:** Rare
- **Category:** Grain
- **Growth Time:** 5 hours
- **Growth Stages:** 5 stages
- **Watering Needs:** 3 times
- **Seasons:** All (best in Summer)
- **Seed Price:** 25 IRF
- **Base Harvest Value:** 80 IRF
- **Quality Multipliers:** Poor 40 IRF, Good 120 IRF, Great 160 IRF, Perfect 240 IRF
- **Harvest Quantity:** 1-3 ears
- **Seeds per Harvest:** 40% chance for 3-6 seeds
- **Acquisition:** Farming Shop (Level 5+), Daily Quest rewards
- **Fertilizer Compatibility:** All types
- **Description:** "Golden grain that grows tall. More valuable than common crops."
- **Familiar Preference:** Birds (High), Herbivores (Medium)
- **Uses:** Rare familiar food, trading, milling (future)

#### CROP_006: Pumpkin
- **CropID:** CROP_006
- **Name:** Pumpkin
- **Rarity:** Rare
- **Category:** Vegetable
- **Growth Time:** 6 hours
- **Growth Stages:** 5 stages
- **Watering Needs:** 4 times
- **Seasons:** All (Halloween Event bonus)
- **Seed Price:** 30 IRF
- **Base Harvest Value:** 100 IRF
- **Quality Multipliers:** Poor 50 IRF, Good 150 IRF, Great 200 IRF, Perfect 300 IRF
- **Harvest Quantity:** 1 large pumpkin
- **Seeds per Harvest:** 50% chance for 5-10 seeds
- **Acquisition:** Farming Shop (Level 8+), Halloween Event
- **Fertilizer Compatibility:** All types (Premium+ for Giant Pumpkins)
- **Description:** "Large orange gourd. Essential for autumn celebrations."
- **Special Effects:** Can grow to Giant size with Perfect Fertilizer (3× value)
- **Familiar Preference:** Medium preference across types
- **Uses:** Trading, Halloween event currency, decoration

#### CROP_007: Watermelon
- **CropID:** CROP_007
- **Name:** Watermelon
- **Rarity:** Rare
- **Category:** Fruit
- **Growth Time:** 7 hours
- **Growth Stages:** 6 stages
- **Watering Needs:** 5 times (high water needs)
- **Seasons:** All (Summer bonus)
- **Seed Price:** 35 IRF
- **Base Harvest Value:** 120 IRF
- **Quality Multipliers:** Poor 60 IRF, Good 180 IRF, Great 240 IRF, Perfect 360 IRF
- **Harvest Quantity:** 1 large melon
- **Seeds per Harvest:** 60% chance for 8-12 seeds
- **Acquisition:** Farming Shop (Level 10+), Summer Event
- **Fertilizer Compatibility:** All types
- **Description:** "Refreshing summer fruit. Requires lots of water but highly profitable."
- **Familiar Preference:** All types (High in summer heat)
- **Uses:** Rare familiar food, summer trading, hydration buff (future)

#### CROP_008: Strawberry
- **CropID:** CROP_008
- **Name:** Strawberry
- **Rarity:** Rare
- **Category:** Fruit
- **Growth Time:** 4 hours
- **Growth Stages:** 4 stages
- **Watering Needs:** 3 times
- **Seasons:** All (Spring bonus)
- **Seed Price:** 20 IRF
- **Base Harvest Value:** 70 IRF
- **Quality Multipliers:** Poor 35 IRF, Good 105 IRF, Great 140 IRF, Perfect 210 IRF
- **Harvest Quantity:** 3-6 berries
- **Seeds per Harvest:** 30% chance for 2-4 seeds
- **Acquisition:** Fishing (rare), Farming Shop (Level 6+)
- **Fertilizer Compatibility:** All types
- **Description:** "Sweet red berries. Popular among farmers for repeat harvesting."
- **Familiar Preference:** Small creatures (High)
- **Uses:** Rare familiar food, trading, dessert crafting (future)

---

### Epic Tier (Purple)

#### CROP_009: Mango
- **CropID:** CROP_009
- **Name:** Mango
- **Rarity:** Epic
- **Category:** Fruit (Tree Crop)
- **Growth Time:** 12 hours
- **Growth Stages:** 6 stages (Sapling → Young Tree → Mature Tree → Flowering → Fruiting → Ripe)
- **Watering Needs:** 6 times
- **Seasons:** All (Tropical, slight bonus in Summer)
- **Seed Price:** 100 IRF or 50 Robux
- **Base Harvest Value:** 400 IRF
- **Quality Multipliers:** Poor 200 IRF, Good 600 IRF, Great 800 IRF, Perfect 1,200 IRF
- **Harvest Quantity:** 2-5 mangoes
- **Seeds per Harvest:** 25% chance for 1 seed (pit)
- **Acquisition:** Tropical Island Expansion Shop, Epic Geode (rare)
- **Fertilizer Compatibility:** Quality+ (requires better fertilizer)
- **Description:** "Tropical fruit tree. Long growth time but excellent returns."
- **Familiar Preference:** Exotic familiars (High)
- **Uses:** Epic familiar food, high-value trading, tropical recipes

#### CROP_010: Dragon Fruit
- **CropID:** CROP_010
- **Name:** Dragon Fruit
- **Rarity:** Epic
- **Category:** Fruit (Cactus)
- **Growth Time:** 10 hours
- **Growth Stages:** 5 stages
- **Watering Needs:** 3 times (drought-resistant)
- **Seasons:** All
- **Seed Price:** 150 IRF or 75 Robux
- **Base Harvest Value:** 500 IRF
- **Quality Multipliers:** Poor 250 IRF, Good 750 IRF, Great 1,000 IRF, Perfect 1,500 IRF
- **Harvest Quantity:** 1-3 fruits
- **Seeds per Harvest:** 20% chance for 1-2 seeds
- **Acquisition:** Desert Expansion Shop, Legendary Fish (very rare drop)
- **Fertilizer Compatibility:** Quality+ only
- **Description:** "Exotic cactus fruit with vibrant pink skin and white flesh. Rare and valuable."
- **Special Effects:** Low water requirement makes it ideal for busy players
- **Familiar Preference:** Dragon-type familiars (Very High)
- **Uses:** Epic familiar food, dragon taming food, prestige trading

#### CROP_011: Golden Wheat
- **CropID:** CROP_011
- **Name:** Golden Wheat
- **Rarity:** Epic
- **Category:** Grain
- **Growth Time:** 8 hours
- **Growth Stages:** 5 stages
- **Watering Needs:** 4 times
- **Seasons:** All
- **Seed Price:** 80 IRF
- **Base Harvest Value:** 350 IRF
- **Quality Multipliers:** Poor 175 IRF, Good 525 IRF, Great 700 IRF, Perfect 1,050 IRF
- **Harvest Quantity:** 5-10 stalks
- **Seeds per Harvest:** 60% chance for 10-20 seeds
- **Acquisition:** Daily Quest rewards (rare), Achievement reward
- **Fertilizer Compatibility:** All types
- **Description:** "Magical wheat that shimmers like gold. Used in advanced crafting."
- **Familiar Preference:** Holy/Light familiars (High)
- **Uses:** Epic familiar food, bread crafting, alchemy ingredient

#### CROP_012: Moonberry
- **CropID:** CROP_012
- **Name:** Moonberry
- **Rarity:** Epic
- **Category:** Fruit (Berry Bush)
- **Growth Time:** 9 hours (grows faster at night)
- **Growth Stages:** 4 stages
- **Watering Needs:** 3 times
- **Seasons:** All (bonus during full moon)
- **Seed Price:** 120 IRF or 60 Robux
- **Base Harvest Value:** 450 IRF
- **Quality Multipliers:** Poor 225 IRF, Good 675 IRF, Great 900 IRF, Perfect 1,350 IRF
- **Harvest Quantity:** 4-8 berries
- **Seeds per Harvest:** 15% chance for 1-3 seeds
- **Acquisition:** Mysterious Lake fishing (rare), Night Market
- **Fertilizer Compatibility:** Quality+ only
- **Description:** "Luminescent berries that glow softly in darkness. Said to have mystical properties."
- **Special Effects:** Glows at night, faster growth during nighttime, full moon bonus
- **Familiar Preference:** Nocturnal familiars (Very High)
- **Uses:** Epic familiar food, night vision potion (future), mystical crafting

---

### Legendary Tier (Gold)

#### CROP_013: Phoenix Pepper
- **CropID:** CROP_013
- **Name:** Phoenix Pepper
- **Rarity:** Legendary
- **Category:** Vegetable (Spice)
- **Growth Time:** 18 hours
- **Growth Stages:** 7 stages
- **Watering Needs:** 7 times
- **Seasons:** All (requires heat, Summer bonus)
- **Seed Price:** 500 IRF or 200 Robux
- **Base Harvest Value:** 2,000 IRF
- **Quality Multipliers:** Poor 1,000 IRF, Good 3,000 IRF, Great 4,000 IRF, Perfect 6,000 IRF
- **Harvest Quantity:** 3-7 peppers
- **Seeds per Harvest:** 10% chance for 1-2 seeds
- **Acquisition:** Legendary Geode (rare), Boss drop (Volcanic Golem), Event rewards
- **Fertilizer Compatibility:** Premium+ only
- **Description:** "Blazing red pepper said to be blessed by the Phoenix. Extremely spicy and valuable."
- **Special Effects:** Fire particle effects when mature, requires high farming level (15+)
- **Familiar Preference:** Fire-type familiars (Very High)
- **Uses:** Legendary familiar food, fire resistance potion, ultimate spice crafting

#### CROP_014: Star Lotus
- **CropID:** CROP_014
- **Name:** Star Lotus
- **Rarity:** Legendary
- **Category:** Flower (Aquatic)
- **Growth Time:** 20 hours
- **Growth Stages:** 6 stages
- **Watering Needs:** Always (requires water plot)
- **Seasons:** All
- **Seed Price:** 800 IRF or 300 Robux
- **Base Harvest Value:** 3,000 IRF
- **Quality Multipliers:** Poor 1,500 IRF, Good 4,500 IRF, Great 6,000 IRF, Perfect 9,000 IRF
- **Harvest Quantity:** 1-2 flowers
- **Seeds per Harvest:** 5% chance for 1 seed
- **Acquisition:** Legendary Fish rare drop, Manta Ray fishing reward, Annual Tournament
- **Fertilizer Compatibility:** Perfect only
- **Description:** "A mystical flower that blooms once per lunar cycle. Its petals resemble a starry night sky."
- **Special Effects:** Blooms with constellation pattern, underwater growth, night glow
- **Familiar Preference:** Water/Celestial familiars (Very High)
- **Uses:** Legendary familiar food, star alchemy, ultimate decoration, prestige item

#### CROP_015: Crystal Carrot
- **CropID:** CROP_015
- **Name:** Crystal Carrot
- **Rarity:** Legendary
- **Category:** Vegetable (Magical)
- **Growth Time:** 15 hours
- **Growth Stages:** 5 stages
- **Watering Needs:** 5 times
- **Seasons:** All
- **Seed Price:** 600 IRF or 250 Robux
- **Base Harvest Value:** 2,500 IRF
- **Quality Multipliers:** Poor 1,250 IRF, Good 3,750 IRF, Great 5,000 IRF, Perfect 7,500 IRF
- **Harvest Quantity:** 1-3 carrots
- **Seeds per Harvest:** 8% chance for 1 seed
- **Acquisition:** Mining (Mythic Geode ultra-rare), Boss drop (Crystal Golem)
- **Fertilizer Compatibility:** Premium+ only
- **Description:** "Crystallized carrot infused with magical minerals. Transparent and glittering."
- **Special Effects:** Glows with inner light, crystal sound when harvested
- **Familiar Preference:** Magical/Rabbit familiars (Very High)
- **Uses:** Legendary familiar food, magic enhancement crafting, premium taming food

---

### Mythic Tier (Red)

#### CROP_016: Yggdrasil Seed
- **CropID:** CROP_016
- **Name:** Yggdrasil Sapling
- **Rarity:** Mythic
- **Category:** Tree (World Tree)
- **Growth Time:** 48 hours (2 real-life days)
- **Growth Stages:** 10 stages (Epic progression)
- **Watering Needs:** 12 times
- **Seasons:** All
- **Seed Price:** 5,000 IRF or 1,000 Robux (if available)
- **Base Harvest Value:** 20,000 IRF
- **Quality Multipliers:** Poor 10,000 IRF, Good 30,000 IRF, Great 40,000 IRF, Perfect 60,000 IRF
- **Harvest Quantity:** 1 Golden Apple + 5-10 Yggdrasil Leaves
- **Seeds per Harvest:** 2% chance for 1 seed
- **Acquisition:** Ultra-rare Boss drop (World Serpent), Annual Grand Tournament reward, Limited seasonal event
- **Fertilizer Compatibility:** Perfect only + Special "Divine Fertilizer"
- **Description:** "Sapling from the legendary World Tree. Growing one is a monumental achievement."
- **Special Effects:** 
  - Massive visual presence (largest crop)
  - Particle effects (golden leaves, rainbow aura)
  - Buffs nearby crops (+20% growth speed in 3-plot radius)
  - Seasonal changes (spring flowers, autumn colors)
  - Permanent decoration after first harvest (produces leaves monthly)
- **Familiar Preference:** All mythic familiars (Extremely High)
- **Uses:** 
  - Ultimate familiar food
  - "Golden Apple" = full familiar stat boost
  - Legendary crafting material
  - Ultimate prestige symbol
  - Private island showcase

#### CROP_017: Chronos Bloom
- **CropID:** CROP_017
- **Name:** Chronos Bloom
- **Rarity:** Mythic
- **Category:** Flower (Time-elemental)
- **Growth Time:** 36 hours (can be affected by time manipulation)
- **Growth Stages:** 8 stages (reverses and repeats stages)
- **Watering Needs:** 10 times
- **Seasons:** All (transcends seasons)
- **Seed Price:** 8,000 IRF or 1,500 Robux (rarely available)
- **Base Harvest Value:** 25,000 IRF
- **Quality Multipliers:** Poor 12,500 IRF, Good 37,500 IRF, Great 50,000 IRF, Perfect 75,000 IRF
- **Harvest Quantity:** 1-3 flowers
- **Seeds per Harvest:** 1% chance for 1 seed
- **Acquisition:** Secret Quest chain reward, Time Event (rare annual event), Leviathan Eel drop (0.1% chance)
- **Fertilizer Compatibility:** Perfect only + "Temporal Fertilizer" (event-exclusive)
- **Description:** "A flower that exists outside normal time. Petals shimmer between past, present, and future."
- **Special Effects:**
  - Visible time distortion effects around plot
  - Randomly accelerates or slows growth of adjacent crops
  - Changes color throughout day (past/present/future themes)
  - Can rarely "rewind" to earlier stage and regrow (extra harvest)
- **Familiar Preference:** Time/Cosmic familiars (Extremely High)
- **Uses:**
  - Mythic familiar food
  - Time manipulation potions (future)
  - Ultimate alchemy ingredient
  - "Temporal Seed" chance on harvest (reusable seed)

---

## Special/Event Crops

### Halloween Event

#### CROP_EVENT_001: Ghost Pumpkin
- **CropID:** CROP_EVENT_001
- **Name:** Ghost Pumpkin
- **Rarity:** Special (Event)
- **Category:** Vegetable (Haunted)
- **Growth Time:** 8 hours
- **Growth Stages:** 5 stages (spooky animations)
- **Watering Needs:** 3 times
- **Seasons:** Halloween Event Only
- **Seed Price:** 200 Halloween Tokens
- **Base Harvest Value:** 800 IRF + 50 Halloween Tokens
- **Quality Multipliers:** Normal special event rewards
- **Harvest Quantity:** 1 glowing pumpkin
- **Seeds per Harvest:** 40% chance for 2-4 seeds
- **Acquisition:** Halloween Event Shop, Trick-or-Treat activity
- **Fertilizer Compatibility:** All types
- **Description:** "Pale white pumpkin that glows and phases in and out of visibility. Spooky!"
- **Special Effects:** Ghostly particles, occasionally disappears/reappears, moaning sound effects
- **Uses:** Halloween event currency, themed decoration, collector's item

---

### Winter Event

#### CROP_EVENT_002: Frost Berry
- **CropID:** CROP_EVENT_002
- **Name:** Frost Berry
- **Rarity:** Special (Event)
- **Category:** Fruit (Frozen)
- **Growth Time:** 6 hours
- **Growth Stages:** 4 stages
- **Watering Needs:** 2 times (ice watering)
- **Seasons:** Winter Event Only
- **Seed Price:** 150 Snowflake Tokens
- **Base Harvest Value:** 600 IRF + 40 Snowflake Tokens
- **Quality Multipliers:** Event scaling
- **Harvest Quantity:** 5-10 berries
- **Seeds per Harvest:** 50% chance for 3-5 seeds
- **Acquisition:** Winter Festival Shop, Ice Fishing rewards
- **Fertilizer Compatibility:** Basic/Quality only (freezes in winter cold)
- **Description:** "Berries frozen solid but still delicious. Never melt, even in summer!"
- **Special Effects:** Ice crystal particles, cold mist, frozen visual
- **Uses:** Winter event currency, ice crafting material, cooldown familiar food

---

## Herbs & Spices

### Rare Tier (Blue)

#### CROP_018: Mint
- **CropID:** CROP_018
- **Name:** Mint
- **Rarity:** Rare
- **Category:** Herb
- **Growth Time:** 3 hours
- **Growth Stages:** 3 stages
- **Watering Needs:** 2 times
- **Seasons:** All
- **Seed Price:** 15 IRF
- **Base Harvest Value:** 50 IRF
- **Quality Multipliers:** Standard
- **Harvest Quantity:** 5-12 leaves
- **Seeds per Harvest:** 70% chance for 4-8 seeds (spreads easily)
- **Acquisition:** Farming Shop (Level 4+), Foraging
- **Fertilizer Compatibility:** All types
- **Description:** "Refreshing herb with a cool flavor. Spreads rapidly if not contained."
- **Familiar Preference:** Small herbivores (Medium)
- **Uses:** Potion ingredient (future), tea crafting, familiar food

---

### Epic Tier (Purple)

#### CROP_019: Celestial Sage
- **CropID:** CROP_019
- **Name:** Celestial Sage
- **Rarity:** Epic
- **Category:** Herb (Magical)
- **Growth Time:** 10 hours
- **Growth Stages:** 5 stages
- **Watering Needs:** 4 times
- **Seasons:** All (night bonus growth)
- **Seed Price:** 180 IRF or 80 Robux
- **Base Harvest Value:** 700 IRF
- **Quality Multipliers:** Standard
- **Harvest Quantity:** 3-7 sprigs
- **Seeds per Harvest:** 20% chance for 2-3 seeds
- **Acquisition:** Moonlight Koi drop (rare), Night Market, Alchemy Quest reward
- **Fertilizer Compatibility:** Quality+ only
- **Description:** "Silver-leafed herb that glows faintly under starlight. Essential for advanced potions."
- **Special Effects:** Gentle glow at night, star particle effects
- **Familiar Preference:** Magical familiars (High)
- **Uses:** Epic alchemy ingredient, mana potions, enchantment crafting

---

## Flowers (Decorative & Functional)

### Common Tier (Grey)

#### CROP_020: Daisy
- **CropID:** CROP_020
- **Name:** Daisy
- **Rarity:** Common
- **Category:** Flower
- **Growth Time:** 1 hour
- **Growth Stages:** 3 stages
- **Watering Needs:** 2 times
- **Seasons:** All (Spring bonus)
- **Seed Price:** 3 IRF
- **Base Harvest Value:** 10 IRF
- **Quality Multipliers:** Standard
- **Harvest Quantity:** 2-5 flowers
- **Seeds per Harvest:** 40% chance for 2-4 seeds
- **Acquisition:** Farming Shop, Foraging (common)
- **Fertilizer Compatibility:** All types
- **Description:** "Simple white flower with yellow center. Cheerful and easy to grow."
- **Uses:** Decoration, bouquet crafting, bee attraction (future apiary)

#### CROP_021: Tulip
- **CropID:** CROP_021
- **Name:** Tulip
- **Rarity:** Common
- **Category:** Flower
- **Growth Time:** 2 hours
- **Growth Stages:** 4 stages
- **Watering Needs:** 2 times
- **Seasons:** All (Spring peak)
- **Seed Price:** 5 IRF
- **Base Harvest Value:** 15 IRF
- **Quality Multipliers:** Standard
- **Harvest Quantity:** 1-3 flowers
- **Seeds per Harvest:** 30% chance for 1-2 bulbs
- **Acquisition:** Farming Shop, Spring Event
- **Fertilizer Compatibility:** All types
- **Description:** "Classic flower available in multiple colors. Symbol of spring."
- **Uses:** Decoration, bouquets, trading, dye crafting (future)

---

### Rare Tier (Blue)

#### CROP_022: Sunflower
- **CropID:** CROP_022
- **Name:** Sunflower
- **Rarity:** Rare
- **Category:** Flower
- **Growth Time:** 5 hours
- **Growth Stages:** 5 stages (grows tall)
- **Watering Needs:** 3 times
- **Seasons:** All (Summer best)
- **Seed Price:** 20 IRF
- **Base Harvest Value:** 70 IRF
- **Quality Multipliers:** Standard
- **Harvest Quantity:** 1 large flower + 10-20 seeds
- **Seeds per Harvest:** 90% chance for 15-30 seeds (produces many seeds)
- **Acquisition:** Farming Shop (Level 5+), Summer Festival
- **Fertilizer Compatibility:** All types
- **Description:** "Tall flower that follows the sun. Produces abundant edible seeds."
- **Familiar Preference:** Birds (Very High - seed eating)
- **Uses:** Decoration, seed production, bird familiar food, oil crafting (future)

#### CROP_023: Rose
- **CropID:** CROP_023
- **Name:** Rose
- **Rarity:** Rare
- **Category:** Flower
- **Growth Time:** 6 hours
- **Growth Stages:** 5 stages
- **Watering Needs:** 4 times
- **Seasons:** All
- **Seed Price:** 30 IRF
- **Base Harvest Value:** 100 IRF
- **Quality Multipliers:** Standard
- **Harvest Quantity:** 1-4 roses
- **Seeds per Harvest:** 15% chance for 1-2 seeds
- **Acquisition:** Farming Shop (Level 8+), Romance Event
- **Fertilizer Compatibility:** All types (Premium for rare colors)
- **Description:** "Classic romantic flower. Comes in multiple colors with different meanings."
- **Special Effects:** Color variants (Red/Pink/White/Yellow), Premium fertilizer unlocks rare colors (Blue/Black)
- **Uses:** Bouquets, romance quests, perfume crafting (future), high-value decoration

---

### Epic Tier (Purple)

#### CROP_024: Moonflower
- **CropID:** CROP_024
- **Name:** Moonflower
- **Rarity:** Epic
- **Category:** Flower (Nocturnal)
- **Growth Time:** 8 hours
- **Growth Stages:** 4 stages
- **Watering Needs:** 3 times
- **Seasons:** All
- **Seed Price:** 150 IRF or 70 Robux
- **Base Harvest Value:** 600 IRF
- **Quality Multipliers:** Standard
- **Harvest Quantity:** 2-5 flowers
- **Seeds per Harvest:** 25% chance for 2-4 seeds
- **Acquisition:** Night Market, Moonlight Koi drop, Mysterious Lake foraging
- **Fertilizer Compatibility:** Quality+ only
- **Description:** "Pale white flower that only blooms at night. Emits soft lunar glow."
- **Special Effects:** Opens at night, closes during day, glowing particles
- **Familiar Preference:** Nocturnal familiars (Very High)
- **Uses:** Night alchemy, moon potion ingredients, prestige decoration

---

## Database Management Notes

### Crop Balancing Formula:
```
Profit = (Harvest Value × Quality Multiplier × Harvest Quantity) - Seed Cost
Profit per Hour = Profit / Growth Time
Target: Common 5-10 IRF/hr, Rare 15-25 IRF/hr, Epic 40-60 IRF/hr, Legendary 100+ IRF/hr
```

### Quality Tier Requirements:
- **Poor:** 0-20% crop care (missed waterings, no fertilizer)
- **Normal:** 21-60% crop care (basic maintenance)
- **Good:** 61-85% crop care (good timing, basic fertilizer)
- **Great:** 86-95% crop care (perfect timing, quality fertilizer)
- **Perfect:** 96-100% crop care (perfect timing, perfect fertilizer, luck bonus)

### Adding New Crops Checklist:
- [ ] Assign unique CropID
- [ ] Balance growth time vs. profit
- [ ] Set appropriate rarity tier
- [ ] Create acquisition methods (minimum 2)
- [ ] Define fertilizer compatibility
- [ ] Write engaging description
- [ ] Test in-game balance
- [ ] Add to seasonal events if applicable
- [ ] Create visual assets
- [ ] Implement growth animations

### Version History:
- v1.0 (Feb 8, 2026): Initial database with 24 permanent crops + 2 event crops
- v1.1 (Planned): Spring Event crops
- v1.2 (Planned): Mythic tier expansions, Tree crops category

---

**Crop Database - End of Document**

*Total Crops: 26 (24 permanent + 2 event)*  
*Categories: Vegetables (8), Fruits (6), Grains (2), Herbs (2), Flowers (8)*  
*Target Total (Future): 80+ crop varieties*
