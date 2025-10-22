# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Harbinger** is a 3D atmospheric horror flight simulator game for iOS, inspired by the Aliens universe. Players control a Weyland-Yutani prospector navigating an exoplanet mission through three distinct phases:

1. **The Approach** - Orbital navigation with 6DoF physics
2. **The Descent** - Atmospheric entry and precision landing
3. **The Escape** - Emergency takeoff and ascent under threat

**Genre:** Flight Simulator / Atmospheric Horror
**Platform:** iOS (iPhone/iPad)
**Target Devices:** iPhone 12 Pro+, iPad Pro (M1+)

## Key Documentation

### Design Documents (Two Approaches)

- **GAME_DESIGN_DOCUMENT.md** - Modern 3D approach with Unreal Engine 5/Unity
  - High-fidelity graphics with Lumen/Nanite
  - PBR texturing and realistic lighting
  - 12-month development timeline
  - Target: iPhone 12 Pro+ only

- **GAME_DESIGN_DOCUMENT_RETRO.md** - SNES-style retro hybrid approach ⭐ **RECOMMENDED**
  - Pixel art cockpit + low-poly 3D flight (Star Fox style)
  - Faster development (6-9 months)
  - Runs on iPhone 8+
  - Lower cost, unique aesthetic
  - Core gameplay mechanics (same across both documents)
  - Asset pipeline recommendations

### Pixel Art Design Documents

- **COCKPIT_DESIGN_SPEC.md** - Complete pixel art specification for cockpit UI
- **COLOR_PALETTES.md** - SNES-era color palette definitions (16-64 colors)
- **COCKPIT_ASCII_MOCKUP.txt** - ASCII art layout references

### Prototype Development

- **PROTOTYPE_SETUP_GUIDE.md** - Unity setup guide for playable prototype ⚡ **START HERE**
  - Step-by-step Unity installation and configuration
  - Placeholder UI with colored rectangles
  - Complete C# flight control script (ShipController.cs)
  - Debris spawning system
  - Collision detection
  - 1-2 week timeline to playable demo

## Project Status

**Current Phase:** Prototype Development
- ✅ Game design documents completed (modern + retro versions)
- ✅ Pixel art specifications ready
- ⏳ Unity prototype in progress (use PROTOTYPE_SETUP_GUIDE.md)
- Recommended: Unity 2022.3 LTS with URP
- No production assets yet (using placeholders)
- Repository structure established

## License & Legal

### Code License
This project is licensed under the GNU General Public License v3.0 (GPL-3.0). All source code contributions must comply with this license.

### Important IP Considerations
⚠️ **CRITICAL:** The current design references the "Aliens" universe as inspiration only.

For legal commercial release, choose one path:
1. **Licensed approach:** Secure IP rights from 20th Century Studios (Disney)
2. **Original IP approach:** Create original universe inspired by similar themes (recommended for indie)

See GAME_DESIGN_DOCUMENT.md Section 8 for detailed legal guidance.

## Recommended Technology Stack

### For Modern 3D Approach
**Primary: Unreal Engine 5**
- Lumen, Nanite, Niagara, MetaSounds
- Native iOS Metal API support

**Alternative: Unity**
- Universal Render Pipeline (URP)
- Cinemachine, Shader Graph

**Asset Tools:**
- Blender, Substance Painter, ZBrush

### For Retro Hybrid Approach ⭐ **RECOMMENDED**
**Primary: Unity**
- Universal Render Pipeline (URP) - excellent 2D/3D hybrid
- Built-in sprite system for pixel art
- Shader Graph for retro effects (flat shading, dithering)
- Lightweight for mobile

**Alternative: Godot**
- Open source, excellent 2D/3D support
- GDScript easy to learn

**Asset Tools:**
- **Aseprite** ($20) - Pixel art and animation
- **Blender** (free) - Low-poly 3D modeling (100-200 triangles)
- **FamiStudio** (free) - Chiptune music composition
- **BFXR** (free) - Retro sound effects

### Version Control
- Git LFS required for binary assets (models, textures, audio)
- .gitignore templates for chosen engine

## Development Workflow

### Current Branch
Working on: `claude/initialize-project-011CULA9hCWjZNaWTrZW8Vkj`

### Git Commands
```bash
# Add changes
git add .

# Commit with message
git commit -m "Your commit message"

# Push to current branch
git push -u origin claude/initialize-project-011CULA9hCWjZNaWTrZW8Vkj
```

## Project Structure (To Be Established)

Once game engine is selected, establish:

