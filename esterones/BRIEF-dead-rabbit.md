# Brief for Dead Rabbit - publish nave.pub/esterones (sample-data mockup)

## Goal
Source: repo `JAFairweather/asada-tech`, branch `esterones-mockup`, file `esterones/index.html`. Do not modify that file in the repo; copy it into the nave.pub deploy.

Serve `esterones/index.html` at **https://nave.pub/esterones** (and `/esterones/`).
It is a design mockup of a water-system monitoring dashboard for the ASADA Esterones (community water board, Sámara, Costa Rica). It must be unmistakable that it is SAMPLE DATA ONLY.

## The file
- `esterones/index.html` - the dashboard. One self-contained static file. Plain HTML + CSS, inline SVG charts, no JS, no external requests (no fonts, CDNs, analytics).
- `esterones/admin/index.html` - a NON-FUNCTIONAL mockup of the admin page (alert contacts, sensor tokens). Same rules: static, no JS. Its form fields and buttons do nothing - keep it that way. It has its own banner: "MAQUETA - NADA SE GUARDA NI SE ENVÍA". The dashboard links to it as `admin/` and it links back as `../`.
- Spanish UI (`lang="es"`), with an English line in the banner and footer.

## Requirements
1) Deploy the dashboard at `/esterones` and the admin mockup at `/esterones/admin/` on nave.pub. `/esterones` and `/esterones/` should both resolve (redirect one to the other is fine), and the relative links between the two pages must work.
2) Do not alter the sample-data labeling. It currently has:
   - a dark full-width banner at the top: "DATOS DE EJEMPLO - NO SON LECTURAS REALES" plus "Sample data only"
   - "(DATOS DE EJEMPLO)" in the `<title>`
   - "valores de ejemplo" under the page heading
   - a footer stating all values, alerts and charts are sample data
   If any of these get lost in your deploy pipeline (templating, minification), put them back.
3) Keep `<meta name="robots" content="noindex, nofollow">`. Also add `X-Robots-Tag: noindex` at the server if easy. Do not add the page to any sitemap or nav on nave.pub.
4) No analytics, no tracking, no form handling, no backend. Nothing on these pages connects to real devices, and nothing typed into the admin mockup may be sent or stored anywhere. Do not add a server endpoint for it.
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
