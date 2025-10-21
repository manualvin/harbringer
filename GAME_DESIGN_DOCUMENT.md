# Harbinger - Game Design Document

**Version:** 1.0
**Last Updated:** October 21, 2025
**Target Platform:** iOS (iPhone/iPad)
**Genre:** 3D Flying Simulator / Atmospheric Horror
**Inspiration:** Aliens Universe (Weyland-Yutani Corporation)

---

## 1. Game Title & Logline

### Title
**Harbinger**

### Logline
You are a lone Weyland-Yutani prospector on a routine exoplanet survey mission. What should have been a simple resource scan becomes a descent into terror as you navigate through alien derelicts, hostile weather, and the growing sense that something ancient and hostile knows you're here. Your ship is your only sanctuary—and your only way out.

### Elevator Pitch
A first-person 3D flying simulator where precision piloting meets atmospheric horror. Navigate orbital debris fields, survive violent atmospheric entry, and escape an exoplanet where every decision could be your last. No combat—only flight, stealth, and survival.

---

## 2. Core Gameplay Loop

### Phase 1: The Approach – Orbital Navigation
**Duration:** 5-10 minutes
**Objective:** Navigate debris field, scan alien wreckage, reach designated landing coordinates

#### Mechanics
- **6DoF Flight Physics**
  - Full six degrees of freedom in zero-gravity
  - Newtonian physics: momentum conservation, thrust vectoring
  - RCS (Reaction Control System) thrusters for fine adjustments
  - Main engine for primary thrust

- **Debris Field Navigation**
  - Ancient alien wreckage slowly drifting in orbit
  - Derelict spacecraft fragments (biomechanical, H.R. Giger-inspired)
  - Collision detection with instant mission failure
  - Limited visibility due to debris shadows and planet eclipse

- **Stealth Mechanics**
  - Energy signature management (radar profile)
  - Active scanning increases detection risk
  - Passive sensors vs. active sensors tradeoff
  - Unknown threat monitoring player energy fluctuations

- **Scanning Objectives**
  - Identify resource deposits on planet surface
  - Log alien artifacts for Weyland-Yutani database
  - Atmospheric composition analysis
  - Each scan increases "presence" meter (unseen threat awareness)

#### Environmental Hazards
- Micrometeorite showers
- Electromagnetic interference near large debris
- Solar radiation bursts
- Orbital decay zones (gravitational pull)

#### Progression Triggers
- Complete minimum 3 of 5 scan objectives
- Reach atmospheric entry coordinates
- Maintain hull integrity above 60%

---

### Phase 2: The Descent – Atmospheric Entry & Landing
**Duration:** 3-7 minutes
**Objective:** Survive atmospheric entry, navigate storm system, execute precision landing

#### Mechanics
- **Atmospheric Flight Physics**
  - Transition from Newtonian to aerodynamic flight model
  - Dynamic lift/drag calculations based on ship orientation
  - Heat shield integrity management during entry
  - Turbulence simulation with procedural intensity

- **Weather System**
  - **Corrosive Rain:** Damages exposed hull sections, obscures vision
  - **Wind Shear:** Violent crosswinds requiring constant correction
  - **Electrical Storms:** Disrupt instruments, temporary system failures
  - **Dense Fog Banks:** Zero visibility zones, instrument-only navigation
  - **Pressure Gradients:** Sudden altitude loss/gain

- **Landing Sequence**
  - Multi-stage descent: entry burn → glide → powered descent → touchdown
  - Designated landing zone with tight clearance margins
  - Terrain scanning while descending (limited by weather)
  - Vertical velocity must be < 2 m/s on touchdown
  - Horizontal drift must be minimal
  - Landing gear deployment at correct altitude

#### System Management
- Heat shield temperature monitoring
- Fuel conservation (landing requires reserve for takeoff)
- Thruster damage from atmospheric stress
- Instrument reliability degradation
- Emergency procedure decisions (abort to orbit vs. commit to landing)

#### Environmental Storytelling
- Glimpses of alien structures through storm breaks
- Radio chatter from previous failed missions (distorted)
- Company transmission: cold, corporate, unhelpful
- Strange energy readings from planet surface

