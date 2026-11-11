# DIGITAL ASH
## Game Design Document · Concept + playable prototype

**Genre:** atmospheric survival / cleaning simulator · **Players:** 1 · **Platform concept:** PC first, controller/touch-friendly web prototype · **Mode:** single-player, finite expedition · **Target session:** 30–60 minutes (full production target)

> *The things we buried still remember.*

## 1. High concept

In the late aftermath of a network collapse, a lone salvage worker is sent to Sector 09: a sprawling cyber-junkyard where whole server farms, domestic waste, and obsolete machines have been buried in layers. Somewhere below is one old USB flash drive containing a wallet with 1,000 Bitcoin. The player clears debris by hand, hauls it to an industrial incinerator, turns waste into credits, upgrades their kit, and checks the occasional recovered drive. Almost every drive is worthless. The jackpot is not.

**Design pillars**

1. **Satisfying work:** every pile becomes a clear patch; each hauling and burning action visibly advances the site.
2. **Tension through uncertainty:** credible traces, junk drives, and atmospheric interruptions create hope without making progress feel random or unfair.
3. **A hostile place with a pulse:** fog, night, weather, the furnace, and the buried layers make the yard feel larger than the current worksite.
4. **Fair luck:** the legendary drive is a guaranteed, uniquely seeded objective, while ordinary drives provide the probabilistic noise around it.

**Player fantasy:** *I am the last person willing to do the dirty work—and I might uncover the most valuable forgotten thing in the world.* The Bitcoin is a fictional narrative prize, not a financial product or real-world earning promise.

## 2. Core gameplay loop

### Moment-to-moment
1. **Read the field.** Scan a grid/sector of debris; note pack capacity, the current shift, weather, depth, and any scanner pings.
2. **Clear a pile.** Use a hand tool (or later machinery) to remove a pile. Bulkier debris yields more salvage and takes more effort in the full game. A pile can conceal a USB drive.
3. **Manage the haul.** Pack capacity limits uninterrupted work. Return to the furnace before the pack fills; choose whether to invest in a larger carrier.
4. **Run the furnace.** Stoke the incinerator into its safe operating band, feed it sorted waste, and earn credits. Too cold wastes a trip; too hot risks a production-game penalty (and could damage equipment in the full design).
5. **Invest and adapt.** Buy tools, scanner parts, lighting, protective gear, or capacity. Weigh a useful upgrade against spending credits on a faster expedition.
6. **Check recovered drives.** Use a terminal to classify each drive. Most are empty, damaged, memes, or malware. A clean signal may point toward an intact casing deeper down.
7. **Descend.** Clear the sector to expose the next burial layer. The deepest layer contains the expedition's uniquely placed jackpot drive.
8. **Verify and escape.** Check the true drive at a terminal to confirm the wallet and trigger the ending.

### Macro progression / intended pacing
- **Layer 1 — The Rim:** tutorial piles, small loads, basic furnace controls. Establish the work rhythm and teach the terminal.
- **Layer 2 — The E-Waste Shelf:** more mixed/valuable debris, heavier piles, first equipment choices, stronger weather and night pressure.
- **Layer 3 — The Buried Stack:** dense server scrap, stronger scanner traces, and the single guaranteed jackpot casing in a random pile. It still must be cleared and verified.
- **Ending:** the wallet verifies, the player receives an understated cinematic moment, and the furnace carries on behind them. The story is about finally being able to leave, not about a real cryptocurrency cash-out.

### Failure and survival pressure (full-game target)
The current web prototype is a low-friction concept slice and has no hard fail state. In production, exposure, fatigue, toxic smoke, battery drain, and hazardous weather should make preparation matter without deleting hours of work. Use recoverable setbacks (lost time, tool wear, a temporary HUD fault, dropped salvage) rather than permadeath. Autosave at each layer and before an upgrade purchase.

## 3. Resource and loot economy

### Resources
- **Salvage units:** general burnable debris carried in a limited pack.
- **Credits (CR):** earned by incinerating salvage; spent on permanent expedition upgrades.
- **Drives:** individually checked at a terminal; results are narrative collectibles and progress clues.
- **Heat:** furnace operating state; active management makes the conversion step tactile rather than a menu-only sale.

### Ordinary USB outcomes
For each **ordinary drive checked**, use this starting distribution:

| Result | Chance | Feedback |
|---|---:|---|
| Empty / 0 bytes | 68% | Quiet dead end; terminal reports no usable files. |
| Corrupt image | 20% | A damaged thumbnail flickers; no recovery. |
| 2010 meme archive | 7% | Brief, dated comedy; a small collectible archive entry. |
| Malware / HUD glitch | 5% | Temporary interface/equipment interference; respirator/firmware upgrade can mitigate. |
| **Jackpot wallet** | **Not rolled here** | It is one unique, guaranteed drive, planted in one random Layer 3 pile at expedition generation. |

