# Dr. Bheeshma — Shoulder Surgeon | Website

Premium, animated, single-file website for **drbheeshmashoulderspecialist.com**, built to the supplied brand kit.

- **Palette:** Midnight Blue `#0A1E3F` · Steel Blue `#3D5F7A` · Silver Gray `#8FA3B4` · Pearl `#E6EBF1` · Soft White `#F7F8FA` · warm scapula beige accent
- **Type:** Poppins (Bold headings / Medium subheads / Regular body)
- **Slogan:** Restore Mobility. Rebuild Life.
- **Pillars:** Arthroscopy · Sports · Trauma · Joint Replacement
- **Signature:** an interactive **3D shoulder** in the hero that echoes the logo mark — navy humeral head in its socket, the two fixation screws, steel scapular spine and beige scapula. It auto-rotates and follows the cursor.

## Files
- `index.html` — the whole site (self-contained; Three.js from CDN at runtime).
- `assets/logo-mark.png` — emblem, used in the nav (blends via `mix-blend-mode:multiply`).
- `assets/logo-full.png` — full lockup, shown in the About section.
- `assets/favicon.png` — browser tab icon.
- `assets/brand-kit.png` — your original brand sheet, kept for reference.

## Open / host it
Double-click `index.html`, or host the whole folder (Netlify, Vercel, cPanel, GitHub Pages). Keep the `assets/` folder next to `index.html`. The 3D needs internet on first load for the Three.js CDN.

## Brand fidelity notes
- The logo files came on a **white background** (not transparent), so they're placed only on light sections and blended with `mix-blend-mode:multiply` — clean on any light background, no visible box. If you get a true transparent PNG or SVG, just replace the files in `assets/`.
- The dark **navy bands** (slogan + stats, footer) mirror how your brand kit alternates navy and pearl blocks. Those use crisp Poppins text rather than the raster logo, since a white-bg logo can't sit on navy.

## Before launch — confirm every `{{ ... }}` token
These are the only fields left blank rather than guessed for a real doctor:
- Qualifications (MBBS / MS Ortho / fellowship), affiliations, memberships
- Clinic name, full address, phone, email, hours
- The four stat numbers (procedures, years, rating, consult time)
- Three patient testimonials
- Portrait photo → `assets/portrait.jpg` (4:5), then replace the placeholder block in About
- Optional: medical council registration number in the footer disclaimer (if required)

## Booking form
Front-end demo only right now (shows a confirmation, sends nothing). Wire it to email / WhatsApp API / a booking tool (Booknetic, Calendly, or your n8n flow) before going live.

## Already real & accurate
- Social links: YouTube `@drbheeshma`, Instagram `@dr.bheeshu_prem`.
- Conditions, treatments and FAQ copy — medically standard for a shoulder surgeon, plain and warm.
- His content-creator voice ("medicine made relatable") reflected in About + content hub.

## Quick re-skin
All colours are CSS variables in `:root` at the top of `index.html`. Change `--navy`, `--steel`, `--beige` etc. and the whole site follows. The 3D model colours are hex values in the script (search `brand materials`) if you ever want to nudge them.

---

## Colour theme switcher (client preview)
A small **Theme** control sits bottom-right. Clicking a swatch instantly re-skins the whole site — including the 3D shoulder — so the client can choose a direction. Three variations, all built from the brand-kit palette:

1. **Pearl & Navy** — the default light, airy look (matches the brand mockups).
2. **Midnight** — a dramatic dark mode using the same navy/steel/beige, for a premium, cinematic feel.
3. **Ivory & Bronze** — a warm luxury variant: cream backgrounds, navy ink, bronze accent.

The choice is remembered in the browser (localStorage) between visits.

**Once the client picks one:**
- To set it as the permanent default, change `"pearl"` to `"midnight"` or `"ivory"` in the small script near the top of the file (search `drb-theme`), and in the `apply(saved)` fallback.
- To remove the switcher for the live site, delete the `<div class="theme-switch">…</div>` block and the `theme switcher` script section — the site keeps whatever default you set.