---

### Phase 3: The Escape – Takeoff & Ascent
**Duration:** 5-12 minutes
**Objective:** Emergency takeoff, escape degrading weather, return to orbit while evading unseen threat

#### Mechanics
- **System Malfunctions**
  - Landing damage manifests as failures (engine misfires, stuck landing gear)
  - Cascading system failures based on previous damage
  - Manual override procedures for failed automation
  - Resource scarcity (fuel, oxygen, coolant)

- **Hostile Weather Evolution**
  - Storm intensity increasing exponentially
  - Multiple weather systems converging on position
  - Visibility deteriorating
  - Safe flight corridors shrinking

- **Unseen Threat**
  - Proximity alerts without visual confirmation
  - Something large moving in the storm
  - Ship systems malfunctioning when threat is near
  - Audio cues: biomechanical sounds, screeching metal
  - Motion sensor blips (never clearly visible)
  - Players must choose between evasive maneuvers (wastes fuel) or maintaining course

- **Ascent Phases**
  - **Launch:** Vertical takeoff with maximum thrust, avoid terrain
  - **Storm Penetration:** Navigate through violent weather layers
  - **Threat Evasion:** Erratic flight through sensor dead zones
  - **Atmospheric Exit:** Maintain trajectory during final push to orbit
  - **Orbital Insertion:** Precision burn to achieve stable orbit

#### Win Conditions
- Reach stable orbit with hull integrity > 15%
- Maintain minimum fuel for orbital maneuvers
- Survive threat encounters
- Transmit scan data to orbital relay

#### Failure States
- Hull breach (integrity reaches 0%)
- Fuel depletion before orbit
- Collision with terrain/debris
- Captured by unseen threat (proximity too close for too long)

---

## 3. Gameplay Mechanics

### Flight Physics

#### Space (Phase 1)
- **Newtonian Model:**
  - No drag, momentum is conserved
  - Thrust changes velocity vector, not position
  - RCS thrusters for rotation on all three axes
  - Translation requires counter-thrust to stop
  - Realistic orbital mechanics (optional simplified mode)

#### Atmosphere (Phases 2 & 3)
- **Aerodynamic Model:**
  - Lift generated by wings/control surfaces
  - Drag increases with speed and poor orientation
  - Stall conditions if angle of attack too high
  - Control surfaces effectiveness varies with air density
  - Engine thrust affected by atmospheric pressure

### Stealth & Detection

#### Energy Management
- **Power States:**
  - **Silent Running:** Minimal emissions, passive sensors only
  - **Standard Operation:** Normal emissions, balanced sensors
  - **Active Scanning:** High emissions, maximum sensor range

- **Detection Risk:**
  - Visual signature (ship lights, engine glow)
  - Thermal signature (heat from engines, systems)
  - Electromagnetic signature (active sensors, communications)
  - Detection meter fills based on player actions
  - Unknown threat responds to high detection levels

### Weather Dynamics

#### Procedural Systems
- **Wind:** Vector-based forces applied to ship
- **Turbulence:** Random impulses varying in intensity
- **Visibility:** Fog density, rain particle density
- **Electrical Interference:** Temporary HUD/sensor disruption
- **Corrosion:** Damage over time when exposed

#### Player Interaction
- Weather radar shows storm systems
- Safe corridors appear and disappear
- Flight through calm zones vs. dangerous zones (risk/reward)
- Weather affects threat visibility (can hide in storm)

### Landing & Takeoff Precision

#### Landing Sequence
1. Approach designated zone (within 100m horizontal)
2. Reduce vertical velocity to < 10 m/s (approach speed)
3. Deploy landing gear at 50m altitude
4. Final descent at < 5 m/s
5. Touchdown with < 2 m/s vertical velocity
6. Horizontal drift < 0.5 m/s

#### Scoring Factors
- Fuel efficiency
- Touchdown precision (distance from center marker)
- Landing softness (vertical velocity on impact)
- Hull integrity preservation
- Time to complete landing

