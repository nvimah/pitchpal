# PitchPal

A pocket-sized, soccer-themed Tamagotchi-style virtual pet. Feed it, train it, let it rest, and watch it grow into a better player depending on how well you look after it. Built on an ESP32-C3 with an OLED screen, three buttons, and a custom 3D-printed shell.

> Status: design phase (Hack Club Half Life). Update this line as the project moves along.

<!-- Add a photo, render, or sketch here once you have one -->
<!-- ![PitchPal sketch](docs/sketch.png) -->

## What it does

- Tracks four stats: **hunger, energy, happiness, fitness**
- Stats drop over time and are saved to flash, so the pet keeps "living" when switched off
- Three-button controls: left, select, right
- Buzzer for beeps, melodies, and game sounds
- Pet mood and sprite change with its stats
- Evolves based on how well it is cared for
- Mini-games: penalty kicks and juggling

### Stretch goals

- Wi-Fi time sync and weather reactions
- Status page hosted on my homelab
- Two pets interacting over ESP-NOW
- Custom PCB shaped to the shell

## Hardware

| Part | Purpose |
|---|---|
| ESP32-C3 SuperMini | Main controller, Wi-Fi |
| 1.3" I2C OLED (128x64) | Display |
| 6x6 mm tactile buttons (x3 used) | Controls |
| Passive piezo buzzer | Sound |
| LiPo battery (~250-400 mAh) | Power |
| TP4056 USB-C charging module | Battery charging |
| Slide switch | Power on/off |
| Perfboard, wire, headers, resistors | Wiring |

Full parts list with prices and links: see [`bom.md`](bom.md) *(or the BOM section of the project page)*.

## Wiring

Pin assignments (fill in as you finalize them):

| Component | ESP32-C3 pin |
|---|---|
| OLED SDA | GPIO ? |
| OLED SCL | GPIO ? |
| Button left | GPIO ? |
| Button select | GPIO ? |
| Button right | GPIO ? |
| Buzzer | GPIO ? |
| Battery voltage sense | GPIO ? |

A wiring diagram goes in [`docs/`](docs/).

## Software

- Language: MicroPython *(or Arduino C++, pick one and edit this line)*
- Core loop: a state machine that updates stats on a timer, reads button input, and redraws the screen
- Saving: stats written to flash at intervals and on sleep
- Power: deep sleep and screen dimming when idle

## The shell

Designed in *(Onshape / Fusion 360 / FreeCAD)* and printed in PLA/PETG.

- Two-part snap-fit or screw-together case
- Cutouts for the screen, three buttons, and USB-C port
- Space for the battery and charging board
- Printed button caps with ~0.2-0.3 mm clearance
- Tolerances tested with small print fits before the final print

CAD files go in [`cad/`](cad/).

## Repository layout

```
pitchpal/
├── README.md
├── bom.md
├── cad/          # shell models (STEP, STL)
├── firmware/     # code
├── hardware/     # schematic / PCB files, if any
└── docs/         # sketches, pinout, wiring diagram, photos
```

## Plan

**Design phase**
1. Define the pet concept, stats, and rules; sketch the screens
2. Breadboard the screen, buttons, and buzzer
3. Write the core stats and game loop
4. Draw sprites and sounds; start the shell
5. Finalize the parts list, wiring, and shell design

**Build phase**
6. Order and test parts individually
7. Assemble the electronics
8. Add battery management, saving, and sleep
9. Print and fit the shell
10. Polish, add mini-games, document, and record a demo

## Challenges I expect

- Battery life: handled with deep sleep and screen dimming
- Sprite memory: small, compact art formats
- Button debouncing in code
- Shell tolerances: test prints before the final one

## Build log

Progress is tracked in the project journal. Entries will be mirrored here.

## License

MIT *(or choose another)*
