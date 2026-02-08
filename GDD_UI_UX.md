# Game Design Document
## UI/UX Design Guidelines

---

### Document Information
**System Name:** User Interface & User Experience  
**Document Version:** 1.0  
**Last Updated:** February 8, 2026  
**Owner:** UI/UX Design Team  
**Status:** Ready for Implementation

---

## Table of Contents
1. [Design Philosophy](#design-philosophy)
2. [Visual Style Guide](#visual-style-guide)
3. [HUD System](#hud-system)
4. [Menu Systems](#menu-systems)
5. [Interaction Patterns](#interaction-patterns)
6. [Accessibility](#accessibility)
7. [Mobile Optimization](#mobile-optimization)
8. [Animation Guidelines](#animation-guidelines)

---

## 1. Design Philosophy

### 1.1 Core Principles

**1. Clarity Over Complexity**
- Information should be immediately understandable
- Avoid cluttered interfaces
- Use iconography consistently
- Clear visual hierarchy

**2. Intuitive Navigation**
- Common patterns users expect
- Minimal clicks to key features
- Breadcrumb navigation where appropriate
- Logical menu organization

**3. Responsive Feedback**
- Every action gets immediate feedback
- Visual, audio, and haptic confirmation
- Loading states clearly communicated
- Error messages are helpful, not punishing

**4. Scalable Design**
- Works on all screen sizes (PC, tablet, mobile)
- Text is readable at minimum supported resolution
- Touch-friendly targets (minimum 44px)
- Adjustable UI scale in settings

**5. Immersive Integration**
- UI doesn't break immersion
- Diegetic elements where possible
- Smooth transitions
- Context-aware displays

### 1.2 Target User Flow

**New Player:**
```
Launch → Tutorial Popups → Guided Actions → Success Feedback → 
Next Step Prompt → Gradual Feature Unlocks → Confidence Building
```

**Returning Player:**
```
Launch → Quick Status Check (HUD) → Direct to Desired Activity → 
Unobtrusive Notifications → Efficient Workflows → Minimal Friction
```

---

## 2. Visual Style Guide

### 2.1 Color Palette

**Primary Colors:**
```
Brand Blue: #3498DB (Primary actions, headers)
Success Green: #2ECC71 (Confirmations, success states)
Warning Orange: #E67E22 (Cautions, warnings)
Error Red: #E74C3C (Errors, critical alerts)
```

**Rarity Colors:**
```
Common: #9E9E9E (Grey)
Rare: #2196F3 (Blue)
Epic: #9C27B0 (Purple)
Legendary: #FFD700 (Gold)
Mythic: #F44336 (Red/Crimson)
Special: Rainbow Gradient
Event: #00BCD4 (Cyan)
```

**Background Colors:**
```
Primary BG: #2C3E50 (Dark blue-grey)
Secondary BG: #34495E (Lighter blue-grey)
Panel BG: #FFFFFF with 80% opacity (Semi-transparent white)
Overlay BG: #000000 with 50% opacity (Semi-transparent black)
```

**Text Colors:**
```
Primary Text: #FFFFFF (White)
Secondary Text: #BDC3C7 (Light grey)
Disabled Text: #7F8C8D (Grey)
Link Text: #3498DB (Blue, same as brand)
```

### 2.2 Typography

**Font Family:**
- Primary: GothamSSm (Roblox standard, clean sans-serif)
- Fallback: SourceSansPro

**Font Sizes:**
```
Heading 1: 32px (Bold) - Major section titles
Heading 2: 24px (Bold) - Sub-section titles
Heading 3: 18px (SemiBold) - Card headers
Body: 14px (Regular) - Standard text
Small: 12px (Regular) - Metadata, timestamps
Tiny: 10px (Regular) - Footnotes, disclaimers
```

**Text Hierarchy:**
```
╔════════════════════════════════════╗
║  INVENTORY (H1, 32px)              ║ 
╠════════════════════════════════════╣
║                                    ║
║  Tools & Equipment (H2, 24px)      ║
║  ─────────────────────────────     ║
║  [Icon] Epic Pickaxe (H3, 18px)    ║
║         Mining Speed: +50%         ║
║         (Body, 14px)               ║
║         Durability: 850/1000       ║
║         (Small, 12px)              ║
╚════════════════════════════════════╝
```

### 2.3 Iconography

**Icon Style:**
- Line style: 2px stroke weight
- Style: Rounded corners, friendly appearance
- Size: 32×32px (standard), 64×64px (large), 24×24px (small)
- Colors: Flat design with rarity color accents

**Standard Icons:**
```
⚒️ Pickaxe - Mining
🎣 Rod - Fishing
🌾 Wheat - Farming
⚔️ Sword - Combat
🐾 Paw - Familiars
🏠 House - Private Island
💰 Coin - Currency (IRF)
💎 Diamond - Premium (Robux)
⚙️ Gear - Settings
📊 Chart - Statistics
📖 Book - Quests
👥 People - Trading
🎒 Backpack - Inventory
```

---

## 3. HUD System

### 3.1 Main HUD Layout

```
╔════════════════════════════════════════════════════╗
║ [HP: ▓▓▓▓▓▓▓▓░░ 1650/2000]  [📍Town Hub]  [☀️Day]║
║ [IRF: 12,345]                         [Lv.15][⚔️] ║
╠════════════════════════════════════════════════════╣
║                                                    ║
║                  [GAMEPLAY AREA]                   ║
║                                                    ║
║  [Mini-Map]                                        ║
║  ┌────────┐                                        ║
║  │ ○   🗺️ │                                        ║
║  │  ●     │                                        ║
║  │    □   │                                        ║
║  └────────┘                                        ║
║                                                    ║
║                                                    ║
║                                                    ║
║                                                    ║
╠════════════════════════════════════════════════════╣
║ [Hotbar: 1⚔️ 2⚒️ 3🎣 4🍞 5💊]                       ║
║                                                    ║
║ [Notifications]        [Quick Actions: E, Q, F]    ║
╚════════════════════════════════════════════════════╝
```

**Top Bar (Always Visible):**
- Health bar (left)
- Location indicator (center)
- Time/Weather (center-right)
- Currency (IRF) (left-bottom)
- Level indicator (right)
- Current tool equipped (right)

**Bottom Bar:**
- Hotbar (quick-access items/tools)
- Active keybinds
- Notifications/alerts

**Side Elements:**
- Mini-map (top-right)
- Quest tracker (right)
- Buff/debuff indicators (below HP)

### 3.2 Context-Specific HUD

**Mining Mode:**
```
┌─────────────────────────────────────┐
│  [Rock Durability]                  │
│  ▓▓▓▓▓▓▓▓▓░░░░░░░░░ 245/300        │
│                                     │
│  [Tool Durability]                  │
│  ⚒️ 847/1000                        │
│                                     │
│  [Hold E to Mine]                   │
└─────────────────────────────────────┘
```

**Fishing Mode:**
```
┌─────────────────────────────────────┐
│  🎣 Waiting for bite...              │
│                                     │
│  Rod: Legendary Rod                 │
│  Location: Deep Sea Port            │
│  Weather: Clear ☀️                  │
└─────────────────────────────────────┘
```

**Combat Mode:**
```
┌─────────────────────────────────────┐
│  ENEMY: Forest Wolf (Rare)          │
│  ▓▓▓▓▓▓░░░░░░░░░ 350/500 HP        │
│                                     │
│  [⚔️ Attack] [🛡️ Block] [⚡ Skill]  │
└─────────────────────────────────────┘
```

### 3.3 Notification System

**Notification Types:**

```
┌─────────────────────────────────────┐
│ ✓ Quest Completed!                  │
│   "Catch 10 Fish"                   │
│   Reward: 100 IRF                   │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ 🌟 Rare Item Obtained!              │
│   [Icon] Diamond × 1                │
│   Value: 500 IRF                    │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ ⚠️ Warning                          │
│   Tool durability low (20/1000)    │
│   Visit Blacksmith to repair        │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ ❌ Error                            │
│   Cannot mine: No tool equipped     │
└─────────────────────────────────────┘
```

**Notification Behavior:**
- Appear top-right, stack vertically
- Auto-dismiss after 5 seconds (adjustable)
- Can be manually dismissed (X button)
- Click notification for more details
- Queue max 5 notifications (older dismissed)

---

## 4. Menu Systems

### 4.1 Main Menu (ESC)

```
╔════════════════════════════════════════════╗
║                                            ║
║         IRIFA: Realms of Adventure         ║
║                                            ║
║  ┌────────────────────────────────────┐   ║
║  │  [📖] Quest Log                    │   ║
║  │  [🎒] Inventory                    │   ║
║  │  [⚒️] Crafting                     │   ║
║  │  [👥] Trading                      │   ║
║  │  [🏠] Private Island               │   ║
║  │  [📊] Statistics                   │   ║
║  │  [⚙️] Settings                     │   ║
║  │  [❓] Help                         │   ║
║  │  [🚪] Exit Game                    │   ║
║  └────────────────────────────────────┘   ║
║                                            ║
║  [Resume Game]                             ║
╚════════════════════════════════════════════╝
```

### 4.2 Inventory System

```
╔════════════════════════════════════════════════════╗
║  INVENTORY                               [X Close] ║
╠════════════════════════════════════════════════════╣
║                                                    ║
║  [Filter: All ▼] [Search: _______] [Sort: Name ▼]║
║                                                    ║
║  ┌────┬────┬────┬────┬────┬────┬────┬────┬────┐  ║
║  │Iron│Cop-│Dia-│    │    │    │    │    │    │  ║
║  │×50 │per │mond│    │    │    │    │    │    │  ║
║  │    │×32 │×1  │    │    │    │    │    │    │  ║
║  ├────┼────┼────┼────┼────┼────┼────┼────┼────┤  ║
║  │Pike│Rare│    │    │    │    │    │    │    │  ║
║  │    │Rod │    │    │    │    │    │    │    │  ║
║  │    │    │    │    │    │    │    │    │    │  ║
║  ├────┼────┼────┼────┼────┼────┼────┼────┼────┤  ║
║  │    │    │    │    │    │    │    │    │    │  ║
║  │    │    │    │    │    │    │    │    │    │  ║
║  │    │    │    │    │    │    │    │    │    │  ║
║  └────┴────┴────┴────┴────┴────┴────┴────┴────┘  ║
║                                                    ║
║  Capacity: 15/50                                   ║
║  [Expand Storage] 2,000 IRF or 50 Robux           ║
║                                                    ║
║  ┌────────────────────────────────────────────┐   ║
║  │ SELECTED: Diamond                          │   ║
║  │ Rarity: Legendary                          │   ║
║  │ Value: 500 IRF                             │   ║
║  │ Description: A rare precious gem           │   ║
║  │                                            │   ║
║  │ [Use] [Drop] [Trade] [Sell to NPC]        │   ║
║  └────────────────────────────────────────────┘   ║
╚════════════════════════════════════════════════════╝
```

**Inventory Features:**
- Grid-based layout
- Drag-and-drop support
- Context menu (right-click)
- Filtering by category
- Search functionality
- Sort options (name, rarity, quantity, value)
- Quick-stack similar items
- Mass-sell options

### 4.3 Crafting Interface

```
╔════════════════════════════════════════════════════╗
║  BLACKSMITH CRAFTING                     [X Close] ║
╠════════════════════════════════════════════════════╣
║                                                    ║
║  RECIPES:          │  SELECTED RECIPE:             ║
║  ─────────         │  ──────────────               ║
║  Weapons           │  [Icon] Epic Sword            ║
║   ⚔️ Common Sword  │                               ║
║   ⚔️ Rare Sword    │  Requirements:                ║
║   ⚔️ Epic Sword ✓  │   [✓] 30× Iron Ore (50/30)   ║
║   ⚔️ Legendary... │   [✓] 25× Silver Ore (30/25) ║
║                    │   [✓] 15× Amethyst (20/15)   ║
║  Tools             │   [✗] 10× Monster Scales      ║
║   ⚒️ Common Pickaxe│        (5/10) - NEED 5 MORE  ║
║   ⚒️ Rare Pickaxe  │   [✓] 2,000 IRF (12,345 IRF) ║
║   ⚒️ Epic Pickaxe  │                               ║
║                    │  Crafting Time: Instant       ║
║  Armor             │                               ║
║   🛡️ ...           │  [CRAFT] (Disabled - Missing  ║
║                    │   materials)                  ║
║                    │                               ║
║                    │  Stats Preview:               ║
║                    │   Attack Damage: +150         ║
║                    │   Attack Speed: 1.2x          ║
║                    │   Critical Chance: +8%        ║
║                    │   Special Effect: None        ║
╚════════════════════════════════════════════════════╝
```

### 4.4 Trading Window

**Player-to-Player Trade:**
```
╔════════════════════════════════════════════════════╗
║  TRADING WITH: PlayerName123             [X Close] ║
╠════════════════════════════════════════════════════╣
║                                                    ║
║  YOUR OFFER:                THEIR OFFER:           ║
║  ┌────────────────┐         ┌────────────────┐    ║
║  │ [Diamond ×5]   │         │ [Epic Sword]   │    ║
║  │                │         │                │    ║
║  │ [Empty]        │         │ [Empty]        │    ║
║  │                │         │                │    ║
║  │ [Empty]        │         │ [Empty]        │    ║
║  │                │         │                │    ║
║  │ [Add Item]     │         │ [Waiting...]   │    ║
║  └────────────────┘         └────────────────┘    ║
║                                                    ║
║  IRF Amount:                IRF Amount:            ║
║  [1,000]                    [500]                  ║
║                                                    ║
║  Trade Value: ~2,500 IRF    Trade Value: ~5,500   ║
║                                                    ║
║  [✗ NOT READY]              [✓ READY]             ║
║                                                    ║
║  [CONFIRM TRADE] (Disabled - Both must be ready)  ║
║  [CANCEL TRADE]                                    ║
╚════════════════════════════════════════════════════╝
```

---

## 5. Interaction Patterns

### 5.1 Button States

**Primary Button:**
```
Normal:    [   CONFIRM   ]  (Brand Blue background)
Hover:     [   CONFIRM   ]  (Lighter Blue, +glow effect)
Pressed:   [   CONFIRM   ]  (Darker Blue, -2px offset)
Disabled:  [   CONFIRM   ]  (Grey, 50% opacity)
Loading:   [ ● CONFIRM   ]  (Spinner animation)
```

**Secondary Button:**
```
Normal:    [   CANCEL    ]  (Grey outline, transparent)
Hover:     [   CANCEL    ]  (Grey filled, +glow)
Pressed:   [   CANCEL    ]  (Darker grey)
Disabled:  [   CANCEL    ]  (Lighter grey, 50% opacity)
```

### 5.2 Input Fields

```
┌─────────────────────────────────────┐
│ Label:                              │
│ [Enter text here...             ]   │
│ Helper text or error message        │
└─────────────────────────────────────┘

States:
- Default: Grey border
- Focus: Blue border, +glow
- Error: Red border, error text below
- Disabled: Light grey, 50% opacity
- Success: Green border (after validation)
```

### 5.3 Confirmation Dialogs

```
╔════════════════════════════════════════════╗
║  ⚠️ CONFIRMATION REQUIRED                  ║
╠════════════════════════════════════════════╣
║                                            ║
║  Are you sure you want to sell this item?  ║
║                                            ║
║  [Icon] Epic Sword                         ║
║  Sell Price: 2,500 IRF                     ║
║                                            ║
║  This action cannot be undone.             ║
║                                            ║
║  [CONFIRM]           [CANCEL]              ║
╚════════════════════════════════════════════╝
```

---

## 6. Accessibility

### 6.1 Text Readability

- Minimum font size: 12px
- High contrast ratios (WCAG AA: 4.5:1)
- Text outlines on semi-transparent backgrounds
- Option to increase UI scale (80%-150%)

### 6.2 Color Blindness Support

- Not relying solely on color for information
- Icons accompany color coding
- Patterns/textures for rarity (in addition to color)
- Colorblind mode options (deuteranopia, protanopia, tritanopia)

### 6.3 Keyboard/Controller Support

**PC Keyboard:**
- Tab navigation through UI elements
- Enter to confirm
- ESC to cancel/close
- Arrow keys for menu navigation
- Number keys for hotbar

**Xbox Controller:**
- A to confirm
- B to cancel
- D-pad for navigation
- Bumpers for tab switching
- Y for quick actions

**PlayStation Controller:**
- X/Cross to confirm
- O/Circle to cancel
- D-pad navigation
- L1/R1 for tabs
- Triangle for quick actions

### 6.4 Screen Reader Support (Future)

- Alt text for all images
- Semantic HTML structure
- ARIA labels where applicable
- Announced state changes

---

## 7. Mobile Optimization

### 7.1 Touch Controls

**Touch Zones:**
- Minimum 44×44px touch targets
- Adequate spacing between buttons (8px minimum)
- Larger icons for primary actions
- Swipe gestures for menu navigation

**Virtual Joystick:**
```
┌────────────────────────────────────────┐
│                                        │
│   [🎮 Left Stick]                      │
│   (Movement)                           │
│                                        │
│                                        │
│                              [A] Attack│
│                         [B] Special    │
│                    [C] Jump            │
└────────────────────────────────────────┘
```

### 7.2 Responsive Layouts

**Portrait Mode:**
- Vertical stacking of UI elements
- Bottom-anchored controls
- Simplified HUD (hide non-essential)

**Landscape Mode:**
- Horizontal layout
- Side-by-side menus
- Full HUD display

### 7.3 Performance Considerations

- Reduced particle effects on mobile
- Lower resolution textures
- Simplified shaders
- 30 FPS target (vs 60 FPS PC)

---

## 8. Animation Guidelines

### 8.1 Transition Timing

**Standard Transitions:**
```
Fast: 0.1s (Hover states, instant feedback)
Normal: 0.3s (Menu opens, panel slides)
Slow: 0.5s (Large modals, full-screen transitions)
```

**Easing Functions:**
- QuadOut: Menu opens, panels slide in
- QuadIn: Menu closes, panels slide out
- ElasticOut: Bouncy effects (notifications, rewards)
- ExpoOut: Dramatic reveals (rare items)

### 8.2 Micro-Interactions

**Button Press:**
1. Scale down to 95% (0.05s)
2. Scale back to 100% (0.1s)
3. Ripple effect from click point

**Item Pickup:**
1. Item flies from world to inventory icon (0.5s)
2. Inventory icon pulses (0.2s)
3. Notification appears (0.3s fade-in)

**Level Up:**
1. Screen flash (0.1s white)
2. Particles burst from player (1s)
3. Level up banner slides in (0.5s)
4. Stat increase numbers animate (1s)
5. Banner fades out (0.5s)

### 8.3 Loading States

**Spinner:**
```
● ○ ○ ○ ○ ○ ○ ○  (Frame 1)
○ ● ○ ○ ○ ○ ○ ○  (Frame 2)
○ ○ ● ○ ○ ○ ○ ○  (Frame 3)
... (rotation at 0.1s per frame)
```

**Progress Bar:**
```
[▓▓▓▓▓▓▓░░░░░░░░] 45%
(Smooth fill animation, duration based on task)
```

**Skeleton Screens:**
- Use for loading lists/content
- Animated shimmer effect
- Placeholder shapes match final content

---

## Implementation Checklist

### Phase 1: Core UI
- [ ] HUD system (HP, currency, level)
- [ ] Inventory interface
- [ ] Notification system
- [ ] Button component library
- [ ] Menu navigation framework

### Phase 2: System UIs
- [ ] Crafting interface
- [ ] Trading windows
- [ ] Quest log
- [ ] Statistics/index screens
- [ ] Settings menu

### Phase 3: Context UIs
- [ ] Mining interface
- [ ] Fishing interface
- [ ] Combat HUD
- [ ] Farming UI
- [ ] Private island editor

### Phase 4: Polish
- [ ] Animations and transitions
- [ ] Sound effects for UI interactions
- [ ] Mobile optimization
- [ ] Accessibility features
- [ ] A/B testing different layouts

---

**UI/UX Design - End of Document**

*For technical implementation, refer to [GDD_Technical_Specs.md](GDD_Technical_Specs.md)*