#### Takeoff Sequence
1. Pre-flight checklist (damaged systems identified)
2. Engine spool-up (potential failures)
3. Maximum vertical thrust
4. Obstacle clearance (terrain, structures)
5. Transition to forward flight
6. Retract landing gear (may jam if damaged)

### Non-Combat Threat Design

#### The Unseen Presence
- **Never Directly Shown:** Only suggested through:
  - Motion sensor contacts (brief, indistinct)
  - Audio cues (biomechanical breathing, metallic scraping)
  - Environmental disturbances (debris moving, energy spikes)
  - System malfunctions when near
  - Shadow/silhouette glimpses in storm

- **Behavioral Patterns:**
  - Attracted to high energy signatures
  - Intelligent pursuit (predicts player path)
  - Relentless but avoidable through skilled flying
  - Multiple entities implied (never confirmed)

- **Encounter Design:**
  - Proximity triggers audio/visual distortions
  - Forces player to make navigation choices under pressure
  - Can be evaded but never fought
  - Creates tension without traditional combat

---

## 4. Thematic Integration

### Tone & Atmosphere

#### Core Pillars
- **Oppressive Isolation:** Alone in a vast, hostile environment
- **Corporate Abandonment:** Weyland-Yutani values data over human life
- **Creeping Dread:** Threat builds slowly, never fully revealed
- **Earned Survival:** Skill and decision-making determine outcome

#### Emotional Journey
1. **Phase 1:** Routine confidence → Growing unease
2. **Phase 2:** Focused tension → Survival instinct
3. **Phase 3:** Raw panic → Desperate escape

### Visual Design

#### "Used Future" Aesthetic
- **Ship Interior:**
  - Worn industrial surfaces, exposed piping
  - Analog gauges mixed with digital displays
  - Coffee stains, personal effects, lived-in details
  - Dim lighting, flickering monitors
  - Utilitarian design over aesthetics

- **Cockpit Layout:**
  - First-person perspective
  - Realistic instrument cluster
  - Physical switches and controls
  - Multi-function displays (MFD)
  - Window view with dynamic dirt/rain effects

#### Alien Wreckage (H.R. Giger Influence)
- **Biomechanical Forms:**
  - Organic curves merged with technological elements
  - Ribbed surfaces, tubular structures
  - Fossilized appearance (ancient)
  - Disturbing symmetry and repetition
  - Subtly unsettling proportions

- **Lighting:**
  - Cold, sterile light from ship systems
  - Warm, ominous glow from alien artifacts
  - High contrast shadows
  - Volumetric fog and god rays
  - Bioluminescent accents on alien tech

#### Planetary Environment
- **Exoplanet LV-426 Aesthetic:**
  - Barren rocky landscape
  - Acid rain-scoured surfaces
  - Alien architecture ruins (distant, implied)
  - Perpetual storm systems
  - Hostile color palette (sickly greens, harsh blues, warning oranges)

### Weyland-Yutani Branding

#### Corporate Integration
- **Ship Designation:** "USCSS Harbinger" (United States Commercial Starship)
- **UI Elements:** Corporate logo on HUD, loading screens
- **Communications:** Cold, procedural corporate voice
- **Mission Briefing:** Jargon-heavy, liability-focused
- **Data Priorities:** Resource extraction over crew safety

#### Narrative Subtext
- Mission parameters change mid-flight (corporate deception)
- Company knows more than they revealed
- Player is expendable, data is not
- "The Company" as invisible antagonist

### Audio Design

#### Sound Categories

**Ship Sounds:**
- Engine hum (changes with thrust level)
- RCS thruster pops
- Metal stress groans during turbulence
- System beeps and alerts
- Radio static and interference

**Environmental Sounds:**
- Wind howling against hull
- Rain impacts (metallic pings)
- Distant thunder/electrical storms
- Eerie planetary ambience
- Debris impacts (micro and macro)

**Threat Sounds:**
- Biomechanical breathing (distant, filtered)
- Metallic scraping on hull
- Organic chittering/clicking
- Deep subsonic rumbles (felt more than heard)
- Sudden silence (equally terrifying)

