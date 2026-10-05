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

### Training visuals mode (outline sections 3 and 4)
Switch the **View** mode to **Training visuals** to get slide-ready visuals for the
"From downlights to custom linear" session. Each one is drawn as vectors on a 16:9 canvas (or as a
3D scene with callouts), so it exports crisply at any scale.

| Section | Visual |
| --- | --- |
| 3 | Running example overview: the 20 ft cove, the four calculations, and their results |
| 3.1 | Load and supply size: formula bar, numbers revealed step by step, supply loading bar with the 80% limit |
| 3.2 | Brightness along the run (single-end vs. both-end feed, with the max-run marker), plus a 3D version of the fading cove |
| 3.3 | Four feed methods with animated current flow, plus a 3D feed-method scene (pick the method in the panel) |
| 3.4 | Supply-to-tape voltage-drop walkthrough (current → round trip → resistance → drop → verdict) and a wire gauge vs. distance table |
| 4.1 | Cut intervals and dark end (overview plus zoomed detail plus decision options), and a 3D close-up of the cut point and end cap |
| 4.2 | 3D corners, joins and jumpers: mitered corner with flex connector, pre-formed corner, jumper with service loop, straight join |
| 4.3 | Nine-step takeoff checklist, and a color-coded plan with the takeoff and accessory tables built row by row |
| 4.4 | Common quoting mistakes, each with its fix |

- **Build steps:** use ◀ ▶ or the ← / → keys. **Export all build steps** saves one PNG per step, ready
  for a PowerPoint build.
- **Animation:** animated visuals show moving current flow. **Record video** saves 6 s as MP4, or as
  WebM if the browser can't record MP4.
- **Shared settings:** CCT, glow, dim, background, transparent export and label size all apply.
- **Editable inputs:** **Running example & placeholders** in the panel, or `EXAMPLE`, `PARTS`,
  `AWG_OHMS_PER_1000FT`, `TAKEOFF_ZONES`, `CHECKLIST` and `MISTAKES` in section 1b of the code.
  Every visual recalculates from these, including:
  - the run length, W/ft, supply distance and max run
  - the supply sizes and the 80% factor
  - the wire gauge and drop limit
  - the cut interval and profile stick length
  - clip spacing, waste allowance, and the part-number placeholders
- **Illustrative model:** the brightness-along-the-run curves are calibrated so a single-end feed at
  the max run drops `dropAtMaxPct`. Replace the figures with ilLumenate spec values.

### Intermediate section 5 and the Advanced session
The **Training visuals** dropdown is grouped by course and block.

**Intermediate · 5 Scaling up**

| Section | Visual |
| --- | --- |
| 5.1 | Supply placement plan: local vs. remote, wire gauge worked out for each distance, plus the rules of placement |
| 5.2 | Dimming cheat sheet, flagged "Go deeper in Advanced" |
| 5.3 | Recap in four lines |

**Advanced · "Integration, profile matching, and control planning"**