The ordinary-drive probabilities total 100%. The jackpot is intentionally **not** a per-drive lottery: there is exactly one true drive in a run, and its location is randomized. Thus, for the special drive, the player has a 100% chance to encounter it by fully clearing Layer 3, independent of how many fake drives happen to spawn. This avoids an unwinnable run and protects the core promise. Optional scanner clues make the hunt feel lucky without allowing upgrades to remove the mystery.

### Physical-drive discovery
Prototype starting rate: **3.5% per cleared ordinary pile**, rolled independently, with scanner upgrade increasing it to **7%**. The jackpot replaces the ordinary roll in its pile. This rate produces enough terminal moments to establish the running gag without flooding the inventory; tune after playtests (desired full-run average: 2–5 ordinary drives, with a large tail of zero-drive runs possible). Luck affects *how many decoys* appear—not whether the objective exists.

### Furnace tuning (prototype values)
- Stoke: +24 heat, capped at 100; routine actions cool the fire slightly.
- Feed range: 50–85 heat inclusive.
- Burn amount: up to `floor((heat - 35) / 10)` salvage, at least one unit.
- Payout: 2 CR per unit; heat cost: 7 per unit.
- Pack: 8 starting capacity; Folding Hauler upgrade adds 6.

These are concept numbers. A production economy should target roughly one modest upgrade every 1–2 work sectors, with useful choices rather than a grind wall.

## 4. Player progression and upgrade tree

### Tier 0 — issued kit
- **Bent spade:** clear a pile and recover its listed salvage weight.
- **Canvas pack (8):** small capacity makes the first furnace return legible.
- **Bare hands / no scanner:** ordinary drives are rare and the objective trace is indistinct.
- **Unsealed clothes:** environmental conditions are atmospheric in the prototype; production game applies exposure risk.

### Upgrade catalog
| Upgrade | Prototype cost | Effect / design intent | Follow-up branch |
|---|---:|---|---|
| Ratchet Spade | 12 CR | +1 salvage per pile in prototype; full game reduces heavy-pile work actions. | Powered prybar → compact hydraulic breaker |
| Folding Hauler | 16 CR | +6 pack capacity; cuts furnace round trips. | Wheeled bin → crawler cart / powered dumper |
| Ghost-Signal Scanner | 22 CR | Doubles ordinary drive appearance to 7%; improves trace visualization. Jackpot remains guaranteed. | Directional antenna → ground-penetrating pulse array |
| Caged Lantern | 15 CR | Better night visibility and clearer signal readout. | Tripod floodlight → portable mast / drone light |
| Sealed Respirator | 18 CR | Prevents prototype HUD glitch from malware; production reduces smoke/toxin exposure. | Filter stack → sealed hazard suit |
| Furnace baffle | (future) 24 CR | Slows heat loss and widens the useful burn window. | Recuperator → automated feed arm |
| Sorting rake | (future) 10 CR | Separates electronics from general burnable waste; unlocks component bonuses. | Magnetic separator → conveyor sorter |

**Branch logic:** hauling and clearing improve throughput; scanner/lighting improve information and night work; safety/furnace investments reduce risk and downtime. Avoid a single mandatory build: the guaranteed deep objective is reachable with starter equipment, though upgrades make it more comfortable.

## 5. World, atmosphere, and procedural generation

### Setting and tone
Sector 09 is a wide industrial basin with a furnace at its edge. Silhouettes of e-waste ridges recede into dense fog; weak neon signage and a distant tower give orientation. Close-range detail contrasts with a simplified, hazy horizon. The work is quiet, tactile, and lonely, punctuated by machinery and radio static—not constant combat or jump scares.

### Art direction
- **Palette:** soot greens, oxidized iron, charcoal, faded cream labels; restrained acid-lime UI; furnace amber as the warm focal point.
- **Materials:** scratched CRT glass, wet plastic, powdery ash, corroded metal, blistered warning paint, waterlogged cardboard.
- **Lighting:** dark ambient fill, localized tool/lantern pools, furnace bounce, occasional distant neon. Keep interactive piles readable at all times.
- **UI:** industrial field instrument, not generic military HUD. Thin rules, compact monospaced telemetry, large plain-language action labels, clear capacity and temperature readouts.
- **Animation:** piles settle/disappear with dust, cargo clicks into the pack, furnace breathes and glows with heat, terminal glyphs resolve slowly. Use brief, accessible effects for malware glitches rather than obstructing all play.

### Sound direction
Furnace crackle and low ventilation form the constant bed. Add boot grit, shovel impacts by material, metal settling, distant loose sheet-metal, and weather on the yard. Terminal reads have a low, dry relay click. The jackpot should briefly pull back the ambient mix before the verification tone and a restrained musical rise.

### Procedural structure
Each expedition uses a run seed. Generate 3 layers of sectors, each with a weighted mix of debris archetypes, pile size, wear state, and optional ordinary drive. Place the unique jackpot in one valid, clearable pile in the deepest layer. Store the seed and target coordinate in the save. Weather and shift schedules can use separate deterministic streams so a reload does not reroll loot. Later levels can add sub-sectors, movable equipment, and multiple disposal routes.