**Music/Score:**
- Minimalist, synth-heavy (Jerry Goldsmith influence)
- Dynamic intensity based on threat proximity
- Silence used as narrative tool
- Stingers for critical moments
- Ambient drones for exploration

---

## 5. Technical Recommendations

### Game Engine Selection

#### Primary Recommendation: Unreal Engine 5
**Advantages for iOS:**
- **Lumen:** Real-time global illumination for dramatic lighting
- **Nanite:** High-detail environments without performance loss
- **Niagara VFX:** Advanced particle systems for weather effects
- **MetaSounds:** Procedural audio for dynamic soundscapes
- **iOS Optimization:** Built-in Metal API support, mobile rendering features
- **Blueprint Visual Scripting:** Rapid prototyping without coding

**iOS-Specific Considerations:**
- Use mobile rendering forward path
- Implement dynamic resolution scaling
- LOD (Level of Detail) aggressive settings
- Texture streaming optimizations
- Touch control schema with optional controller support

**Performance Targets (iOS):**
- iPhone 12 Pro and newer: 60 FPS @ 1080p
- iPad Pro M1 and newer: 60 FPS @ native resolution
- Adaptive quality settings for older devices (iPhone XS minimum)

#### Alternative: Unity
**Advantages:**
- Larger asset store for mobile
- More straightforward mobile deployment
- Better multi-platform support
- Lower learning curve

**Recommended Packages:**
- Universal Render Pipeline (URP) for mobile optimization
- Cinemachine for camera control
- Post-Processing Stack
- Shader Graph for custom materials

### 3D Modeling & Asset Creation

#### Software Stack
- **Blender (Free):** Primary 3D modeling, UV unwrapping, animation
- **ZBrush:** High-detail alien organic modeling (biomechanical assets)
- **Substance Painter:** PBR texturing (metallic, roughness, normal maps)
- **Substance Designer:** Procedural material creation
- **Houdini (Indie):** Procedural debris field generation

#### Asset Pipeline for iOS
1. Model in Blender (mobile poly count limits: 5K-15K per asset)
2. High-poly sculpt in ZBrush for baking
3. Retopology for game-ready mesh
4. UV unwrap and optimize (texture atlasing)
5. Texture in Substance Painter (2K max for mobile)
6. Bake normal maps from high-poly
7. Import to engine with LOD levels (3-4 LODs)

### Asset Sources

#### Unreal Marketplace
- **Recommended Packs:**
  - "Sci-Fi Interior" packs for ship cockpit
  - "Modular Sci-Fi" systems
  - Weather/particle effect systems
  - Audio packs (sci-fi ambience, ship sounds)

#### Unity Asset Store
- **Recommended Packs:**
  - "Space Graphics Toolkit" for orbital rendering
  - "Atmospheric Height Fog" for weather
  - "Sci-Fi Modular Environment" kits

#### Free Resources
- **Sketchfab:** CC-licensed sci-fi models (optimize for mobile)
- **Quixel Megascans:** High-quality PBR materials (via UE5)
- **Freesound.org:** Royalty-free audio samples
- **NASA 3D Resources:** Spacecraft reference models

#### Custom Assets Required
- **Unique Ship Design:** Player vessel (hero asset)
- **Alien Wreckage:** Biomechanical debris (10-15 unique pieces)
- **Planetary Terrain:** Procedural + hand-crafted landing zones
- **UI Elements:** Weyland-Yutani branded HUD
- **VFX:** Rain, fog, engine exhaust, electrical arcs

### Dynamic Weather System

#### Unreal Engine Implementation
1. **Volumetric Clouds:** Use UE5 volumetric clouds for storm systems
2. **Niagara Particles:** Rain, debris, sparks, fog
3. **Post-Process Effects:** Color grading for atmosphere, lens distortion
4. **Wind System:** Global wind vector affecting particles and ship
5. **Lightning:** Randomized light flashes with audio sync
6. **Procedural Generation:** Weather intensity based on timer/player actions

#### Unity Implementation
1. **Shader Graph:** Custom rain/fog shaders
2. **Particle System:** GPU particles for rain/debris
3. **Post-Processing Stack:** Bloom, color grading, vignette
4. **C# Scripts:** Weather manager system with states
5. **Audio Mixer:** Dynamic audio based on weather intensity

