# IRIFA: Realms of Harvest & Adventure
## Game Design Document - Trading & Market System

---

### Document Information
**Document Type:** System Design  
**System:** Trading & Market Economy  
**Version:** 1.0  
**Last Updated:** February 9, 2026  
**Status:** Implementation Ready

---

## Table of Contents
1. [Overview](#1-overview)
2. [Player-to-Player Trading](#2-player-to-player-trading)
3. [Global Market System](#3-global-market-system)
4. [Auction House](#4-auction-house)
5. [Trading Post & Commissions](#5-trading-post--commissions)
6. [Trading Reputation](#6-trading-reputation)
7. [System Interconnections](#7-system-interconnections)
8. [Economic Balancing](#8-economic-balancing)
9. [Security & Anti-Scam](#9-security--anti-scam)
10. [Technical Implementation](#10-technical-implementation)

---

## 1. Overview

### 1.1 System Purpose
Trading system creates a **player-driven economy** where:
- Players exchange items and currency
- Market prices fluctuate based on supply/demand
- Crafters sell their goods
- Collectors trade rare items
- Creates social bonds through commerce

### 1.2 Core Design Philosophy
**INTERCONNECTED PROGRESSION:**
- Mining → Crafting → Trading (material flow)
- Farming → Cooking → Market (food chain)
- Taming → Breeding → Familiar sales
- Fishing → Alchemy → Potion trading
- Dungeons → Loot → Auction House

**No system operates in isolation** - Trading is the connective tissue.

### 1.3 Trading Channels

| Method | Use Case | Fees | Speed |
|--------|----------|------|-------|
| Direct Trade | Friends, specific items | 0% | Instant |
| Market Stall | Passive sales on island | 5% | Hours-Days |
| Global Market | Mass trading, commodities | 10% | Minutes-Hours |
| Auction House | Rare items, bidding wars | 15% | 24-48 hours |
| Commission Board | Custom crafted items | 20% (to crafter) | Variable |

---

## 2. Player-to-Player Trading

### 2.1 Direct Trade Window

#### Initiating Trade
```lua
function TradingService:RequestTrade(sender, recipient)
    -- Check proximity (must be within 20 studs)
    local distance = (sender.Character.HumanoidRootPart.Position - 
                     recipient.Character.HumanoidRootPart.Position).Magnitude
    
    if distance > 20 then
        return false, "Too far away to trade"
    end
    
    -- Check if recipient busy
    if recipient.CurrentActivity == "Trading" then
        return false, "Player is already trading"
    end
    
    -- Send trade request
    TradeRequests[recipient.UserId] = {
        From = sender,
        Timestamp = os.time(),
        Status = "Pending"
    }
    
    -- Notify recipient
    RemoteEvents.TradeRequest:FireClient(recipient, sender.Name)
    
    return true
end
```

#### Trade Window Interface
```
╔════════════════════════════════════════════╗
║           TRADING WITH: PlayerName         ║
╠═══════════════════╦════════════════════════╣
║   YOUR OFFER      ║   THEIR OFFER          ║
║                   ║                        ║
║ [Item Slot 1]     ║ [Item Slot 1]          ║
║ [Item Slot 2]     ║ [Item Slot 2]          ║
║ [Item Slot 3]     ║ [Item Slot 3]          ║
║ [Item Slot 4]     ║ [Item Slot 4]          ║
║ [Item Slot 5]     ║ [Item Slot 5]          ║
║                   ║                        ║
║ IRF: [____]       ║ IRF: [____]            ║
║                   ║                        ║
║ [✓ Ready]         ║ [✗ Not Ready]          ║
╠═══════════════════╩════════════════════════╣
║  Both must click Ready to complete trade   ║
║  [Confirm Trade]  [Cancel]                 ║
╚════════════════════════════════════════════╝
```

#### Trade Validation
```lua
function TradingService:ValidateTrade(trade)
    local player1 = trade.Player1
    local player2 = trade.Player2
    
    -- Check both players are ready
    if not (trade.Player1Ready and trade.Player2Ready) then
        return false, "Both players must ready up"
    end
    
    -- Validate player 1's items
    for _, item in ipairs(trade.Player1Offer.Items) do
        if not InventoryService:HasItem(player1, item.Id) then
            return false, player1.Name .. " doesn't have " .. item.Name
        end
    end
    
    -- Validate player 1's currency
    if trade.Player1Offer.Currency > CurrencyService:GetBalance(player1) then
        return false, player1.Name .. " doesn't have enough IRF"
    end
    
    -- Same validation for player 2
    -- ... (similar checks)
    
    -- Check inventory space
    if not InventoryService:HasSpace(player1, #trade.Player2Offer.Items) then
        return false, player1.Name .. " doesn't have enough inventory space"
    end
    
    return true
end
```

### 2.2 Trade Features

#### Item Inspection
- Hover over items to see full stats
- View equipment durability, quality, enchantments
- Check familiar stats, bond level, breed count
- Prevent scams through transparency

#### Trade History
- Last 50 trades logged per player
- Shows: Partner, items exchanged, timestamp
- Can report suspicious trades
- Used for dispute resolution

#### Quick Trade Templates
- Save common trades (e.g., "10 Iron Ore for 100 IRF")
- One-click repeat trades with trusted partners
- Speeds up bulk material trading

---

## 3. Global Market System

### 3.1 Market Overview

**Purpose:** Amazon-style marketplace for commodities

#### Listed Categories
1. **Materials**
   - Mining (ores, gems, crystals)
   - Farming (crops, seeds, fertilizer)
   - Fishing (fish, bait, equipment)
   - Monster drops (leather, bones, essence)

2. **Equipment**
   - Weapons (by tier)
   - Armor (by tier and set)
   - Tools (pickaxes, fishing rods, hoes)
   - Accessories (rings, necklaces)

3. **Consumables**
   - Potions (health, mana, buffs)
   - Food (cooked meals, buffs)
   - Scrolls (enchantments, upgrades)

4. **Familiars**
   - Eggs (unhatched, tradeable)
   - Low-bond familiars (bond <3)
   - Cannot trade high-bond familiars (prevents scams)

5. **Decorations**
   - Furniture
   - Outdoor decor
   - Limited edition items

### 3.2 Listing Items

```lua
function MarketService:ListItem(player, itemId, quantity, pricePerUnit, duration)
    local item = InventoryService:GetItem(player, itemId)
    
    -- Validate ownership
    if not item or item.Quantity < quantity then
        return false, "You don't have enough of this item"
    end
    
    -- Check listing limit (max 20 active listings per player)
    local activeListings = MarketService:GetActiveListings(player.UserId)
    if #activeListings >= 20 then
        return false, "Maximum 20 listings at once"
    end
    
    -- Calculate listing fee (5% of asking price, non-refundable)
    local totalPrice = pricePerUnit * quantity
    local listingFee = totalPrice * 0.05
    
    if CurrencyService:GetBalance(player) < listingFee then
        return false, "Not enough IRF for listing fee"
    end
    
    -- Remove items from inventory (held in escrow)
    InventoryService:RemoveItem(player, itemId, quantity)
    CurrencyService:RemoveCurrency(player, listingFee)
    
    -- Create listing
    local listing = {
        ListingId = HttpService:GenerateGUID(false),
        SellerId = player.UserId,
        SellerName = player.Name,
        ItemId = itemId,
        Quantity = quantity,
        PricePerUnit = pricePerUnit,
        TotalPrice = totalPrice,
        ListedAt = os.time(),
        ExpiresAt = os.time() + duration,
        Status = "Active"
    }
    
    -- Save to market database
    MarketDatabase:AddListing(listing)
    
    return true, listing
end
```

#### Listing Durations & Fees
| Duration | Listing Fee | Use Case |
|----------|-------------|----------|
| 1 hour | 5% | Quick sales, hot items |
| 6 hours | 7% | Standard duration |
| 24 hours | 10% | Patient sellers |
| 7 days | 15% | Rare items, high prices |

### 3.3 Buying from Market

```lua
function MarketService:PurchaseItem(buyer, listingId, quantity)
    local listing = MarketDatabase:GetListing(listingId)
    
    -- Validate listing
    if not listing or listing.Status ~= "Active" then
        return false, "Listing no longer available"
    end
    
    if quantity > listing.Quantity then
        return false, "Not enough quantity available"
    end
    
    -- Calculate cost
    local cost = listing.PricePerUnit * quantity
    
    -- Validate buyer funds
    if CurrencyService:GetBalance(buyer) < cost then
        return false, "Not enough IRF"
    end
    
    -- Process transaction
    CurrencyService:RemoveCurrency(buyer, cost)
    
    -- Market fee (10% to system, 90% to seller)
    local marketFee = cost * 0.10
    local sellerRevenue = cost - marketFee
    
    -- Credit seller (even if offline)
    CurrencyService:AddCurrencyOffline(listing.SellerId, sellerRevenue)
    
    -- Give items to buyer
    InventoryService:AddItem(buyer, listing.ItemId, quantity)
    
    -- Update listing
    listing.Quantity = listing.Quantity - quantity
    if listing.Quantity == 0 then
        listing.Status = "Sold"
    end
    
    -- Log transaction
    TransactionLog:Record({
        Type = "MarketPurchase",
        Buyer = buyer.UserId,
        Seller = listing.SellerId,
        Item = listing.ItemId,
        Quantity = quantity,
        Price = cost,
        Timestamp = os.time()
    })
    
    -- Notify seller (if online)
    NotificationService:SendOffline(listing.SellerId, 
        string.format("Sold %d %s for %d IRF!", quantity, listing.ItemName, sellerRevenue))
    
    return true
end
```

### 3.4 Price Discovery

**Market Price Trends:**
```lua
function MarketService:GetPriceTrend(itemId, days)
    local sales = TransactionLog:GetSalesHistory(itemId, days)
    
    local avgPrice = 0
    local totalVolume = 0
    
    for _, sale in ipairs(sales) do
        avgPrice = avgPrice + (sale.Price * sale.Quantity)
        totalVolume = totalVolume + sale.Quantity
    end
    
    avgPrice = avgPrice / totalVolume
    
    return {
        AveragePrice = avgPrice,
        TotalVolume = totalVolume,
        TrendDirection = CalculateTrend(sales),
        LowestPrice = GetLowestActivePrice(itemId),
        HighestPrice = GetHighestActivePrice(itemId)
    }
end
```

**Price Display:**
```
Iron Ore
Current Listings: 45
Price Range: 8-15 IRF each
Average (7 days): 12 IRF
Volume: 15,432 sold this week
Trend: ↗ +15% (high demand)
```

---

## 4. Auction House

### 4.1 Auction System

**For rare, unique, or high-value items:**

#### Creating Auction
```lua
function AuctionService:CreateAuction(seller, itemId, startingBid, buyoutPrice, duration)
    -- Validate item is auction-worthy
    local item = InventoryService:GetItem(seller, itemId)
    
    if item.Rarity < "Epic" then
        return false, "Only Epic+ items can be auctioned"
    end
    
    -- Create auction
    local auction = {
        AuctionId = HttpService:GenerateGUID(false),
        SellerId = seller.UserId,
        ItemId = itemId,
        ItemData = item, -- Full item stats
        StartingBid = startingBid,
        CurrentBid = startingBid,
        BuyoutPrice = buyoutPrice,
        HighestBidder = nil,
        BidCount = 0,
        StartsAt = os.time(),
        EndsAt = os.time() + duration,
        Status = "Active"
    }
    
    -- Remove item from inventory (escrow)
    InventoryService:RemoveItem(seller, itemId, 1)
    
    -- Listing fee: 1,000 IRF (flat rate for auctions)
    CurrencyService:RemoveCurrency(seller, 1000)
    
    AuctionDatabase:AddAuction(auction)
    
    -- Announce in global chat
    ChatService:AnnounceAuction(auction)
    
    return true, auction
end
```

#### Bidding Process
```lua
function AuctionService:PlaceBid(bidder, auctionId, bidAmount)
    local auction = AuctionDatabase:GetAuction(auctionId)
    
    -- Validate auction
    if auction.Status ~= "Active" then
        return false, "Auction has ended"
    end
    
    if os.time() > auction.EndsAt then
        return false, "Auction time expired"
    end
    
    -- Bid must be at least 5% higher than current
    local minBid = auction.CurrentBid * 1.05
    if bidAmount < minBid then
        return false, string.format("Minimum bid: %d IRF", math.ceil(minBid))
    end
    
    -- Check funds
    if CurrencyService:GetBalance(bidder) < bidAmount then
        return false, "Not enough IRF"
    end
    
    -- Refund previous bidder
    if auction.HighestBidder then
        CurrencyService:AddCurrencyOffline(auction.HighestBidder, auction.CurrentBid)
        NotificationService:SendOffline(auction.HighestBidder, "You've been outbid!")
    end
    
    -- Place new bid (hold in escrow)
    CurrencyService:RemoveCurrency(bidder, bidAmount)
    
    auction.HighestBidder = bidder.UserId
    auction.CurrentBid = bidAmount
    auction.BidCount = auction.BidCount + 1
    
    -- Extend auction if last-minute bid (anti-sniping)
    if auction.EndsAt - os.time() < 300 then -- Less than 5 min left
        auction.EndsAt = auction.EndsAt + 300 -- Add 5 minutes
    end
    
    -- Notify seller
    NotificationService:SendOffline(auction.SellerId, 
        string.format("New bid: %d IRF on your auction!", bidAmount))
    
    return true
end
```

#### Auction Completion
```lua
function AuctionService:CompleteAuction(auctionId)
    local auction = AuctionDatabase:GetAuction(auctionId)
    
    if auction.HighestBidder then
        -- Successful auction
        local auctionFee = auction.CurrentBid * 0.15 -- 15% fee
        local sellerRevenue = auction.CurrentBid - auctionFee
        
        -- Pay seller
        CurrencyService:AddCurrencyOffline(auction.SellerId, sellerRevenue)
        
        -- Give item to winner
        InventoryService:AddItemOffline(auction.HighestBidder, auction.ItemId)
        
        -- Notifications
        NotificationService:SendOffline(auction.SellerId, 
            string.format("Auction sold for %d IRF!", sellerRevenue))
        NotificationService:SendOffline(auction.HighestBidder, 
            "You won the auction!")
        
        auction.Status = "Sold"
    else
        -- No bids - return item to seller
        InventoryService:AddItemOffline(auction.SellerId, auction.ItemId)
        NotificationService:SendOffline(auction.SellerId, "Auction ended with no bids")
        auction.Status = "Expired"
    end
end
```

### 4.2 Buyout Option

Players can set instant buyout price:
- Buyer pays buyout price → immediately wins
- Auction ends early
- Good for impatient buyers
- Seller gets guaranteed price

---

## 5. Trading Post & Commissions

### 5.1 Commission Board

**Request custom crafted items:**

```
╔═══════════════════════════════════════════════╗
║         COMMISSION BOARD - Blacksmithing      ║
╠═══════════════════════════════════════════════╣
║ [New Commission] [My Requests] [My Jobs]      ║
╠═══════════════════════════════════════════════╣
║                                               ║
║ 🔨 Requesting: Dragon Sword                   ║
║    Posted by: PlayerName                      ║
║    Payment: 50,000 IRF + Materials            ║
║    Materials Provided: Dragon Heart, Mithril  ║
║    Deadline: 24 hours                         ║
║    [Accept Job]                               ║
║                                               ║
║ 🔨 Requesting: 50x Steel Ingots               ║
║    Posted by: AnotherPlayer                   ║
║    Payment: 10,000 IRF                        ║
║    Materials: Not provided                    ║
║    Deadline: 48 hours                         ║
║    [Accept Job]                               ║
╚═══════════════════════════════════════════════╝
```

#### Commission Flow
1. **Player posts request:**
   - Select item or describe custom
   - Set payment amount
   - Provide materials or not
   - Set deadline

2. **Crafter accepts:**
   - Materials transferred to crafter (if provided)
   - Payment held in escrow
   - Crafter has until deadline

3. **Completion:**
   - Crafter delivers item
   - Client accepts or disputes
   - If accepted: Crafter gets payment + 20% commission bonus
   - If disputed: GM review

### 5.2 Market Stall (Private Island)

**Automated shop on your island:**

```lua
function MarketStallService:SetupStall(owner, products)
    local stall = {
        OwnerId = owner.UserId,
        Products = {},
        TotalSales = 0,
        Visitors = 0
    }
    
    for _, product in ipairs(products) do
        table.insert(stall.Products, {
            ItemId = product.ItemId,
            Price = product.Price,
            Stock = product.Stock,
            AutoRestock = product.AutoRestock, -- Pull from storage
            SoldCount = 0
        })
    end
    
    return stall
end

-- Visitor purchases
function MarketStallService:Purchase(visitor, stallId, productIndex, quantity)
    local stall = GetStall(stallId)
    local product = stall.Products[productIndex]
    
    -- Check stock
    if product.Stock < quantity then
        -- Try auto-restock
        if product.AutoRestock then
            RestockFromStorage(stall, product)
        else
            return false, "Out of stock"
        end
    end
    
    -- Process purchase
    local cost = product.Price * quantity
    CurrencyService:RemoveCurrency(visitor, cost)
    CurrencyService:AddCurrencyOffline(stall.OwnerId, cost * 0.95) -- 5% market fee
    
    -- Give item
    InventoryService:AddItem(visitor, product.ItemId, quantity)
    
    -- Update stock
    product.Stock = product.Stock - quantity
    product.SoldCount = product.SoldCount + quantity
    
    return true
end
```

**Stall Benefits:**
- Passive income while offline
- Automated restocking from storage
- Display rare items to visitors
- Good for crafters selling in bulk

---

## 6. Trading Reputation

### 6.1 Merchant Rank System

**Progression through trading:**

| Rank | Trades Required | Benefits |
|------|-----------------|----------|
| Novice Trader | 0 | Standard fees (10%) |
| Merchant | 50 | -1% market fees |
| Expert Trader | 200 | -2% fees, Priority listings |
| Master Merchant | 500 | -3% fees, Featured shop badge |
| Trade Baron | 1,000 | -5% fees, Custom shop banner |
| Tycoon | 2,500 | -7% fees, Exclusive auction slots |

### 6.2 Reputation Score

```lua
function TradingService:CalculateReputation(playerId)
    local rep = 0
    
    -- Total trades completed
    local totalTrades = GetTradeCount(playerId)
    rep = rep + (totalTrades * 10)
    
    -- Volume traded (IRF)
    local totalVolume = GetTotalTradeVolume(playerId)
    rep = rep + (totalVolume / 1000) -- 1 rep per 1,000 IRF traded
    
    -- Positive reviews from trade partners
    local positiveReviews = GetPositiveReviews(playerId)
    rep = rep + (positiveReviews * 50)
    
    -- Penalties
    local disputes = GetDisputeCount(playerId)
    rep = rep - (disputes * 200)
    
    local scamReports = GetScamReports(playerId)
    rep = rep - (scamReports * 1000)
    
    return math.max(0, rep)
end
```

### 6.3 Trade Reviews

After each trade, players can review partner:
- **Positive (+1):** Fast, fair, good communication
- **Neutral (0):** Standard transaction
- **Negative (-1):** Slow, communication issues
- **Report Scam (-10):** Requires GM review

Public reputation score shown on profile.

---

## 7. System Interconnections

### 7.1 Trading as Central Hub

**Every system feeds into trading:**

#### Mining → Trading
- Mine ores → Sell raw materials on market
- Rare gems → Auction house for high prices
- Geodes → Sell unopened for gambling appeal

#### Farming → Trading
- Grow crops → Sell to cooks via commission
- Perfect quality crops → Premium prices
- Seeds → Breed and sell rare varieties

#### Fishing → Trading
- Common fish → Bulk sell on market
- Rare fish → Auction for collectors
- Event fish → Limited-time high demand

#### Taming → Trading
- Breed familiars → Sell eggs/low-bond creatures
- Perfect stat offspring → High auction prices
- Shiny variants → Collector's items

#### Crafting → Trading
- Craft equipment → Main income for blacksmiths
- Potions → Sell to dungeon runners (consumables always in demand)
- Enchanted gear → Premium auction items

#### Combat/Dungeons → Trading
- Boss drops → Rare materials for crafting
- Legendary gear → If not needed, auction
- Excess loot → Convert to IRF via market

#### Private Island → Trading
- Market stall → Passive income
- Showcase rare items → Attract buyers
- Host auction events → Community gatherings

### 7.2 Progression Loop Example

**New Player Path:**
```
Day 1: Mine copper → Sell 100 ore → 800 IRF
Day 2: Buy better pickaxe → Mine iron → 2,000 IRF
Day 3: Commission blacksmith for sword → Fight monsters → Get rare drops
Day 4: Sell monster drops → Buy fishing rod → Catch rare fish
Day 5: Auction rare fish → 15,000 IRF → Expand farm
Day 6: Grow crops → Sell perfect quality → 30,000 IRF
Day 7: Learn blacksmithing → Craft for commissions → Passive income
```

**Mid-Game Optimization:**
```
- Farm generates 50,000 IRF/day from perfect crops
- Market stall sells crafted gear for 30,000 IRF/day passive
- Accept 3 crafting commissions daily for 20,000 IRF each
- Auction rare familiar eggs weekly for 100,000+ IRF
- Total: 200,000+ IRF/day income
```

### 7.3 Material Flow Chart

```
Mining → Raw Ores
    ↓
Smelting → Ingots
    ↓
Blacksmithing → Equipment
    ↓
Enhancement → Enchanted Gear
    ↓
Trading → IRF
    ↓
Reinvest in better tools → Higher tier content
```

**Cross-System Dependencies:**
- **Crafting** needs materials from **Mining**, **Farming**, **Fishing**
- **Combat** requires equipment from **Crafting**
- **Taming** needs food from **Farming** and **Fishing**
- **Dungeons** require consumables from **Alchemy** (Cooking)
- **Private Island** decorations from all systems
- **Trading** monetizes ALL activities

---

## 8. Economic Balancing

### 8.1 Currency Sinks (Remove IRF from economy)

**Essential Sinks:**
1. **NPC Repairs:** Equipment durability (5-10% of value)
2. **Island Expansion:** 10K-500K IRF per tier
3. **Crafting Fees:** NPC fees for using stations
4. **Market Fees:** 5-15% on all trades
5. **Taming Supplies:** Nets, flutes consumed
6. **Teleportation:** Fast travel costs (50-500 IRF)
7. **Recipe Purchases:** Learn new crafting recipes
8. **Respec Fees:** Change specialization (5,000 IRF)

### 8.2 Currency Faucets (Add IRF to economy)

**Controlled Faucets:**
1. **Quest Rewards:** Fixed amounts per quest
2. **Daily Login:** 500 IRF/day base
3. **Achievements:** One-time rewards
4. **Dungeon Rewards:** Cleared dungeons
5. **Selling to NPCs:** Last resort (50% of market value)

### 8.3 Inflation Control

```lua
function EconomyService:MonitorInflation()
    -- Track average wealth per player
    local totalWealth = 0
    local playerCount = 0
    
    for _, player in ipairs(game.Players:GetPlayers()) do
        totalWealth = totalWealth + CurrencyService:GetBalance(player)
        playerCount = playerCount + 1
    end
    
    local avgWealth = totalWealth / playerCount
    
    -- If average wealth growing too fast (>10% per week)
    if avgWealth > LastWeekAvg * 1.10 then
        -- Increase sink costs
        AdjustRepairCosts(1.05) -- +5%
        AdjustMarketFees(1.05)
        
        -- Reduce faucet outputs
        AdjustQuestRewards(0.95) -- -5%
    end
end
```

### 8.4 Market Manipulation Prevention

**Anti-Bot Measures:**
- Trading cooldowns (5 seconds between trades)
- Listing limits (20 active listings)
- Price floor/ceiling (can't list 1 IRF or 999,999,999 IRF)

**Anti-RWT (Real World Trading):**
- Flag suspiciously lopsided trades
- Monitor wealth transfers to new accounts
- Track IP addresses for account linking
- Ban both parties if RWT detected

---

## 9. Security & Anti-Scam

### 9.1 Scam Prevention

**Built-in Protections:**

1. **Trade Confirmation:**
```
╔════════════════════════════════════════════╗
║           CONFIRM TRADE                    ║
╠════════════════════════════════════════════╣
║  You are giving:                           ║
║  • Dragon Sword (Legendary, 800 DMG)       ║
║  • 50,000 IRF                              ║
║                                            ║
║  You are receiving:                        ║
║  • Wooden Stick (Common, 10 DMG)           ║
║  • 100 IRF                                 ║
║                                            ║
║  ⚠️ WARNING: This trade appears unfair!    ║
║                                            ║
║  Type "CONFIRM" to proceed: [_________]    ║
║  [Cancel]                                  ║
╚════════════════════════════════════════════╝
```

2. **Item Locking:**
- Bound items cannot be traded (quest rewards)
- High-bond familiars cannot be traded (bond ≥8)
- Recently obtained mythic items have 7-day trade lock

3. **Trade Value Assessment:**
```lua
function TradingService:AssessTradeFairness(offer1, offer2)
    local value1 = CalculateTotalValue(offer1)
    local value2 = CalculateTotalValue(offer2)
    
    local ratio = math.max(value1, value2) / math.min(value1, value2)
    
    if ratio > 3 then
        return "VERY_UNFAIR" -- 3× difference
    elseif ratio > 1.5 then
        return "UNFAIR" -- 50% difference
    else
        return "FAIR"
    end
end
```

### 9.2 Dispute Resolution

**If trade goes wrong:**

1. **Player reports issue** within 24 hours
2. **System reviews trade log:**
   - Both players' offers
   - Chat logs during trade
   - Item stats at time of trade
3. **Automated decision** for clear cases
4. **GM review** for complex disputes
5. **Rollback** if scam confirmed (both players restored to pre-trade state)

**Scammer Penalties:**
- First offense: 7-day trade ban
- Second offense: 30-day trade ban + reputation -5,000
- Third offense: Permanent trade ban

---

## 10. Technical Implementation

### 10.1 Trade Data Structure

```lua
TradeInstance = {
    TradeId = "UUID",
    Player1 = {
        UserId = 12345,
        Offer = {
            Items = {
                {ItemId = "WPN_IRON_SWORD", Quantity = 1, Data = {...}},
                {ItemId = "MAT_IRON_ORE", Quantity = 50}
            },
            Currency = 1000
        },
        Ready = false,
        Confirmed = false
    },
    Player2 = {
        UserId = 67890,
        Offer = {
            Items = {...},
            Currency = 0
        },
        Ready = false,
        Confirmed = false
    },
    Status = "InProgress", -- InProgress, Completed, Cancelled
    StartedAt = 1707437000,
    CompletedAt = nil
}
```

### 10.2 Market Database Schema

```lua
-- Market Listings (OrderedDataStore for price sorting)
MarketListing = {
    ListingId = "UUID",
    SellerId = 12345,
    ItemId = "MAT_IRON_ORE",
    Quantity = 100,
    PricePerUnit = 10,
    TotalPrice = 1000,
    ListedAt = 1707437000,
    ExpiresAt = 1707458600,
    Status = "Active" -- Active, Sold, Expired, Cancelled
}

-- Transaction History (DataStore)
Transaction = {
    TransactionId = "UUID",
    Type = "MarketPurchase", -- MarketPurchase, DirectTrade, Auction
    BuyerId = 12345,
    SellerId = 67890,
    ItemId = "MAT_IRON_ORE",
    Quantity = 50,
    Price = 500,
    Timestamp = 1707437000
}
```

### 10.3 Network Optimization

```lua
-- Batch market updates
function MarketService:BroadcastMarketUpdates()
    local updates = {}
    
    -- Collect all changes in last 5 seconds
    for _, listing in ipairs(RecentChanges) do
        table.insert(updates, {
            ListingId = listing.ListingId,
            Status = listing.Status,
            Quantity = listing.Quantity,
            CurrentBid = listing.CurrentBid
        })
    end
    
    -- Send batch update to all clients
    RemoteEvents.MarketUpdate:FireAllClients(updates)
    
    RecentChanges = {} -- Clear
end

-- Run every 5 seconds
RunService.Heartbeat:Connect(function()
    wait(5)
    MarketService:BroadcastMarketUpdates()
end)
```

---

## Implementation Checklist

### Phase 1: Core Trading (Month 5)
- [ ] Direct P2P trade window
- [ ] Trade validation and security
- [ ] Trade history logging
- [ ] Basic market listings (buy/sell)
- [ ] Item escrow system

### Phase 2: Market Expansion (Month 6)
- [ ] Global market interface (search, filters)
- [ ] Price trend tracking
- [ ] Market stall on private island
- [ ] Commission board (crafting requests)
- [ ] Trading reputation system

### Phase 3: Auction House (Month 7)
- [ ] Auction creation and bidding
- [ ] Buyout system
- [ ] Auction notifications
- [ ] Auction history and leaderboards
- [ ] Anti-snipe protection

### Phase 4: Advanced Features (Month 8)
- [ ] Bulk trading tools
- [ ] Trade templates
- [ ] Market analytics dashboard
- [ ] Merchant rank benefits
- [ ] Cross-server market integration

### Phase 5: Security & Polish (Month 9)
- [ ] Scam detection algorithms
- [ ] Dispute resolution system
- [ ] Economic monitoring tools
- [ ] Market events (sales, special auctions)
- [ ] Trading achievements

---

## Related Documentation
- [GDD_Economy.md](GDD_Economy.md) - Economic foundation
- [GDD_Systems_Crafting.md](GDD_Systems_Crafting.md) - Items to trade
- [GDD_Systems_PrivateIsland.md](GDD_Systems_PrivateIsland.md) - Market stalls
- All Database files - Items available for trading

---

**Document End - Trading & Market System**  
*A player-driven economy that connects all game systems*