Each theme is a small block of CSS variables under `html[data-theme="…"]` in the `<style>`, and a matching colour set in the `THEMES3D` object in the script (for the 3D model). Tweak either freely.

---

## 3D shoulder joint (updated)
The hero now shows a **generic, interactive shoulder joint** — you can **drag to rotate** it, it auto-rotates when idle, and its lighting/accent follow the active theme.

**Two modes, automatic:**
1. **Built-in (default):** a clean bone-white **ball-and-socket** (humeral head + glenoid socket + humerus shaft + cartilage rim). No file needed — it just works.
2. **Real anatomical model (recommended):** drop any shoulder model named **`assets/shoulder.glb`** into the folder and it loads automatically — the scene centres, scales and lights it for you. No code changes required.

**Where to get a free `.glb`:**
- Sketchfab — search "shoulder joint", filter to *Downloadable* + a licence you're happy with, download **glTF/GLB**.
- Meshy AI — anatomy gallery models are **CC0** (royalty-free, commercial-safe).
- AnatomyTool Open3DModel — Creative Commons anatomy `.glb` files (check attribution terms).

Rename the downloaded file to `shoulder.glb`, put it in `assets/`, refresh. If you want, send me the `.glb` and I'll bundle it and fine-tune the framing/scale.

> Note: the earlier "signature" description (a 3D model echoing the logo mark) is superseded by this generic joint.

---

## A real model is now included (`assets/shoulder.glb`)
I built an actual mesh with **trimesh** (a Python 3D toolkit) from your reference image and exported it to `assets/shoulder.glb` — so the hero now loads a real GLB model (humeral head, glenoid, humerus, scapula blade, acromion, clavicle, coracoid + ligaments) instead of browser shapes. It's Y-up, vertex-coloured, drag-to-rotate, and theme-lit. It renders smooth in the browser (any faceting you may have seen in a preview is not present in WebGL).

To swap it for a higher-fidelity model later (e.g. an AI image-to-3D result from Meshy/Tripo, or a real scan), just replace `assets/shoulder.glb` — no code changes.

---

## Hero visual is now a coded SVG (supersedes the 3D)
Per the latest direction, the hero shoulder is a **hand-coded SVG illustration** traced from the reference image and styled/animated with CSS — not a 3D model. It has:
- Anatomically-labelled parts (Humeral Head, Humerus, Glenoid, Scapula, Clavicle, Acromion) that **reveal on hover** with a leader line.
- A gentle float animation + a slow-rotating "precision" ring; both respect reduced-motion.
- Colours drawn straight from the reference (navy humeral head, grey glenoid, bone scapula/humerus/clavicle) and labels/ring that follow the theme switcher.

To restyle it, the SVG lives in the hero `.stage` and its CSS is under `/* ANATOMY ILLUSTRATION */` in the `<style>`. All Three.js/WebGL and the GLB loader have been removed; `assets/shoulder.glb` is no longer used by the site (left in the folder for reference — safe to delete).

---

## Cinematic video hero (final)
The hero is now a **full-bleed cinematic video** — your Flow/Veo render of the glenohumeral joint (navy humeral head rotating in the socket, steel-blue rim light, drifting particles). Files in `assets/`:
- `hero-video.mp4` + `hero-video.webm` — web-optimised, muted, autoplay-loop (audio stripped so it autoplays everywhere).
- `hero-poster.jpg` — shown before the video loads, on mobile, and for reduced-motion users.
- `hero-still-a.jpg` / `hero-still-b.jpg` — the two 2K stills, kept for reuse (section backgrounds, social, etc.).

A left-weighted dark-navy overlay sits over the video so the headline, slogan and CTAs stay readable, and the nav switches to light text + a logo badge while it's over the video, then back to your theme colours once you scroll. Respects `prefers-reduced-motion` (shows the still instead). The SVG anatomy it replaced is still in the file's styles but no longer rendered.

To swap the clip later, just replace `hero-video.mp4/.webm` (and `hero-poster.jpg`) — no code changes.