### Physics System Setup

#### Unreal Engine
- **Custom Flight Component:** C++ or Blueprint-based
- **PhysX Integration:** Hull damage simulation
- **Collision Channels:** Debris, terrain, threat zones
- **Trace Checks:** Sensor scanning, threat detection
- **Force Application:** Thrust, wind, gravity zones

#### Unity
- **Custom Rigidbody Controller:** C# physics script
- **Force Modes:** Thrust (ForceMode.Force), impacts (ForceMode.Impulse)
- **Collision Layers:** Separate layers for different interaction types
- **Raycasting:** Sensor systems, ground detection

### iOS-Specific Technical Considerations

#### Touch Controls
- **Virtual Joysticks:** Dual-stick layout (left: thrust/rotation, right: camera/pitch)
- **Gesture Controls:** Swipe for quick maneuvers, pinch for throttle
- **Context Buttons:** Dynamic on-screen buttons for landing gear, scanning, etc.
- **Haptic Feedback:** iPhone Taptic Engine for impacts, warnings
- **Controller Support:** Full MFi (Made for iPhone) controller compatibility

#### Performance Optimization
- **Metal API:** Native iOS graphics API
- **LOD System:** Aggressive distance-based detail reduction
- **Occlusion Culling:** Hide objects behind debris/terrain
- **Texture Compression:** ASTC format for iOS
- **Audio Compression:** AAC for music, compressed PCM for effects
- **Memory Management:** Target 2GB RAM footprint (iPhone compatibility)
- **Battery Optimization:** Cap frame rate at 60 FPS, optimize GPU usage

#### Device-Specific Features
- **iPhone ProMotion (120Hz):** Optional high frame rate mode
- **LiDAR (iPad Pro):** Not used but could enable AR features in future
- **Face ID:** Quick resume without interruption
- **iCloud Save:** Progress sync across devices
- **Game Center:** Leaderboards for landing precision, completion times

---

## 6. Development Notes

### Non-Linear Player Agency

#### Exploration Freedom
- **Orbital Phase:** Players choose scan order, debris path
- **Descent Phase:** Multiple landing zones with varying difficulty
- **Ascent Phase:** Dynamic escape routes based on weather/threat

#### Risk vs. Reward Systems
- **Scanning:** More scans = better score but higher detection risk
- **Landing Zones:** Difficult zones offer fuel bonuses, easier zones cost fuel
- **Storm Navigation:** Dangerous paths are shorter, safe paths consume more fuel
- **Stealth vs. Speed:** Silent running is safer but slower

#### Player Expression
- **Flying Style:** Aggressive vs. cautious piloting
- **Resource Management:** Fuel conservation strategies
- **Risk Tolerance:** Push systems to limits or maintain safety margins

### Environmental Storytelling

#### Narrative Without Text Dumps
- **Ship Details:** Personal effects suggest previous pilot's fate
- **Debris Field:** Wreckage tells story of ancient disaster
- **Radio Chatter:** Fragments of previous mission recordings (environmental audio)
- **Corporate Messages:** Coded language reveals true mission intent
- **Planetary Scars:** Visible signs of alien civilization collapse

#### Show, Don't Tell
- No cutscenes during gameplay
- No forced tutorials (organic learning through HUD prompts)
- Environmental clues over exposition
- Player discovers story through exploration

#### Audio Logs (Optional)
- **Previous Pilot Logs:** Found during orbital phase (debris data cores)
- **Corporate Transmissions:** Received during descent
- **Distress Signals:** Cryptic messages from planet surface
- All optional, never interrupt gameplay

### Audio Design Amplification

#### Layered Soundscape
1. **Constant Layer:** Ship ambience, always present (comfort)
2. **Environmental Layer:** Weather, debris, planetary sounds (context)
3. **Threat Layer:** Biomechanical sounds, only when near (fear)
4. **UI Layer:** Beeps, warnings, system sounds (information)

#### Dynamic Mixing
- Threat sounds duck (lower) environmental sounds
- Critical warnings interrupt all other audio
- Music fades during intense moments (let sounds speak)
- Silence before major scares

