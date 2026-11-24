# Brief for Dead Rabbit - publish nave.pub/esterones (sample-data mockup)

## Goal
Source: repo `JAFairweather/asada-tech`, branch `esterones-mockup`, file `esterones/index.html`. Do not modify that file in the repo; copy it into the nave.pub deploy.

Serve `esterones/index.html` at **https://nave.pub/esterones** (and `/esterones/`).
It is a design mockup of a water-system monitoring dashboard for the ASADA Esterones (community water board, Sámara, Costa Rica). It must be unmistakable that it is SAMPLE DATA ONLY.

## The file
- `esterones/index.html` - one self-contained static file. Plain HTML + CSS, inline SVG charts, no JS, no external requests (no fonts, CDNs, analytics).
- Spanish UI (`lang="es"`), with an English line in the banner and footer.

## Requirements
1) Deploy it as a static page at `/esterones` on nave.pub. Both `/esterones` and `/esterones/` should resolve (redirect one to the other is fine).
2) Do not alter the sample-data labeling. It currently has:
   - a dark full-width banner at the top: "DATOS DE EJEMPLO - NO SON LECTURAS REALES" plus "Sample data only"
   - "(DATOS DE EJEMPLO)" in the `<title>`
   - "valores de ejemplo" under the page heading
   - a footer stating all values, alerts and charts are sample data
   If any of these get lost in your deploy pipeline (templating, minification), put them back.
3) Keep `<meta name="robots" content="noindex, nofollow">`. Also add `X-Robots-Tag: noindex` at the server if easy. Do not add the page to any sitemap or nav on nave.pub.
4) No analytics, no tracking, no forms, no backend. Nothing on this page connects to real devices.
5) Do not touch other nave.pub routes (waggle.nave.pub, etc.).
6) Ask me before doing anything beyond this scope (DNS changes, new services, cert changes other than routine renewal).

## Done means
- `curl -sI https://nave.pub/esterones/` returns 200 (or a 301 to it) with content-type text/html.
- The page body contains "DATOS DE EJEMPLO" and the robots meta.
- Reply with the live URL, what you changed (files, config), and how to roll it back.

## Decision log
Keep a dated decision log in your reply: every tactic change (new or dropped approach, tool swap, scope cut, out-of-order step) - what changed, why, and what it affects.

## Context (not for this task)
Later this may become a live dashboard fed by a Shelly Pro EM-50 on a single-phase 240V pump (current/voltage/PF over MQTT) and a ParemTech PTLevel tank sensor. Not now - static mockup only.

- James
