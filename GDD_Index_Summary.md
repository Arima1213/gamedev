# Game Design Document
## Complete Documentation Index & Quick Reference

---

### Document Information
**Project Name:** IRIFA: Realms of Harvest & Adventure  
**Documentation Version:** 1.0  
**Last Updated:** February 8, 2026  
**Status:** Complete - Ready for Development

---

## Documentation Structure

This Game Design Document consists of multiple specialized files covering all aspects of the game's design and implementation. This index provides quick navigation and summaries of each document.

---

## Core Documentation Files

### 1. [GDD_Main.md](GDD_Main.md) - Main Overview Document
**Purpose:** High-level game vision, design pillars, and project scope  
**Key Sections:**
- Executive Summary
- Game Vision & Core Pillars
- Target Audience & Player Archetypes
- Unique Selling Points
- Development Phases & Timeline
- Success Metrics

**Quick Facts:**
- **Genre:** Multiplayer Sandbox, Life Simulation, RPG
- **Platform:** Roblox
- **Target Age:** 10-18 years
- **Monetization:** Robux (Premium Currency)
- **Development Time:** 12 months to launch

---

## System Documentation Files

### 2. [GDD_Systems_Mining.md](GDD_Systems_Mining.md) - Mining System
**Purpose:** Complete mining mechanics specification  
**Key Sections:**
- Core mining mechanics and tool requirements
- Rock types and durability systems
- Mining tools and rarity progression
- Geode system and loot generation
- Resource yields and drop rates
- Technical implementation details

**Quick Reference:**
- **Location:** Dungeons only
- **Tool Requirement:** Mining pickaxe (mandatory)
- **Rock Sizes:** Small (50 HP) → Massive (500 HP)
- **Tool Rarities:** Common (1.0x) → Special (3.5x speed)
- **Mineral Types:** 12+ types across 7 rarity tiers

---

### 3. [GDD_Systems_Fishing.md](GDD_Systems_Fishing.md) - Fishing System
**Purpose:** Complete fishing mechanics specification  
**Key Sections:**
- Fishing rod system and upgrades
- Location-based fish spawning
- Catch mini-game mechanics
- Fish species catalog (50+ species)
- Weather and time influences
- Treasure chest system

**Quick Reference:**
- **Locations:** Ocean zones (4) + River zones (4)
- **Mini-Game:** Tension bar timing challenge
- **Rod Rarities:** Common → Special (affects catchable fish)
- **Fish Catalog:** 50+ species across all rarity tiers
- **Treasure Rate:** 0.05% - 2% depending on type

---

### 4. [GDD_Systems_Farming.md](GDD_Systems_Farming.md) - Farming System (To be created)
**Purpose:** Agricultural mechanics and crop systems  
**Key Topics:**
- Seed types and rarity tiers
- Crop growth mechanics and timers
- Farm plot expansion system
- Quality system (harvest grades)
- Sprinkler automation
- Seasonal crops and events

**Quick Reference:**
- **Starting Plots:** 2 free plots (5 seeds each)
- **Watering:** Daily requirement (or use sprinkler)
- **Growth Times:** 2-21 days depending on rarity
- **Quality Tiers:** 5 levels (affects sell price)
- **Profit Range:** 25-714 IRF per day per plot

---

### 5. [GDD_Systems_Dungeon.md](GDD_Systems_Dungeon.md) - Dungeon & Combat (To be created)
**Purpose:** Dungeon exploration and monster encounters  
**Key Topics:**
- Dungeon instance system
- Monster AI and spawning
- Combat mechanics and stats
- Boss encounters
- Loot tables and drop rates
- Difficulty scaling

**Quick Reference:**
- **Access:** Unlocked via Guild Master quest
- **Instances:** Support 1-10 players
- **Monster Rarities:** Common → Special
- **Boss Types:** Normal, Elite, Event
- **Rewards:** Materials, IRF, Equipment

---

### 6. [GDD_Systems_Taming.md](GDD_Systems_Taming.md) - Creature Taming System (To be created)
**Purpose:** Familiar capture and progression  
**Key Topics:**
- Taming mechanics and success rates
- Familiar types (Active vs Passive)
- Leveling and evolution
- Buff systems
- Familiar catalog and index