| Section | Visual |
| --- | --- |
| A1.1 | Animated leading- vs. trailing-edge waveforms, the failure-mode table, and a dimmer load window (min load, LED rating, inrush, neutral and ghosting) |
| A1.2 | Animated CVR vs. PWM, a PWM-frequency-vs-camera filmstrip, and a tape type × dimming method matrix |
| A1.3 | Integration paths (wall dimmer / processor / DMX-DALI), dim-to-warm vs. tunable white (CCT curve and comparison table), and a sample integration wiring template |
| A2.1 | Mixing-distance section with simulated brightness ripple (pick the optics case), and a hotspot gallery |
| A2.2 | Thermal comparison with the tape limit, plus max W/ft by profile |
| A2.3 | Mud-in (5/8" drywall) and knife-edge sections, the profile selection matrix, and the mud-in install sequence |
| A3.1 | Client scenes → zone schedule, with DMX addresses assigned automatically |
| A3.2 | Protocol table and decision tree |
| A3.3 | DMX address map, and daisy-chain / termination / splitter diagrams |
| A3.4 | Multi-supply power topology ("never parallel outputs"), and a commissioning checklist handout |
| A4 | "What to verify before you install" checklist and listing-details card |

**Editing the content**

Advanced numbers and tables live in **section 1c** of the code:

| Values | Covers |
| --- | --- |
| `PLACEMENT`, `CONTROL_TYPES`, `RECAP` | Intermediate section 5 |
| `DIMMER`, `FAILURE_MODES`, `PWM`, `TAPE_METHODS` | A1.1–A1.2 |
| `DTW`, `DTW_TABLE` | A1.3 |
| `DIFFUSERS`, `OPTICS_CASES` | A2.1 |
| `THERMAL`, `PROFILE_MATRIX` | A2.2–A2.3 |
| `ADV_ZONES`, `SCENES`, `DMX`, `PROTOCOLS` | A3 |
| `COMMISSION_CHECKS`, `CODE_CHECKLIST`, `LISTING` | A3.4 and A4 |

The main numeric placeholders can also be edited live in the panel. The hotspot and thermal figures
are simulated or illustrative, so replace them with your measured values.

### Install guide (custom job walkthrough)
The **Install guide · Custom cove** group in the Training visuals dropdown is a step-by-step install
walkthrough for one job, written for an installer who is new to LED tape. It ships set up for a
57″ × 119.5″ cove:
- St. Helens SF channel (SH01) with LED-HD-SW 24 V tape.
- Two strips, both fed from corner A:
  - Strip 1 runs A → B → C: 57″, a jumper at B, then 119.5″.
  - Strip 2 runs A → D → C: 119.5″, a jumper at D, then 57″.
- Both strips end, capped, at corner C.

| Section | Visual |
| --- | --- |
| Guide | Cover: the job, the plan and the ten steps |
| Overview | Plan view built strip by strip, and the cove in 3D (layout, power and jumpers, finished) |
| Parts | The channel, lens, snap clip, swivel bracket and tape drawn from the CAD files; parts list and tools |
| Step 1 | Measure and check square, snap the channel line, and a clip-mark table for every side |
| Step 2 | 3D clip install: marks, screws, snapping the channel in, the swivel-bracket option |
| Step 3 | Channel cut list per side, how the cuts come out of each stick, cutting tips |
| Step 4 | Cutting tape only on the marks, the four pieces (segments and lengths), labeling |
| Step 5 | Four corner routes in 3D (gap + jumper, miter + inside jumper, miter + L connector, butt + notch), and what goes at each corner |
| Step 6 | Making the jumpers: strip, solder + to +, heat-shrink, service loop |
| Step 7 | Running power to corner A in 3D (from the attic, up through the wall, or a supply in the cove), and a wiring diagram |
| Step 8 | Assembly in cross-section: clean, tape, test, lens, clips |
| Step 9 | Meter checks before closing up |
| Step 10 | Troubleshooting |
| Done | The finished cove, lit |

**Panel → Install guide · custom job**
- **▶ Play guide** steps through every visual and build step. A caption bar shows the narration, and
  3D steps get a slow camera move. **Pace** sets the speed. **Voice-over** reads the captions aloud
  (live playback only). Press `Esc` to stop.
- **● Record video** plays the whole guide into one video file: MP4, or WebM where the browser can't
  record MP4. It records a 16:9 frame; hide the panel (`P`) first for a larger frame.
- **Printable guide** renders every step and opens a self-contained page with images, numbered
  instructions, the clip-mark table, the cut lists and the parts list. Print it, or save it as PDF.
- **Copy job link** copies a URL with the job encoded (`#guide&job=…`). Opening that link goes
  straight into the guide with those settings.
- The job inputs (sides, cut interval, W/ft, clip spacing, corner route, feed route, supply location,
  and so on) recalculate everything: tape pieces snapped to the cut marks, clip marks, the cut list,
  the parts list, the supply size and the lead gauge.

**Editing**: job values are in `JOB` (section 1d). The CAD geometry is in `CAD_SH01`, flattened from
the supplied DWG: the channel, lens and clip outlines, plus the swivel-bracket views. It's used for
the 2D drawings and is extruded for the 3D parts. Captions are the `say` lines in each guide entry
(section 21).

Values marked **[CAD]** come from the CAD files:
- channel 0.673″ × 0.332″ with lens;
- channel floor 0.48″ (12.2 mm);
- tape cut interval 1.97″ (50 mm), with pads at both ends of each segment;
- swivel-bracket holes Ø0.165″ at 1.01″ centers.

Values marked **[confirm]** are placeholders to check against the spec sheets before the guide goes
out: tape W/ft, max run, reel length, tape width, channel stick length, clip spacing and supply sizes.

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