#### 3D Positional Audio
- Debris impacts directionally accurate
- Threat sounds source from proximity zones
- Wind/rain intensity varies by ship orientation
- Engine sounds spatialize in cockpit

### Modular Development Path

#### Phase 1 Development (Prototype)
**Milestone 1: Core Flight (2-3 months)**
- Basic ship model (placeholder)
- 6DoF space flight physics
- Simple debris field (procedural spheres)
- Collision detection
- Camera controls

**Milestone 2: Orbital Navigation (1-2 months)**
- Enhanced debris (10-15 unique models)
- Scanning system UI
- Detection meter mechanic
- Planetary approach sequence

#### Phase 2 Development (Vertical Slice)
**Milestone 3: Atmospheric Flight (2-3 months)**
- Aerodynamic flight model
- Weather system implementation
- Landing zone terrain
- Precision landing mechanics
- Heat shield/damage system

**Milestone 4: Visual Polish (2 months)**
- Cockpit interior details
- Weather VFX (rain, fog, lightning)
- Audio implementation
- UI/HUD design

#### Phase 3 Development (Complete Loop)
**Milestone 5: Escape Sequence (2-3 months)**
- Takeoff mechanics
- System failure events
- Unseen threat implementation
- Ascent to orbit
- Win/fail states

**Milestone 6: Integration & Polish (2-3 months)**
- Three-phase integration
- Difficulty balancing
- Performance optimization for iOS
- QA and bug fixing
- Audio mixing and mastering

#### Post-Launch Development
**Milestone 7: Content Updates**
- Additional exoplanets (varied environments)
- New ship types with different flight characteristics
- Harder difficulty modes
- Leaderboard challenges
- Story mode expansion

### Testing & Balancing

#### Core Metrics to Track
- **Completion Rate:** % of players finishing all three phases
- **Death Points:** Where players fail most frequently
- **Average Completion Time:** Per phase and total
- **Fuel Usage:** Efficiency patterns
- **Detection Levels:** Stealth engagement metrics

#### Difficulty Tuning
- **Accessibility Options:**
  - Flight assist modes (auto-stabilization)
  - Extended fuel reserves
  - Reduced weather intensity
  - Visible threat mode (for testing/accessibility)

- **Challenge Options:**
  - Permadeath mode
  - Limited fuel
  - No HUD elements
  - Realistic physics (no assists)

### Scope Management

#### Minimum Viable Product (MVP)
- Single exoplanet environment
- One ship type
- Three-phase gameplay loop
- Basic weather system
- Implied threat (audio only)
- Essential UI/HUD

#### Phase 1 Expansion
- Enhanced weather variety
- Additional debris types
- Improved alien wreckage models
- Full threat visual implementation (optional glimpses)
- Expanded audio design

#### Phase 2 Expansion
- Multiple exoplanets with unique challenges
- Ship customization (different modules)
- Story campaign (linked missions)
- Multiplayer leaderboards
- Endless mode (procedural missions)

---

## 7. iOS Platform-Specific Design Considerations

### User Experience (UX)

#### Session Length Design
- **Quick Play Mode:** 10-15 minute complete run (mobile-friendly)
- **Save Points:** Auto-save at phase transitions
- **Interruption Handling:** Pause on app background, quick resume

#### Monetization Strategy (Optional)
- **Premium Model:** $4.99-$9.99 upfront (no ads, complete experience)
- **Freemium Model:** Free first mission, $2.99 unlock full game
- **Cosmetic IAP:** Ship skins, cockpit customization (ethical monetization)
- **No Pay-to-Win:** Skill-based gameplay, no purchasable advantages

#### Accessibility Features
- **Touch Sensitivity:** Adjustable virtual joystick sensitivity
- **Colorblind Modes:** UI color adjustments
- **Audio Subtitles:** Visual indicators for directional sounds
- **Difficulty Presets:** Story mode (easy), Standard, Hardcore

### Marketing & App Store Optimization

