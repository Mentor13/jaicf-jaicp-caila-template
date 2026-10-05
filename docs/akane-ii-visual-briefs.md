# Akane II — Visual Briefs

Companion to [akane-ii-design.md](akane-ii-design.md) (§1 Art Direction). Briefs for concept artists and animators: foundations, characters, enemies, bosses, zones and effects.

> Sizes are in pixels at the **640 x 360 base resolution.** All numbers are starting values for the art team. Akane's base design follows the original character art; this document covers only what is new or adapted. Boss and telegraph colors are reserved for threats (see §1.3).

## Contents

1. [Foundations](#1-foundations)
2. [Akane](#2-akane)
3. [Enemies](#3-enemies)
4. [Bosses](#4-bosses)
5. [Zones and environment](#5-zones-and-environment)
6. [Effects and UI visuals](#6-effects-and-ui-visuals)
7. [Animation guidelines](#7-animation-guidelines)
8. [Asset inventory](#8-asset-inventory)

---

## 1. Foundations

### 1.1 Technical targets

| Item | Target |
|---|---|
| Base resolution | **640 x 360,** scaled by whole numbers (720p, 1080p, 4K) |
| Akane's height | About **48 px** |
| Standard enemies | 40-56 px tall (Tank about 72 px) |
| Bosses | Varied by boss (see §4), from human-scale to about 4x |
| Production method | **Hand-drawn pixel sprites** with brush-stroke shading |
| Frame rate | 60 FPS gameplay. Sprite animation at 12-24 frames per second of art, with smooth timing |

### 1.2 The look

A highly unique blend of **Japanese ink wash (sumi-e)** and **modern pixel animation,** inspired in smoothness and impact by *Dead Cells*, set on a **rainy neon night in 2121.**

- **Sumi-e principles to use:** bold brush-stroke outlines on threats, tonal washes (bokashi gradients) for shading, deliberate negative space (*ma*), and one accent color at a time.
- **Pixel principles to use:** clean pixel clusters, no anti-aliased smears on sprites, strong silhouettes, high frame counts on key actions, and clear anticipation and follow-through.
- **How they meet:** sprites are drawn in pixel clusters that imitate brush stroke edges and wash tones. Backgrounds use dithered washes. Effects (kills, deflects, dashes) are brush-stroke animations.
- **Mood:** wet, dark and neon-lit. Rain and reflections add ink texture.

### 1.3 Color rules

- **Base palette:** shared across the whole game: ink black, a range of cool grays, and paper white.
- **Zone accent hue (set dressing only):** one per zone, low to medium saturation, static, never animated like a threat.

| Zone | Accent |
|---|---|
| Neon Plaza | Neon pink |
| Rooftop Signage | Electric blue |
| Shrine Heights | Jade green |
| Underpass Canals | Jade-teal |
| Hidden Network | Dim white |

- **Regular-enemy threat language:** a **vermilion and white** flare, line or ring. This is the only color for regular-enemy telegraphs and projectiles. It is never used on set dressing.
- **Boss accents** (high saturation, used only on that boss's attacks, trails and core):

| Boss | Accent |
|---|---|
| Katsuro | Hot pink |
| The Debt Collector | Coin gold |
| The Hunter | Pale violet |
| The Crimson Kite | Crimson |
| The Demolisher | Hazard orange |
| The Floodgate Warden | Deep teal |

- **Hazard marks:** black-and-white hatching (no color).
- **Destructibles:** a faint crack-line mark.
- **Night clock:** lighting deepens over the run (late night, midnight, small hours, before dawn). Telegraph colors and hazard marks keep their contrast in every lighting band.

### 1.4 Readability rules

- Threats are on a **higher-contrast layer** than backgrounds: hard ink edges on threats, soft washes on backgrounds.
- Each enemy has a **unique silhouette** at 1x scale in a crowd of 10+.
- Akane has a **distinct silhouette and reserved palette.**
- Telegraphs are visible in every lighting band and every weather state.
- Backdrops (skyline, distant towers) are visually quiet.

---

## 2. Akane

- **Base design:** follows the original character art. She is an **adult** swordswoman.
- **New in Akane II:**
  - **Standard Jacket:** the default outfit, dark and rain-wet, with a single accent shade so she reads at a glance.
  - **Wet look:** rain beads on the jacket and a subtle wet sheen (a shading pass, not a separate sprite set).
  - **Loadout visibility:** the equipped katana (7 designs) and gun (6 designs) are visible on her sprite. The gadget is a small visible detail where it makes sense (for example, a bracelet or gloves).
  - **Flow aura:** an ink aura around her that grows with the Flow tier (see §6).
  - **Outfits (6 unlockable):** Rooftop Scarf, Rain Coat, Night Courier, Gilded Jacket, Ashen Hoodie and Crimson Dojo Gi. Each keeps her silhouette and her reserved palette readable.
- **Cosmetics:** sword trails (7 unlockable plus the default) and cigarette ink styles for Dragon Slash and Dragon Slayer (7, including the default) are effects, not sprite changes.

---

## 3. Enemies

### 3.1 Shared language

- **Yakuza identity:** every enemy has at least one marker of the organization: dark suits, sunglasses, irezumi-style tattoos (drawn in ink), or cybernetic parts. Cybernetic parts increase with higher-cost enemies.
- **Role shapes** (the silhouette rule):

| Role | Shape language |
|---|---|
| **Anchor** | Wide, planted stance. A visible front (shield, plating, weapon) |
| **Pincer** | Lean, forward-leaning, asymmetrical. Built to look fast |
| **Suppressor** | Tall, still and vertical, with an obvious long weapon or optic |
| **Support** | Carries a tall object (banner, staff, controller) above the head line |
| **Special** | A distinctive unusual shape tied to how it arrives (harness, cloak, coat) |

- **Telegraph pose:** each attack has a clear wind-up pose that matches its telegraph tier (Quick 0.35 s, Standard 0.55 s, Heavy 0.8 s, Long 1.0 s). The pose must be readable even without the flare.
- **Elites** keep the base silhouette and add one clear marker (a gold coat trim, an extra weapon, a glow), so players read "stronger version" instantly.
- **Modifiers** (Hasted, Armored, Volatile, Shrouded, Vengeful) each have a fixed overlay: speed streaks, an ink plate, a glowing core, a shimmer, and a red mark.

### 3.2 Enemy briefs

| # | Enemy | Role | Height | Silhouette and key details |
|---|---|---|---|---|
| 1 | **Yakuza Guy** | Anchor / fodder | 44 px | Standard suit and sunglasses. Short blade or baton, raised overhead in the wind-up. The "baseline" body that others build on |
| 2 | **Shooter** | Suppressor | 50 px | Tall, still. Rifle arm and a glowing optic over one eye. Red laser line from the optic |
| 3 | **Skirmisher** | Pincer | 42 px | Lean, forward-leaning, light armor, twin short blades. Curved running stance and trailing coat |
| 4 | **Tank** | Anchor | 72 px | Wide, heavy plating, a visible rear plate with a seam (the weak point). Slow turning animation |
| 5 | **Lancer** | Anchor, reach | 56 px | Tall, narrow stance with a very long spear and a white sash. The spear defines the silhouette |
| 6 | **Archer** | Suppressor | 52 px | Hooded cloak and a long bow, usually on high ground. Cloak sways in the rain |
| 7 | **Shieldbearer** | Anchor | 58 px | Broad figure behind a large ink-black riot shield. The shield is the main shape |
| 8 | **Cyber Ninja** | Pincer | 50 px | Slim cybernetic body with a glowing seam. Long blade. A visible guard pose |
| 9 | **Bomber** | Suppressor | 46 px | Hunched, a bandolier of glowing charges. The charges are the identity |
| 10 | **Zipline Raider** | Special | 48 px | Hook-and-wire harness and a short blade. Appears with a visible wire |
| 11 | **Banner Caller** | Support | 52 px | Carries a tall banner with an ink-red emblem above the head line. The banner defines the shape |
| 12 | **Hexer** | Support | 52 px | White mask, a brush-like staff. Draws ink zones |
| 13 | **Drone Handler** | Support | 46 px | Wrist controller, three small drones orbiting. The drones are the identity |
| 14 | **Phantom** | Special | 50 px | Cloaked figure with a shimmer. Mostly negative space until it strikes |
| 15 | **Duelist** | Special | 54 px | Poised, in a long coat with a straight blade. A distinctive counter stance |
| 16 | **Sniper** | Suppressor | 52 px | Long rifle with a laser scope on a high perch. A steady, still pose |

### 3.3 Named elite markers

| Elite | Marker |
|---|---|
| Enforcer | Gold coat trim and a second weapon |
| Marksman | Twin optics |
| Siege Tank | Shoulder-mounted ram plates |
| Shadow Ninja | A second glowing seam and a trail |
| Naginata Master | A longer curved polearm |
| Riot Guard | A shield with crackling light |
| Fire Archer | An ember-lit bow |
| Demolition Bomber | A larger pack with a cluster of charges |

---

## 4. Bosses

Each boss is drawn at **high detail** with its own accent color (§1.3), a recognizable silhouette, and animations for **intro, idle, each move, phase break, and death.**

| Boss | Scale | Silhouette | Key visuals |
|---|---|---|---|
| **Katsuro** | Human-scale, about 52 px | Lean figure in a dark coat | Hot pink dash trail. Cybernetic upgrades grow with the tier (see below). A sword that drags a line of ink |
| **The Debt Collector** | Human-scale, about 56 px | Long coat, heavy shoulders | A floating ledger drone, a cybernetic arm cannon, gold coin-yellow shots |
| **The Hunter** | Human-scale, about 50 px | Nearly invisible: shimmering cloak lines | Pale violet flicker. Fully visible only at the moment of a strike or when revealed |
| **The Crimson Kite** | About 3x (aerial, wingspan about 150 px) | Winged drone-mech | Red-and-white frame, long rotor blades like brush strokes. Crimson dive lines |
| **The Demolisher** | About 4x (a crane rig, about 200 px) | Exo-suit pilot in a crane cab with a wrecking ball | Hazard orange impact circles. The cab is a clear target |
| **The Floodgate Warden** | About 3x (about 150 px) | Bulky waterproof exo-rig with a pump cannon | Deep teal water gauge on his chest. The gauge shows the tide state |

**Katsuro by tier** (visual progression, matching the move tiers)

| Tier | Waves | Visual change |
|---|---|---|
| 1 | 10-29 | Base design |
| 2 | 30-59 | Adds a holstered pistol and a second cybernetic part |
| 3 | 60-99 | More visible cybernetics. A longer coat tear and a brighter trail |
| 4 | 100+ | A fully rebuilt look. The sword gains a glowing edge |
| 5-6 | 150+, 200+ | Additional glowing seams. Trails take on a second layer |

**Boss visual rules**

- Every attack has a pose, a flare in the boss's color, and a fixed telegraph time.
- The **vulnerability window** is shown by a clear visual state (an exposed core, a stagger pose, a glow), in the boss's color.
- **Phase pips** are shown in the boss's color on the HUD.
- **Intro:** the title card appears in brush lettering, with the boss's department tag in small type.
- **Death:** a freeze-frame ink slash, then the boss dissolves into an ink splash in its accent color.

---

## 5. Zones and environment

Each zone uses the shared ink base plus its accent (§1.3). Sub-areas are listed in the map design document.

| Zone | Mood | Key materials and props | Landmark |
|---|---|---|---|
| **Neon Plaza** | Busy, wet, lit | Food stalls, vending machines, awnings, neon signs, a koi pond | A giant rotating neon fish sign |
| **Rooftop Signage** | Windswept, electric | Water tanks, antennas, giant signs, a crane, bridges | A huge vertical kanji sign |
| **Shrine Heights** | Quiet, open, cold | Stone lanterns, a torii gate, a bell, a small shrine | A red torii gate against the skyline |
| **Underpass Canals** | Dim, echoing, wet | Pipes, tunnels, canals, floodgates, pump machinery | The floodgate wheel |
| **Hidden Network** | Cramped, humming | Vents, cables, shafts, server racks, a sealed dojo | A lit server room door |

**Rules**

- Walkable surfaces: hard ink edges. Climbable surfaces: a consistent grip-line mark. Destructible objects: a faint crack-line mark.
- Backgrounds use soft, low-contrast washes and **dithering** for depth, with 3-4 parallax layers on PC and 2-3 on Switch.
- **Weather:** baseline light rain; the Rain Shower event is a downpour; reflections of neon on wet surfaces.
- **Night clock:** the sky and lighting shift over the run, from dusk-blue to a pale pre-dawn glow that never grows.
- The **Old Dojo** is a distinct, warm-lit secret space: paper walls and wood, in contrast with the rest of the city.

---

## 6. Effects and UI visuals

| Effect | Brief |
|---|---|
| **Kill splash** | A bold ink splash in the enemy's base color (bold on kills only) |
| **Hit / deflect** | A short brush-stroke spark. Deflect adds a white ring |
| **Ink Step** | A brush-stroke afterimage of Akane and a very short slow-motion beat |
| **Dash** | A thin ink streak. Boots change its length and shape |
| **Flow aura** | An ink aura around Akane. Tier I faint, tier II brighter, tier III bold with drips. A pulse warns before a tier drops |
| **Dragon Slash** | A bold ink streak along the dash path. Its color follows the equipped cigarette ink style |
| **Dragon Slayer** | A screen-wide ink wash that kills in a large radius. Also follows the cigarette ink style |
| **Telegraphs** | Vermilion and white for regular enemies, and the boss's accent for bosses. Line, ring and flare shapes per telegraph tier |
| **Hazards** | Black-and-white hatching with an arc or steam animation |
| **Destruction** | Ink splash and short dust. Debris clears from the walking plane in 2 seconds |
| **Zipline / updraft** | A bright ink stroke for ziplines and upward ink streaks for updrafts |
| **Off-screen threat smears** | Ink smears at the screen edge, shaped by threat type (see the run and narrative document) |
| **HUD** | Minimal brush-drawn elements that hide when unused |
| **Story beat card** | An ink silhouette image with brush lettering |

**Cigarette ink styles (7)** change the color and texture of the two specials: Ink Black, Wildfire, Rain, Crimson, Lantern Fire, Ash and Moonlight.

---

## 7. Animation guidelines

Starting frame counts for the art team. Responsiveness beats animation completeness: anticipation frames can be canceled by deliberate player actions.

| Animation | Frames **[TBD]** | Notes |
|---|---|---|
| Idle | 8-10 | Subtle breathing and rain on the jacket |
| Run | 10 | A strong silhouette change per foot plant |
| Jump / fall / land | 4 / 4 / 3 | Short landing recovery only for long falls |
| Dash | 5-6 | Few frames, stretched and smeared |
| Sword attack (per katana) | 6-9 | Startup / active / recovery matching the katana tables |
| Gun fire (per gun) | 3-5 | Recoil visible, especially the Vicious S36 |
| Ink Step | 6 | Reads even in slow motion |
| Human shield grab / hold / throw | 6 / 4 loop / 6 | Grab must be readable |
| Zipline / climb / grapple | 4 loop / 6 loop / 5 | Responsive entry and exit |
| Death (Akane) | 8 | Short and clean, so restarts stay fast |

**Enemy and boss animation**

- Every enemy has: **idle, move, wind-up pose per attack, attack, recovery, hit and death.**
- Wind-up time matches the telegraph tier exactly.
- Recovery poses clearly show the **weak window.**
- Bosses add: intro, each move, phase break and death.

**Principles:** strong anticipation, short but visible follow-through, and smears or squash and stretch on fast moves (in the spirit of *Dead Cells*).

---

## 8. Asset inventory

Rough counts for scoping (animation sets, not individual frames).

| Group | Count | Notes |
|---|---|---|
| Akane core set | 1 | About 20 animations |
| Akane loadout overlays | 7 katanas, 6 guns, 6 mod-capable gadgets (visible parts), 4 boots | Layered on the core set |
| Outfits | 6 unlockable + default | Recolor and detail passes |
| Standard enemies | 16 | Each about 8-12 animations |
| Named elites | 8 | Base sprite plus markers and one extra animation each |
| Modifier overlays | 5 | Reused across enemies |
| Bosses | 6 | Katsuro has 6 tier looks. The environmental bosses are large multi-part sprites |
| Zone tilesets and backdrops | 5 | Plus lighting bands for the night clock |
| Destructible sets | About 15 object types | With broken states |
| Effects | About 25 distinct effects | See §6 |
| UI / HUD | About 30 elements | Brush-drawn |
| Story beat and codex images | 4 beat silhouettes, Dojo Memory (about 8 images) | Ink illustrations |
