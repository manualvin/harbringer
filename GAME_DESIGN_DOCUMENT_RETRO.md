# Harbinger - Retro Edition Game Design Document

**Version:** 2.0 - SNES-Style Hybrid Approach
**Last Updated:** October 22, 2025
**Target Platform:** iOS (iPhone/iPad)
**Genre:** Retro 3D Flying Simulator / Atmospheric Horror
**Visual Style:** Hybrid - 2D Pixel Art Cockpit + Low-Poly 3D Flight
**Inspiration:** Star Fox, Pilot Wings, Super Metroid atmosphere

---

## 1. Game Title & Logline

### Title
**Harbinger**

### Logline
A retro-styled flight horror simulator where you pilot a Weyland-Yutani prospector through three deadly phases. View the mission through a detailed pixel art cockpit while navigating simple 3D space filled with alien debris, violent weather, and an unseen threat. SNES-era aesthetics meet modern atmospheric tension.

### Elevator Pitch
Imagine Star Fox's low-poly 3D flight combined with Super Metroid's oppressive atmosphere, viewed through a meticulously crafted pixel art cockpit. Pure skill-based piloting with retro charm and modern horror sensibilities. No combat—only flight, stealth, and survival.

---

## 2. Visual Style & Technical Approach

### Hybrid Rendering System

#### The Cockpit View (2D Pixel Art - Always Visible)
- **Resolution:** 16-bit era pixel art (320x224 SNES native, upscaled for iOS)
- **Fixed Frame:** Cockpit interior occupies screen borders
- **Animated Elements:**
  - Flickering instrument panels (3-4 frame animations)
  - Gauge needles rotating (fuel, speed, altitude, temperature)
  - Warning lights pulsing (red/amber/green states)
  - Static/glitch effects when damaged
  - Hand/arm movements on controls (subtle)

- **HUD Elements (Pixel Art):**
  - Radar scope (top-right) - 2D green screen with blips
  - Damage indicator (bottom-left) - ship schematic with red zones
  - Fuel gauge (analog style with chunky needle)
  - Threat proximity meter (horizontal bar, fills red)
  - Text readouts (chunky bitmap font, green/amber terminal style)

#### The Window View (Low-Poly 3D - Center Screen)
- **Star Fox Aesthetic:**
  - Flat-shaded polygons (no textures)
  - Limited color palette (16-64 colors per scene)
  - Vertex count: 50-300 per object
  - No anti-aliasing (sharp, crisp edges)
  - Dithering for gradients (optional)

- **Rendering Style:**
  - **Space Scenes:** Black background, white/cyan stars (Mode 7 style scrolling)
  - **Debris:** Simple geometric shapes (tetrahedrons, cubes, angular forms)
  - **Planet Surface:** Flat planes with height variance, grid lines for altitude reference
  - **Weather:** Particle effects (pixel-sized dots for rain, simple lightning flashes)
  - **Fog:** Depth fade to single background color

- **Frame Rate:** Target 60 FPS (30 FPS acceptable for retro authenticity)
- **Draw Distance:** Limited fog for performance and aesthetic

### Color Palette Strategy

#### Space Phase (Phase 1)
- Deep blacks and dark blues
- Cyan/white for stars and UI
- Gray/silver for debris
- Warning red for hazards
- Alien green for mysterious objects

#### Atmospheric Phase (Phases 2-3)
- Murky greens and sickly yellows (acid rain atmosphere)
- Dark browns for planet surface
- Orange/red for heat and danger
- Purple/magenta for alien energy
- White flashes for lightning

---

## 3. Core Gameplay Loop (Retro Optimized)

### Phase 1: The Approach – Orbital Navigation
**Duration:** 5-8 minutes
**Objective:** Navigate debris field, scan alien wreckage, reach atmosphere

#### Simplified Mechanics for Retro Style
- **Flight Controls:**
  - **D-Pad/Left Stick:** Rotate ship (8-directional or analog)
  - **A Button:** Main thrust (hold for acceleration)
  - **B Button:** Reverse thrust
  - **L/R Triggers:** Strafe left/right
  - Simple momentum system (not full Newtonian physics)

- **Debris Field:**
  - 20-30 simple geometric objects on screen
  - Procedural spawning at distance
  - Slow rotation for visual interest
  - Collision = instant death (restart phase)

- **Scanning System:**
  - Point ship at object
  - Press Y button to scan
  - Progress bar fills (2-3 seconds)
  - Success = object glows green, radar blip updates
  - Each scan increases threat meter by 10%

