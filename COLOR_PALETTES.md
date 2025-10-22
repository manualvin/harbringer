# Harbinger - Color Palettes

Complete color palette definitions for all game phases and UI states.

---

## Aseprite Palette Files

### How to Import
1. Open Aseprite
2. Palette menu → Load Palette
3. Select .gpl or .ase palette file
4. Or manually enter hex codes below

---

## 1. Cockpit UI Palette (16 Colors)

**Filename:** `harbinger_cockpit.gpl`

```
GIMP Palette
Name: Harbinger Cockpit
Columns: 8
#
0   0   0    Black         (Space, deep shadows)
26  26  26   Dark Gray     (Metal shadows)
45  45  45   Medium Gray   (Panel surfaces)
74  74  74   Light Gray    (Highlighted edges)
107 107 107  Silver        (Rivets, details)
138 138 138  Bright Silver (Reflections)
0   255 0    Bright Green  (Active systems)
0   170 0    Medium Green  (Gauges, text)
0   85  0    Dark Green    (Screen backgrounds)
255 170 0    Amber         (Warnings)
255 0   0    Red           (Alerts, damage)
255 255 255  White         (Critical text)
0   136 255  Cyan          (Secondary displays)
34  0   51   Deep Purple   (Alien energy)
74  48  32   Brown         (Rust, worn)
255 255 136  Pale Yellow   (Backlit buttons)
```

### Hex Codes for Digital Tools
```
#000000 #1a1a1a #2d2d2d #4a4a4a #6b6b6b #8a8a8a
#00ff00 #00aa00 #005500 #ffaa00 #ff0000 #ffffff
#0088ff #220033 #4a3020 #ffff88
```

---

## 2. Phase 1: Orbital Space Palette (24 Colors)

**For debris field and space environment**

### Hex Values
```
Space & Stars:
#000000  Pure black (space)
#0a0a1a  Deep space blue
#1a1a2a  Lighter space blue
#ffffff  White (stars)
#aaaaff  Blue-white (bright stars)
#4444ff  Cyan stars

Debris (Geometric Alien):
#2d2d2d  Dark gray metal
#4a4a4a  Medium gray
#6b6b6b  Light gray
#8a8a8a  Bright gray
#445544  Dark green tint (alien)
#667766  Medium green tint
#889988  Light green tint

Ship & Effects:
#0088ff  Engine glow (cyan)
#00aaff  Bright engine
#ff4400  Thruster orange
#ff8800  Bright thruster
#ffaa44  Exhaust yellow

Alien Energy:
#220033  Deep purple
#440066  Medium purple
#8800ff  Bright purple
#aa44ff  Glowing purple
#ff00ff  Magenta (high energy)
```

---

## 3. Phase 2: Atmospheric Descent Palette (32 Colors)

**For planet surface and weather**

### Hex Values
```
Atmosphere:
#1a2a1a  Dark murky green
#2a3a2a  Medium murky green
#3a4a3a  Light murky green
#4a5a4a  Atmospheric haze

Planet Surface:
#2a1a0a  Dark brown rock
#3a2a1a  Medium brown
#4a3a2a  Light brown
#5a4a3a  Highlighted rock
#1a1a0a  Dark soil
#2a2a1a  Medium soil

Weather Effects:
#ffffff  Rain drops (white)
#cccccc  Rain (light gray)
#ffff88  Lightning flash
#ffffcc  Lightning glow
#ffaa00  Orange lightning core

Acid Rain:
#88ff88  Pale green (corrosive)
#66cc66  Medium green acid
#44aa44  Dark green acid
#228822  Acidic ground effects

Fog/Clouds:
#2a3a2a  Dark fog
#3a4a3a  Medium fog (50% opacity)
#4a5a4a  Light fog (25% opacity)
#5a6a5a  Bright fog highlights

Alien Structures (Distance):
#220033  Deep purple (alien tech)
#330044  Medium purple
#440066  Light purple
#6600aa  Glowing purple

Landing Zone:
#ffaa00  Landing pad markers (amber)
#ff8800  Bright markers
#ff4400  Critical zone red
```

