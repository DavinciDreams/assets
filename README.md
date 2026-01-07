# HyperScape Assets

Static game assets for the HyperScape 3D RPG. This repo is cloned into the main project and served via CDN.

## Directory Structure

```
assets/
├── audio/              # Game audio
│   ├── music/          # Background music tracks
│   │   ├── intro/      # Intro themes
│   │   ├── normal/     # Exploration tracks
│   │   ├── combat/     # Battle themes
│   │   └── draft/      # WIP tracks
│   ├── soundeffects/   # SFX library
│   └── voice/          # NPC dialogue audio + voice profiles
│
├── avatars/            # Player avatar models (4 VRM files)
│
├── emotes/             # Character animations (27 GLB clips)
│                       # idle, walk, run, jump, combat, dances, etc.
│
├── models/             # Game object models (42 directories)
│                       # Flat structure - see Models section below
│
├── vegetation/         # World vegetation
│   ├── garden-trees/   # Garden tree variants
│   ├── jungle-trees/   # Jungle/palm trees
│   ├── bushes/         # Bush models
│   ├── flowers/        # Flower models
│   ├── ferns/          # Fern models
│   ├── ivy/            # Ivy models
│   └── fallen_trees/   # Dead/fallen trees
│
├── rocks/              # Rock formations
│   ├── pathway_rocks/  # Pathway rock variants
│   ├── round_rocks/    # Round rock variants
│   ├── tall_rocks/     # Tall rock formations
│   └── *.glb           # Individual large rocks
│
├── grass/              # Grass/foliage models for terrain
│
├── trees/              # Standalone tree models
│
├── terrain/            # Terrain assets
│   └── textures/       # PBR texture atlases
│       ├── dirt/
│       ├── dirt_ground/
│       ├── grass/
│       ├── rock/
│       ├── leafy_texture/
│       ├── stylized_grass/
│       ├── stylized_snow/
│       └── stylized_stone/
│
├── textures/           # Additional textures
│   ├── noise/          # Noise maps
│   └── terrain/        # Terrain textures
│
├── water/              # Water effects
│   ├── water-shader/   # Shader textures + cubemaps
│   └── water-particle/ # Particle effects
│
├── world/              # Base environment
│                       # Skybox HDR, base terrain mesh
│
├── manifests/          # Game configuration (10 JSON files)
│                       # See Manifests section below
│
├── web/                # Runtime dependencies
│                       # PhysX WASM, TypeScript defs, fonts
│
├── luts/               # Color grading look-up tables
│
├── noise/              # Simplex noise textures
│
├── cache/              # Cached manifest data
│
└── *.wasm, *.js        # PhysX runtime (root copies)
```

## Models Directory

The `models/` directory uses a **flat structure** with 42 individual model directories (not nested by category).

### Model Categories

**Weapons:**
- `sword-base`, `sword-bronze`, `sword-steel`, `sword-mithril`
- `bow-base`, `bow-oak`, `bow-willow`, `bow-wood`
- `arrows-base`, `arrows-bronze`
- `shield-base`, `shield-bronze`, `shield-steel`, `shield-mithril`
- `mace`, `mace-dragon`

**Armor:**
- `chainbody`, `chainbody-dragon`
- `spiked-helmet`

**Tools:**
- `pickaxe`, `pickaxe-bronze`, `pickaxe-steel`, `pickaxe-mithril`
- `hatchet-base`, `hatchet-bronze`
- `fishing-rod-base`, `fishing-rod-standard`

**Resources:**
- `logs-base`, `logs-wood`
- `ore-copper`, `ore-tin`
- `tree`, `basic-reg-tree`, `basic-reg-tree-stump`

**NPCs:**
- `human`, `goblin`, `imp`, `troll`, `thug`

**Environment:**
- `grass`, `vegetation`, `rocks`

### Model Directory Contents

Each model directory contains:

```
model-name/
├── {model-name}.glb       # 3D model (GLTF binary)
├── metadata.json          # Generation/variant metadata
└── concept-art.png        # Reference artwork
```

**NPCs additionally have:**
```
├── {model-name}.vrm       # VRM humanoid model
├── {model-name}_rigged.glb # Rigged GLB variant
└── animations/            # Walking, running animations
```

**Dragon armor has:**
```
├── sprites/               # 8-angle sprite sheets (0deg-315deg)
└── sprite-metadata.json   # Sprite configuration
```

## Manifest Files

The `manifests/` directory contains 10 JSON configuration files:

| File | Purpose |
|------|---------|
| `items.json` | Item database - weapons, armor, tools, consumables, resources |
| `npcs.json` | NPC definitions - stats, dialogue, loot tables, spawns |
| `resources.json` | Harvestable resources - trees, ore deposits, fishing spots |
| `tools.json` | Tool definitions - pickaxes, hatchets, fishing rods |
| `biomes.json` | Terrain biome parameters - vegetation, colors, heights |
| `world-areas.json` | Named zones - boundaries, NPC placements, spawn points |
| `stores.json` | Shop inventories - items, pricing, buyback rates |
| `music.json` | Audio track metadata - paths, durations, categories |
| `vegetation.json` | Vegetation asset catalog - weights, scales, distributions |
| `buildings.json` | Building definitions (reserved for future use) |

See `manifests/README.md` for detailed schema documentation.

## File Formats

| Type | Format | Notes |
|------|--------|-------|
| 3D Models | `.glb` | GLTF binary |
| Avatars/NPCs | `.vrm` | VRM humanoid format |
| Audio | `.mp3` | Compressed audio |
| Textures | `.png`, `.jpg` | Standard images |
| HDR | `.hdr`, `.ktx2` | Skybox/environment maps |
| LUTs | `.ktx2`, `.CUBE`, `.3dl` | Color grading |
| Config | `.json` | Game data |
| Runtime | `.wasm`, `.js`, `.d.ts` | PhysX physics engine |
| Fonts | `.woff2` | Web fonts |

## Git LFS

Large binary files (`.glb`, `.png`, `.mp3`, `.vrm`, `.wasm`) are tracked with Git LFS. Ensure LFS is installed before cloning:

```bash
git lfs install
git clone <repo-url>
```

## Repository Statistics

| Category | Count |
|----------|-------|
| Model directories | 42 |
| Emote animations | 27 |
| Avatar models | 4 |
| Manifest configs | 10 |
| Vegetation subdirs | 7 |
| Terrain texture types | 8 |
