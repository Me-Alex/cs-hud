<h1 align="center">
  <br>
  cs-hud
  <br>
</h1>

<p align="center">
  <strong>A free, customizable spectator HUD for Counter-Strike 2 streams and broadcasts.</strong>
</p>

<p align="center">
  <a href="https://github.com/drweissbrot/cs-hud/releases/latest">
    <img src="https://img.shields.io/github/v/release/drweissbrot/cs-hud?style=flat-square&color=orange&label=latest+release" alt="Latest Release">
  </a>
  <a href="https://github.com/drweissbrot/cs-hud/blob/master/license.txt">
    <img src="https://img.shields.io/badge/license-ISC-blue?style=flat-square" alt="License">
  </a>
  <a href="https://github.com/drweissbrot/cs-hud/issues">
    <img src="https://img.shields.io/github/issues/drweissbrot/cs-hud?style=flat-square" alt="Issues">
  </a>
  <img src="https://img.shields.io/badge/CS2-supported-brightgreen?style=flat-square" alt="CS2 Supported">
  <img src="https://img.shields.io/badge/node-%3E%3D18-informational?style=flat-square" alt="Node Version">
</p>

<p align="center">
  <a href="#-getting-started">Getting Started</a> •
  <a href="#-obs-browser-source">OBS Setup</a> •
  <a href="#-customization">Customization</a> •
  <a href="#-faq">FAQ</a> •
  <a href="#-credits">Credits</a>
</p>

<br>

![cs-hud screenshot](assets/cs2-hud-screenshot-1080.png)

---

## ✨ Features

- **Live game data** — health, armor, money, weapons, round timer, score, and more
- **Team panels** — all 10 players visible at once with kills, assists, deaths, and utility
- **Mini radar** — powered by [Simple Radar](https://readtldr.gg/simpleradar) for clear map reads
- **OBS-ready** — transparent background via `?transparent` URL param, plug-and-play Browser Source
- **Fullscreen overlay** — dedicated overlay app for on-top display without OBS
- **Fully customizable** — colors, fonts, scale, and advanced theming via the `/config` page
- **Free & open source** — use it for personal streams, community events, or tournaments

---

## 🚀 Getting Started

### 1 — Download the server

| Platform | Download |
|----------|----------|
| Windows  | [`cs-hud-server-win.exe`](https://github.com/drweissbrot/cs-hud/releases/latest/download/cs-hud-server-win.exe) |
| Linux    | [`cs-hud-server-linux`](https://github.com/drweissbrot/cs-hud/releases/latest/download/cs-hud-server-linux) |

### 2 — Install the GSI config

1. Download [`gamestate_integration_drweissbrot_hud.cfg`](https://github.com/drweissbrot/cs-hud/releases/latest/download/gamestate_integration_drweissbrot_hud.cfg)
2. Place it in your CS2 cfg folder:
   ```
   C:\Program Files (x86)\Steam\steamapps\common\Counter-Strike Global Offensive\game\csgo\cfg
   ```
   > **Tip:** In Steam, right-click CS2 → `Properties` → `Installed Files` → `Browse`, then navigate to `game/csgo/cfg`.

### 3 — Run & spectate

1. (Re)start CS2
2. Run `cs-hud-server-win.exe` — you should see `cs-hud is active` in the console
3. Open a demo or spectate via CSTV
4. Visit **http://localhost:31982/hud** in your browser — the HUD is live!

> Additional pages:
> - **Config:** http://localhost:31982/config
> - **Radar only:** http://localhost:31982/radar

---

## 📺 OBS Browser Source

Best option for streamers who don't need the HUD overlaid on their own screen.

1. In OBS, add a **Browser Source**
2. Set the URL to:
   ```
   http://localhost:31982/hud?transparent
   ```
3. Set **Width** and **Height** to match your stream resolution (e.g. `1920` × `1080`)
4. Clear the **Custom CSS** field completely
5. Spectate a match in CS2 — the HUD will appear automatically

---

## 🪟 Fullscreen Overlay

Use this if you want the HUD on top of CS2 while you play/spectate.

| Platform | Download |
|----------|----------|
| Windows  | [`cs-hud-overlay-win32-x64.zip`](https://github.com/drweissbrot/cs-hud/releases/latest/download/cs-hud-overlay-win32-x64.zip) |
| Linux    | [`cs-hud-overlay-linux-x64.tar.gz`](https://github.com/drweissbrot/cs-hud/releases/latest/download/cs-hud-overlay-linux-x64.tar.gz) |

1. Extract and run `cs-hud-overlay.exe` (Windows) or `cs-hud-overlay` (Linux)
2. In CS2: `Settings` → `Video` → set **Display Mode** to `Fullscreen Windowed`
3. Spectate a match — the overlay appears automatically
4. If the HUD is on the wrong monitor, select it in the taskbar and press `Win + Shift + Arrow Keys`

---

## 🎨 Customization

Open **http://localhost:31982/config** and scroll to **Style Overrides**.

| What to change | Setting key |
|---|---|
| T-side color | `css.terrorists-fill-rgb` |
| CT-side color | `css.counter-terrorists-fill-rgb` |
| Text color | `css.terrorists-text-rgb` |
| Font | `css.primary-font-family` (must be installed on your PC) |
| Overall scale | `css.base-scale-factor` (default: `10px`) |

After any change, press **Save** then **Force HUD Refresh**.

For advanced theming (custom layouts, new panels, full CSS overrides), see [`docs/theming.md`](docs/theming.md).

---

## ❓ FAQ

<details>
<summary><strong>Does this work with CS2?</strong></summary>

Yes — fully supported. It also works with CS:GO. If you notice anything broken, [please open an issue](https://github.com/drweissbrot/cs-hud/issues).
</details>

<details>
<summary><strong>Can I use this for my event or tournament?</strong></summary>

Yes — attribution is not required, but a link back to this repo is always appreciated.
</details>

<details>
<summary><strong>Why use a custom HUD at all?</strong></summary>

CS2's built-in spectator HUD isn't designed for video. Viewers can't press Tab, player names were missing in early CS2, and readability on large screens is poor. Custom HUDs like this one show everything at a glance, look better on TV, and are built specifically for broadcast.
</details>

<details>
<summary><strong>I need help!</strong></summary>

1. Check the [`docs` folder](https://github.com/drweissbrot/cs-hud/tree/master/docs) first
2. If you're still stuck, [open an issue](https://github.com/drweissbrot/cs-hud/issues)

Please don't send emails asking for support — issues are the right place.
</details>

---

## 🛠 Running from Source

Requires **Node.js ≥ 18** and **Yarn**.

```bash
git clone https://github.com/drweissbrot/cs-hud.git
cd cs-hud
yarn install
yarn start
```

For live-reload during development:
```bash
yarn watch
```

---

## 📄 Changelog

See [`changelog.md`](changelog.md) for the full version history.

---

## 🙏 Credits

- [**Simple Radar**](https://readtldr.gg/simpleradar) by [readtldr.gg](https://readtldr.gg) — clean minimaps bundled with this project
- [**u/Bkid**](https://www.reddit.com/user/bkid) — for the [definitive Game State Integration documentation](https://www.reddit.com/r/GlobalOffensive/comments/cjhcpy/game_state_integration_a_very_large_and_indepth) that made this project possible

![Simple Radar logo](assets/simpleradar.webp)

---

<p align="center">
  Made with ❤️ for the CS community · <a href="https://github.com/drweissbrot/cs-hud/issues">Report a bug</a> · <a href="https://github.com/drweissbrot/cs-hud/releases">Releases</a>
</p>