- **Stealth Mechanic:**
  - Speed affects detection (faster = more visible)
  - Active scanning raises alert level
  - Silent running (hold X) = slower but safer
  - Visual feedback: cockpit lights dim in silent mode

#### Retro Challenge Design
- Tight corridors between debris clusters
- Timed gates (must pass through within window)
- Rotating obstacle patterns
- Resource nodes require risky positioning to scan

---

### Phase 2: The Descent – Atmospheric Entry & Landing
**Duration:** 4-7 minutes
**Objective:** Survive entry, navigate storm, land precisely

#### Retro Flight Model (Simplified Aerodynamics)
- Ship "feels" heavier (slower rotation)
- Pitch affects vertical movement
- Auto-stabilization with small drift
- No complex lift/drag calculations

#### Weather System (Retro Style)
- **Visual Effects:**
  - Rain: White pixel dots streaking down (parallax layers)
  - Wind: Screen shake + ship drift
  - Lightning: White screen flash + brief visibility boost
  - Fog: Draw distance reduces to 30-40 polygons ahead

- **Gameplay Impact:**
  - Wind pushes ship (must counter-steer)
  - Lightning temporarily disables HUD (1-2 seconds)
  - Fog forces instrument-only navigation
  - Rain obscures distant objects

#### Landing Sequence (Arcade Style)
1. **Approach:** Follow radar arrow to landing zone
2. **Descent Corridor:** Navigate between terrain obstacles
3. **Final Approach:**
   - Reduce speed below threshold (green indicator)
   - Center crosshair on landing pad
   - Touch down while centered = success
   - Off-center = partial damage, still proceeds
   - Too fast = crash, restart phase

#### Scoring System (Retro Arcade)
- **Perfect Landing:** 10,000 points
- **Good Landing:** 5,000 points
- **Rough Landing:** 1,000 points (25% damage)
- **Crash:** 0 points, retry

---

### Phase 3: The Escape – Takeoff & Ascent
**Duration:** 5-10 minutes
**Objective:** Emergency launch, escape atmosphere, avoid threat

#### System Damage (Visual Feedback)
- **Damaged Instruments:**
  - Radar flickers on/off
  - Fuel gauge stuck/jumping
  - HUD text corrupts (glitch effect)
  - Screen static overlays

- **Flight Impairments:**
  - Thrust stutters (random power drops)
  - Control lag (200ms delay on damaged systems)
  - Forced yaw/pitch drift
  - Landing gear won't retract (drag effect)

#### The Unseen Threat (Retro Horror)
- **Never Shown Clearly:**
  - Radar: Large contact moving erratically
  - Shadows: Brief silhouette crossing window
  - Audio: Deep bass rumble (use iOS haptics)
  - Screen distortion when close

- **Pursuit Mechanics:**
  - Threat moves toward player at set speed
  - Attacks in straight lines (dodgeable)
  - Forces player into dangerous flight paths
  - Can't be fought, only evaded

#### Ascent Phases
1. **Launch:** Vertical climb avoiding terrain
2. **Storm Layer:** Dense fog, heavy turbulence
3. **Pursuit:** Threat appears, must outmaneuver
4. **Space Transition:** Break atmosphere, reach orbit
5. **Victory:** Escape trajectory achieved

#### Victory Conditions
- Reach orbital altitude
- Maintain 20% hull integrity
- Transmit data (automatic if alive)

---

## 4. Thematic Integration (Retro Style)

### Atmosphere Through Limitation

#### "Less is More" Horror
- **Limited View:** Small 3D window creates claustrophobia
- **Simple Shapes:** Geometric aliens are unsettling through suggestion
- **Minimal Animation:** Stiff, unnatural movement patterns
- **Retro Audio:** Low-fi samples, crunchy sound effects
- **Palette Restrictions:** Sickly colors enhance unease

#### SNES-Era Techniques
- **Mode 7 Horizon:** Fake 3D for planet surface
- **Sprite Scaling:** Approaching objects grow pixelated
- **Parallax Scrolling:** Layered star fields
- **Scanline Effects:** CRT-style distortion
- **Dithering:** Cross-hatch patterns for transparency

### Pixel Art Cockpit Design

#### Interior Details (Hand-Pixeled)
- **Control Panels:**
  - Chunky switches and buttons
  - Worn labels (faded text)
  - Coffee cup secured to console
  - Personal photo taped to panel
  - Scratches and dents

- **Window Frame:**
  - Riveted metal borders
  - Corner-mounted monitors
  - Emergency handle (red)
  - Condensation drops on glass

- **Lighting:**
  - Green instrument glow (primary)
  - Amber warning lights
  - Red alert strobes
  - Blue emergency lighting
  - Flickering fluorescent tube