---

## 4. Phase 3: Escape/Threat Palette (Additional 8 Colors)

**For threat presence and emergency states**

### Hex Values
```
Threat Indicators:
#ff0000  Danger red (pure)
#aa0000  Dark danger red
#ff4444  Pulsing red
#ff8888  Alert highlight

Biomechanical Hints:
#001100  Deep alien green
#002200  Medium alien green
#003300  Bright alien green (glow)
#004400  Bioluminescent

Emergency:
#ffffff  Strobe white (flashing)
```

---

## 5. Damage State Palette Shifts

### Normal → Damaged Transition

When hull integrity drops, shift the cockpit palette:

**50-100% Hull:**
```
Normal colors (use base cockpit palette)
```

**25-50% Hull:**
```
#00ff00 → #00aa00  (Bright green dims)
#00aa00 → #005500  (Medium green darkens)
Add flicker: Alternate between normal and dark every 15 frames
```

**0-25% Hull (Critical):**
```
#00ff00 → #005500  (Bright green very dark)
#00aa00 → #003300  (Medium green very dark)
Red overlay: Flash #ff0000 at 50% opacity every 30 frames
Static: Random pixels turn white (10% of screen)
```

---

## 6. Palette Animation Sequences

### Warning Light Pulse
```
Frame 1: #ffaa00 (Amber)
Frame 2: #ff8800 (Brighter)
Frame 3: #ffaa00 (Amber)
Frame 4: #cc6600 (Darker)
Loop: 4 frames, 120ms each
```

### Critical Alert Pulse
```
Frame 1: #ff0000 (Red)
Frame 2: #ffffff (White flash)
Frame 3: #ff0000 (Red)
Frame 4: #aa0000 (Dark red)
Loop: 4 frames, 60ms each (faster)
```

### Screen Flicker
```
Frame 1-58: Normal palette
Frame 59:   Shift all colors -20% brightness
Frame 60:   Shift all colors -40% brightness
Frame 61:   Normal palette
Loop: Every 60 frames (1 second at 60 FPS)
```

---

## 7. Unity Shader Palette Swapping

### Implementation Notes

For dynamic palette changes (damage, alert states), use Unity shader:

```csharp
// Pseudo-code for palette swap shader
// Maps source colors to target colors at runtime

Shader "Harbinger/PaletteSwap" {
    Properties {
        _MainTex ("Sprite Texture", 2D) = "white" {}
        _PaletteTex ("Palette", 2D) = "white" {}
        _SwapIndex ("Swap Index", Float) = 0
    }
    // Lookup pixel color in _MainTex
    // Use color as index into _PaletteTex row
    // _SwapIndex selects which row (normal, damaged, critical)
}
```

**Palette Texture Layout:**
- Row 0: Normal state colors (16 colors)
- Row 1: 50% damaged colors (16 colors, darker greens)
- Row 2: Critical damaged colors (16 colors, very dark + red tint)
- Row 3: Alien energy colors (special effects)

---

## 8. Color Usage Guidelines

### Do's ✓

- **Use green for "good"**: Systems operational, normal readings
- **Use amber for "caution"**: Warnings, non-critical issues
- **Use red for "danger"**: Critical alerts, damage, threats
- **Use cyan for "info"**: Secondary data, non-critical displays
- **Use white sparingly**: Critical text, flashes, highlights only
- **Limit simultaneous colors**: Max 8 colors on screen at once for clarity

### Don'ts ✗

- ❌ Don't use pure blue (#0000ff) - Reads as purple on SNES
- ❌ Don't use gradients - Indexed color only
- ❌ Don't mix warm and cool palettes in same scene
- ❌ Don't rely on color alone - Use shapes/icons too (colorblind)
- ❌ Don't saturate screen - Leave black spaces for rest areas

---

## 9. Testing Your Palette

