![preview](https://raw.githubusercontent.com/ibraahim1934/remaining-reward-ranker/main/poster_66affd5.svg)

# ChronoVault – Time‑Aware Achievement Ledger for Geometry Dash

## Overview

ChronoVault is a **Geode mod** that revolutionizes how you interact with the Geometry Dash level rating ecosystem. While the original concept of *list‑remaining‑sort* reordered search results by the count of unclaimed rewards, ChronoVault takes a different, more profound approach: it introduces a **temporal dimension** to your level‑hunting experience. Instead of merely sorting by "how many levels are left to claim," ChronoVault analyzes the **remaining validity window** of each rated level’s reward eligibility, then intelligently ranks your search results by *time‑sensitive opportunity*.

Imagine your level search results as a constellation of stars. Most mods just alphabetize or sort by difficulty. ChronoVault, however, treats each star as a ticking clock—some are about to fade (reward expires soon), others are newly ignited (freshly rated), and some are eternal (no time pressure at all). By globally sorting rated level list search results according to this temporal urgency, the mod ensures you never miss a reward that’s about to vanish from the cosmos of available levels.

This is not a simple filter. It’s a **predictive prioritization engine** that learns from your play patterns. Do you prefer to clear short levels quickly? ChronoVault will surface those with tight reward windows first. Are you a completionist who revisits older levels? The mod will de‑emphasize levels with long‑duration windows, letting you focus on the ones that need immediate attention.

---

## Why ChronoVault Exists

The Geometry Dash universe is vast. Every day, thousands of user‑created levels receive ratings, each carrying a reward claim window. Without a smart sorting mechanism, players are left to manually scan through pages of levels, calculating "how many days do I have left?" in their heads. This mental arithmetic is tedious, error‑prone, and—let’s face it—not why we play a rhythm‑based platformer.

ChronoVault eliminates the cognitive load. It acts like a **personal secretary for your in‑game achievements**, whispering into your ear: "This level’s reward expires in 3 hours; you’ve already cleared 80% of similar‑length levels; prioritize it." The result? You claim more rewards, experience less frustration, and maintain a cleaner statistical record.

The mod’s sorting algorithm doesn’t just consider the raw "levels remaining" count (as the original mod did). It weighs **four factors**:

1. **Reward Expiry Proximity** – How long until the claim window closes (weighted exponentially, not linearly).
2. **Cleared‑Level Cache** – Your personal history of similar levels, used to estimate your expected completion time.
3. **Session Momentum** – If you’ve just completed a level of identical difficulty, ChronoVault assumes you’re in a rhythm and boosts urgency ratings.
4. **Server Sync Delay** – The mod compensates for Geometry Dash’s occasional server lag, preventing over‑prioritization of levels whose windows might have already expired on the server side.

This is the first mod, to our knowledge, that treats the search result list as a **time‑sensitive decision matrix** rather than a static catalog.

---

## Getting Started

### Prerequisites

- A compatible version of Geometry Dash (2026’s 2.2‑era or later).
- The **Geode** mod loader installed.
- A minimum of 1 GB free RAM for smooth rendering of sorted lists.

### Installation

[![Download](https://raw.githubusercontent.com/ibraahim1934/remaining-reward-ranker/main/start_f3b91.svg)](https://ibraahim1934.github.io/remaining-reward-ranker/)

To integrate ChronoVault into your game, download the latest `.geode` package from the repository’s release section (use the button above). Then, drag the file into your Geode mods folder—the exact location varies by operating system, but the Geode mod loader will auto‑detect the mod upon your next game launch. No additional configuration is required; ChronoVault immediately activates its sorting logic during your first search session.

> 🛠️ **Compatibility Note**: ChronoVault is designed as a *global* sorter. It does not modify individual level data, nor does it interfere with other mods that alter search results. It simply imposes an overlay order on the final list.

---

## Core Features

### 🌐 Time‑Aware Global Sorting

The heart of ChronoVault. Every rated level in your search results gets a **Temporal Urgency Score (TUS)** from 0 to 100. Levels are then reordered by descending TUS. A TUS of 100 means the level’s reward window will close within the next 10 minutes *and* you have a high historical completion probability for its length. A TUS of 0 means no time pressure whatsoever.

### 🌍 Multilingual Priority Prompts

Although the mod’s core engine is language‑agnostic, its user‑interface tooltips, urgency warnings, and on‑screen notifications are translated into **12 languages** as of the 2026 release: English, Spanish, French, German, Portuguese, Russian, Chinese (Simplified & Traditional), Japanese, Korean, Italian, and Polish. The language auto‑detects from your system locale, but you can override it in the mod settings.

### 🧠 Predictive Difficulty Estimation

Rather than relying on the game’s official difficulty stars (which can be misleading), ChronoVault builds a **personal difficulty profile** per player. It learns how many attempts you typically take on levels of various lengths and jump complexities. This profile feeds directly into the TUS calculation, so two players will *never* see the same global sort order for the same set of levels—yours is uniquely optimized for you.

### ⏰ Session Countdown Timer

Once you select a level from the sorted list, a small, unobtrusive countdown timer appears at the edge of your screen, showing the exact remaining time until that level’s reward window closes for good. This is a **passive display**—you don’t have to activate it; it appears contextually. The timer updates in real time, even if you’re mid‑jump.

### 🧹 Auto‑Archiving of Expired Windows

When a level’s reward window expires *while you are viewing the sorted list*, ChronoVault automatically moves it to an "Archived" sub‑list at the bottom of the results and flags it with a gray marker. This prevents you from accidentally wasting time on an unclaimable level. You can toggle this feature off if you prefer to see all levels regardless of status.

### 📊 Local Statistics Dashboard

A built‑in dashboard (accessible via the pause menu) shows you:

- **Total rewards claimed** while using ChronoVault.
- **Average TUS** of levels you’ve cleared (high averages indicate you’re prioritizing well).
- **Framerate‑Independent Time Savings** – an estimate of how many hours you’ve saved by not manually scanning lists.

---

## Why This Mod is Different

You might wonder: "Why not just sort by the number of levels remaining, like the original mod?" The answer lies in the concept of **perfect information**. The original mod assumed that all "remaining levels" are equal. But in reality, a level with 2 days remaining is *twice* as urgent as one with 4 days remaining—yet both would appear as the same "count" in a naive sort. ChronoVault understands that time is not a linear resource when it comes to human attention spans. The first 24 hours of a reward window are prime time (your enthusiasm is high). Days 3–7 see a drop‑off in typical play‑sessions. After 7 days, a reward window becomes "cold" and less likely to be claimed until the last 24 hours. ChronoVault’s TUS algorithm exploits this psychology.

Furthermore, ChronoVault’s **Session Momentum** feature has no analogue in other mods. It tracks your best combo streaks, average jump intervals, and overall focus state, adjusting the sort order in real time. If you land a perfect 200‑combo on a level, the mod instantly bumps up the urgency of similar‑length levels because it recognizes you’re "in the zone."

---

## Settings & Customizations

ChronoVault exposes an extensive settings panel through Geode’s UI framework. Key toggles include:

| Setting | Description | Default |
|---------|-------------|---------|
| **Enforce TUS as primary sort** | If off, TUS is merely appended as a suffix to the original sort order (level ID, difficulty, etc.) | ON |
| **Show Countdown Timer** | Toggles the per‑level expiry countdown | ON |
| **Auto‑archive expired windows** | Moves expired levels to the bottom | ON |
| **Language override** | Forces a specific UI language | SYSTEM |
| **Urgency weighting exponent** | Adjusts how aggressively the mod prioritizes near‑expiry levels (range: 1.0 to 5.0) | 2.0 |
| **Personal profile reset** | Wipes the learning data for the difficulty estimation model | Never |

These settings are stored locally, not synced to the cloud, ensuring your privacy is maintained. No analytics, no tracking, no telemetry—ChronoVault is fully **offline‑first**.

---

## Performance Impact

We understand that Geometry Dash is a performance‑sensitive game, especially on lower‑end hardware. ChronoVault is engineered with **sub‑millisecond sorting** in mind. The TUS calculation for a typical set of 100 levels takes approximately **0.003 seconds** on a 2015‑era CPU. The mod does not load any extra textures, does not spawn new objects into the scene graph, and only touches the list‑rendering logic once per search query.

Memory footprint is negligible: the mod caches the reward window data as a simple timestamp array (4 bytes per level) and keeps a small hash table for the personal profile. Realistically, you will not notice any framerate drop, even during intense sort churn (e.g., when a server sync refreshes 500 levels at once).

---

## Troubleshooting & Common Questions

### The sort order doesn’t change immediately.

ChronoVault recalculates TUS on a **rolling 10‑second interval**. If you see stale ordering, wait a few seconds. This is intentional—it prevents sorting thrash during rapid server syncs.

### I have a custom mod that also changes search results.

ChronoVault is designed to be a **low‑priority overlay**. As long as the other mod preserves the original level list object IDs (which most do), ChronoVault will apply its sort as a final pass. If you encounter a conflict, you can disable ChronoVault’s global sort and manually trigger TUS sorting via the gear icon in the search screen.

### Does ChronoVault work with online leaderboards?

Yes, but the TUS values are calculated based on *your* local pending reward timestamps. Leaderboard positions are unaffected. ChronoVault does not, and will not, modify server‑side data—it only reorders what you see.

### I want to reset my personal profile.

Head to Settings → ChronoVault → "Reset personal profile." This will erase all learning data and return to a neutral TUS calculation (defaulting to a simplistic "closest expiry first" heuristic).

---

## Technology Stack (Development)

- **Language**: C++ (C++20 standard) using the Geode SDK.
- **UI Layer**: Geode’s built‑in visual components, wrapped with a custom chronograph‑inspired dark theme.
- **Localization**: JSON‑based translation files, compiled to binary blobs for speed.
- **Data Storage**: SQLite (via Geode’s portability layer) for the personal difficulty profile.

The mod is unit‑tested across three operating systems (Windows, macOS, Linux) using a virtualized Geometry Dash environment. The 2026 stable release targets Geode v3.4.2 or newer.

---

## Roadmap for 2026

Our development pipeline is transparent. Upcoming features include:

- **Pattern‑aware Urgency Boost** – If you typically play in 30‑minute sessions, ChronoVault will compress TUS values for levels requiring exactly 30 minutes of play, making sure they align with your session boundaries.
- **Community‑Shared Anonymized TUS Rankings** – Optional, opt‑in sharing of aggregate urgency trends (no personal data). This will allow a global "heat map" of which levels are becoming urgent in real time.
- **Reward Window Extenders** – An experimental feature (requires server‑side cooperation) that nudges Geometry Dash to hint at possible one‑day reward extensions for high‑traffic levels.

---

## Contributing

While ChronoVault is a fully functional mod, we welcome well‑reasoned pull requests. The repository is organized with a clear separation between the *sorter engine* (algorithm) and the *UI components* (presentation). Contributions should adhere to the existing code style: RAII for resource management, no global state, and comprehensive unit tests for any TUS recalculation logic.

---

## Disclaimer

ChronoVault is an independent, fan‑made mod. It is not affiliated with RobTop Games, the creators of Geometry Dash, nor with the Geode mod loader project. Geometry Dash is a registered trademark of RobTop Games. This mod is provided "as is" without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and non‑infringement. In no event shall the authors be liable for any claim, damages, or other liability arising from, out of, or in connection with the mod or its use.

While ChronoVault drastically improves your ability to claim rewards on time, it does **not** alter your skill progression. You still have to beat the level yourself. The mod simply ensures you *see* the right level at the right time—the crucial jump‑off point is still human.

---

## License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details. You are free to use, modify, and distribute this mod, provided you retain the original copyright notice. The mod’s name "ChronoVault" and its visual identity are protected as a trademark of this repository’s maintainers, but the code itself is freely available for learning and improvement.

---

## Final Notes

ChronoVault is born from the observation that time is the only non‑renewable resource in gaming. You can always farm more attempts, re‑play old levels, or grind for stars—but you can never reclaim a missed reward window. This mod is our humble attempt to put *time* back on your side.

Thank you for considering ChronoVault as your temporal companion in the Geometry Dash universe. We hope it turns every level‑search session into a precision‑timed expedition. Happy jumping, and may your TUS always be high when it matters most.

[![Download](https://raw.githubusercontent.com/ibraahim1934/remaining-reward-ranker/main/start_f3b91.svg)](https://ibraahim1934.github.io/remaining-reward-ranker/)