# Game Design Document
## Economy & Currency System

---

### Document Information
**System Name:** Economy & Currency System  
**Document Version:** 1.0  
**Last Updated:** February 8, 2026  
**Owner:** Economy Design Team  
**Status:** Ready for Implementation

---

## Table of Contents
1. [Currency System](#currency-system)
2. [Income Sources](#income-sources)
3. [Expenditure Sinks](#expenditure-sinks)
4. [Price Tables](#price-tables)
5. [Trading Systems](#trading-systems)
6. [Monetization Strategy](#monetization-strategy)
7. [Economic Balance](#economic-balance)
8. [Anti-Inflation Measures](#anti-inflation-measures)

---

## 1. Currency System

### 1.1 Primary Currency: IRIFA (IRF)

**Currency Properties:**
- **Full Name:** IRIFA
- **Abbreviation:** IRF
- **Symbol:** Ⓘ or IRF
- **Soft Currency:** Earned through gameplay only
- **Not Purchasable:** Cannot buy with Robux directly
- **Tradeable:** Can be traded between players (with limits)
- **Storage:** No maximum cap
- **Display:** Formatted with commas (e.g., 1,234,567 IRF)

**Acquisition Methods:**
1. Selling resources to NPCs
2. Completing quests
3. Trading with players
4. Dungeon monster drops
5. Daily login bonuses (optional system)
6. Achievement rewards
7. Seasonal event rewards

### 1.2 Premium Currency: Robux

**Usage in Game:**
- Expansions (island, storage, farm plots)
- Cosmetic items (skins, decorations)
- Convenience items (auto-watering, luck boosters)
- Premium seeds (rare varieties)
- Skip timers (not recommended, future consideration)

**Critical Rule:** 
**NO PAY-TO-WIN**
- Robux items must be convenience or cosmetic
- All gameplay content accessible without Robux
- Premium items can be obtained via trading with other players
- Free players can compete with paying players

---

## 2. Income Sources

### 2.1 Resource Selling

#### Mining Materials (to Blacksmith or Market)
| Material | Rarity | NPC Buy Price | Avg. Market Price | Farming Rate |
|----------|--------|---------------|-------------------|--------------|
| Iron Ore | Common | 5 IRF | 8-10 IRF | 30-50/hour |
| Copper Ore | Common | 8 IRF | 12-15 IRF | 20-30/hour |
| Silver Ore | Rare | 25 IRF | 35-50 IRF | 15-20/hour |
| Amethyst | Epic | 100 IRF | 150-200 IRF | 8-12/hour |
| Diamond | Legendary | 500 IRF | 800-1,200 IRF | 3-5/hour |
| Mythril | Mythic | 2,000 IRF | 3,500-5,000 IRF | 1-2/hour |

#### Fish (to Fisherman or Market)
| Fish Type | Rarity | NPC Buy Price | Avg. Market Price | Catch Rate |
|-----------|--------|---------------|-------------------|------------|
| Common Fish | Common | 5-15 IRF | 10-20 IRF | 15-20/hour |
| Rare Fish | Rare | 50-90 IRF | 70-130 IRF | 8-12/hour |
| Epic Fish | Epic | 250-500 IRF | 400-700 IRF | 3-5/hour |
| Legendary Fish | Legendary | 1,500-3,000 IRF | 2,500-4,500 IRF | 1-2/hour |
| Mythic Fish | Mythic | 10,000-18,000 IRF | 15,000-25,000 IRF | 0-1/hour |

#### Crops (to Farmer or Market)
| Crop | Rarity | NPC Buy Price | Growth Time | Profit/Day |
|------|--------|---------------|-------------|------------|
| Wheat | Common | 10 IRF | 2 days | 25 IRF |
| Corn | Common | 15 IRF | 3 days | 25 IRF |
| Tomato (Multi) | Rare | 25 IRF | 4 days, harvest 3x | 93.75 IRF |
| Strawberry (Multi) | Rare | 30 IRF | 5 days, harvest 4x | 120 IRF |
| Melon | Epic | 120 IRF | 7 days | 85.7 IRF |
| Dragon Fruit | Legendary | 800 IRF | 14 days | 285.7 IRF |
| Starfruit | Mythic | 3,000 IRF | 21 days | 714.3 IRF |

### 2.2 Quest Rewards

**Tutorial Quests (One-time):**
- Mayor Introduction: 100 IRF
- First Fishing Quest: 200 IRF + Common Rod
- First Farming Quest: 150 IRF + 5 Seeds
- Dungeon Unlock Quest: 500 IRF + Basic Sword
- Blacksmith Craft Quest: 300 IRF
- Workshop Tour: 250 IRF + 1 Decoration
- **Total Tutorial Earnings:** ~1,500 IRF

**Daily Quests (Repeatable):**
- Catch 10 Fish: 100 IRF
- Mine 20 Rocks: 150 IRF
- Harvest 15 Crops: 120 IRF
- Defeat 25 Monsters: 200 IRF
- Trade with 2 Players: 80 IRF
- **Total Daily Potential:** 650 IRF/day

**Weekly Quests (Repeatable):**
- Complete 5 Daily Quests: 500 IRF
- Catch 1 Epic+ Fish: 800 IRF
- Mine 100 Rocks: 1,000 IRF
- Defeat 1 Boss: 2,000 IRF
- **Total Weekly Potential:** 4,300 IRF/week

**NPC Story Quests (One-time, Progressive):**
- Each NPC has 10 story quests
- Quest rewards scale: 200 → 10,000 IRF
- Total per NPC: ~25,000 IRF
- 7 NPCs = ~175,000 IRF total lifetime

### 2.3 Combat Drops

**Monster Loot Tables:**
| Monster Rarity | IRF Drop Range | Drop Rate | Avg IRF/Kill |
|----------------|----------------|-----------|--------------|
| Common | 10-25 IRF | 40% | 6 IRF |
| Rare | 50-100 IRF | 30% | 22.5 IRF |
| Epic | 200-400 IRF | 20% | 60 IRF |
| Legendary | 1,000-2,500 IRF | 10% | 175 IRF |
| Mythic | 5,000-10,000 IRF | 5% | 375 IRF |

**Boss Encounters:**
| Boss Tier | Guaranteed IRF | Materials | Kill Time | IRF/Hour |
|-----------|----------------|-----------|-----------|----------|
| Normal Boss | 5,000 IRF | Epic+ | 10 min | 30,000 |
| Elite Boss | 15,000 IRF | Legendary+ | 20 min | 45,000 |
| Event Boss | 50,000 IRF | Special | 30 min | 100,000 |

### 2.4 Trading Profits

**Player-to-Player Trading:**
- Buy low, sell high strategy
- Typical margin: 20-40% profit
- Active traders: 5,000-15,000 IRF/hour
- Requires market knowledge

**Global Trading Board:**
- List items for sale (10% fee)
- Undercut competition for fast sales
- Rare item flipping
- Event item speculation

---

## 3. Expenditure Sinks

### 3.1 Essential Purchases

**Tools & Equipment:**
| Item | Cost | Frequency | Notes |
|------|------|-----------|-------|
| Common Pickaxe | 100 IRF | Once | Starter tool |
| Rare Pickaxe | 500 IRF | Once | Early upgrade |
| Epic Pickaxe | 2,000 IRF | Once | Mid game |
| Legendary Pickaxe | 10,000 IRF | Once | Late game |
| Mythic Pickaxe | 50,000 IRF | Once | End game |
| Tool Repairs | 25% craft cost | Weekly | Ongoing sink |

**Combat Equipment:**
| Item | Cost | Frequency |
|------|------|-----------|
| Common Sword | 200 IRF | Once |
| Rare Sword | 1,000 IRF | Once |
| Epic Sword | 5,000 IRF | Once |
| Legendary Sword | 25,000 IRF | Once |
| Mythic Sword | 100,000 IRF | Once |
| Armor Sets | 1.5x weapon cost | Per tier |

**Fishing Rods:**
| Rod | Cost | Unlock Requirement |
|-----|------|---------------------|
| Common Rod | 200 IRF | Tutorial |
| Rare Rod | 1,000 IRF | 10 Fish Quest |
| Epic Rod | 5,000 IRF | 50 Fish Quest |
| Legendary Rod | 25,000 IRF | 150 Fish Quest |
| Mythic Rod | 100,000 IRF | 300 Fish Quest |

### 3.2 Crafting Costs

**Material Crafting:**
- Each craft requires base materials + IRF fee
- Fee scales with output rarity
- Common: 100 IRF per craft
- Rare: 500 IRF per craft
- Epic: 2,000 IRF per craft
- Legendary: 10,000 IRF per craft
- Mythic: 50,000 IRF per craft

**Enhancement System:**
- Tool/Weapon enhancements require materials + IRF
- Enhancement +1: 1,000 IRF
- Enhancement +2: 3,000 IRF
- Enhancement +3: 7,500 IRF
- Enhancement +4: 15,000 IRF
- Enhancement +5: 30,000 IRF

### 3.3 Expansion Costs (IRF + Robux Options)

**Farm Plot Expansion:**
| Expansion Level | IRF Option | Robux Option |
|-----------------|------------|--------------|
| 2→3 plots | 5,000 IRF | 100 Robux |
| 3→4 plots | 15,000 IRF | 200 Robux |
| 4→5 plots | 35,000 IRF | 350 Robux |
| 5→6 plots | 70,000 IRF | 500 Robux |
| 6→7 plots | 150,000 IRF | 700 Robux |

**Storage Expansion:**
| Upgrade | Slots Added | IRF Cost | Robux Alternative |
|---------|-------------|----------|-------------------|
| +10 slots | +10 | 2,000 IRF | 50 Robux |
| +20 slots | +20 | 5,000 IRF | 100 Robux |
| +30 slots | +30 | 12,000 IRF | 200 Robux |
| +50 slots | +50 | 30,000 IRF | 400 Robux |

**Private Island Expansion:**
| Size Increase | IRF Cost | Robux Cost |
|---------------|----------|------------|
| +25% area | 20,000 IRF | 300 Robux |
| +50% area | 60,000 IRF | 600 Robux |
| +100% area | 150,000 IRF | 1,000 Robux |
| +200% area | N/A | 2,000 Robux |

### 3.4 Convenience Purchases

**NPC Services:**
| Service | Cost | Effect |
|---------|------|--------|
| Geode Opening | 50-1,500 IRF | Per geode type |
| Tool Repair | 25% of craft | Restore durability |
| Item Rush Craft | +50% cost | Instant delivery |
| Storage Chest | 1,000 IRF | Additional storage unit |

**Consumables:**
| Item | Cost | Duration/Use |
|------|------|--------------|
| Luck Potion | 500 IRF | 1 hour |
| Combat Buff | 300 IRF | 30 minutes |
| Fishing Bait | 100 IRF | 10 uses |
| Fertilizer (IRF version) | 2,000 IRF | 1 use, 80% quality |

### 3.5 Trading Fees

**Global Trading Board:**
- Listing fee: None (encourages listings)
- Sale fee: 10% of final price (removed from seller earnings)
- Example: Sell item for 1,000 IRF → Receive 900 IRF

**Direct Player Trading:**
- No fees (encourages face-to-face trading)
- Monthly trade limit: 50 trades
- Can expand limit: 2,000 IRF per +10 trades

---

## 4. Price Tables

### 4.1 Standard Market Values

**Reference Prices (NPC Buy Prices = 50% of Market Value):**

```
COMMON TIER:
- Iron Ore: 10 IRF market, 5 IRF NPC
- Basic Fish: 20 IRF market, 10 IRF NPC
- Common Crop: 20 IRF market, 10 IRF NPC

RARE TIER:
- Silver Ore: 50 IRF market, 25 IRF NPC
- Rare Fish: 100 IRF market, 50 IRF NPC
- Rare Seed: 200 IRF market, 100 IRF NPC

EPIC TIER:
- Amethyst: 200 IRF market, 100 IRF NPC
- Epic Fish: 500 IRF market, 250 IRF NPC
- Epic Crop: 800 IRF market, 400 IRF NPC

LEGENDARY TIER:
- Diamond: 1,000 IRF market, 500 IRF NPC
- Legendary Fish: 3,000 IRF market, 1,500 IRF NPC
- Legendary Seed: 5,000 IRF market (NPC doesn't buy)

MYTHIC TIER:
- Mythril: 5,000 IRF market, 2,000 IRF NPC
- Mythic Fish: 20,000 IRF market, 10,000 IRF NPC
- Mythic Seed: Market-only, 50,000+ IRF
```

### 4.2 Crafting Recipe Costs

**Example Equipment Crafting:**

**Common Sword Recipe:**
- 15× Iron Ore (75 IRF materials)
- 5× Wood (25 IRF materials)
- 100 IRF crafting fee
- **Total: 200 IRF**

**Epic Sword Recipe:**
- 30× Iron Ore (150 IRF)
- 25× Silver Ore (625 IRF)
- 15× Amethyst (1,500 IRF)
- 10× Monster Scales (500 IRF)
- 2,000 IRF crafting fee
- **Total: 4,775 IRF**

**Mythic Pickaxe Recipe:**
- 50× Iron Ore (250 IRF)
- 40× Titanium Ore (4,000 IRF)
- 30× Mythril (60,000 IRF)
- 20× Boss Materials (20,000 IRF)
- 50,000 IRF crafting fee
- **Total: 134,250 IRF**

---

## 5. Trading Systems

### 5.1 Player-to-Player Direct Trade

**Trade Window Interface:**
```
╔════════════════════════════════════════════╗
║       TRADING WITH: PlayerName             ║
╠════════════════════════════════════════════╣
║  YOUR OFFER:          THEIR OFFER:         ║
║  [Slot 1: Item A]     [Slot 1: Item X]     ║
║  [Slot 2: Item B]     [Slot 2: ------]     ║
║  [Slot 3: ------]     [Slot 3: ------]     ║
║  [Slot 4: ------]     [Slot 4: ------]     ║
║  [Slot 5: ------]     [Slot 5: ------]     ║
║                                            ║
║  IRF Amount: [1,000]  IRF Amount: [500]    ║
║                                            ║
║  [✓ READY]            [⧗ NOT READY]        ║
║                                            ║
║  [CONFIRM TRADE]      [CANCEL]             ║
╚════════════════════════════════════════════╝
```

**Trade Rules:**
- Maximum 5 items per side
- Maximum 100,000 IRF per trade
- Both players must click "Ready"
- Final confirmation required
- 3-second cooldown between trades (anti-spam)

**Trade Limits:**
- Free players: 50 trades/month
- Expansion available: +10 trades for 2,000 IRF
- No limit on Robux amount (to prevent restrictions)

### 5.2 Global Trading Board

**Listing System:**
```
╔════════════════════════════════════════════╗
║       GLOBAL TRADING BOARD                 ║
╠════════════════════════════════════════════╣
║  [Search: _______] [Filter: All Rarities]  ║
║                                            ║
║  📊 ACTIVE LISTINGS: 1,247                 ║
║                                            ║
║  [Icon] Diamond × 5                        ║
║         Price: 5,000 IRF                   ║
║         Seller: Player123                  ║
║         [BUY NOW]                          ║
║                                            ║
║  [Icon] Epic Sword                         ║
║         Price: 12,000 IRF                  ║
║         Seller: WarriorKing                ║
║         [BUY NOW]                          ║
║                                            ║
║  [< Previous] Page 1 of 42 [Next >]        ║
║                                            ║
║  [MY LISTINGS] [POST NEW ITEM]             ║
╚════════════════════════════════════════════╝
```

**Posting Rules:**
- Free players: 3 active listings
- Expansion: +5 slots for 5,000 IRF (permanent)
- Listing duration: 15 days
- Auto-pricing: +10% of input price (seller receives 90% after fees)
- Expired items: 3-day grace period to reclaim
- Unclaimed expired items: Deleted (warning given)

**Board Fees:**
- Listing fee: None
- Sale fee: 10% (deducted from sale price)
- Example: List for 1,000 IRF → Seller gets 900 IRF

**Withdrawal Limits:**
- Free players: 50,000 IRF/day withdrawal
- Expansion: +25,000 IRF for 3,000 IRF
- Prevents money laundering/exploitation

---

## 6. Monetization Strategy

### 6.1 Robux Purchase Options

**Convenience Items:**
1. **Sprinkler System:** 400 Robux
   - Auto-waters crops daily
   - Saves 5 minutes/day
   - Quality of life, not mandatory

2. **Server Luck Booster:** 100-500 Robux
   - +10% to +50% luck for entire server
   - Duration: 1 hour to 24 hours
   - Benefits all players (creates good will)

3. **Storage Expansion:** 50-400 Robux
   - +10 to +50 slots
   - Alternative to IRF purchase
   - Permanent upgrade

4. **Island Expansion:** 300-2,000 Robux
   - Increases island size
   - Alternative to IRF (some tiers Robux-only)
   - One-time purchase

**Cosmetic Items:**
1. **Tool Skins:** 200-800 Robux
   - Purely visual
   - No stat changes
   - Tradeable
   - Prestige items

2. **Decorations:** 100-1,000 Robux
   - Island beautification
   - Some exclusive to Robux
   - Tradeable
   - Social/prestige value

3. **Familiar Skins:** 300-600 Robux
   - Change creature appearance
   - No stat changes
   - Tradeable

**Premium Seeds:**
1. **Rare Seeds:** 50-200 Robux
   - Alternative to grinding
   - Can also be earned in-game
   - Tradeable (allows F2P access)

2. **Mythic Seeds:** 500-1,000 Robux
   - High-value crops
   - Also obtainable from dungeon drops (rare)
   - Tradeable

**Value Packs:**
1. **Starter Pack:** 800 Robux
   - Rare fishing rod
   - Rare pickaxe
   - 10 rare seeds
   - Storage +20 slots
   - One-time purchase

2. **Farmer's Bundle:** 1,200 Robux
   - Sprinkler system
   - 5 farm plot expansions
   - 50 mixed seeds
   - Fertilizer ×10

3. **Adventurer's Bundle:** 1,500 Robux
   - Epic weapon
   - Epic pickaxe
   - Luck booster ×5
   - Storage +50 slots

### 6.2 Fair Monetization Principles

**Core Principles:**
1. **No Pay-to-Win:** Robux items don't provide competitive advantages
2. **Earnable Alternatives:** Most Robux items obtainable through gameplay or trading
3. **Transparent Pricing:** Clear value proposition for all purchases
4. **Respect Time:** Convenience items save time but don't bypass progression
5. **Tradeable Items:** Premium items can be traded to F2P players

**What We DON'T Sell:**
- ❌ IRF currency directly
- ❌ Stat-boosting items exclusive to Robux
- ❌ Exclusive rarity tiers only for paying players
- ❌ Loot boxes / gacha mechanics
- ❌ Time-limited FOMO pressure (seasonal items return)

### 6.3 Conversion Goals

**Target Metrics:**
- 15% of players spend Robux
- Average spending: 500 Robux/month per payer
- Whales (>2,000 Robux/month): <5% of spenders
- 85% of revenue from convenience + cosmetics
- 15% of revenue from premium seeds/items

**Estimated Revenue:**
- 10,000 DAU
- 15% conversion = 1,500 paying players
- 500 Robux/player/month = 750,000 Robux/month
- At $0.0035/Robux = ~$2,625/month revenue

---

## 7. Economic Balance

### 7.1 Income vs Expenditure Projection

**New Player (Week 1):**
- Income: 5,000 IRF (quests + basic farming/fishing)
- Spending: 2,500 IRF (tools, equipment)
- Net: +2,500 IRF

**Intermediate Player (Month 1):**
- Income: 50,000 IRF (efficient farming, trading)
- Spending: 30,000 IRF (upgrades, expansions)
- Net: +20,000 IRF

**Advanced Player (Month 3):**
- Income: 200,000 IRF (optimized loops, market trading)
- Spending: 150,000 IRF (mythic equipment, enhancements)
- Net: +50,000 IRF

**End-Game Player (Month 6+):**
- Income: 500,000+ IRF (market dominance, boss farming)
- Spending: Minimal (collection complete)
- Net: Accumulation phase (hoarding for future updates)

### 7.2 Wealth Distribution Goals

**Target Distribution:**
- Bottom 25%: 0-10,000 IRF (new/casual players)
- Middle 50%: 10,000-100,000 IRF (active players)
- Top 20%: 100,000-1,000,000 IRF (dedicated players)
- Top 5%: 1,000,000+ IRF (market experts, veterans)

**Healthy Economy Indicators:**
- Active market listings: 1,000+ daily
- Trade volume: 10,000+ IRF/day marketplace
- Price stability: ±20% variance on common items
- Wealth mobility: New players can reach middle tier in 2-4 weeks

---

## 8. Anti-Inflation Measures

### 8.1 Currency Sinks

**Mandatory Sinks (Unavoidable):**
- Tool/equipment degradation (repair costs)
- Crafting fees (every craft)
- Trading board fees (10% of sales)
- Quest item purchases (consumables)

**Optional Sinks (Player Choice):**
- Expansions (island, storage, farm)
- Enhancements (permanent upgrades)
- Cosmetic purchases (decorations)
- Convenience purchases (rush crafting)

**Targeted Sink Rate:**
- 60% of earned IRF should be spent
- 40% retained for player savings/trading

### 8.2 Material Scarcity

**Supply Control:**
- Rare+ materials have low drop rates
- Luck systems provide controlled increases
- Event materials are time-limited
- Boss materials require group effort

**Demand Drivers:**
- Equipment upgrades need multiple materials
- Enhancements consume materials permanently
- Trading creates speculation demand
- New content introduces new recipes

### 8.3 Monitoring & Adjustment

**Economy Dashboard (Dev Tools):**
- Track IRF generation rate
- Monitor IRF sink rate
- Analyze price trends
- Identify exploits or imbalances

**Adjustment Levers:**
- NPC buy prices (adjust within ±20%)
- Drop rates (tune based on data)
- Crafting costs (rebalance if needed)
- New sinks (introduce via updates)

**Red Flags:**
- Hyperinflation (>50% price increases/month)
- Market stagnation (<100 trades/day)
- Wealth concentration (top 1% hold >80%)
- Material shortages (critical items unavailable)

**Response Actions:**
- Balance patches within 48 hours
- Communicate changes to playerbase
- Compensate affected players if major adjustments
- Run special events to inject/remove currency

---

## Implementation Checklist

### Phase 1: Core Currency
- [ ] IRF currency system (earning, spending, display)
- [ ] NPC vendor shops (buy/sell interface)
- [ ] Basic crafting cost integration
- [ ] Player balance persistence (data store)

### Phase 2: Trading
- [ ] Player-to-player trade UI
- [ ] Trade validation (anti-exploit)
- [ ] Global Trading Board UI
- [ ] Listing/buying/withdrawing system
- [ ] Trading Board database

### Phase 3: Monetization
- [ ] Robux purchase integration
- [ ] Premium item catalog
- [ ] Cosmetic application system
- [ ] Value pack purchasing

### Phase 4: Balance
- [ ] Economy dashboard (admin tools)
- [ ] Price monitoring system
- [ ] Inflation tracking
- [ ] Balance adjustment tools
- [ ] Playtesting and tuning

---

**Economy System - End of Document**

*Related Documentation: [GDD_Systems_Trading.md](GDD_Systems_Trading.md), [GDD_Progression.md](GDD_Progression.md)*