**Quick Reference:**
- **Taming Method:** Feed specific items
- **Types:** Active (combat) + Passive (buffs)
- **Max Companions:** 2 active at once
- **Buffs:** Luck, speed, damage, harvest quality
- **Familiar Rarities:** Common → Special

---

### 7. [GDD_Systems_Crafting.md](GDD_Systems_Crafting.md) - Crafting System (To be created)
**Purpose:** Item creation and recipe system  
**Key Topics:**
- NPC crafting stations
- Recipe discovery system
- Material requirements
- Enhancement system
- Cost scaling by rarity

**Quick Reference:**
- **NPCs:** Blacksmith, Fisherman, Farmer, Workshop
- **Recipe Types:** Equipment, Tools, Decorations
- **Material Tiers:** Match output rarity
- **Enhancements:** +1 to +5 levels
- **Costs:** 100 IRF (Common) → 50,000 IRF (Mythic)

---

### 8. [GDD_Systems_PrivateIsland.md](GDD_Systems_PrivateIsland.md) - Private Island System (To be created)
**Purpose:** Player housing and customization  
**Key Topics:**
- Island expansion mechanics
- Farm plot placement
- Decoration system
- Familiar habitat
- Aesthetic scoring
- Visitor system

**Quick Reference:**
- **Starting Size:** Small (expandable)
- **Expansion Cost:** 20,000 IRF or 300 Robux (first tier)
- **Farm Plots:** 2 starter, expandable to 7+
- **Decorations:** 100+ items available
- **Visitors:** Other players can tour islands

---

### 9. [GDD_Systems_Trading.md](GDD_Systems_Trading.md) - Trading Systems (To be created)
**Purpose:** Player economy and marketplace  
**Key Topics:**
- Player-to-player direct trading
- Global Trading Board system
- Listing and fee structure
- Trade limits and security
- Market monitoring tools

**Quick Reference:**
- **Direct Trade:** 5 items + IRF, no fees
- **Trading Board:** 10% sale fee
- **Free Slots:** 3 listings, expandable
- **Listing Duration:** 15 days
- **Withdrawal Limit:** 50,000 IRF/day (expandable)

---

## Supporting Documentation Files

### 10. [GDD_Economy.md](GDD_Economy.md) - Economy & Currency
**Purpose:** Complete economic design and balance  
**Key Sections:**
- IRIFA (IRF) currency system
- Income sources and rates
- Expenditure sinks
- Price tables and balance
- Monetization strategy (Robux)
- Anti-inflation measures

**Quick Reference:**
- **Currency:** IRIFA (IRF) - Soft currency
- **Early Game Income:** ~5,000 IRF/week
- **Mid Game Income:** ~50,000 IRF/month
- **End Game Income:** 500,000+ IRF/month
- **Trading Board Fee:** 10% of sale price
- **NPC Buy Rate:** 50% of market value

---

### 11. [GDD_Technical_Specs.md](GDD_Technical_Specs.md) - Technical Implementation
**Purpose:** Roblox-specific technical guidelines  
**Key Sections:**
- Platform requirements
- Architecture overview
- Data management (DataStore)
- Networking and multiplayer
- Performance optimization
- Security and anti-exploit
- Module structure
- Development guidelines

**Quick Reference:**
- **Target FPS:** 55-60 server, 60 client
- **Max Parts:** <10,000 per area
- **DataStore Calls:** <60/minute
- **Architecture:** Client-Server with Remote Events
- **Security:** Server-side validation for all actions
- **Instancing:** Support up to 50 dungeons/server

---

### 12. [GDD_UI_UX.md](GDD_UI_UX.md) - UI/UX Design Guidelines
**Purpose:** User interface and experience standards  
**Key Sections:**
- Design philosophy and principles
- Visual style guide (colors, typography)
- HUD system layouts
- Menu systems and navigation
- Interaction patterns
- Accessibility features
- Mobile optimization
- Animation guidelines

**Quick Reference:**
- **Color Palette:** Brand Blue #3498DB, Rarity-coded
- **Font:** GothamSSm (Roblox standard)
- **Button Sizes:** Min 44×44px (touch-friendly)
- **Animations:** 0.1s-0.5s transitions
- **Accessibility:** WCAG AA compliance
- **Mobile:** Portrait + Landscape support

---

## Additional Documentation (To Be Created)

