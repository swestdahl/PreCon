# The Board Bard Pre-Con Escalation League Tracker (v0.7)
## Complete User's Guide & Tournament Organizer Manual

---

### 🌟 Overview

**The Board Bard Pre-Con Escalation League Tracker** is a zero-dependency, self-contained web application designed for Magic: The Gathering Commander leagues. It handles player rosters, automated pod pairings, TopDeck.gg-style match lobbies, banlist validations, standings leaderboards, and a searchable catalog of official Magic preconstructed decks.

---

### 📋 Table of Contents
1. [Getting Started & Installation](#1-getting-started--installation)
2. [Managing Players & The League Roster](#2-managing-players--the-league-roster)
3. [Running Game Night with the Pod Generator](#3-running-game-night-with-the-pod-generator)
4. [Using Active Match Lobbies (Self-Reporting & Verification)](#4-using-active-match-lobbies-self-reporting--verification)
5. [Understanding Deck & Commander Legality (The Ban List)](#5-understanding-deck--commander-legality-the-ban-list)
6. [Precon Deck Catalog & Alternate Commanders](#6-precon-deck-catalog--alternate-commanders)
7. [Leaderboard, Scoring, & Standings](#7-leaderboard-scoring--standings)
8. [Admin Controls & Data Backups](#8-admin-controls--data-backups)

---

### 1. Getting Started & Installation

- **File Location:** Open `MTG Pre-con League Tracker.html` directly in any standard browser (Chrome, Safari, Firefox, Edge).
- **Single-Device / Tablet Mode:** The app operates entirely locally in your browser using `localStorage`. No internet connection is required during events.
- **Home Screen App:** On iOS (Safari) or Android (Chrome), tap **Share ➔ Add to Home Screen** to run it as a fullscreen app.

---

### 2. Managing Players & The League Roster

The tracker builds a continuous roster from all recorded matches:
* **Interactive League Roster:** Located under the **🎲 Pods & Lobbies** tab. Click any player's name pill (`+` / `✓`) to quickly toggle them in or out of tonight's attending list.
* **⚡ Quick-Add Search:** Type a player's name in the quick-add input with autocomplete and press **Enter** to add them to the attendee list.
* **Manual Entry / Paste:** You can paste a full list of names (one per line) into the player input box.
* **Clear List:** Resets the active attendee box at the start or end of the evening.

---

### 3. Running Game Night with the Pod Generator

Commander events are structured into two rounds per game night:

#### 🎲 Game 1: Open / Random Pods
1. Ensure all attending players for Round 1 are in the attendee box.
2. Click **`🎲 Generate Game 1 Pod Lobbies`**.
3. The app automatically partitions the players into optimal 4-player pods (or 3-player pods when numbers require it, e.g., 6, 7, 9, 10, 11 players).
4. An active **Match Lobby** card is spawned for each table (Table 1, Table 2, Table 3, etc.).

#### 🏆 Game 2: Seeded Winners Pods
1. If players leave or late players arrive after Game 1, simply adjust the attendee list (click pills or edit the box).
2. Click **`🏆 Pair Game 2 (Winners Pods)`**.
3. The pairing engine retrieves the most recent Game 1 results:
   - **1st Place Winners** are paired together at **Table 1** (and Table 2 if >4 winners).
   - **2nd Place Finishers** are paired in the next tier.
   - **3rd/4th Place Finishers** are placed in lower brackets.
   - **Late Arrivals** (who did not play Game 1) are smoothly seeded into middle pods without displacing top winners.

---

### 4. Using Active Match Lobbies (Self-Reporting & Verification)

Once pods are generated, each table gets its own **Active Match Lobby**:

1. **Table Seating & Turn Order:**
   - Players roll physical dice at their table to determine play order.
   - Set each player's **Turn Order** (`Seat 1 / T1`, `Seat 2 / T2`, etc.).
2. **Precon Deck & Commander Selection:**
   - Type or choose the player's **Precon Deck** from the autocomplete dropdown.
   - The **Commander** box automatically pre-fills with the default legal commander for that deck.
   - If using a secondary commander or partner, click the Commander dropdown or type the custom card name.
3. **Placements:**
   - Set each player's finish (`🥇 1st`, `🥈 2nd`, `🥉 3rd`, `4th`). Placement options adapt dynamically to the exact number of players at that table.
4. **Handling Mid-Round Table Changes:**
   - Click **`+ Add Player`** on any table card to seat a late entrant.
   - Click **`✕`** next to any player row to drop someone who stepped away.
5. **✓ Verify & Record Match:**
   - Click the green button to commit the match to the official standings.
   - The app verifies that a 1st place winner is selected and that no banned commanders were run in the command zone.
   - A success toast notification confirms the save, and the lobby clears.

---

### 5. Understanding Deck & Commander Legality (The Ban List)

The tracker enforces a two-tier ban model:

#### 🚫 1. Banned Decks (Entire Deck Ineligible)
The deck is completely banned from the league regardless of who is in the Command Zone:
* *Arcane Wizardry* (`C17`)
* *Counter Blitz* (`FIC`)
* *Draconic Domination* (`C17`)
* *Eldrazi Incursion* (`M3C`)
* *Eldrazi Unbound* (`CMM`)
* *Eternal Bargain* (`C13`)
* *Goblin Storm* (`SLD`)
* *Guided by Nature* (`C14`)
* *Heavenly Inferno* (`CMD`)
* *Necron Dynasties* (`40K`)
* *Open Hostility* (`C16`)
* *Raining Cats and Dogs* (`SLD`)
* *Sliver Swarm* (`CMM`)
* *Tyranid Swarm* (`40K`)
* *Vampiric Bloodlust* (`C17`)

#### ⚠️ 2. Conditional / Alt Commander Required (Deck Legal, Face Card Banned)
The 99-card deck is legal, but the printed face card cannot be in the Command Zone:
* *Breed Lethality* ➔ Legal with **Ishai, Ojutai Dragonspeaker + Reyhan, Last of the Abzan** (or Ikra Shidiqi / Tymna). *Atraxa banned in CZ.*
* *Timeless Wisdom* ➔ Legal with **Brallin, Skyshark Rider + Shabraz, the Skyshark** (or Akim, the Soaring Wind). *Gavi banned in CZ.*
* *Elven Empire* ➔ Legal with **Harald, King of Skemfar / Miara + Numa / Abomination of Llanowar**. *Lathril banned in CZ.*

---

### 6. Precon Deck Catalog & Alternate Commanders

Under the **📚 Precon Catalog** tab:
* Browse all official paper preconstructed decks.
* **Alternate Commander(s) Column:** Shows official secondary commanders and partners for each precon (e.g. *Wildsear, Scouring Maw* for *Animated Army*, *Chatterfang, Squirrel General* for *Squirreled Away*).
* **Interactive Sorting:** Click any column header (`Deck Name`, `Face Commander`, `Alternate Commander`, `Colors`, `Status`, `Set`) to sort.
* **Instant Search:** Type any card name, deck title, or set code to filter in real time.

---

### 7. Leaderboard, Scoring, & Standings

League scoring follows the official Board Bard Escalation structure:
* **🥇 1st Place (Win):** `4 Points`
* **🥈 2nd Place:** `3 Points`
* **🥉 3rd Place:** `2 Points`
* **4th Place:** `1 Point`
* **5th / 6th Place:** `1 Point`
* **Tie-Breaker:** Win Percentage ➔ Total Wins ➔ Matches Played.

Standings update immediately on the **🏆 Standings** leaderboard and summary dashboard.

---

### 8. Admin Controls & Data Backups

Under the **⚙️ League Rules & Admin** tab:
* **Admin Match Editor:** Edit or delete past matches if a turn order or finish was entered incorrectly.
* **💾 Export Data (JSON):** Download a backup copy of all league records, lobbies, and players.
* **📥 Import Data (JSON):** Restore data onto any computer, tablet, or phone.
* **Clear Data:** Full reset for starting a brand-new season.

---
*Created by SomewhatUnique & rool*
