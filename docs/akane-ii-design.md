# Akane II — Design Document

**Studio:** Ludic Studios
**Protagonist:** Sugahara Akane
**Status:** Draft v0.1 (pre-production)
**Scope:** Design only. No implementation is covered here.

> Names for enemies, bosses, moves and zones are **working titles**. Items marked **[TBD]** need a decision or input from the team (several depend on the original *Akane*).

---

## Contents

1. [Art Direction](#1-art-direction)
2. [Vision and Pillars](#2-vision-and-pillars)
3. [Core Combat and Movement](#3-core-combat-and-movement)
4. [The Arena Map](#4-the-arena-map)
5. [Wave System](#5-wave-system)
6. [Enemies](#6-enemies)
7. [Bosses](#7-bosses)
8. [Progression and Scoring](#8-progression-and-scoring)
9. [Story and Presentation](#9-story-and-presentation)
10. [Risks and Open Questions](#10-risks-and-open-questions)

---

## 1. Art Direction

A highly unique pixel art style that blends **Japanese ink wash (sumi-e)** with **modern pixel sprite animation**, with some inspiration from *Dead Cells*.

**Goals**

- Ink wash sensibility: tonal washes, bold brush-stroke silhouettes, deliberate negative space, and color used sparingly as an accent.
- Modern pixel animation: high frame counts, smooth interpolation-feeling motion, strong anticipation and follow-through, and impactful hit-stop and screen response (the *Dead Cells* influence).
- Readability over beauty when the two conflict. A one-hit-kill game is only fair if the player can read every threat at a glance.

**Readability rules (non-negotiable)**

- Enemies and projectiles always sit on a **higher-contrast layer** than the background. Backgrounds use soft, low-contrast washes; threats use hard ink edges.
- **Attack telegraphs** use a consistent visual language across all enemies and bosses (for example, a brush-stroke flare in a reserved accent color before any lethal attack). That accent color is used for nothing else.
- Background parallax and ink-bleed effects are kept out of the combat plane.
- Akane has a distinct silhouette and a reserved palette, visible even among 10+ enemies.

**Open art questions**

- Ink wash effect in motion: how much animated bleeding or splatter on hits and kills? **[TBD]**
- Color palette per map zone versus one unified palette. **[TBD]**

---

## 2. Vision and Pillars

*Akane II* is an arcade action game about fast, lethal, stylish combat. Akane and every enemy die in one hit, so mastery comes from movement, positioning and timing.

**Pillars**

1. **One-hit-kill momentum.** Every fight is fast and decisive. Death is quick, and restarting is quicker.
2. **A map worth mastering.** One large, vertical, multi-path level that rewards exploring and experimenting with routes.
3. **Fair but smart opposition.** Enemies flank, cooperate and adapt, but always telegraph lethal attacks. No bugs, no frozen enemies, no cheap deaths.
4. **Expressive movement.** Dash, precise dodge, traversal and human shields should all feel responsive and give players room to show style.
5. **Ink and motion.** The game should look and feel unlike any other pixel art game.

**What changed from *Akane***

| *Akane* | *Akane II* |
|---|---|
| Single-floor arcade arena | One huge, vertical, multi-path level |
| 4 basic enemy types | ~16 enemy types |
| 1 boss | Multiple bosses across 3 types |
| Enemies could forget to attack or bug out | Robust, readable AI with flanking |
| Dash | Dash plus precise dodge plus human shields |

**Not in scope:** a campaign or story mode. It was cut because it did not fit the arcade design. Bosses live inside arcade mode instead.

---

## 3. Core Combat and Movement

### 3.1 Toolkit

Akane keeps the original structure: **sword + gun + one gadget** **[TBD: confirm exact gun behavior (ammo, reload, range) and gadget(s) from the original]**.

- **Sword:** primary close-range kill tool.
- **Gun:** ranged option with limited ammo or cooldown **[TBD]**. Keeps flyers and distant enemies answerable.
- **Gadget:** one slot, carried over from the original. A single gadget keeps loadouts simple **[TBD: type and whether it is fixed or chosen at run start]**.

### 3.2 Feel and responsiveness

The original's core was strong, so Akane II tunes it rather than redesigns it.

- **Input buffering and cancel windows:** attacks, dashes and dodges can be buffered and cancel out of recovery frames. Inputs should rarely feel dropped.
- **Coyote time and jump forgiveness** for the new vertical map.
- **Hit-stop and screen response** are short, consistent and tunable. Kills feel crunchy without costing momentum.
- **Animation priority:** responsiveness beats animation completeness. Anticipation frames can be skipped by actions the player intentionally cancels into.
- **Target:** input-to-visible-response within ~2 frames at 60 FPS **[TBD: validate in prototyping]**.

### 3.3 Dash (carried over)

A short, fast movement burst. Keeps its role as the player's basic repositioning and gap-closing tool. Limited by a short cooldown or charge system **[TBD]**.

### 3.4 Precise dodge: *Ink Step* (working title)

The new, more precise defensive move that adds depth beyond the dash.

- **How it works:** a tight-window dodge timed against an incoming attack. Success triggers a short slow-motion beat, a brush-stroke afterimage and a reward.
- **Reward:** refunds the dash, and opens a brief counter-attack window or a safe reposition. It never grants invulnerability beyond the dodge itself.
- **Design constraint:** attack timing must be consistent. Every enemy telegraph has a fixed, learnable duration so the window is fair across the roster.
- **Risk:** a failed dodge is a normal hit, which means death. Dash remains the safe option. Ink Step is the high-skill, high-reward one.
- **Directional variants:** [TBD: single dodge or directional (forward/back/vertical)].

### 3.5 Human shields

Akane grabs an enemy and uses them as a shield.

- **Grab:** a short-range grab that targets standard-sized enemies. Not usable on bosses or heavy enemy types.
- **Effect:** the held enemy absorbs hits from the front. Enemy projectiles that strike the shield kill it; melee hits from enemies may also hit the shield rather than Akane, depending on enemy type.
- **Hold limit:** a short hold timer (about 3–4 seconds) or a limited number of absorbed hits, so shields are a tool and not a permanent state **[TBD]**.
- **Mobility:** Akane moves at reduced speed and cannot dash while holding a shield. She can still attack with the gun or release the shield.
- **Release options:** **throw** (the enemy becomes a projectile that damages others on impact) or **drop**.
- **Abuse prevention:** enemies with area attacks, armored enemies and some special types ignore or break the shield. The grab has a cooldown.
- **Enemy response:** AI treats shield-holding as a state. Ranged enemies reposition for a flank rather than shooting into the shield.
- **Why it works:** it creates a new risk/reward question for crowded fights without breaking the one-hit-kill rhythm.

---

## 4. The Arena Map

One large, vertical single-level map that replaces the original single floor. It is the centerpiece of arcade mode.

### 4.1 Design goals

- **Multiple approaches:** every major area has at least two ways in (ground, high route, hidden route).
- **Verticality:** multiple tiers connected by climbing, ledges, ziplines and drops.
- **Secrets:** hidden routes, optional rooms and traversal shortcuts reward curiosity.
- **Fast traversal:** ziplines and similar tools let players cross the map quickly, and let enemies and bosses use them as well, in controlled cases.
- **Readable at a glance:** each region has a distinct silhouette and landmark so players can orient quickly.

### 4.2 Structure

The map is divided into **zones** (working structure, **[TBD]** theme and number):

| Zone | Role | Traversal |
|---|---|---|
| Courtyard | Open ground-level hub, easy entry and the main starting area | Wide, flat, several exits |
| Rooftops | Upper tier of rooftops and beams | Ziplines, climbable walls, long jumps |
| Underpass | Lower tier of tunnels and canals | Tight corridors, ambush spots |
| Shrine Heights | Highest tier and the boss-friendly open area | Steep climbs, ziplines, wind or ink effects |
| Secret rooms | Hidden alcoves with pickups or shortcuts | Hidden entrances, discovered through exploration |

### 4.3 Traversal tools

- **Ziplines:** one-way or two-way. They can be cut or disabled by certain enemies or bosses.
- **Climbable walls and ledges:** short vertical shortcuts.
- **Launch points** (updrafts, springs) **[TBD]**: fast ascent options.
- **Drops and slides:** fast descent.
- **Shortcut gates:** locked in one direction, openable from the other side.

### 4.4 Secrets

- Hidden paths, breakable walls and fake floors.
- Environmental hints: ink stains, odd brush marks, sound cues.
- Rewards are **non-power** items: score bonuses, cosmetics unlocks and lore fragments (see §8).

### 4.5 Map-level risks

- **Camera and readability** at large scale and across vertical tiers: the camera should look ahead in the direction of travel and show enough above and below. **[TBD: prototype early.]**
- **Navigation for AI** is a hard requirement (see §6.3). Every traversal tool needs an AI-usable representation.

---

## 5. Wave System

Enemies arrive in **waves** across the whole map. The game is infinite, with difficulty rising over time.

### 5.1 Structure

- **Waves** are timed or cleared-based groups of enemies **[TBD: clear-to-advance versus timed pressure versus a hybrid]**.
- A short **breather** between waves for pickups, route changes and positioning.
- **Boss waves** every **5 waves** (default **[TBD: tune after playtesting]**), see §7.
- Difficulty scales through enemy count, enemy mix, spawn pressure and elite or modified enemies. Individual enemy lethality does not scale, because everything is already one-hit.

### 5.2 Spawning on a large map

- Enemies **spawn out of sight** at spawn points in different zones and route toward the player. They never spawn in the player's view.
- Spawn points are chosen to **encourage use of the whole map**. The game weights spawns away from the player's last N seconds of positions, so camping a corner is not optimal.
- Wave composition draws from a **budget system**: each enemy type has a cost, and each wave has a budget. Higher waves unlock more expensive types.
- **Pressure rules:** a cap on simultaneous active attackers (see §6.3) keeps fights fair even when there are many enemies.

### 5.3 Pacing

- Early waves: small groups, easy to read. Teaches enemy types one at a time.
- Mid waves: mixed groups, flanking begins, ranged and melee combined.
- Late waves: large mixed groups, elites, modifiers and bosses.

---

## 6. Enemies

### 6.1 Roster overview

The original had 4 basic enemy types. *Akane II* aims for **around 16**. With the campaign gone, all 16 appear in arcade mode and are introduced progressively: **8 are available from early waves, and the other 8 trickle in as the run progresses** (unlock waves in the table below).

The roster is organised by **role**, so each enemy does a distinct job and combines interestingly with others.

| # | Working title | Role | Behavior summary | Unlock |
|---|---|---|---|---|
| 1 | **Carried over A** | Grunt / melee | **[TBD: original type]** | Wave 1 |
| 2 | **Carried over B** | Ranged | **[TBD: original type]** | Wave 1 |
| 3 | **Carried over C** | **[TBD]** | **[TBD: original type]** | Wave 1 |
| 4 | **Carried over D** | **[TBD]** | **[TBD: original type]** | Wave 1 |
| 5 | Lancer | Melee, long reach | Thrusts from range. Punishes careless dashes | Wave 2 |
| 6 | Shieldbearer | Armored | Front-blocking shield. Must be flanked, dodged around or shield-broken | Wave 3 |
| 7 | Archer | Ranged, high ground | Prefers elevated spots. Telegraphed arrow lines | Wave 4 |
| 8 | Skirmisher | Flanker | Fast, circles to the player's back. Low commitment attacks | Wave 5 |
| 9 | Bomber | Area denial | Throws delayed charges that zone the ground | Wave 7 |
| 10 | Zipline Raider | Traversal | Uses ziplines and ledges to arrive from above | Wave 8 |
| 11 | Banner Caller | Support | Buffs nearby enemies' speed. Priority target | Wave 10 |
| 12 | Hexer | Control | Places lingering ink zones that restrict movement | Wave 12 |
| 13 | Heavy | Armored, slow | Cannot be human-shielded. Telegraphed crushing attacks | Wave 14 |
| 14 | Phantom | Ambusher | Appears from hidden spots, attacks, then repositions | Wave 16 |
| 15 | Duelist | Elite melee | Mirrors Akane's timing. Tests Ink Step | Wave 18 |
| 16 | Sniper | Long-range elite | Long telegraphed line shot. Forces cover and verticality | Wave 20 |

The first 8 types (the four carried-over types plus Lancer, Shieldbearer, Archer and Skirmisher) are the early set, available by wave 5. The other 8 (Bomber through Sniper) trickle in between waves 7 and 20. **[TBD: tune the unlock curve in playtesting.]**

### 6.2 Design rules for every enemy

- **One-hit kill.** Every standard enemy dies in one hit, except armored types which have a defined counter (flank, break or dodge-counter).
- **Telegraphed lethal attacks.** Every attack that can kill Akane has a visible telegraph with fixed timing, using the shared telegraph language from §1.
- **Single clear role** and a recognizable silhouette.
- **Counter-play:** each enemy has at least one intended answer using sword, gun, gadget, dash, Ink Step or a human shield.
- **Combinations:** designed to pair. For example, Banner Caller plus Skirmishers, or Hexer plus Archers.

### 6.3 Enemy AI

The original's enemy bugs (forgetting to attack, getting stuck) are a **bug class to eliminate**, and flanking is a **feature to add**.

**Reliability requirements**

- Enemies must always be in a defined state with defined transitions. No state is a dead end.
- **Stuck detection:** if an enemy cannot make progress (blocked path, no valid attack position, idle too long), a recovery behavior triggers: re-path, teleport-free repositioning, or despawn and respawn out of sight.
- Each enemy has a **forced re-engagement timer**, so it can never idle indefinitely while the player is nearby and visible.
- Pathfinding supports every traversal tool in §4.3, including ziplines, climbs and drops.

**Group behavior**

- **Attack tokens:** only a limited number of enemies may attack at once (scaled by wave), the rest circle, reposition or flank. This is the main fairness tool against being swarmed.
- **Flanking:** a group assigns roles. Some engage from the front, and others path around to approach from the sides and back, using the map's alternate routes.
- **Telegraph stagger:** simultaneous attacks are offset so overlapping telegraphs are always dodgeable.
- **Audio and visual cue** for off-screen or behind-the-player threats, since flanking only works if the player can perceive it.
- **Shield awareness:** AI responds to Akane holding a human shield (see §3.5).
- **Use of the map:** archers take high ground, zipline raiders arrive from above, and phantoms use secret passages.

**Difficulty tuning knobs**

- Token count, reaction time before telegraph, flank aggressiveness and spawn rate, all adjustable per wave band.

---

## 7. Bosses

*Akane* had one boss, which was fun but became stale. *Akane II* has **multiple bosses across three types**, appearing inside arcade mode.

### 7.1 Boss waves

- A boss arrives at **every 5th wave** (default **[TBD]**), replacing or accompanying a normal wave.
- **No consecutive repeats:** a boss rotation ensures the same boss doesn't appear back-to-back.
- **Escalation on return:** when a boss appears again later in a run, it gains new attacks or a modified phase, so repeats stay fresh.
- **Reward:** a large score bonus, and a clear breather before the next wave.
- Bosses use **one-hit-kill logic on Akane** (a hit still kills her). Boss health works through **multiple weak points, phases or vulnerability windows** **[TBD: confirm one-hit versus phased for boss kills]**, not a long health bar, to stay faithful to the game's identity.

### 7.2 Boss types

**Standard Duel bosses**
A classic, pattern-based fight in an open area. Provide contrast and a pure skill test. Suited to Ink Step and precise play.

**Roaming bosses**
Hunt Akane across the map, using the same traversal tools. They force the player to use ziplines, verticality and route knowledge, and prevent camping.

**Arena-shifting bosses**
Alter the map during the fight: collapse a bridge, flood a tunnel, cut a zipline, or open a new route. The environment is part of the fight, and the map visibly changes during a run.

### 7.3 Roster (working titles)

| Boss | Type | Concept |
|---|---|---|
| **The Ronin** | Standard Duel | The reimagined original boss: a swordmaster duel with new phases. **[TBD: tie to the original boss]** |
| **The Masked Magistrate** | Standard Duel | Ranged and zoning duel with gun patterns. Tests dodge timing |
| **The Hunter** | Roaming | Stalks Akane through the map, using ziplines and ambushes |
| **The Crimson Kite** | Roaming | A fast aerial boss that dives from above, with high-ground control |
| **The Bridge Demon** | Arena-shifting | Collapses sections of rooftops and bridges, shrinking safe ground |
| **The Tidecaller** | Arena-shifting | Floods and drains the Underpass, shifting routes between phases |

**Initial target:** 6 bosses (2 per type), with room for more post-launch **[TBD]**.

### 7.4 Boss design rules

- Every boss attack follows the shared telegraph language (§1).
- No boss can be defeated by a single exploit (for example, only human shields). Multiple valid approaches are expected.
- Bosses never spawn or move in ways that make traversal tools unusable for long. Cut ziplines come back or have alternatives.
- Roaming bosses must always be **perceivable**: audio and visual cues indicate their direction when off-screen.

---

## 8. Progression and Scoring

**Pure skill.** There is no power progression within or between runs. Every run starts equal.

- **Reward:** score and leaderboards.
- **Score** comes from kills, combos, style actions (Ink Steps, human shield kills, zipline kills), speed and boss clears.
- **Secrets** give score bonuses and cosmetic or lore unlocks. They must not provide power advantages.
- **Cosmetic unlocks** (outfits, ink effects, sword trails) **[TBD]** are allowed, as they don't change gameplay.
- **Leaderboards** by wave reached, score and time **[TBD]**.

---

## 9. Story and Presentation

There is no campaign. Story is delivered lightly.

- **Light continuity** with the original *Akane* **[TBD: confirm direction]** through short intro text, boss and enemy flavor text, and environmental details.
- Lore fragments found in secret rooms.
- Menus, UI and audio should carry the same ink wash identity as the art.

**Audio direction [TBD]:** traditional instrumentation with a modern pulse, adaptive intensity across wave bands, strong audio cues for telegraphs and off-screen threats.

---

## 10. Risks and Open Questions

### Risks

1. **Flanking versus one-hit kills.** Enemies surrounding a player who dies in one hit can feel cheap. *Mitigation:* attack tokens, telegraph stagger, directional cues.
2. **Human shield abuse.** Could trivialize crowds or ranged enemies. *Mitigation:* hold limits, ignore rules for some enemies, cooldown, speed penalty.
3. **Large map readability and camera.** Verticality and scale can hurt clarity. *Mitigation:* early prototyping, strict contrast rules, camera look-ahead.
4. **AI navigation complexity.** Traversal tools multiply path states. *Mitigation:* build navigation and stuck recovery first, before enemy variety.
5. **Content scope.** 16 enemies, 6 bosses and a large map is a lot of animation and balancing. *Mitigation:* roles first, shared telegraph language, ship boss roster in stages.
6. **Boss repetition.** Arcade runs repeat bosses. *Mitigation:* rotation, escalation on return, map-changing bosses.
7. **Precise dodge tuning.** Must be learnable and not mandatory. *Mitigation:* dash stays viable, window and reward tuned through playtests.

### Open questions

- [ ] Original game: the four enemy types, gun and gadget details, and the original boss.
- [ ] Boss kills: one-hit, multiple weak points, or phased?
- [ ] Wave advancement: clear-based, timed, or hybrid?
- [ ] Boss interval: every 5 waves, or a different cadence?
- [ ] Map: number of zones, theme per zone, and total traversal scale.
- [ ] Gadget: fixed or chosen at run start? Single gadget or several to choose from?
- [ ] Story: continuity level with the original.
- [ ] Platforms and input methods.
- [ ] Multiplayer or co-op (currently out of scope).
- [ ] Post-launch content plan (more bosses, enemies, map areas).

---

## Appendix: Decisions Log

| Decision | Outcome |
|---|---|
| Campaign / story mode | **Cut.** Does not fit the arcade design |
| Boss placement | Inside arcade mode, at wave milestones (every N waves) |
| Boss types | Roaming, arena-shifting and standard duel |
| Combat toolkit | Original structure: sword + gun + one gadget |
| Progression | None. Pure skill |
| Enemy roster | ~16 types, introduced progressively across arcade waves |
| Story | Light continuity (assumed, to be confirmed) |