### Colorblind Simulation

Test palettes using these tools:
- **Coblis** (online): Color Blindness Simulator
- **Sim Daltonism** (Mac): Real-time colorblind preview
- **Photoshop**: View → Proof Setup → Color Blindness

**Key checks:**
- Red/green warnings distinguishable?
- Fuel gauge readable at all levels?
- Threat indicator visible?

### CRT Simulation

SNES games were designed for CRT TVs. Test with:
- **Aseprite**: Add scanline overlay (1-pixel horizontal lines, 50% opacity)
- **Curvature**: Optional barrel distortion filter
- **Bloom**: Add slight glow to bright colors (white, green)

### Contrast Test
```
Minimum contrast ratios (WCAG guidelines):
- Text: 4.5:1 (e.g., #00ff00 on #000000 = 15:1 ✓)
- UI Elements: 3:1 minimum
- Use online contrast checker tools
```

---

## 10. Palette Files for Download

### File Formats Provided

After design finalized, export these formats:

1. **harbinger_cockpit.gpl** - GIMP/Aseprite palette
2. **harbinger_cockpit.ase** - Aseprite palette
3. **harbinger_cockpit.png** - 16x1 pixel image (each pixel = 1 color)
4. **harbinger_space.gpl** - Phase 1 orbital palette
5. **harbinger_atmosphere.gpl** - Phase 2 descent palette
6. **harbinger_threat.gpl** - Phase 3 escape palette

### Creating .GPL File

Save as text file with .gpl extension:
```
GIMP Palette
Name: Harbinger Cockpit
Columns: 8
#
0   0   0    Black
26  26  26   Dark Gray
... (continue for all 16 colors)
```

---

## 11. Real SNES Color Limitations

### Technical Reference

SNES supported:
- **32,768 total colors** (15-bit RGB: 5 bits per channel)
- **256 colors on screen** simultaneously
- **16 colors per palette** for sprites
- **16 palettes total** (256 colors = 16 × 16)

Harbinger uses **4 palettes**:
1. **Cockpit UI** (16 colors) - Always loaded
2. **Phase Environment** (48 colors) - Swapped per phase
3. **Effects** (16 colors) - Explosions, glitches, particles
4. **Reserved** (16 colors) - Spare for expansion

**Total:** 96 colors defined, 64 on-screen max

---

## 12. Quick Reference Table

| Color Name | Hex     | RGB         | Use Case |
|------------|---------|-------------|----------|
| Black      | #000000 | 0,0,0       | Space, shadows |
| Dark Gray  | #1a1a1a | 26,26,26    | Metal shadows |
| Panel Gray | #2d2d2d | 45,45,45    | Console surfaces |
| Light Gray | #4a4a4a | 74,74,74    | Highlights |
| Silver     | #6b6b6b | 107,107,107 | Rivets |
| HUD Green  | #00ff00 | 0,255,0     | Active systems |
| Text Green | #00aa00 | 0,170,0     | Readable text |
| BG Green   | #005500 | 0,85,0      | Screen background |
| Warning    | #ffaa00 | 255,170,0   | Caution state |
| Alert      | #ff0000 | 255,0,0     | Danger state |
| White      | #ffffff | 255,255,255 | Critical info |
| Info Cyan  | #0088ff | 0,136,255   | Secondary data |
| Alien      | #220033 | 34,0,51     | Threat energy |
| Rust       | #4a3020 | 74,48,32    | Wear detail |
| Button     | #ffff88 | 255,255,136 | Lit switches |

---

## Conclusion

These palettes provide:
- ✅ Authentic SNES-era color limitations
- ✅ Clear visual hierarchy (green = good, red = bad)
- ✅ Atmospheric variety across three phases
- ✅ Colorblind-friendly with high contrast
- ✅ Efficient (16 colors for cockpit UI)

**Next Step:** Import `harbinger_cockpit.gpl` into Aseprite and start pixeling!

---

*"16 colors is not a limitation—it's a style."*