#### Animation Budget
- 3-5 frames per animated element
- 10-15 total animated objects in cockpit
- Priority: Gauges > Buttons > Environmental

---

## 5. Technical Recommendations (Retro Edition)

### Game Engine Selection

#### Recommended: Unity (Best for 2D/3D Hybrid)
- **Universal Render Pipeline (URP):** Efficient for mobile
- **2D Sprite System:** Perfect for pixel art cockpit
- **Built-in 3D:** Low-poly rendering without complexity
- **Shader Graph:** Custom retro shaders (flat shading, dithering)
- **Asset Store:** Abundant retro/pixel art tools

#### Alternative: Godot (Open Source)
- Excellent 2D/3D hybrid support
- Lightweight for mobile
- GDScript easy to learn
- Free and open source
- Growing asset library

#### Not Recommended: Unreal Engine
- Overkill for retro aesthetic
- Harder to achieve authentic pixel art look
- Heavier runtime for simple graphics

### Development Tools

#### Pixel Art Creation
- **Aseprite ($20):** Industry standard, animation support, palette management
- **Pyxel Edit ($9):** Tileset/animation tools
- **GIMP (Free):** General pixel editing
- **Lospec Palette List:** Pre-made retro color palettes (free)

#### 3D Modeling (Low-Poly)
- **Blender (Free):**
  - Model with low vertex count
  - Use flat shading
  - Export without smoothing groups
  - No textures needed (vertex colors only)

#### Audio Creation (Retro Sound)
- **FamiStudio (Free):** Authentic 8/16-bit chiptune composer
- **BeepBox (Free, Web):** Simple melodic chiptunes
- **Audacity (Free):** Bit-crush modern audio for retro effect
- **BFXR (Free):** Retro sound effect generator (explosions, lasers, alerts)

#### Font Resources
- **Bitmap Fonts:**
  - "Press Start 2P" (Google Fonts, free)
  - "VT323" (Terminal style)
  - "04b_03" (Tiny pixel font)
  - Create custom fonts in Aseprite

### Asset Pipeline

#### Pixel Art Workflow
1. Design at 1x resolution (320x224 base)
2. Use indexed color mode (16-64 colors)
3. Animate in Aseprite (export sprite sheets)
4. Import to Unity as sprites (point filter, no compression)
5. Scale with nearest-neighbor for crisp pixels

#### Low-Poly 3D Workflow
1. Model in Blender (target 100-200 triangles per object)
2. Use minimal faces, no subdivision
3. Apply flat shading
4. Assign vertex colors (no UV mapping needed)
5. Export as FBX/OBJ
6. Import to Unity, disable smoothing

#### Performance Targets (iOS)
- **60 FPS:** iPhone 8 and newer
- **30 FPS:** iPhone 7 minimum
- **Resolution:**
  - Render 3D at 320x224 or 640x448
  - Upscale with nearest-neighbor to device resolution
  - Pixel art overlay at native resolution

### Unity Project Setup

#### Recommended Packages
- **Universal RP:** Mobile-optimized rendering
- **Input System:** Modern touch/controller support
- **2D Sprite:** Pixel art management
- **ProBuilder:** Rapid low-poly level design
- **Post Processing:** CRT effects, scanlines

#### Project Structure
```
Assets/
├── Sprites/
│   ├── Cockpit/          # Pixel art UI elements
│   ├── HUD/              # Gauges, radar, indicators
│   └── Effects/          # Screen glitches, static
├── Models/
│   ├── Debris/           # Low-poly space junk
│   ├── Terrain/          # Planet surface chunks
│   └── Ship/             # Player vessel (external view)
├── Materials/
│   ├── FlatShading.mat   # Retro 3D material
│   └── PixelPerfect.mat  # Sprite material
├── Scripts/
│   ├── Flight/           # Ship controls
│   ├── Weather/          # Particle systems
│   └── UI/               # HUD management
├── Audio/
│   ├── Music/            # Chiptune tracks
│   ├── SFX/              # Retro sound effects
│   └── Ambience/         # Drones, rumbles
└── Scenes/
    ├── Phase1_Orbital.unity
    ├── Phase2_Descent.unity
    └── Phase3_Escape.unity
```

---

## 6. Development Roadmap (Retro Edition)

### Faster Timeline (6-9 Months vs. 12)

#### Month 1: Prototype Core Flight
- **Week 1-2:** Unity project setup, basic ship movement
- **Week 3-4:** Low-poly debris field, collision detection
- **Deliverable:** Playable space flight with obstacles