### 13. GDD_Content_NPCs.md - NPC Characters & Dialogues
**Topics:**
- NPC character designs
- Dialogue trees
- Quest givers
- Vendor inventories
- Personality and voice

### 14. GDD_Content_Story.md - Main Story & Quests
**Topics:**
- Tutorial quest line
- NPC story arcs
- Side quests
- Achievement system
- Lore and world-building

### 15. GDD_Content_Events.md - Seasonal Events
**Topics:**
- Seasonal event calendar
- Event-exclusive content
- Limited-time items
- Boss encounters
- Rewards and progression

### 16. GDD_Rarity_System.md - Rarity & Grade Definitions
**Topics:**
- Universal rarity tiers
- Drop rate formulas
- Color coding standards
- Visual effects by rarity
- Balance considerations

### 17. GDD_Luck_System.md - Luck Mechanics
**Topics:**
- Luck calculation formulas
- Buff sources and stacking
- Diminishing returns
- Server-wide boosters
- Balance and limits

### 18. GDD_Progression.md - Player Progression
**Topics:**
- Level system
- Experience curves
- Milestone unlocks
- Quest progression
- Endgame content

### 19. GDD_Balance_Sheet.md - Balance Calculations
**Topics:**
- Damage formulas
- Resource generation rates
- Time-to-progression metrics
- Economic equilibrium
- Playtesting results

---

## Quick Reference Tables

### Rarity Tier Overview
| Rarity | Color | Drop Rate Range | Visual Effect |
|--------|-------|-----------------|---------------|
| Common | Grey | 30-50% | None |
| Rare | Blue | 15-25% | Subtle glow |
| Epic | Purple | 5-10% | Medium glow |
| Legendary | Gold | 1-3% | Bright glow + particles |
| Mythic | Red | 0.3-1% | Intense glow + aura |
| Special | Rainbow | 0.1-0.5% | Rainbow shimmer + trail |
| Event | Cyan | Event-only | Unique themed effects |

### Currency Conversion Reference
| Activity | Time Investment | IRF Earned | IRF/Hour |
|----------|-----------------|------------|----------|
| Mining (Beginner) | 1 hour | 300 IRF | 300 |
| Mining (Expert) | 1 hour | 8,000 IRF | 8,000 |
| Fishing (Beginner) | 1 hour | 200 IRF | 200 |
| Fishing (Expert) | 1 hour | 10,000 IRF | 10,000 |
| Farming (Passive) | 24 hours | 500 IRF | 21/hr |
| Dungeon Boss | 20 minutes | 15,000 IRF | 45,000 |
| Trading (Active) | 1 hour | 5,000-15,000 IRF | 10,000 avg |

### Development Priority Levels
| System | Priority | Phase | Complexity |
|--------|----------|-------|------------|
| Data Management | Critical | Phase 1 | High |
| Mining System | High | Phase 1 | Medium |
| Fishing System | High | Phase 1 | Medium |
| Farming System | High | Phase 1 | Medium |
| Inventory System | Critical | Phase 1 | Medium |
| Combat System | High | Phase 2 | High |
| Dungeon System | High | Phase 2 | High |
| Crafting System | High | Phase 2 | Medium |
| Taming System | Medium | Phase 3 | Medium |
| Trading System | High | Phase 3 | High |
| Private Island | Medium | Phase 3 | High |
| Events System | Low | Phase 4 | Low |

---

## Implementation Timeline

### Phase 1: Foundation (Months 1-3)
**Goal:** Core systems functional, playable prototype

**Deliverables:**
- ✅ Town hub environment (explorable)
- ✅ Basic private island (farm plots)
- ✅ Fishing system (complete with mini-game)
- ✅ Farming system (planting, watering, harvesting)
- ✅ Mining system (basic rock mining)
- ✅ Storage system (inventory management)
- ✅ NPC interactions (basic dialogues)
- ✅ Tutorial quest line

**Milestone:** Vertical slice demonstrating core gameplay loop

---

### Phase 2: Combat & Exploration (Months 4-6)
**Goal:** Dungeon content, combat depth

**Deliverables:**
- ✅ Dungeon environment (instanced)
- ✅ Combat system (complete mechanics)
- ✅ Monster AI and spawning
- ✅ Crafting system (weapons, tools, equipment)
- ✅ Equipment stats and effects
- ✅ Basic boss encounters (3 bosses)
- ✅ Guild system foundation

