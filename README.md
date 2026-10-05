# product_training_visuals

## LED Tape System Visualizer — `led-system-visualizer.html`

A single-file, interactive 3D model of a residential LED tape lighting system, built for producing
clean, presentation-ready images for training slides. No build step: open the HTML file in a desktop
browser (Chrome, Edge, Firefox, Safari). The only dependency is Three.js r128, loaded from cdnjs.

### What's in the scene
- Context architecture (light gray, adjustable X-ray opacity): walls, ceiling, floor, base and upper
  cabinets, bookcase, shower wall with recessed niche, cove ledge, a closet behind the wall, and optional framing.
- Five lighting zones, each color-coded:

  | Zone | Location | Power supply |
  | --- | --- | --- |
  | Z1 Cove | Deep channel on a ledge, aimed at the ceiling | Attic (remote) |
  | Z2 Under-cabinet | Front-mounted channel | Sink base cabinet |
  | Z3 Toe-kick | Low-profile channel | Sink base cabinet |
  | Z4 Shelving | Edge-mounted channels in the bookcase | Closet |
  | Z5 Shower niche | Sealed IP67 channel | Closet, outside the wet area |

- Each channel assembly has LED tape (PCB + LED chips), an aluminum channel, a frosted diffuser,
  end caps, mounting clips, connectors and jumpers.
- Power and controls: one power supply per zone (wattage placeholders), a breaker panel, and a
  5-gang dimmer bank. Wiring has realistic routing: low-voltage wires colored by zone, line-voltage
  feed and switched legs.

### Controls (side panel, collapsible with `P`)
- **View**: switch between 3D and the flat system diagram (breaker → dimmer → power supply → tape).
  - Camera presets: Perspective, Isometric, Top/Plan, Front and Side elevation, Cross-section close-up.
  - Lens (FOV) and a frame aspect lock (16:9 / 4:3 / 1:1) so captures match your slide.
  - Six in-memory saved-view slots.
- **Layers**: per-layer checkboxes, plus Show all / Hide all / Solo per group (lighting, wiring,
  power, controls, architecture, labels). Architecture also has an X-ray opacity slider.
- **Zones**: toggle each zone, or click **Only** to isolate one.
- **Lighting**: glow on/off, brightness (emissive strength), dim level, and CCT (2700/3000/3500/4000K).
- **Detail**: pick any channel segment, then use the exploded-view slider, the cross-section
  (clipping plane with filled cut faces), the cut position, and a close-up camera.
- **Labels**: component callouts, dimensions, wire labels (gauge and length placeholders),
  room labels, and label size.
- **Render**: background (white / light gray / dark / transparent) and soft shadows. Anti-aliasing is always on.
- **Export** (panel footer):
  - **Export PNG** saves the view at 1×, 2× or 4×, with labels composited in. Use **Transparent
    background** for drop-on-any-slide images.
  - **Export all saved views** saves one PNG per saved slot.
  - File names look like `your-brand_<view-name>_<YYYYMMDD-HHMMSS>_<scale>x.png`.
  - **Hide UI for capture** (`H` / `Esc`) hides the panel and on-screen helpers.

Mouse: drag to orbit · right-drag or Shift-drag to pan · wheel to zoom toward the cursor · double-click to re-center on a point.
Keys: `1`–`6` recall a saved view · `Shift+1`–`6` save one · `E` exports · `H` toggles capture mode · `P` toggles the panel.

### Customizing
Everything you're likely to edit is at the top of the `<script>` block:
- `BRAND`, `ZONE_COLORS`, `COLORS`, `BACKGROUNDS`, `CCT_COLORS`: brand colors, fonts and name.
- `UNITS` (imperial/metric) and `PROFILE_SCALE` (how much channel cross-sections are exaggerated).
- `LAYERS`: every toggleable layer and its group. Architecture layers name their builder function.
- `PROFILES`: channel profile dimensions (nominal mm, shown in labels).
- `ZONES`: one entry per zone. It holds:
  - channel runs and segments
  - power supply location, wattage and label text
  - wire gauges, plus line-voltage and low-voltage routing waypoints
  - light-wash surfaces, callout offsets and dimensions

  Add an entry to add a zone. The 3D model, labels, diagram row and panel controls are generated from it.
- `CAMERA_PRESETS`: preset camera angles.
