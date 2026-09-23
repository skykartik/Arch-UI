# Arch UI

A premium, fully customizable new tab page for Chrome — themes, animated wallpapers, custom clocks, sound packs, live widgets, and a real theme-pack system anyone can build for.

<!-- Add a screenshot or two here once you have one:
![Arch UI screenshot](docs/screenshot.png)
-->

## Install

**From source (this repo):**

1. `git clone` or download this repo.
2. Open `chrome://extensions`.
3. Turn on **Developer mode** (top right).
4. Click **Load unpacked** and select the `arch-ui` folder.
5. Open a new tab. A short first-run setup walks you through your look, clock, search engine, shortcuts, and bookmarks — all skippable.

**Not yet on the Chrome Web Store.** If you publish it there, update this section with the store link.

## Features

The gear icon opens two modes:

- **Themes** — one-click looks, laid out as a grid of cards. Three built in, each with real custom content, not just a recolored default:
  - **Aurora Classic** — default.
  - **Minecraft** — theme inspired from minecraft.
  - **Synth Wave** — animated retrowave scene.

- **Custom** — the full dial-by-dial editor: Look, Clock, Search, Shortcuts, Sound, Layout, and Widgets tabs.

### Loading a theme pack

Below the built-in gallery, the Themes tab has a dropzone for **theme packs** — folders (or zips of them) anyone can build, containing their own wallpaper image/video and click/type sound files, not just settings. See [`docs/theme-pack-format.md`](docs/theme-pack-format.md) for the full spec.

Drag a folder or a `.zip` onto the dropzone, or use the picker buttons. Zip support handles both stored and DEFLATE-compressed zips — it parses the zip container itself and hands compressed bytes to the browser's own built-in `DecompressionStream`, rather than a hand-rolled decompressor.

Every `theme.json` field is checked against a strict whitelist on load; unrecognized or malformed keys are silently dropped. There's no way for a pack to run code — it can only set the same options available by hand in Custom mode, plus its own media files.

### Look

5 palettes, flat colors, gradients, or full wallpapers: 5 animated Live scenes (canvas-drawn, paused automatically while the tab is hidden *and* while the settings drawer is open, so they don't burn CPU when nobody's looking), 6 curated Photo wallpapers, or your own upload (image, video, or a pasted link). The interface palette recomputes automatically from whichever you pick.

### Clock

8 designs with live thumbnails in the picker: Serif, Mono, Analog, Flip, Spoken, Comic Pop, Graffiti, Handwritten — plus two theme-exclusive styles (an 8-bit LCD look and a neon glow) that ship with the Minecraft and Synth Wave themes. Adjustable position/size, independent greeting/date color overrides.

### Search

4 bar styles, 5 engines with real favicons, 4 focus animations, and a slide-down engine picker anchored to the icon's actual on-screen position.

### Shortcuts & Bookmarks

Shortcuts: 4 shapes, 5 hover animations, 5 tap-to-open effects, imported from your browsing history on request during setup. Bookmarks: a menu next to Google Apps in the top bar, listing your real Chrome bookmarks.

### Sound

7 synthesized interface click/typing packs (including two built for the Minecraft and Synth Wave themes), generated on the fly with the Web Audio API — no audio files bundled for these. A theme pack can also supply real audio files, played back directly.

### Widgets

- **Weather** — you search for a city and pick it; nothing is auto-detected. Live conditions and air quality (US AQI) from [Open-Meteo](https://open-meteo.com/) (free, no key, no account). Three card styles.
- **Weather effects** — an optional, toggleable overlay: rain, snow, fog, or a storm (with occasional lightning) matching current conditions, plus a light haze layered in on poor air-quality days. Painted behind all page content, so it never intercepts a click — it's decorative, not interactive.

### Layout

Independent show/hide toggles for the clock, search bar, shortcuts, Google Apps menu, bookmarks menu, and account button.

### Sharing your look

"Copy theme code" (Layout tab) bundles your current settings — palette, wallpaper choice, clock, search, layout — into a portable text code. "Add a theme code" (Themes tab) applies one someone sends you and saves it to your gallery permanently.
```

## Contributing a theme pack

See [`docs/theme-pack-format.md`](docs/theme-pack-format.md) for the format, then open a PR adding your pack under `assets/themes/<your-theme>/` and a matching entry in `THEME_PRESETS` (`js/state.js`) if you'd like it built in, or just share the folder/zip directly with other users via the in-app loader.

## License

MIT — see [`LICENSE`](LICENSE). Update the copyright name/year if you're publishing this as your own repo.
