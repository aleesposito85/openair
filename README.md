# OpenAir

OpenAir is an open-source, 3D-printed HEPA air purifier you can build yourself: a backward-curved
EC blower pulling through a widely available Xiaomi 2/3-series compatible H13 cartridge, an
ESP32-S3 running ESPHome, and a printed shell in three variants — Side Table, Value Tower, and a
445 m³/h Reference Tower.

**Status: pre-prototype.** The design is complete on paper — a 71-page engineering document,
parametric CAD, ESPHome firmware, and a priced bill of materials — but a physical prototype has
not yet been built or measured. CADR and noise figures are engineering estimates, not
measurements. Building and measuring the Value Tower is the next step; measured figures will
replace the estimates before anything ships.

## Live

- Site: <https://openair.craftwisp.com>
- Shop: <https://openair.craftwisp.com/shop/> — printed-part kits, electronics kits and spares
- Design document: [OpenAir-Design.pdf](OpenAir-Design.pdf) — system-curve model, blower
  selection against published datasheets, full circuit schematic, firmware listing, assembly
  sequence.

## What is in this repository

| Path | What it is |
|---|---|
| `index.html` | The public site (single page, no build step) |
| `shop/index.html` | The shop page as published — catalog inlined, checkout posts to an order workflow |
| `shop/index.template.html` | Source template for the shop page (`__CATALOG__` placeholder) |
| `assets/` | Product renders, shop cards, gallery images |
| `OpenAir-Design.pdf` | 71-page engineering design document |
| `robots.txt`, `sitemap.xml` | Site metadata |

Not included: internal shop tooling, cost/pricing data and campaign planning documents (kept
private).

## Why a centrifugal blower

Most DIY purifiers fail because they use axial computer fans, which move air at almost no
pressure. A cylindrical HEPA cartridge needs 135–160 Pa at its working point; an axial PC fan tops
out around 100 Pa — a published smoke-decay test of 120 mm PC fans on exactly that cartridge
measured about 16 m³/h CADR. OpenAir uses a backward-curved EC centrifugal blower (the class
Xiaomi runs at 38–50 W), takes PWM speed control directly from the ESP32, and joins Home
Assistant natively through ESPHome — no cloud account, no vendor app.

Features: auto mode from smoothed PM2.5 · sleep / turbo / manual with five touch pads ·
PM1/PM2.5/PM10 sensing (SEN66 adds CO₂, VOC, NOx, temperature and humidity on the reference
build) · filter life tracked by both processed air volume and calendar age · hall-sensor
interlock that cuts the blower when the base is removed · blower stall detection · air-quality
light · on-device timers and night schedule.

## Licensing

- Code in this repository (HTML/JavaScript): **MIT** — see `LICENSE`.
- Design document and documentation: **CC BY 4.0**.
- The project's full source pack, to be published with the campaign: CAD under **CERN-OHL-S v2**,
  firmware under **MIT**.