Prototype is a responsive 5×4 debris field per layer, with randomized materials and pile weights. On Layer 3 one random pile is visibly a sealed case; that is a readability concession for the concept slice. A production build should hide it in a plausible pile and let a sufficiently upgraded scanner produce progressively clearer hints, without revealing the tile immediately.

## 6. Interface / controls

### Layout concept
- **Header:** game mark, sector name, shift, weather, field-notes/help.
- **Top telemetry:** credits, total salvage recovered, burial depth, drive count.
- **Main field:** clickable/tappable debris grid with clear/cleared state, pile material, signal state, and day/night fog treatment.
- **Side instruments:** pack meter and contents; furnace temperature with Stoke/Feed controls; terminal drive list with Check action; field-modification shop; short shift log.
- **Mobile:** cards stack vertically; piles use a four-column grid with large tap targets; key gauges and action buttons remain visible and labels remain explicit.

### Input
- Mouse/touch: click a pile to clear; use labeled buttons to stoke, feed, buy, and inspect.
- Keyboard/controller direction: future production input can move a focus cursor across the debris grid. All actions should be reachable without hover.
- Accessibility: do not encode status only by color; use labels and icon/text; scale UI; reduce motion; offer a brighter visibility option and adjustable sound mix.

## 7. Narrative delivery

A few terse site logs and terminal returns reveal that the yard once belonged to a defunct data-hosting company. Keep the 1,000-BTC legend uncertain through empty drives, damaged files, and conflicting worker notes. Do not force a long exposition sequence: the player is working, and the environment carries the history. On verification, confirm the wallet locally and let the player choose whether to leave, keep salvaging, or start a seeded new run in a complete version.

## 8. Success criteria and playtest questions

- A first-time player understands clear → haul → burn → upgrade within two minutes.
- Furnace controls feel interactive but do not require busywork for every single salvage unit.
- Players routinely make at least two meaningful upgrade decisions before Layer 3.
- Ordinary drives feel funny/haunting, not like a repetitive slot machine.
- The deep objective is always reachable; median expedition length can be tuned by sector size and capacity.
- Night and weather change mood/readability without making the game inaccessible.

Playtest questions: How many drives feel like enough? Does the jackpot location feel earned when the scanner can hint at it? Is the furnace a satisfying ritual or a bottleneck? Does upgrading the pack compete fairly with scanner upgrades?

## 9. Playable concept project

Open `index.html` in a modern browser. It is a dependency-free web prototype with three layers, generated debris, capacity-limited hauling, a heat-managed furnace, upgrades, decoy-drive terminal results, changing shifts/weather, and a guaranteed jackpot on Layer 3. It auto-renders to mobile layouts. No server, account, or real cryptocurrency wallet is involved.

### Core mechanic reference (JavaScript)

```js
function clearPile(pile, player, rng) {
  if (pile.cleared || player.pack >= player.capacity) return;
  pile.cleared = true;
  const haul = Math.min(
    pile.weight + (player.ratchetSpade ? 1 : 0),
    player.capacity - player.pack
  );
  player.pack += haul;
  player.salvaged += haul;

  // One unique jackpot is assigned to a random pile when Layer 3 is generated.
  if (pile.jackpot) {
    player.drives.push({ kind: "jackpot", checked: false });
  } else {
    const driveChance = player.scanner ? 0.07 : 0.035;
    if (rng() < driveChance) player.drives.push({ kind: "ordinary", checked: false });
  }
}

function generateLayer(depth, rng, materials) {
  const piles = Array.from({ length: 20 }, () => ({
    material: materials[Math.floor(rng() * materials.length)],
    weight: 1 + Math.floor(rng() * 2),
    cleared: false,
    jackpot: false
  }));
  if (depth === 3) piles[Math.floor(rng() * piles.length)].jackpot = true;
  return piles;
}

function checkDrive(drive, rng) {
  if (drive.kind === "jackpot") return "VERIFIED: 1,000 BTC";
  const roll = rng();
  if (roll < 0.68) return "EMPTY / 0 BYTES";
  if (roll < 0.88) return "CORRUPT IMAGE";
  if (roll < 0.95) return "2010 MEME ARCHIVE";
  return "MALWARE / TEMPORARY HUD GLITCH";
}

function burn(player) {
  if (player.heat < 50 || player.heat > 85 || player.pack < 1) return 0;
  const units = Math.min(player.pack, Math.max(1, Math.floor((player.heat - 35) / 10)));
  player.pack -= units;
  player.credits += units * 2;
  player.heat = Math.max(0, player.heat - units * 7);
  return units;
}
```

The browser prototype uses the same essential logic with UI events and its own random generator. For a shippable production game, use a seedable PRNG and save the seed plus jackpot coordinate so reloading cannot reroll the objective.

## 10. Scope and assumptions

The requested concept is interpreted as a complete **playable browser vertical slice**, not a full commercial-scale 3D simulator. This prototype abstracts hauling to pack capacity and the disposal trip to the furnace panel; it does not simulate walking, physical tools, 3D debris, audio, or an actual crypto wallet. The guaranteed location is randomized within Layer 3. These limits keep the main loop, progression, atmosphere, and luck hook demonstrable in a small standalone project.