#### Month 2: Cockpit & HUD
- **Week 1-2:** Pixel art cockpit frame design in Aseprite
- **Week 3:** Implement gauges and HUD elements
- **Week 4:** Animated instrument panels
- **Deliverable:** Complete visual presentation

#### Month 3: Phase 1 Complete
- **Week 1:** Scanning mechanics
- **Week 2:** Stealth/detection system
- **Week 3:** Threat presence implementation
- **Week 4:** Polish and balance
- **Deliverable:** Shippable Phase 1

#### Month 4: Atmospheric Flight
- **Week 1-2:** Simplified aerodynamic model
- **Week 3:** Weather particle systems
- **Week 4:** Screen effects (fog, rain, lightning)
- **Deliverable:** Atmospheric flight prototype

#### Month 5: Landing & Phase 2
- **Week 1-2:** Terrain generation, landing zones
- **Week 3:** Landing mechanics and scoring
- **Week 4:** Audio implementation
- **Deliverable:** Complete Phase 2

#### Month 6: Escape Sequence
- **Week 1:** System damage mechanics
- **Week 2:** Threat pursuit AI
- **Week 3:** Ascent challenges
- **Week 4:** Victory conditions
- **Deliverable:** Complete Phase 3

#### Month 7-8: Integration & Polish
- **Polish Tasks:**
  - Link all three phases
  - Save/load system
  - Options menu (CRT filter toggle, difficulty)
  - Credits sequence
  - Tutorial hints

- **iOS Optimization:**
  - Test on iPhone 8, X, 12, 14
  - Optimize particle counts
  - Memory profiling
  - Battery usage optimization

#### Month 9: QA & Release
- **Testing:**
  - Bug fixing
  - Balance tuning
  - Accessibility testing
  - Localization (text only, minimal)

- **Release Prep:**
  - App Store screenshots
  - Trailer (capture gameplay with CRT filter)
  - Press kit
  - Submit to Apple

---

## 7. Audio Design (Retro Edition)

### Chiptune Music Strategy

#### Composition Style
- **Influences:**
  - Metroid (ambient dread)
  - Star Fox (action themes)
  - Mega Man (energetic melodic)

- **Track List:**
  1. **Title Theme** (30 sec loop) - Hopeful to ominous
  2. **Phase 1: Orbital** (2 min loop) - Tense, sparse
  3. **Phase 2: Descent** (2 min loop) - Intense, driving rhythm
  4. **Phase 3: Escape** (3 min loop) - Panicked, chaotic
  5. **Victory** (15 sec) - Brief triumphant jingle
  6. **Game Over** (10 sec) - Descending failure tones

#### Sound Channels (SNES-Style)
- **Channel 1:** Lead melody
- **Channel 2:** Harmony/counter-melody
- **Channel 3:** Bass line
- **Channel 4:** Percussion (noise channel)

### Retro Sound Effects

#### Ship Sounds
- **Thrust:** Square wave buzz (pitch varies with power)
- **Reverse:** Lower pitch pulse
- **Strafe:** Short blip
- **Collision Warning:** Rapid beeping (increasing frequency)

#### Environmental Sounds
- **Wind:** White noise filtered, panning
- **Rain:** Rapid ticks (randomized pitch)
- **Thunder:** Low rumble (noise burst)
- **Lightning:** Sharp crack (sample + start)

#### Threat Sounds
- **Proximity Alert:** Deep pulse (warning tone)
- **Presence:** Sub-bass drone (felt via haptics)
- **Attack:** Screeching static burst

#### UI Sounds
- **Menu Select:** Click beep
- **Menu Confirm:** Rising chime
- **Scan Complete:** Success jingle
- **Damage:** Crunch + error beep
- **Critical Warning:** Siren loop

### iOS Audio Implementation
- **Format:** OGG Vorbis (music), WAV (SFX)
- **Sample Rate:** 22,050 Hz (authentic retro)
- **Bit Depth:** 8-bit for extreme retro, 16-bit for quality
- **Haptic Feedback:** Use iOS Taptic Engine for rumble effects

---

## 8. Monetization & Business Model

### Premium Pricing Strategy
- **Price Point:** $3.99-$4.99 USD
- **No Ads:** Respects player experience
- **No IAP:** Complete game upfront
- **Value Proposition:** "Console quality retro experience"

### Marketing Angles
- "Star Fox meets Alien"
- "SNES aesthetics, modern tension"
- "Pure skill-based flight sim"
- "No timers, no ads, no nonsense"
- "One-time purchase, yours forever"

### App Store Optimization
- **Keywords:**
  - Retro, SNES, 16-bit, pixel art
  - Flight simulator, space, sci-fi
  - Indie game, premium, no ads