**Milestone:** Full combat loop with progression

---

### Phase 3: Social & Economy (Months 7-9)
**Goal:** Player interaction and trading

**Deliverables:**
- ✅ Player-to-player trading
- ✅ Global Trading Board (full marketplace)
- ✅ Creature taming system
- ✅ Familiar mechanics (active & passive)
- ✅ Enhanced private island features
- ✅ Decoration system
- ✅ Weather system integration

**Milestone:** Social features and economy functional

---

### Phase 4: Polish & Content (Months 10-12)
**Goal:** Launch-ready quality and content

**Deliverables:**
- ✅ First seasonal event
- ✅ Advanced crafting recipes (100+ recipes)
- ✅ Boss dungeon content (10+ bosses)
- ✅ Leaderboard systems
- ✅ Performance optimization
- ✅ Balance adjustments (playtesting feedback)
- ✅ Quality of life features
- ✅ Tutorial improvements

**Milestone:** Soft launch, beta testing

---

### Phase 5: Live Service (Month 13+)
**Goal:** Ongoing content and community engagement

**Cadence:**
- Bi-weekly updates (bug fixes, minor features)
- Monthly content drops (new fish, creatures, items)
- Quarterly major updates (new zones, systems, events)
- Seasonal events (4 major events per year)

---

## Contact & Collaboration

### Document Owners
- **Lead Designer:** [Name] - Game Vision, Systems Design
- **Technical Lead:** [Name] - Architecture, Performance
- **UI/UX Designer:** [Name] - Interface, User Experience
- **Economy Designer:** [Name] - Balance, Monetization
- **Content Designer:** [Name] - NPCs, Quests, Story

### Version Control
- **Repository:** [Git Repository URL]
- **Documentation:** Google Docs (live collaboration)
- **Assets:** [Asset Management System]
- **Builds:** [Build Server URL]

### Feedback & Revisions
- **Review Meetings:** Weekly design reviews (Fridays)
- **Playtesting:** Bi-weekly internal tests
- **Document Updates:** Continuous (notify team of major changes)
- **Version Numbering:** [Major].[Minor].[Patch]

---

## Glossary of Terms

**IRIFA (IRF):** In-game soft currency, earned through gameplay  
**Robux:** Roblox premium currency, purchased with real money  
**Rarity:** Tier system (Common → Special) indicating item value/difficulty  
**Luck:** Stat influencing drop rates and rare spawns  
**Familiar:** Tameable creature companion providing buffs  
**Instance:** Private dungeon copy for individual/group  
**NPC:** Non-Player Character (quest givers, vendors)  
**Private Island:** Player's personal home/farming space  
**Trading Board:** Global marketplace for item listings  
**Geode:** Sealed rock containing random minerals  
**Enhancement:** Permanent upgrade to tools/equipment  
**IRF Sink:** Mechanic that removes currency from economy  
**LOD:** Level of Detail (performance optimization)  
**DataStore:** Roblox's player data persistence system

---

## Change Log

### Version 1.0 (February 8, 2026)
- Initial complete documentation package
- All core system specifications finalized
- Technical architecture defined
- Economy and balance frameworks established
- UI/UX guidelines completed
- Ready for development kickoff

### Planned Updates
- v1.1: Farming system detailed specification
- v1.2: Dungeon and combat deep-dive
- v1.3: Taming system complete
- v1.4: NPC and story content
- v1.5: Event system framework

---

## Final Notes

This GDD represents a comprehensive blueprint for **IRIFA: Realms of Harvest & Adventure**. All systems are designed to be:

✅ **Interconnected:** Every system feeds into and supports others  
✅ **Balanced:** Fair progression for free and premium players  
✅ **Scalable:** Architecture supports future content expansions  
✅ **Engaging:** Multiple gameplay loops cater to different player types  
✅ **Monetizable:** Ethical premium offerings without pay-to-win

The documentation is **living** - it will evolve based on playtesting, technical constraints, and community feedback. Regular reviews and updates ensure alignment between vision and implementation.

**Next Steps:**
1. Full team review of all documentation
2. Technical feasibility assessment
3. Asset production planning
4. Prototype development (Phase 1)
5. Alpha testing and iteration

---

**Ready to begin development. Good luck, team! 🎮**

---

*For questions or clarifications, refer to specific system documents or contact the document owners listed above.*
