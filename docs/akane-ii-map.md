# Akane II — Map Layout Spec

Companion to [akane-ii-design.md](akane-ii-design.md) (§4 The Arena Map).

> This is a **paper spec** for level designers. It fixes the structure (zones, routes, traversal, spawns, secrets) and leaves the exact geometry to a graybox pass. Sizes and distances are starting values **[TBD]**.

## Contents

1. [Overall shape](#1-overall-shape)
2. [Zone-by-zone](#2-zone-by-zone)
3. [Route graph](#3-route-graph)
4. [Ziplines and launch points](#4-ziplines-and-launch-points)
5. [Spawn points and navigation tags](#5-spawn-points-and-navigation-tags)
6. [Secrets catalogue](#6-secrets-catalogue)
7. [Boss arenas](#7-boss-arenas)
8. [Level design rules and checks](#8-level-design-rules-and-checks)

---

## 1. Overall shape

A single connected **vertical district** of Mega-Tokyo. The ground is at the bottom, the shrine at the top, and a hidden network threads through all of it.

- **Size:** about **6 screens wide and 5 screens tall** (a screen being one 16:9 view at the standard zoom) **[TBD]**. Narrower at the top (Shrine Heights).
- **Spawn and start:** Akane starts at the **center of the Neon Plaza.**
- **Vertical order, bottom to top:** Underpass Canals (below ground level), Neon Plaza (ground), Rooftop Signage (mid to high), Shrine Heights (top). The Hidden Network is threaded through all four.

```
            [ Shrine Heights ]            <- top: shrine, plateau, bell
              /     |      \
     Z-A (long zipline)  U-2 (updraft)  ladder
        /           |           \
   [ Rooftop Signage W ]--Z-B--[ Rooftop Signage E ]
        |  \          crane (Demolisher)   |   \
     Z-C   fire escape               service lift (one-way up, after use)
        |                                  |
   [ Neon Plaza W ]--[ Plaza center ]--[ Neon Plaza E ]   <- start
        |        \         |         /        |
     stairs    manhole   U-1        stairs   drop gate
        |                                     |
   [ Canals W ]--------[ Canals E ]------[ Floodgate chamber ]
        \                  |                 /
         =====  Hidden Network (vents, shafts, secret rooms)  =====
```

---

## 2. Zone-by-zone

### 2.1 Neon Plaza (ground hub)

- **Role:** the start, the widest and flattest area, and the easiest to read. Players learn movement and the first enemies here.
- **Layout:** a central square with food stalls and neon signs, three alley exits (north, west, east), stairs down to the Canals on both sides, and a fire escape and ladders up to the Rooftops.
- **Cover:** food stalls, vending machines and low walls. Enough cover for Shooters and for Akane, none that blocks every sightline.
- **Accent hue:** neon pink.
- **Landmark:** a giant rotating neon fish sign over the square.
- **Traversal:** short zipline hops between signs (Z-D), one updraft (U-1) to the lower Rooftops, stairs and a manhole down.

### 2.2 Rooftop Signage (mid to upper)

- **Role:** the main combat and traversal playground, with the largest zipline network and the most vertical variety.
- **Layout:** two rooftop clusters (West and East) linked by bridges and ziplines, covered in giant signs that can be climbed, walked on and shot out. A central **crane** (the Demolisher's rig) stands between them.
- **Cover:** sign backs, water tanks and chimneys. Plenty of high-ground spots for Archers.
- **Accent hue:** electric blue.
- **Landmark:** a huge vertical kanji sign, visible from most of the map.
- **Traversal:** ziplines Z-A, Z-B and Z-C, springs, an updraft (U-2) to the Shrine, climbable sign frames, and a **service lift** (one-way up, after it is activated from below).

### 2.3 Shrine Heights (top)

- **Role:** the highest tier, a quieter space with a rooftop shrine and an open **plateau** that hosts the Katsuro fight. Hardest to reach, and a rewarding place to camp for snipers.
- **Layout:** a narrow approach (stairs, a ladder and the long zipline) leading to a wide open plateau with a torii gate, a bell, stone lanterns and a small shrine building.
- **Cover:** lanterns and the torii gate pillars only. Mostly open.
- **Accent hue:** warm gold.
- **Landmark:** the red torii gate against the skyline.
- **Traversal:** a long motorized zipline up (Z-A), an updraft (U-2), a ladder, and a shaft down to the Hidden Network (with a hidden ladder back up).

### 2.4 Underpass Canals (below ground)

- **Role:** tight corridors, ambush spots and a rhythm of water. A contrast to the open Plaza and Rooftops.
- **Layout:** tunnels and canal channels with walkways on both sides, a few bridges, drain mouths, and a large **floodgate chamber** (the Warden's arena).
- **Cover:** pipes and pillars. Many blind corners, good for Phantoms and Skirmishers.
- **Accent hue:** deep teal.
- **Landmark:** the floodgate wheel, visible down the main channel.
- **Traversal:** slides and chutes down, a spring up to the Plaza underside (U-3), narrow ladders, and water crossings.

### 2.5 Hidden Network (threaded through all zones)

- **Role:** secrets, shortcuts and ambush routes. It is never required, and is always an option.
- **Layout:** maintenance shafts, vents, service corridors and a few secret rooms (including the server room and the old dojo). It links to each zone through at least two entrances.
- **Cover:** tight, and mostly corridors.
- **Accent hue:** shared with the zone it connects to near the entrance, shifting to a dim white deeper in.
- **Traversal:** vents (crawl), shafts (climb), and a one-way drop that lands in the Canals.

---

## 3. Route graph

Direct connections between zones, with direction. "Both" means walkable either way.

| From - To | Routes |
|---|---|
| Plaza - Rooftops | Fire escape (both), ladders (both), **U-1 updraft** (up), **Z-H** (up), **Z-C** (down) |
| Plaza - Canals | Stairs west (both), stairs east (both), drop gate (down), **U-3** (up) |
| Plaza - Hidden Network | Manhole (both) |
| Rooftops - Shrine Heights | **U-2 updraft** (up), ladder (both), **Z-A** (up), **Z-E** (down) |
| Rooftops - Hidden Network | Roof vent (down), **U-4** secret updraft (up) |
| Rooftops - Canals | Service lift (up, after it is activated from below), **Z-F** (down) |
| Canals - Hidden Network | Drain vents (both), maintenance ladder (both) |
| Shrine Heights - Hidden Network | Maintenance shaft (down), hidden ladder from the old dojo (up) |

**Redundancy check.** Every pair of zones has at least two routes that share no intermediate zone, in both directions:

| Pair | Route 1 | Route 2 |
|---|---|---|
| Plaza - Rooftops | Direct (fire escape, ladders) | Via Canals (stairs, then service lift up or Z-F down) |
| Plaza - Canals | Stairs west | Stairs east |
| Plaza - Hidden | Manhole | Via Canals (stairs, then vents) |
| Plaza - Shrine | Via Rooftops (fire escape, then U-2) | Via Hidden (manhole, then the old dojo ladder) |
| Rooftops - Canals | Service lift / Z-F | Via Plaza (fire escape, then stairs) |
| Rooftops - Shrine | U-2 updraft | Ladder (or Z-A) |
| Rooftops - Hidden | Roof vent / U-4 | Via Canals (Z-F, then vents) |
| Canals - Hidden | Drain vents | Maintenance ladder |
| Canals - Shrine | Via Hidden (vents, then the dojo ladder up) | Via Plaza and Rooftops (stairs, fire escape, U-2) |
| Hidden - Shrine | Maintenance shaft down / dojo ladder up | Via Rooftops (roof vent or U-4, then U-2) |

This redundancy is required by the Demolisher's persistent damage rule (see §8).

---

## 4. Ziplines and launch points

### 4.1 Ziplines

Ziplines are the signature fast route. Most descend, and **upward travel uses launch points, climbs and gadgets.**

| ID | Route | Direction | Length **[TBD]** | Notes |
|---|---|---|---|---|
| **Z-A** | Rooftop East (high) to Shrine approach | One-way up (motorized rising cable) | Long | The long scenic line. Can be **cut** by the Hunter or Demolisher |
| **Z-B** | Rooftop West to Rooftop East | Two-way (motorized) | Medium | Passes the crane. Cut by the Demolisher in phase 2 |
| **Z-C** | Rooftop West to Plaza West | One-way down | Medium | Fast escape to the ground |
| **Z-D** | Plaza sign to sign (three short hops) | Two-way | Short | Used by Zipline Raiders to enter the Plaza |
| **Z-E** | Shrine plateau edge to Rooftop East | One-way down | Medium | The return from the top. Z-A and Z-E together form a loop |
| **Z-F** | Rooftop East to a Canals roof opening | One-way down | Short | A shortcut into the Canals |
| **Z-G** | Hidden Network (inside the server room) | Two-way | Short | A secret line |
| **Z-H** | Plaza East to Rooftop West low | One-way up (motorized) | Short | A starter line for new players |

Rules:

- Every zipline has two **anchors** that can be cut by the sword (for boss events) or shot. Cut lines **reset after 20 seconds** unless a boss event says otherwise.
- Zipline Raiders use ziplines Z-A, Z-B, Z-D and Z-E.
- No zipline crosses a boss arena's central fighting space.

### 4.2 Launch points

| ID | Location | Takes Akane to | Notes |
|---|---|---|---|
| **U-1** | Plaza north alley | Lower Rooftops | The first launch point players find |
| **U-2** | Rooftop East edge | Shrine Heights approach | An alternative to Z-A |
| **U-3** | Canals channel vent | Plaza underside / drop gate | Returns players to the Plaza |
| **U-4** | Hidden Network (secret) | Rooftop vent | A secret way up |
| **S-1, S-2** | Rooftop springs | Higher signage | Short hops over gaps |

---

## 5. Spawn points and navigation tags

### 5.1 Spawn points

Enemies spawn **out of sight** at least 12 tiles from Akane, weighted away from where she has been recently (see §5.2 of the main doc).

| Zone | Ground spawns | Special spawns |
|---|---|---|
| Neon Plaza | 3 (north, west and east alleys) | 1 high anchor for Zipline Raiders (Z-D) |
| Rooftop Signage | 3 (ladders, a helipad, a stairwell) | 2 high anchors (Z-B, Z-A) |
| Shrine Heights | 1 (the approach stairs) | 1 perch for Snipers |
| Underpass Canals | 3 (drain mouths) | none |
| Hidden Network | 2 (vent exits) | 3 ambush nodes for Phantoms |

### 5.2 Navigation tags

Level designers mark these on the map for the AI:

- **Perch nodes:** high spots for Archers and Snipers (about 10 across the map).
- **Ambush nodes:** hidden spots for Phantoms (about 6, mostly in the Hidden Network and signage).
- **Staging points:** side-route waypoints for Pincers (about 2 per zone).
- **Cover nodes:** cover spots for Shooters and Shieldbearer lines.
- **Zipline anchors:** linked to ride and cut logic.
- **Boss anchors:** fixed locations that bosses use.

Every traversal tool (ziplines, climbs, drops, launch points, vents) must have a matching navigation link, or the flanking AI cannot use it.

---

## 6. Secrets catalogue

Twelve secrets. All rewards are **non-power** (score, cosmetics, lore). Score rewards are once per run. Cosmetics and lore are once ever.

| # | Secret | Zone | How to find | Reward |
|---|---|---|---|---|
| 1 | **Koi Pond Wall** | Plaza | A cracked wall behind the pond. Hit it with the sword | 300 score + lore fragment 1 |
| 2 | **Manhole Maze** | Plaza | The manhole near the pond. Opens the Hidden Network | Access, and 200 score on first entry |
| 3 | **Vending Machine Cache** | Plaza | Slash the vending machine three times (a coin sound) | An ammo cache + 200 score |
| 4 | **Flooded Shrine** | Canals | Time the drain gate and slip through before it closes | Sword trail: *Rainwater* |
| 5 | **Pipe Whisper** | Canals | Follow a faint whisper from the pipes to a hidden alcove | Lore fragment 2 |
| 6 | **Neon Kanji** | Rooftops | Shoot out the sign's characters in the order shown by a flicker | Sword trail: *Neon Brush* |
| 7 | **Broken Sign Roost** | Rooftops | A hard climb along a collapsed sign | Outfit piece: *Rooftop Scarf* |
| 8 | **Roof Vent Drop** | Rooftops | Open the vent. A risky drop to the Hidden Network | 300 score + a shortcut |
| 9 | **Bell of the Shrine** | Shrine | Shoot the bell during a breather | 500 score + a bell chime, and the breather lasts 3 s longer |
| 10 | **Lantern Path** | Shrine | Follow the unlit lanterns, lighting each with a gun shot | Cigarette ink style: *Lantern Fire* |
| 11 | **Server Room** | Hidden | A locked room opened with a code found in the lore fragments | Lore fragments 3 to 6 (four terminals) |
| 12 | **The Old Dojo** | Hidden | Needs all fragments. Opens a sealed room | Codex entry on Ishikawa, and the **Final Scene** flashback (see the narrative section) |

**Rules**

- Secrets are never required to clear a wave, and never give a power advantage.
- Each secret has a **subtle hint** in the environment (an ink stain, a sound, an odd glow) so it rewards observation without a guide.
- Secrets near a wave's likely combat zone are safe between waves, and some (Roof Vent Drop) are intentionally risky.
- The Hidden Network is the primary home of secrets, so it always has something worth finding.

---

## 7. Boss arenas

| Boss | Arena | Notes |
|---|---|---|
| **Katsuro** | The Shrine Heights plateau | Flat, open and walled by the skyline. No ziplines cross it. Cover is only the torii pillars and lanterns |
| **The Debt Collector** | The Neon Plaza central square | Food stalls and low walls give cover and sightlines. Stalls can be destroyed by his shots |
| **The Hunter** | Rooftops, Canals and the Hidden Network | No fixed arena. A roaming range, bounded by these zones. He avoids Shrine Heights |
| **The Crimson Kite** | Rooftops and Shrine Heights | Open sky. Perches on signage and lanterns |
| **The Demolisher** | The central crane in the Rooftops | The crane stands between the two rooftop clusters. Platforms and ziplines Z-B and Z-C are destroyed during the fight |
| **The Floodgate Warden** | The floodgate chamber in the Canals | A large chamber with walkways at three heights and a central channel |

---

## 8. Level design rules and checks

- **Two independent routes between every pair of zones,** at all times, including after boss damage (the Demolisher's collapsed rooftops). A graybox review must verify this.
- **Orientation:** each zone has a landmark visible from its neighbors.
- **No dead ends** except secret rooms, which have a clear exit.
- **Combat spaces:** every zone has at least one open area wide enough for a full group to engage and flank.
- **Flank paths:** every open area has at least two side routes of different lengths, so the AI has real flanking choices.
- **Traversal pace:** a vertical crossing from the Plaza to Shrine Heights takes about 30-45 seconds with traversal tools, and over a minute without them **[TBD]**.
- **Camera:** vertical transitions have enough look-ahead for Akane to see where a zipline or updraft will land.
- **Performance:** only the current zone and its neighbors are active, to keep Switch budgets in check.
- **Readability:** accent hues are used only for set dressing and zone identity, never for telegraphs.