- **Categories:**
  - Primary: Games > Simulation
  - Secondary: Games > Action

---

## 9. Scope & MVP Definition

### Minimum Viable Product (3-4 Months)
- Single continuous mission (3 phases)
- 10-15 unique debris models
- Full pixel art cockpit with animations
- Basic weather system (rain, fog)
- Threat presence (audio + radar only)
- Simple scoring system
- One difficulty level

### Version 1.5 (Post-Launch)
- Additional missions (different planets)
- Cockpit customization (color schemes)
- Hard mode (permadeath)
- Leaderboards (Game Center)
- CRT filter options (scanlines, curvature)

### Version 2.0 (Expansion)
- Story mode (5-7 linked missions)
- Different ship types
- Co-pilot mode (two-player async)
- "Mystery Mode" (procedural generation)
- Expanded chiptune OST

---

## 10. Legal & IP (Retro Edition)

### Original IP Approach (Recommended)

#### Rebranded Elements
- ~~Weyland-Yutani~~ → **"HELIX DYNAMICS"** or **"ATLAS EXTRACTION CORP"**
- ~~Aliens biomechanical~~ → Geometric crystalline alien ruins
- ~~LV-426~~ → Procedurally named exoplanets (e.g., "KEPLER-1649c")

#### Safe Harbor Aesthetic
- Avoid H.R. Giger's specific biomechanical curves
- Use angular, faceted alien designs (fits low-poly style)
- Corporate dystopia theme (not copyrightable)
- Cosmic horror atmosphere (not copyrightable)

### License Structure
- **Code:** GNU GPL v3.0 (as per repository)
- **Pixel Art Assets:** Consider Creative Commons BY-NC-SA or proprietary
- **Music:** Separate license (composer retains rights or buyout)
- **Engine Assets:** Unity Asset Store licenses (varied)

---

## 11. Competitive Analysis

### Retro Flight Games on iOS
- **Stellar Fox:** Paid Star Fox clone ($2.99)
- **Galaxy on Fire 2:** Older space sim (freemium)
- **Grimvalor:** Retro platformer (premium) - successful model
- **Dead Cells:** Pixel art action (premium) - $8.99, huge success

### Market Gap
- No atmospheric horror flight sims in retro style
- Limited skill-based premium games (market full of F2P)
- Nostalgia for SNES aesthetics (30-40 year olds with money)
- Alien/cosmic horror underserved on mobile

### Unique Selling Points
1. Hybrid 2D/3D rendering (unique visual style)
2. Horror without jumpscares (tension-based)
3. No combat (pure piloting skill)
4. Premium model (no predatory monetization)
5. Authentic retro aesthetic (not "retro-inspired")

---

## 12. Next Steps & Action Plan

### Week 1: Pre-Production
- [ ] Finalize branding (corporation name, ship name)
- [ ] Create 16-color palette for Phase 1
- [ ] Sketch cockpit layout (paper or pixel draft)
- [ ] List 10 debris shapes (simple geometric forms)
- [ ] Choose chiptune composer or tool

### Week 2: Project Setup
- [ ] Install Unity 2023 LTS
- [ ] Create project with URP template
- [ ] Setup Git LFS for binary assets
- [ ] Create folder structure (see Section 5)
- [ ] Import input system package

### Week 3: First Playable
- [ ] Model simple ship (cube with thrust indicator)
- [ ] Implement basic movement (8-directional + thrust)
- [ ] Create 5 debris models (< 50 triangles each)
- [ ] Spawn debris in grid pattern
- [ ] Test on iOS device

### Week 4: Visual Foundation
- [ ] Pixel cockpit frame (Aseprite)
- [ ] Basic HUD elements (speed, fuel gauges)
- [ ] Flat shading material for 3D
- [ ] Retro color palette application
- [ ] Deploy build to TestFlight

---

## Conclusion

The retro hybrid approach for Harbinger offers:
- **Achievable scope** for solo/small team
- **Unique aesthetic** that stands out on iOS
- **Faster development** (6-9 months vs. 12+)
- **Lower costs** (pixel art vs. high-poly 3D)
- **Strong nostalgia appeal** for target demographic
- **Technical feasibility** on all iOS devices

By combining Star Fox's low-poly 3D flight with Super Metroid's atmospheric dread, presented through a meticulously crafted pixel art cockpit, Harbinger carves a unique niche in mobile gaming.

**The retro limitation becomes the aesthetic strength.**

---

**Next Document:** Create a detailed pixel art style guide for cockpit design?

---

*"The past is the best filter for the future."*
