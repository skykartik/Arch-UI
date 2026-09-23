# Changelog

## 2.4.0

- **Weather effects on screen** (toggle in Widgets) — an animated rain/snow/fog/storm overlay matching current conditions, plus a light haze on poor air-quality days (US AQI, fetched alongside the forecast). Painted behind all page content — it never intercepts a click.
- Fixed the weather widget's layout — the temperature and description were rendering crammed onto one line; they now stack properly and truncate cleanly instead of stretching the card.
- Film grain is now on by default.
- Theme gallery is now a grid instead of a list.
- Fixed a bug where a fresh install showed "Aurora Classic" as already applied, just because its settings happened to match the defaults — the gallery now only marks a card active once you've actually picked one.
- Renamed the "Blocky World" theme to **Minecraft**, and added support for a bundled custom wallpaper video (`assets/themes/minecraft/wallpaper.mp4`) with an automatic fallback to the built-in pixel-art scene if that file isn't present.
- Renamed the "Cyberpunk" theme to **Synth Wave**.
- "Reset everything to default" no longer wipes out theme packs you've loaded.

## 2.3.0

- **Real `.zip` support for theme packs** — parses the zip container format itself and decompresses via the browser's native `DecompressionStream`, so it works for both stored and DEFLATE-compressed zips without a hand-rolled (and unverifiable) decompressor.
- Much more specific error messages throughout theme pack loading (missing `theme.json`, malformed JSON, a referenced asset that isn't found, an empty pack) instead of failing silently.
- **Removed the Now Playing widget** — it could only ever be a manual card, not a real sync (no extension API can read what's playing in another app or tab), and a manual "widget" that shows whatever you typed isn't worth the UI real estate.
- **Weather location is now fully manual** — search a city and pick it; the automatic geolocation prompt is gone entirely.
- Fixed a real bug: switching to a prebuilt wallpaper and then trying to switch back to your own uploaded photo/video did nothing — the "Your photo/video" thumbnail had no click handler at all, and was incorrectly always shown as "active" regardless of what was actually applied.
- Live wallpapers now also pause while the settings drawer is open, not just when the tab itself is hidden.

## 2.2.0

- **Themes vs. Custom** mode split. Two built-in theme packs beyond the original look, each with genuinely custom content (not just recolored defaults): an animated pixel-art wallpaper with an 8-bit LCD clock and a chunky click sound; an animated synthwave grid with a neon glow clock and a laser-blip click sound.
- **Theme packs** — folder-based loading of community-style themes (wallpaper image/video + click/type sound files + a settings JSON), validated against a strict whitelist.
- **Widgets tab** — Weather (live) and Now Playing (manual — later removed in 2.3.0).
- Local theme codes: copy your current look as a portable text code, paste one someone shares with you.

## 2.1.0

- Real favicons for search engines, the Google Apps menu, and bookmarks (fetched live, colored-letter fallback if one fails to load).
- Fixed the search-engine dropdown colliding with the shortcuts grid — it was nested inside a stacking context that trapped its z-index; moved it to the document root and positioned it dynamically from the icon's real on-screen location.
- Fixed the ripple tap-effect animation (was animating `width`/`height` directly instead of `transform: scale()`, which is what was causing the jank).
- Fixed an intermittent shortcuts-grid flicker — every settings change was rebuilding (and re-fetching) every shortcut's favicon, even when shortcuts hadn't changed.
- Removed the Cartoon, Neon, Analog Minimal, and Minimal clock styles (with a migration for anyone who had one selected).
- Added shortcut hover animations (5), tap-to-open effects (5), and search bar focus animations (4).
- Every on/off setting is now an animated pill toggle instead of a checkbox.
- Removed background ambience sounds (rain/wind/lo-fi/cafe loops) — decided they weren't worth keeping.

## 2.0.0

- Renamed from "Aurora — Custom New Tab" to **Arch UI**, with a new transparent arch-shaped icon.
- First-run setup wizard: look, clock, search engine, and explicit opt-in questions for shortcuts and bookmarks (nothing is auto-added without asking).
- **Bookmarks** menu in the top bar, next to Google Apps.
- **Layout tab** — independent show/hide for the clock, search bar, shortcuts, Google Apps menu, bookmarks menu, and account button.

## 1.0.0

- Initial release ("Aurora — Custom New Tab"): 5 palettes, animated/photo/upload wallpapers with automatic palette matching, 7 clock styles, a customizable search bar (4 styles, 5 engines), customizable shortcuts imported from browsing history, 4 synthesized sound packs, a Google Apps menu, and an account chip showing the signed-in email.
