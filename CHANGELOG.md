# Changelog

Public release notes for Gridelio. Newest first.

The app updates itself from [`gridelio.com/updates.json`](https://gridelio.com/updates.json). Patch releases (`x.y.z`) and minor releases (`x.y`) are included in the licence; only major versions (`x.0`) are planned as paid upgrades.

---

## 1.2.1 — 2026-11-11 (build 127)

**New**

- **Desktop bar colour palettes** — Gruvbox, Dracula, Tokyo Night, Nordic, Papirus, WhiteSur, Arc, Orchis, Qogir, Vimix, plus light and dark variants, with preview and persistence in Settings › Appearance.
- **Disks widget** in the desktop bar: mounted volumes are listed by default, and you choose which ones appear from the bar's menu.
- **"Center window" shortcut** (⌃⌥C, Settings › Shortcuts › Zones): centers the active window on the visible area of its screen and floats it; ⌘⌥F puts it back in its cell.

**Fixed**

- A window that cannot fit the grid (because of its neighbours' minimum sizes) now beeps instead of silently staying out of the layout.
- A suspended desktop recovers by itself after 10 seconds instead of staying blocked until you reactivate it manually.
- The difference between a saved zone snapshot and the live layout is no longer reported as a restoration incident after screen changes.
- A fresh copy of the app reads inherited preferences from `.plist` files and no longer asks for permission to access another app's data.

---

## 1.2.0 — 2026-10-28 and 2026-10-17 (builds 126 and 125)

**New**

- **Desktop bar** at the top of the screen: switchable styles (native glass, powerline, floating islands, side rail), colour palettes, transparency, and per-screen visibility.
- **Resize by dragging** in Auto Layout: dragging a window edge keeps the size you choose, and the whole side of the layout shares the difference.
- **Shrink a lone window**: it keeps its size and the freed space becomes an empty cell that the next window fills. Growing it back reclaims the cell.
- **Snapping steps while dragging**: hold ⌘ (configurable) to snap the edge in 20, 40, 60 or 80-point steps.
- **Main window shortcut**: in Auto Layout, the shortcut swaps the active window with the largest cell; press it again to undo.
- **Redesigned drop preview**, placed under the window being dragged so you can still see it.
- **Compact layout popup** (⌃⌥P), with favourites you can drop anywhere on a card.
- **Configurable shortcuts** for switching macOS desktops and applying layouts.

**Fixed**

- Changing desktops during a placement no longer inverts windows or suspends the desktop.
- The layout now picks up the columns already on screen at launch instead of reordering them.
- Terminal app tabs (Ghostty) stay in their cell when you switch tabs or drag by the tab bar.
- Learned minimum window sizes survive a desktop reactivation, so the first exchange is right.
- An impossible drop and a rebalance with nothing to do are now signalled with a beep instead of doing nothing silently.
- A window moved by macOS right after a placement (an animation) no longer suspends desktop management.
- Windows that refuse to shrink near the boundary between two screens are placed correctly.

---

## 1.1.1 — 2026-10-10 (build 123)

- **Apple Silicon only.** Intel Macs are no longer supported; the app is arm64-only and dropped from ~31 MB to ~6.5 MB.
- **Automation is off by default on new installations.** The local automation interface could be read by other programs in your session; enable it in Settings › Automation if you need it. Existing installations keep their current setting.
- The app no longer declares the Apple Events entitlement, which it never used.
- Auto Layout no longer disconnects after switching desktop or screen while it was adjusting.
- Choosing a layout now actually places the visible windows in it.
- Apps that refuse to shrink (minimum width or height) widen their cell instead of overlapping their neighbours.
- Layouts of a screen that briefly disappears (screen recorder, monitor waking, laptop reconnected) are kept and restored when it returns.
- In manual grids, a new window stays where macOS opens it instead of being pulled into a free cell.

---

## 1.1.0 — 2026-10-08 (build 121)

- **New weighted Auto Layout** becomes the public engine: adjustable columns and rows, new windows inserted next to the active one, and every placement verified — a failed placement keeps the previous arrangement.
- A window moved to another desktop (Mission Control) is integrated into that desktop's automatic layout.
- Reliable first-time placement for Chrome, Obsidian, VS Code and other Electron apps.
- Second-screen coordinate fix.
- Grid commands (`⌥⌘` + arrows, rebalance) are refused with a beep on Auto Layout desktops instead of fighting the engine.
- Settings › Reset restores the default shortcuts; export now includes shortcuts, mouse settings and custom layouts (never the licence).
- Automation `resize` and `rebalance` are all-or-nothing.