### For Unreal Engine 5:
```
harbringer/
├── Content/               # Game assets
│   ├── Blueprints/       # Game logic
│   ├── Models/           # 3D meshes
│   ├── Materials/        # Shaders and materials
│   ├── Audio/            # Sound effects and music
│   ├── UI/               # HUD and menus
│   └── Maps/             # Levels/scenes
├── Source/               # C++ source code (if used)
├── Config/               # Project configuration
└── Plugins/              # Third-party plugins
```

### For Unity (Modern 3D):
```
harbringer/
├── Assets/
│   ├── Scripts/          # C# game logic
│   ├── Models/           # 3D meshes
│   ├── Materials/        # Shaders and materials
│   ├── Audio/            # Sound effects and music
│   ├── Scenes/           # Game levels
│   └── Prefabs/          # Reusable game objects
├── Packages/             # Package manager dependencies
└── ProjectSettings/      # Unity configuration
```

### For Unity (Retro Hybrid) ⭐ **RECOMMENDED**:
```
harbringer/
├── Assets/
│   ├── Sprites/          # Pixel art assets
│   │   ├── Cockpit/      # Cockpit UI elements
│   │   ├── HUD/          # Gauges, radar, indicators
│   │   └── Effects/      # Screen glitches, static
│   ├── Models/           # Low-poly 3D (100-200 tris)
│   │   ├── Debris/       # Space junk
│   │   ├── Terrain/      # Planet surface chunks
│   │   └── Ship/         # Player vessel
│   ├── Materials/
│   │   ├── FlatShading.mat    # Retro 3D material
│   │   └── PixelPerfect.mat   # Sprite material
│   ├── Scripts/
│   │   ├── Flight/       # Ship controls
│   │   ├── Weather/      # Particle systems
│   │   └── UI/           # HUD management
│   ├── Audio/
│   │   ├── Music/        # Chiptune tracks (OGG)
│   │   ├── SFX/          # Retro sound effects (WAV)
│   │   └── Ambience/     # Drones, rumbles
│   └── Scenes/
│       ├── Phase1_Orbital.unity
│       ├── Phase2_Descent.unity
│       └── Phase3_Escape.unity
├── Packages/             # URP, Input System
└── ProjectSettings/
```

## Development Commands (To Be Added)

After game engine setup, add commands for:
- Building for iOS device
- Building for iOS simulator
- Running tests
- Packaging for App Store
- Asset import pipeline

## iOS Platform Requirements

### Modern 3D Approach
- iOS 15.0+
- iPhone 12 Pro or newer
- iPad Pro (M1) or newer
- Metal API support required
- 60 FPS @ 1080p (iPhone), 60 FPS @ native resolution (iPad Pro)
- < 2GB RAM footprint

### Retro Hybrid Approach ⭐ **RECOMMENDED**
- iOS 13.0+
- iPhone 8 or newer (wider device support)
- iPad Air 2 or newer
- 60 FPS on iPhone 8+ (30 FPS acceptable for retro feel)
- Render at 640x448, upscale to device resolution
- < 500MB RAM footprint
- Touch controls + MFi controller support

## Architecture Notes (To Be Developed)

Future sections to add as development progresses:
- Flight physics system architecture
- Weather simulation pipeline
- Procedural debris generation
- Audio system structure
- Save/load system
- Performance optimization strategies

## Development Phases

### Modern 3D Approach (12 Months)
- **Phase 1 (Months 1-3):** Prototype - Core flight physics, basic debris field
- **Phase 2 (Months 4-6):** Vertical Slice - Atmospheric flight, weather, landing
- **Phase 3 (Months 7-9):** Complete Loop - Escape sequence, threat, integration
- **Phase 4 (Months 10-12):** Polish - iOS optimization, QA, App Store submission

### Retro Hybrid Approach ⭐ **RECOMMENDED** (6-9 Months)
- **Month 1:** Core flight prototype + low-poly debris
- **Month 2:** Pixel art cockpit + HUD implementation
- **Month 3:** Phase 1 complete (orbital navigation)
- **Month 4:** Atmospheric flight + weather systems
- **Month 5:** Phase 2 complete (landing mechanics)
- **Month 6:** Phase 3 complete (escape sequence)
- **Months 7-8:** Integration, polish, optimization
- **Month 9:** QA, release prep, App Store submission

## Important Conventions (To Be Established)

Once development begins, document:
- Naming conventions for assets
- Code style guidelines
- Git commit message format
- Branch naming strategy
- Code review process
