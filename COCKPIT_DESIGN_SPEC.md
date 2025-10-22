# Harbinger - Cockpit Pixel Art Design Specification

**Version:** 1.0
**Target Resolution:** 320x224 (SNES native) upscaled to iOS devices
**Color Depth:** 16-64 colors total
**Software:** Aseprite (recommended)
**Art Style:** Industrial retro sci-fi, "used future" aesthetic

---

## 1. Overall Layout

### Screen Composition

```
┌─────────────────────────────────────────────────┐
│  ┌─────────────────────────────────────────┐   │
│  │                                         │   │
│ ┌┤                                         ├┐  │
│ ││                                         ││  │
│ ││         3D FLIGHT VIEW WINDOW           ││  │
│ ││          (Low-poly 3D area)             ││  │
│ ││          160x140 center area            ││  │
│ ││                                         ││  │
│ └┤                                         ├┘  │
│  └─────────────────────────────────────────┘   │
│                                                 │
│  [GAUGES]    [CONSOLE BOTTOM]    [RADAR/HUD]   │
└─────────────────────────────────────────────────┘
```

### Frame Breakdown (320x224 pixels)

**Top Cockpit Frame:** 0-40 pixels from top
- Window frame top edge
- Emergency lights (left/right corners)
- Structural rivets

**Left Side Panel:** 0-60 pixels from left
- Instrument cluster
- Gauges (fuel, speed, temperature)
- Warning lights
- Damage schematic (lower left)

**Right Side Panel:** 260-320 pixels from right
- Radar scope (circular, top right)
- Threat proximity meter
- System status indicators
- Communications panel

**Bottom Console:** 0-50 pixels from bottom
- Control panel switches
- Text readout displays
- Thruster indicators
- Manual override handles

**3D Window:** Center area approximately 160x140 pixels
- Clear view for low-poly 3D rendering
- Slightly rounded corners for realism
- Subtle dirty glass overlay (optional layer)

---

## 2. Color Palette

### Primary Cockpit Palette (16 colors)

#### Structural Colors (6 colors)
```
#000000  Black           - Deep shadows, space view
#1a1a1a  Dark Gray       - Metal shadows
#2d2d2d  Medium Gray     - Panel surfaces
#4a4a4a  Light Gray      - Highlighted edges
#6b6b6b  Silver          - Rivets, metal details
#8a8a8a  Bright Silver   - Reflective highlights
```

#### UI/Display Colors (6 colors)
```
#00ff00  Bright Green    - Active systems, radar
#00aa00  Medium Green    - Gauge needles, text
#005500  Dark Green      - Screen backgrounds
#ffaa00  Amber/Orange    - Warnings, caution lights
#ff0000  Red             - Alerts, damage indicators
#ffffff  White           - Critical text, highlights
```

#### Accent Colors (4 colors)
```
#0088ff  Cyan/Blue       - Secondary displays
#220033  Deep Purple     - Alien energy indicators
#4a3020  Brown           - Worn surfaces, rust
#ffff88  Pale Yellow     - Backlit buttons
```