#### Target Audience
- **Primary:** Sci-fi/horror fans, 18-35 years old
- **Secondary:** Simulation enthusiasts, Aliens franchise fans
- **Tertiary:** Mobile gamers seeking premium experiences

#### Key Selling Points
- "Aliens universe meets flight simulator"
- "No combat, pure atmospheric horror"
- "Skill-based precision gameplay"
- "Console-quality graphics on mobile"
- "Designed for one-handed play or controllers"

#### App Store Assets
- **Icon:** Ship silhouette against storm/alien planet
- **Screenshots:** Showcase cockpit view, weather, alien wreckage
- **Preview Video:** 30-second trailer of tense descent sequence
- **Description Focus:** Unique gameplay loop, atmosphere, quality

---

## 8. Legal & Licensing Considerations

### Intellectual Property

#### Aliens Universe License
⚠️ **CRITICAL:** This design document uses the "Aliens" universe as **inspiration only**.

**To legally develop this game, you must:**
1. **Option A:** Secure official license from 20th Century Studios (Disney)
   - Costly and time-consuming
   - Requires negotiation and approvals
   - Best for commercial release with franchise branding

2. **Option B:** Create original IP inspired by Aliens aesthetic
   - Change "Weyland-Yutani" to original corporation name
   - Redesign alien aesthetic to avoid H.R. Giger estate claims
   - Remove direct Aliens references
   - File "derivative work" becomes "inspired by"
   - **Recommended path for indie development**

#### Safe Harbor Approach (Original IP)
**Rename Elements:**
- ~~Weyland-Yutani~~ → "Meridian Dynamics" / "Helix Corporation"
- ~~LV-426~~ → "Kepler-442b" / "Proxima Centauri c" (real exoplanets)
- ~~USCSS~~ → "CMSS" (Commercial Mining Survey Ship)

**Redesign Visuals:**
- Biomechanical alien tech → Crystalline/geometric alien structures
- Giger aesthetic → Original alien design language
- Keep "corporate greed + cosmic horror" themes (not copyrightable)

### Open Source & GPL-3.0

#### Current License: GNU GPL v3.0
**Implications:**
- All source code must remain open source
- Any derivative works must also be GPL-3.0
- Commercial sale is allowed (GPL ≠ free)
- Asset files (models, audio) can use different licenses

**Considerations for Game Development:**
- **Code:** GPL-3.0 (as required by repository license)
- **Assets:** Consider Creative Commons or proprietary license
- **Unity/Unreal Projects:** Engine licenses compatible with GPL code
- **Third-Party Assets:** Ensure licenses are compatible

**Recommendation:** If commercial release is planned, consult IP attorney for license structure.

---

## 9. Conclusion & Next Steps

### Project Vision Summary
Harbinger is a skill-based atmospheric horror flight simulator for iOS that challenges players to survive three distinct phases of a doomed corporate mission. By focusing on precision piloting, environmental storytelling, and psychological tension without combat, the game carves a unique niche in mobile gaming.

### Immediate Next Steps
1. **Legal Clearance:** Decide on licensed vs. original IP approach
2. **Prototype Phase 1:** Build basic 6DoF flight in chosen engine
3. **Asset Pipeline:** Create placeholder ship model and debris field
4. **iOS Test Build:** Deploy early prototype to device for control testing
5. **Gather Feedback:** Playtest core flight feel before expanding

### Long-Term Roadmap
- **Months 1-3:** Orbital navigation prototype
- **Months 4-6:** Atmospheric descent vertical slice
- **Months 7-9:** Escape sequence and integration
- **Months 10-12:** Polish, optimization, iOS submission
- **Post-Launch:** Content updates, additional planets, story mode

### Success Metrics
- **Critical:** 4.5+ star App Store rating
- **Commercial:** 10,000+ downloads in first month (premium model)
- **Community:** Positive reception from sci-fi/horror gaming communities
- **Technical:** Stable 60 FPS on iPhone 12 Pro and newer

---

**Document prepared for:** Harbinger game development project
**Repository:** manualvin/harbringer
**License:** GNU General Public License v3.0
**Contact:** [To be added]

---

*"In space, no one can hear you scream. In atmosphere, they can hear everything."*
