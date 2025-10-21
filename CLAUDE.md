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

- **GAME_DESIGN_DOCUMENT.md** - Complete game design specification including:
  - Core gameplay mechanics
  - Technical requirements
  - Asset pipeline recommendations
  - Development roadmap

## Project Status

**Current Phase:** Pre-development / Design
- Game design document completed
- Game engine not yet selected (Unreal Engine 5 recommended, Unity alternative)
- No implementation code yet
- Repository structure to be established

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

### Game Engine (Choose One)
**Primary Recommendation: Unreal Engine 5**
- Lumen (real-time global illumination)
- Nanite (high-detail geometry)
- Niagara (VFX for weather systems)
- MetaSounds (procedural audio)
- Native iOS Metal API support

**Alternative: Unity**
- Universal Render Pipeline (URP)
- Cinemachine for camera control
- Shader Graph for custom materials

### 3D Asset Creation
- **Blender** - Primary 3D modeling (free)
- **Substance Painter** - PBR texturing
- **ZBrush** - High-detail sculpting (optional)

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

### For Unity:
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

## Development Commands (To Be Added)

After game engine setup, add commands for:
- Building for iOS device
- Building for iOS simulator
- Running tests
- Packaging for App Store
- Asset import pipeline

## iOS Platform Requirements

### Minimum Specifications
- iOS 15.0+
- iPhone 12 Pro or newer
- iPad Pro (M1) or newer
- Metal API support required

### Performance Targets
- 60 FPS @ 1080p (iPhone)
- 60 FPS @ native resolution (iPad Pro)
- < 2GB RAM footprint
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

### Phase 1: Prototype (Months 1-3)
- Core 6DoF flight physics
- Basic debris field navigation
- Placeholder assets

### Phase 2: Vertical Slice (Months 4-6)
- Atmospheric flight model
- Weather system implementation
- Landing mechanics
- Visual polish

### Phase 3: Complete Loop (Months 7-9)
- Escape sequence
- System failure mechanics
- Threat implementation
- Integration

### Phase 4: Polish (Months 10-12)
- iOS optimization
- QA and bug fixing
- Audio mastering
- App Store submission

## Important Conventions (To Be Established)

Once development begins, document:
- Naming conventions for assets
- Code style guidelines
- Git commit message format
- Branch naming strategy
- Code review process