### Alternate Damaged State Palette
When ship takes damage, shift palette:
- Greens become dimmer (#00aa00 → #005500)
- Add flickering by alternating palettes per frame
- Red lights pulse (animate between #ff0000 and #aa0000)

---

## 3. Detailed Component Specifications

### 3.1 Left Side Panel (60x224 pixels)

#### Fuel Gauge (Top Left, 12x12 at position 8,8)
```
┌──────────┐
│    /\    │  ← Needle rotates 180° (full to empty)
│   /  \   │
│  /    \  │
│ /  F E \ │  F = Full, E = Empty
└──────────┘
```
**Design Notes:**
- Circular gauge with white tick marks (8 divisions)
- Green needle when > 50% fuel
- Amber needle when 25-50% fuel
- Red needle when < 25% fuel
- "FUEL" label below in 3x5 pixel font
- 3-frame animation for needle movement

#### Speed Gauge (Below fuel, 12x12 at position 8,28)
```
┌──────────┐
│  0 ──→ 9 │  Numbers 0-9 (arbitrary units)
│    /\    │  Needle points to current speed
│   /  \   │
└──────────┘
```
**Design Notes:**
- Horizontal arc gauge
- Green needle
- "VELOCITY" label (tiny 3x5 font)

#### Temperature Gauge (Below speed, 12x12 at position 8,48)
```
┌──────────┐
│  C  ||  H│  C = Cold, H = Hot
│     ||   │  Vertical bar fill gauge
│     ||   │
│    ████  │  Fills red when overheating
└──────────┘
```
**Design Notes:**
- Vertical bar gauge
- Green (normal) → Amber (warm) → Red (critical)
- "TEMP" label

#### Warning Lights Panel (8x68, 4x4 each light)
```
┌──┐ ┌──┐ ┌──┐
│ 1│ │ 2│ │ 3│  1 = Engine, 2 = Hull, 3 = Systems
└──┘ └──┘ └──┘
┌──┐ ┌──┐ ┌──┐
│ 4│ │ 5│ │ 6│  4 = Landing Gear, 5 = Fuel, 6 = Comms
└──┘ └──┘ └──┘
```
**Design Notes:**
- Each light 4x4 pixels
- Off state: Dark gray (#2d2d2d)
- Caution: Amber (#ffaa00), 2-frame pulse
- Alert: Red (#ff0000), 4-frame rapid pulse
- 2-pixel labels below each

#### Damage Schematic (Bottom Left, 40x40 at position 8,170)
```
    ╔════╗
   ╔╝    ╚╗     Top-down ship schematic
  ╔╝  ▓▓  ╚╗    Red blocks = damaged sections
 ╔╝   ▓▓   ╚╗   8 damage zones
║══════════════║
 ╚╗        ╔╝   Updates in real-time
  ╚╗      ╔╝
   ╚══════╝
```
**Design Notes:**
- Simple ship outline (white lines)
- 8 sections can turn red when damaged
- "HULL" label above
- Percentage text below (e.g., "87%")

---

### 3.2 Right Side Panel (60x224 pixels)

#### Radar Scope (Top Right, 50x50 at position 265,8)
```
        │
    ·   │   ·
  ·     │     ·
─────┼─────┼─────  Rotating sweep line
  ·     │     ·    Green blips = debris/objects
    ·   │   ·      Red blip = threat
        │
```
**Design Notes:**
- Circular radar (50x50 pixels)
- Dark green background (#005500)
- Bright green grid lines (#00ff00)
- Rotating sweep line (8-frame animation, 45° per frame)
- Blips appear as 2x2 pixel dots
- Center crosshair (player position)
- "RADAR" label below

#### Threat Proximity Meter (Below radar, 50x12 at position 265,68)
```
THREAT
├────────────┤
█████░░░░░░░░  ← Horizontal bar (fills red)
```
**Design Notes:**
- Empty: Dark gray background
- Fills left-to-right with red (#ff0000) as threat approaches
- 4-frame pulse animation when > 75% full
- Border flashes white when at 100%

#### System Status Indicators (265,90, 50x80 block)
```
┌─────────────┐
│ ENG [████░] │  Engine power
│ SHD [██░░░] │  Heat shield
│ RCS [█████] │  Reaction control
│ SNR [███░░] │  Sensors
│ LND [█████] │  Landing gear status
└─────────────┘
```
**Design Notes:**
- 5 horizontal bars, each 30x5 pixels
- Labels: 3-letter codes (3x5 font)
- Bars: Green (healthy) → Amber (damaged) → Red (critical)
- Empty sections: Dark gray
- Each bar can flicker independently when damaged

#### Communications Panel (265,180, 50x40)
```
┌─────────────┐
│ ┌─────────┐ │
│ │ MSG 001 │ │  Scrolling text display
│ │MAINTAIN │ │  3x5 pixel font
│ │ALTITUDE │ │  Green terminal text
│ └─────────┘ │
└─────────────┘
```
**Design Notes:**
- Small text window (45x30 pixels inside)
- Green monospace font (#00aa00)
- Scrolls vertically (8 lines visible)
- Message types: Company orders, alerts, coordinates
- Static overlay (2-frame flicker for CRT effect)

---

### 3.3 Bottom Console (320x50 pixels)

#### Control Panel Switches (Left section, 0-100x184-224)
```
┌─┐ ┌─┐ ┌─┐ ┌─┐
│█│ │░│ │█│ │░│  Toggle switches (on/off states)
└─┘ └─┘ └─┘ └─┘
 A   B   C   D    Labels: Auto/Manual/Scan/Gear
```
**Design Notes:**
- 8 switches total across bottom
- Up position (█): Active (bright)
- Down position (░): Inactive (dim)
- 2x4 pixel switches
- 1-pixel labels below (A, B, C, D, etc.)
- Animate on toggle (2-frame flip)

#### Central Text Readout (Center, 110-210x184-224)
```
╔══════════════════╗
║ ALTITUDE: 1247 M ║  2 lines of text
║ VELOCITY: 34 M/S ║  Critical flight data
╚══════════════════╝
```
**Design Notes:**
- 100x40 pixel display area
- Green terminal font (#00ff00)
- 2 lines of scrolling data
- Updates every second
- Border: Light gray (#4a4a4a)
- Display messages:
  - Altitude / Velocity
  - Coordinates
  - System status
  - Mission objectives

#### Thruster Indicators (Right section, 220-320x184-224)
```
    ↑         Direction indicators
  ← ◊ →       Show active thrusters
    ↓         Light up when firing
```
**Design Notes:**
- 5 arrows (up, down, left, right, forward)
- Off: Dark gray (#2d2d2d)
- Active: Bright cyan (#0088ff)
- Each arrow 6x6 pixels
- Center diamond (player ship indicator)
- Labels: "THRUST" above

#### Emergency Handle (Far right, 300-318x190-220)
```
  ┌───┐
  │ ! │  Red emergency handle
  ║   ║  Striped warning pattern
  ║   ║
  └───┘
 EJECT   Label
```
**Design Notes:**
- 18x30 pixel handle
- Red (#ff0000) with amber stripes
- "EJECT" or "ABORT" label
- Glows when mission critical
- Not interactive (visual only)

---

### 3.4 Window Frame Details

#### Top Frame (0-40 pixels from top)
```
╔═══════════════════════════════════╗
║ ◯  USCSS HARBINGER - WY CORP  ◯ ║  Top bar
╠═══════════════════════════════════╣
```
**Design Notes:**
- Riveted metal appearance
- Gray gradient (#2d2d2d → #4a4a4a)
- Ship name centered: "USCSS HARBINGER" (3x5 font)
- Warning lights in corners (◯):
  - Green: Normal operation
  - Amber: Caution
  - Red: Emergency
- Weyland-Yutani logo text (tiny)

#### Side Frame Rivets
```
╔  Rivet pattern down sides
◯  Every 16 pixels vertically
║  2x2 pixel circles
◯  Highlighted top-left (#6b6b6b)
║  Shadowed bottom-right (#1a1a1a)
◯
```

#### Window Scratches/Dirt (Overlay layer)
```
   ·    ·        Random 1-pixel white/gray dots
  ·        ·     Scattered across window
    ·   ·        Subtle, 10-15 total
      ·      ·   Adds "used" feeling
```

---

## 4. Animation Specifications

### 4.1 Idle Animations (Looping)

**Gauge Needles:**
- Slight wobble (±1 pixel) every 30 frames
- Smooth interpolation (not snapped)

**Radar Sweep:**
- 8 frames, 360° rotation
- 45° per frame
- Loop infinitely
- Leaves 4-frame trails on blips

**Warning Lights:**
- Slow pulse: 15 frames on, 15 frames off (caution)
- Fast pulse: 4 frames on, 4 frames off (alert)
- Offset different lights by 5 frames for visual interest

**Screen Flicker:**
- Every 120 frames: 2-frame brightness drop
- Simulates CRT instability
- Only on text displays

**Thruster Indicators:**
- Instant on/off (no fade)
- Add 2-frame "bloom" when activating (white outline)

### 4.2 Damage State Animations

**When Hull Integrity < 50%:**
- All green UI shifts darker
- Random screen static (5x5 pixel blocks appear/disappear)
- Warning lights flash continuously
- Gauges occasionally freeze for 3 frames

**When Critical (< 25%):**
- Full screen red flash every 60 frames
- All text glitches (swap random characters)
- Radar loses blips intermittently
- Sparks (3-pixel white dots) appear randomly on panel edges

**Screen Shake (Turbulence):**
- Entire cockpit layer shifts ±2 pixels X/Y
- Occurs during weather events
- 4-frame shake sequence: (0,0) → (-2,1) → (2,-1) → (0,0)

---

## 5. Layering Structure (Aseprite)

### Layer Order (Bottom to Top)

1. **Background** - Pure black (#000000)
2. **Frame Structure** - Gray metal panels (static)
3. **Gauges Base** - Gauge backgrounds and labels (static)
4. **Gauge Needles** - Animated rotating elements
5. **Lights** - Warning lights and indicators (animated)
6. **Displays** - Text and bar graphs (updated per frame)
7. **Radar** - Separate layer for rotation
8. **Window Frame Overlay** - Scratches and dirt (50% opacity)
9. **Damage Effects** - Sparks, glitches (conditional, top layer)

### Aseprite Project Settings
- Canvas: 320x224 pixels
- Color Mode: Indexed (16-64 colors)
- Frame Duration: 60 FPS (16.67ms per frame) or 30 FPS (33.33ms)
- Export: PNG sprite sheets + JSON metadata

---

## 6. Typography

### Bitmap Fonts Required

#### Primary Font: 3x5 Pixel Font
```
 █ ███ ███ █ █ ███ ███ ███ ███ ███ ███
█  █   █   █ █ █   █   █     █ █ █ █ █
█  ███ ███ ███ ███ ███ ███   █ ███ ███
█  █     █   █   █ █     █   █ █ █   █
 █ ███ ███   █ ███ ███ ███   █ ███ ███
 0   1   2   3   4   5   6   7   8   9
```

#### Labels Font: 3x5 (All caps)
- Letters A-Z in 3x5 grid
- 1-pixel spacing between characters
- Green (#00aa00) for normal text
- Amber (#ffaa00) for warnings
- Red (#ff0000) for alerts

#### Display Font: 5x7 (Optional, larger readouts)
- Use for critical information
- Central text display only
- Green terminal aesthetic

---

## 7. Reference Images to Study

### Inspiration Sources (Research these)

**Movies/Shows:**
- Alien (1979) - Nostromo cockpit panels
- Aliens (1986) - Dropship interior
- 2001: A Space Odyssey - HAL interface panels
- Blade Runner - Retro-future CRT displays

**Games:**
- Star Fox (SNES) - Low-poly 3D + pixel UI
- F-Zero (SNES) - Speed gauges and HUD
- Metroid Prime - Visor HUD elements (simplified)
- Elite Dangerous - Cockpit layout (simplified)

**Real References:**
- Apollo spacecraft instrument panels
- F-16 fighter jet cockpit (simplified)
- Submarine control rooms
- Industrial control panels (1970s-80s)

---

## 8. Implementation Checklist

### Phase 1: Static Frame (Week 1)
- [ ] Create 320x224 Aseprite project
- [ ] Import color palette (16 colors)
- [ ] Draw window frame outline
- [ ] Add rivets and structural details
- [ ] Create left panel background
- [ ] Create right panel background
- [ ] Draw bottom console base

### Phase 2: Gauges (Week 1-2)
- [ ] Fuel gauge background + needle
- [ ] Speed gauge background + needle
- [ ] Temperature gauge background + bar
- [ ] Test needle rotation (3 keyframes)
- [ ] Add gauge labels

### Phase 3: Displays (Week 2)
- [ ] Radar scope circle and grid
- [ ] Threat proximity bar
- [ ] System status bars (5 systems)
- [ ] Communications panel border
- [ ] Central text display box

### Phase 4: Details (Week 2)
- [ ] Warning lights (6 total)
- [ ] Control switches (8 total)
- [ ] Thruster indicators (5 arrows)
- [ ] Emergency handle
- [ ] Damage schematic ship outline

### Phase 5: Animation (Week 3)
- [ ] Radar sweep rotation (8 frames)
- [ ] Gauge needle movement test
- [ ] Warning light pulse animations
- [ ] Screen flicker effect (2 frames)
- [ ] Text scroll test (communications)

### Phase 6: Polish (Week 3)
- [ ] Window scratches overlay
- [ ] Subtle reflections on panels
- [ ] Shadow gradients for depth
- [ ] Test at 2x, 3x, 4x scale (iOS devices)
- [ ] Export sprite sheets for Unity

---

## 9. Export Specifications for Unity

### Sprite Sheet Layout

**Cockpit_Base.png** (Static elements)
- 320x224 single frame
- All non-animated elements
- PNG-24 with transparency where needed

**Cockpit_Gauges.png** (Animated)
- 320x224 per frame × N frames
- Horizontal sprite sheet
- Each gauge animation isolated

**Cockpit_Lights.png** (Animated)
- Individual 4x4 sprites for each light state
- Off, On, Pulse1, Pulse2, Pulse3
- 6 lights × 5 states = 30 sprites

**Cockpit_Radar.png** (Animated)
- 50x50 per frame × 8 frames
- Sweep line rotation
- Isolated on transparent background

### Unity Import Settings
```
Texture Type: Sprite (2D and UI)
Sprite Mode: Multiple
Pixels Per Unit: 1
Filter Mode: Point (no filter)
Compression: None
Max Size: 4096
Format: RGBA 32 bit
```

---

## 10. Notes for Aseprite Workflow

### Tips for Pixel Art Beginners

1. **Start with the frame** - Block out the major shapes first
2. **Use grid** - Enable 8x8 grid overlay for alignment
3. **Limit colors** - Start with 8 colors, add more only if needed
4. **Pixel-perfect lines** - Use Line tool with Shift for straight edges
5. **Onion skinning** - Enable for smooth animations
6. **Reference layer** - Import a photo reference at 50% opacity
7. **Save often** - Aseprite auto-save every 5 minutes

### Common Mistakes to Avoid

- ❌ Mixing pixel sizes (stay consistent with 1:1 pixels)
- ❌ Anti-aliasing on edges (keep it crisp)
- ❌ Too many colors (16 is plenty for retro look)
- ❌ Over-animating (subtle movement is better)
- ❌ Forgetting export settings (use point filtering)

### Keyboard Shortcuts (Aseprite)
```
B - Pencil tool
L - Line tool
G - Paint bucket
E - Eraser
M - Rectangular marquee
K - Eyedropper
Z - Zoom
X - Swap foreground/background color
[ / ] - Decrease/increase brush size
```

---

## 11. Accessibility Considerations

### Colorblind-Friendly Design

**Deuteranopia (Red-Green colorblindness):**
- Don't rely solely on red/green for critical info
- Add icons/shapes to warning states
  - Green light = Circle
  - Amber light = Triangle
  - Red light = X or !

**High Contrast Mode Option:**
- All UI elements can have white outlines toggled
- Increase brightness of active elements by 50%
- Add scanline overlay for CRT effect (optional)

### Readability
- Minimum font size: 3x5 pixels
- White text on dark backgrounds (never dark on light)
- 2-pixel spacing between UI elements minimum
- Critical info (fuel, altitude) always visible

---

## Conclusion

This specification provides everything needed to create the Harbinger cockpit in Aseprite. The design prioritizes:

✅ **Authentic retro aesthetic** (SNES-era limitations)
✅ **Functional UI** (all game info clearly displayed)
✅ **Atmospheric immersion** ("used future" industrial feel)
✅ **Animation readiness** (layered for easy Unity import)
✅ **Performance** (minimal sprite count, efficient rendering)

**Estimated Time:** 3-4 weeks for complete cockpit (all states, animations)

**Next Step:** Open Aseprite and start with Phase 1 (Static Frame)

---

*"Every pixel tells a story."*
