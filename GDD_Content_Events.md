# IRIFA: Realms of Harvest & Adventure
## Game Design Document - Seasonal Events & Live Content

---

### Document Information
**Document Type:** Content Design  
**Category:** Events, Seasons, Live Service  
**Version:** 1.0  
**Last Updated:** February 9, 2026  
**Update Frequency:** Bi-weekly patches, Monthly major events

---

## Table of Contents
1. [Live Service Overview](#1-live-service-overview)
2. [Seasonal Calendar](#2-seasonal-calendar)
3. [Major Holiday Events](#3-major-holiday-events)
4. [Mini-Events](#4-mini-events)
5. [Limited-Time Content](#5-limited-time-content)
6. [Event Rewards System](#6-event-rewards-system)
7. [Community Events](#7-community-events)
8. [Technical Implementation](#8-technical-implementation)

---

## 1. Live Service Overview

### 1.1 Content Strategy

**Goals:**
- Keep players engaged between major updates
- Celebrate real-world holidays and seasons
- Create FOMO (Fear of Missing Out) with exclusive rewards
- Build community through shared server events
- Provide consistent content without development burnout

**Update Schedule:**

| Frequency | Type | Content |
|-----------|------|---------|
| Weekly | Hotfix | Bug fixes, minor balance |
| Bi-weekly | Patch | Small features, QoL improvements |
| Monthly | Event | Major seasonal event with new content |
| Quarterly | Expansion | New systems, storylines, zones |

### 1.2 Event Design Principles

**Accessibility:**
- All players can participate (no level gates for joining)
- Rewards scaled to player level
- Solo AND group content available

**Variety:**
- Rotate between different activity types
- Don't repeat same event format consecutively
- Mix combat, gathering, crafting, and social events

**Exclusivity:**
- Event-exclusive cosmetics drive engagement
- Core gameplay items can be obtained year-round
- Limited-time items may return (with variants) in future years

---

## 2. Seasonal Calendar

### 2.1 Year-Round Event Schedule

**SPRING (March-May)**
| Week | Event | Type | Duration |
|------|-------|------|----------|
| 1-2 | Spring Festival | Major | 2 weeks |
| 3 | Cherry Blossom Viewing | Mini | 1 week |
| 4 | Fishing Tournament | Mini | 3 days |
| 5-6 | Easter Egg Hunt | Major | 2 weeks |
| 7 | Earth Day Cleanup | Community | 1 week |
| 8 | Planting Competition | Mini | 1 week |

**SUMMER (June-August)**
| Week | Event | Type | Duration |
|------|-------|------|----------|
| 1-2 | Summer Beach Party | Major | 2 weeks |
| 3 | Fishing Competition | Mini | 3 days |
| 4 | Familiar Sports Day | Mini | 1 week |
| 5-6 | Treasure Hunt | Major | 2 weeks |
| 7 | Swimming Championship | Mini | 3 days |
| 8 | Fireworks Festival | Major | 1 week |

**AUTUMN (September-November)**
| Week | Event | Type | Duration |
|------|-------|------|----------|
| 1-2 | Harvest Festival | Major | 2 weeks |
| 3 | Mining Expedition | Mini | 1 week |
| 4 | Boss Rush | Mini | 3 days |
| 5-6 | Halloween Spooktacular | Major | 3 weeks |
| 7 | Thanksgiving Feast | Community | 1 week |
| 8 | Autumn Market | Mini | 1 week |

**WINTER (December-February)**
| Week | Event | Type | Duration |
|------|-------|------|----------|
| 1-3 | Winter Solstice | Major | 3 weeks |
| 4-6 | New Year Celebration | Major | 3 weeks |
| 7 | Ice Fishing Derby | Mini | 1 week |
| 8 | Valentine's Day | Major | 2 weeks |

---

## 3. Major Holiday Events

### 3.1 Spring Festival (March)

**Theme:** Renewal, Growth, New Beginnings

**Duration:** 2 weeks  
**Event Story:**
*"Spring has arrived in IRIFA! The town celebrates the season of growth with a grand festival. Plant special event seeds, catch rare spring fish, and help Mayor Theo organize the perfect celebration!"*

**Event Activities:**

#### Flower Field Quest Chain
- Plant Spring Blossom Seeds (event exclusive)
- Create massive flower field (community goal: 100,000 flowers planted server-wide)
- Reward: Rainbow Flower Crown (cosmetic)

#### Spring Fishing Contest
- Catch Cherry Blossom Koi (event exclusive fish)
- Leaderboard for biggest catch
- Top 100 get exclusive Spring Rod (epic, rainbow trail)

#### Spring Familiar Hunt
- Spring Rabbit (event familiar) spawns in fields
- Pink coloration, grants +20% farming speed
- Increased spawn rate during event

#### Cooking Competition
- New temporary feature: Cooking system preview
- Craft Spring Salads from event vegetables
- Submit to NPC judge, win prizes

**Event Shop:**
| Item | Event Currency | Description |
|------|---------------|-------------|
| Spring Blossom Seeds | 100 Petals | Grows in 1 hour, event exclusive |
| Cherry Blossom Tree | 5,000 Petals | Decoration, 100 aesthetic score |
| Flower Crown (Head) | 8,000 Petals | Cosmetic, rainbow particles |
| Spring Outfit Set | 15,000 Petals | Full cosmetic set |
| Spring Furniture Bundle | 10,000 Petals | 10 spring decorations |

**Event Currency:** "Petals"
- Earned from: Planting event seeds (50), catching event fish (100), completing event quests (500)

**Exclusive Rewards:**
- Spring Wings (back cosmetic, butterfly wings)
- Bunny Ears (head cosmetic)
- Pastel color palette for decorations

---

### 3.2 Halloween Spooktacular (October)

**Theme:** Spooky, Scary, Fun Frights

**Duration:** 3 weeks (entire October)  
**Event Story:**
*"Strange things are happening in IRIFA! Pumpkins grow overnight, ghosts appear in the graveyard, and the Pumpkin King has challenged adventurers to defeat his Haunted Mansion! Embrace the spooky season!"*

**Event Activities:**

#### Haunted Mansion Dungeon
- **NEW LIMITED DUNGEON** with spooky aesthetic
- 5 floors, progressively harder
- Boss: The Pumpkin King (giant jack-o-lantern golem)
- Drops: Halloween weapons and armor

#### Trick-or-Treat System
- Visit other players' islands
- Knock on their doors (if they have house built)
- Receive random candy (event currency)
- Homeowners can choose "Trick" (prank) or "Treat" (give candy)

#### Pumpkin Patch Farming
- Ghost Pumpkin Seeds (event crop)
- Grow enormous pumpkins
- Carve them for decorations
- Submit to contest (biggest pumpkin wins title)

#### Costume Contest
- Players vote on best costumes (cosmetic combinations)
- Top 10 showcased in town square
- Winner gets exclusive "Best Dressed" title

#### Monster Invasion
- Nightly event (8 PM - 12 AM game time)
- Undead, Ghosts, and Werewolves spawn in town
- Players defend together
- Rewards scale with participation

**Event Shop:**
| Item | Candy Cost | Description |
|------|------------|-------------|
| Ghost Pumpkin Seeds | 50 | Grows glowing pumpkins |
| Haunted House Decoration | 10,000 | Large spooky house |
| Vampire Cape | 8,000 | Back cosmetic, bat transformation emote |
| Witch Hat & Broom | 6,000 | Hat + broom mount (flies!) |
| Pumpkin Familiar Egg | 15,000 | Pumpkin Fiend (event familiar) |
| Spooky Furniture Set | 12,000 | Gothic themed furniture |

**Event Currency:** "Candy"
- Earned from: Haunted Mansion runs (500), Trick-or-Treat (50-200), Monster kills (25), Event quests (1,000)

**Exclusive Rewards:**
- Jack-o-Lantern Head (helmet cosmetic)
- Skeleton Outfit
- Ghost Pet (follows player, translucent)
- Haunted Mansion Music Track

**Special Feature - "Cursed Items":**
- Rare drops from Pumpkin King
- High stats but visual "curse" effect (dark aura)
- Aesthetic choice: power vs appearance

---

### 3.3 Winter Solstice (December)

**Theme:** Snow, Ice, Holiday Cheer

**Duration:** 3 weeks (all December)  
**Event Story:**
*"The longest night approaches! IRIFA is blanketed in snow, and the legendary Frost Wyrm has appeared. Mayor Theo is organizing a town-wide celebration - help prepare for the Winter Festival!"*

**Event Activities:**

#### Ice Palace Raid
- **NEW RAID DUNGEON** in frozen zone
- Requires 5-10 players
- Boss: Frost Wyrm (event legendary boss)
- Drops: Winter weapons, Frost Wyrm mount (rare)

#### Snowman Building Competition
- New feature: Build snowmen on your island
- Stack snow blocks, add decorations
- Community votes on best snowman
- Winner's design becomes permanent NPC decoration

#### Gift Exchange Event
- Players can wrap items and send as gifts
- Mystery gift system (random player receives)
- Opening gifts gives bonus event currency
- Encourages trading and generosity

#### Ice Skating Rink
- Temporary location in town square
- Minigame: Racing, figure skating
- Leaderboard rewards
- Social gathering spot

#### Holiday Lights Contest
- Decorate island with lights
- Judges (NPCs) visit and rate
- Best decorated island showcased
- Winner gets "Festival of Lights" title

**Event Shop:**
| Item | Snowflake Cost | Description |
|------|---------------|-------------|
| Frozen Seeds | 100 | Blue glowing crops, winter themed |
| Christmas Tree | 8,000 | Large decorated tree, lights animate |
| Winter Outfit | 12,000 | Warm coat, scarf, earmuffs |
| Snowboard Mount | 15,000 | Slides on snow, +100% speed |
| Frost Wyrm Egg | 25,000 | Event legendary familiar |
| Ice Sculpture Set | 10,000 | 5 ice decorations |

**Event Currency:** "Snowflakes"
- Earned from: Ice Palace runs (800), Gift exchanges (100), Ice skating wins (200), Event quests (1,500)

**Exclusive Rewards:**
- Santa Hat (cosmetic, jingle bell sounds)
- Reindeer Antlers
- Snowflake Wings (back cosmetic, leaves ice trail)
- Holiday Music Track for island

---

### 3.4 Summer Beach Party (July)

**Theme:** Sun, Sand, Ocean Fun

**Duration:** 2 weeks  
**Event Story:**
*"It's the hottest time of year! Marina has organized a beach party on the tropical island. Surfing competitions, sandcastle building, and legendary sea creatures await!"*

**Event Activities:**

#### Surfing Minigame
- NEW MECHANIC: Ride waves
- Timed scoring based on tricks
- Leaderboard competition
- Rewards: Surfboard mount variations

#### Sandcastle Contest
- Build sandcastles on beach
- Use sand blocks + decorations
- Judges rate creativity
- Winner gets "Master Architect" title

#### Leviathan Hunt
- Leviathan Eel (mythic fish) increased spawn rate
- Server-wide goal: Catch 1,000 collectively
- Unlocks bonus boss: Leviathan King
- Raid boss in ocean depths

#### Beach Volleyball
- New social minigame
- 2v2 teams
- Simple mechanics (timing-based)
- Casual fun, small rewards

#### Underwater Exploration
- Temporary diving mechanic
- Find sunken treasure chests
- Collect pearls (event currency)
- Discover secret underwater cave

**Event Shop:**
| Item | Pearl Cost | Description |
|------|-----------|-------------|
| Tropical Seeds | 150 | Pineapple, coconut, mango |
| Beach Hut | 7,000 | Tiki bar decoration |
| Swimsuit Outfit | 5,000 | Summer cosmetics |
| Surfboard Mount | 10,000 | Water travel, does tricks |
| Sea Turtle Mount | 15,000 | Swim speed +100% |
| Beach Furniture Set | 8,000 | Lawn chairs, umbrella, cooler |

**Event Currency:** "Pearls"
- Earned from: Surfing wins (200), Sandcastle votes (100), Leviathan parts (500), Diving treasures (50), Event quests (1,000)

**Exclusive Rewards:**
- Snorkel & Flippers (cosmetic + function)
- Hawaiian Shirt
- Sunglasses (head cosmetic)
- Beach Ball Pet (follows player)

---

## 4. Mini-Events

### 4.1 Fishing Tournament (Recurring)

**Duration:** 3 days (weekend)  
**Frequency:** Monthly

**Format:**
- Leaderboard: Biggest fish caught
- Leaderboard: Most fish caught
- Leaderboard: Rarest fish caught

**Rewards:**
- Top 10 each category: Exclusive rod cosmetic
- Top 100: Event currency bundle
- All participants: Participation trophy

---

### 4.2 Boss Rush (Recurring)

**Duration:** 1 week  
**Frequency:** Bi-monthly

**Format:**
- All dungeon bosses respawn instantly
- No cooldowns
- Double drop rates
- Leaderboard: Fastest clear times

**Rewards:**
- Titles for speed records
- Bonus loot for multiple clears
- Event-exclusive boss cosmetic drops

---

### 4.3 Familiar Sports Day

**Duration:** 1 week  
**Frequency:** Quarterly

**Format:**
- Familiar racing (mount speed competition)
- Familiar beauty contest (aesthetic voting)
- Familiar battle tournament (1v1 PvP)

**Rewards:**
- Champion Familiar Collar (cosmetic for familiars)
- Gold/Silver/Bronze medals (cosmetics)
- Event currency

---

### 4.4 Crafting Expo

**Duration:** 1 week  
**Frequency:** Quarterly

**Format:**
- Players submit crafted items to exhibition
- Categories: Weapons, Armor, Decorations
- NPCs and players vote
- Winners showcased in museum

**Rewards:**
- Master Craftsman title (category winners)
- Recipe unlocks
- Crafting material bundles

---

## 5. Limited-Time Content

### 5.1 Rotating Rare Spawns

**Weekly Rotation:**
- Each week, one Legendary creature has increased spawn rate
- Announced via in-game notification
- Creates urgency to hunt specific familiars

**Example Schedule:**
- Week 1: Unicorn (5× spawn rate)
- Week 2: Phoenix (5× spawn rate)
- Week 3: Void Sprite (5× spawn rate)
- Week 4: Storm Hawk (5× spawn rate)

---

### 5.2 Flash Sales

**Random 24-Hour Sales:**
- Workshop items discounted 50%
- Announced suddenly
- Creates login incentive

---

### 5.3 Mysterious Merchant Extended Visits

**Monthly Event:**
- Traveling Merchant stays in town for 3 days
- Expanded inventory
- Exclusive monthly item
- Discounted prices

---

### 5.4 Double XP Weekends

**Frequency:** Twice per month

**Format:**
- All XP gains doubled (player level AND proficiencies)
- Announced in advance
- Helps new players catch up

---

### 5.5 Community Challenges

**Monthly Goals:**
- Server-wide objectives (e.g., "Mine 1 Million ores collectively")
- Progress bar visible to all
- Rewards unlock for entire server upon completion

**Example Challenges:**
- Harvest 500,000 crops → Unlock rare seed for everyone
- Defeat 100,000 monsters → Boss spawn rate +50% for 1 week
- Place 1 Million decorations → Town square gets permanent upgrade

---

## 6. Event Rewards System

### 6.1 Event Currency Design

**General Structure:**
- Each major event has unique currency
- Earned through event activities
- Spent at event shop (limited time)
- Leftover currency converts to IRF after event (poor conversion rate)

**Earning Rates:**
- Easy activities: 50-100 per action
- Medium activities: 200-500 per action
- Hard activities: 1,000+ per action
- Daily quests: 500-1,000 per quest

**Shop Pricing:**
- Cosmetics: 5,000-15,000
- Mounts: 10,000-25,000
- Exclusive items: 20,000-50,000

**Target:** Average player should earn 30,000-50,000 currency over event duration with moderate play (1-2 hours/day)

---

### 6.2 Reward Tiers

**Participation Rewards (Easy):**
- Everyone gets something for logging in
- Event currency bundle
- Basic cosmetic item

**Engagement Rewards (Medium):**
- Complete event quests
- Exclusive equipment (cosmetic variants)
- Event titles

**Mastery Rewards (Hard):**
- Top leaderboards
- Rare mounts/familiars
- Prestigious titles
- Showcase on leaderboards

**Completionist Rewards (Extreme):**
- Obtain ALL event items
- Meta-achievement
- Ultra-rare cosmetic (glowing effect, particles)
- Permanent bragging rights

---

### 6.3 FOMO vs Accessibility Balance

**FOMO Elements (Create Urgency):**
- Limited-time cosmetics
- Event-exclusive familiars
- Leaderboard titles
- First-time bonuses

**Accessibility Elements (Avoid Frustration):**
- Core gameplay items available year-round
- Event items may return in future (variants)
- Multiple paths to earn currency
- No pay-to-win (Robux only for cosmetics)

**Philosophy:** *"You can miss an event and still enjoy the game, but participating feels rewarding and special."*

---

## 7. Community Events

### 7.1 Server-Wide Boss Battles

**Format:**
- Massive boss appears in shared zone
- All online players can attack
- Health pool scales with server population
- Loot distributed to all participants

**Frequency:** Monthly

**Example Bosses:**
- Void Titan (appears from sky rift)
- Leviathan King (ocean event)
- Ancient Dragon (flies over islands)

---

### 7.2 Town Building Projects

**Format:**
- Mayor announces project (e.g., "Build a Museum!")
- Players donate materials
- Progress bar tracks donations
- Upon completion, new building appears in town

**Benefits:**
- New NPC or service
- Permanent world improvement
- Contributor names on plaque

**Example Projects:**
- Museum (display collections)
- Library (lore repository)
- Arena (PvP future feature)
- Observatory (astronomy minigame)

---

### 7.3 Design Contests

**Format:**
- Monthly theme announced (e.g., "Underwater Base")
- Players submit island screenshots
- Community votes on favorites
- Winners showcased in-game

**Categories:**
- Best Overall
- Most Creative
- Best Use of Theme
- Funniest Design

**Rewards:**
- Exclusive title
- Feature on official social media
- In-game trophy item
- Robux prize (for top winner)

---

### 7.4 Speed Run Competitions

**Format:**
- Official tournament bracket
- Race to complete dungeons fastest
- Streamed on official channel
- Prizes for top times

**Frequency:** Quarterly

---

## 8. Technical Implementation

### 8.1 Event System Architecture

```lua
EventService = {}

EventData = {
    EventId = "EVENT_HALLOWEEN_2026",
    Name = "Halloween Spooktacular",
    StartDate = DateTime.fromIsoDate("2026-10-01T00:00:00Z"),
    EndDate = DateTime.fromIsoDate("2026-10-31T23:59:59Z"),
    
    Currency = {
        Name = "Candy",
        Icon = "rbxassetid://12345"
    },
    
    Activities = {
        {
            ActivityId = "HAUNTED_MANSION",
            Type = "Dungeon",
            Rewards = {
                {Type = "Currency", Amount = 500},
                {Type = "Item", ItemId = "PUMPKIN_SWORD", DropRate = 0.1}
            }
        }
    },
    
    Shop = {
        {
            ItemId = "GHOST_PET",
            Cost = 15000,
            Stock = -1 -- Infinite
        }
    }
}

function EventService:IsEventActive(eventId)
    local event = EventData[eventId]
    local now = DateTime.now().UnixTimestamp
    
    return now >= event.StartDate and now <= event.EndDate
end

function EventService:AwardEventCurrency(player, eventId, amount)
    if not IsEventActive(eventId) then return end
    
    local playerData = GetPlayerData(player)
    playerData.EventCurrency[eventId] = (playerData.EventCurrency[eventId] or 0) + amount
    
    SavePlayerData(player)
    UpdateEventCurrencyUI(player)
end

function EventService:PurchaseEventItem(player, eventId, itemId)
    local event = EventData[eventId]
    local item = event.Shop[itemId]
    local playerData = GetPlayerData(player)
    
    -- Check currency
    if playerData.EventCurrency[eventId] < item.Cost then
        return false, "Not enough currency"
    end
    
    -- Deduct currency
    playerData.EventCurrency[eventId] = playerData.EventCurrency[eventId] - item.Cost
    
    -- Award item
    GiveItem(player, itemId)
    
    SavePlayerData(player)
    return true
end
```

### 8.2 Event Notification System

```lua
function NotificationService:AnnounceEvent(eventId)
    local event = EventData[eventId]
    
    -- Server-wide notification
    for _, player in pairs(game.Players:GetPlayers()) do
        FireClient(player, "ShowEventNotification", {
            Title = event.Name .. " HAS BEGUN!",
            Description = event.Description,
            Icon = event.Icon,
            Duration = 10
        })
    end
    
    -- Set up event spawn systems
    EventSpawnService:InitializeEvent(eventId)
end
```

### 8.3 Leaderboard System

```lua
function LeaderboardService:UpdateEventLeaderboard(eventId, category, player, value)
    local key = eventId .. "_" .. category
    
    -- Store in OrderedDataStore
    EventLeaderboards:SetAsync(player.UserId, value)
    
    -- Update real-time UI for all players
    UpdateLeaderboardUI(eventId, category)
end

function LeaderboardService:GetTopPlayers(eventId, category, count)
    local key = eventId .. "_" .. category
    local pages = EventLeaderboards:GetSortedAsync(false, count)
    
    local topPlayers = {}
    for rank, data in ipairs(pages:GetCurrentPage()) do
        table.insert(topPlayers, {
            Rank = rank,
            UserId = data.key,
            Value = data.value
        })
    end
    
    return topPlayers
end
```

---

## Implementation Checklist

### Phase 1: Foundation (Month 6)
- [ ] Event system framework
- [ ] Event currency system
- [ ] Event shop UI
- [ ] Basic event activities
- [ ] First small event (test run)

### Phase 2: Major Events (Month 7-9)
- [ ] Halloween event (full implementation)
- [ ] Winter event (full implementation)
- [ ] Event-specific dungeons
- [ ] Leaderboard systems

### Phase 3: Recurring Content (Month 10-12)
- [ ] Mini-event rotation system
- [ ] Community challenges
- [ ] Double XP weekends
- [ ] Flash sales

### Phase 4: Live Service (Ongoing)
- [ ] Monthly event calendar
- [ ] Content pipeline (3-month ahead planning)
- [ ] Community feedback integration
- [ ] Seasonal rotations

---

## Related Documentation
- [GDD_Content_Story.md](GDD_Content_Story.md) - Narrative integration
- [GDD_Economy.md](GDD_Economy.md) - Event currency balance
- [GDD_Systems_Trading.md](GDD_Systems_Trading.md) - Event item trading

---

**Document End - Seasonal Events & Live Content**  
*There's always something to celebrate in IRIFA!*
