<p align="center"><img src="docs/exports/banner.svg" alt="AlienSound — an experiment in electronic sound" width="100%"></p>

<p align="center"><strong>A hands-on audio synth project, from breadboard experiments to a custom PCB.</strong><br>By Clarisse, Raphael &amp; Zoé</p>

<p align="center"><a href="#watch--listen">Watch &amp; listen</a> · <a href="#breadboard-experiments">Breadboard gallery</a> · <a href="#kicad-design">KiCad design</a></p>

---

## The project

**AlienSound** explores electronic sound through physical circuits, adjustable controls and visible LED activity. This repository brings together photographs of the prototypes, recordings of the breadboard experiments, and the editable KiCad schematic and PCB layout.

The documentation follows the build from **breadboard exploration → soldered circuit → extended PCB version**. The breadboard media, hand-drawn schematic, TinkerCAD breadboard diagram and simulation video, soldered-build photographs, and KiCad files are available below. 

## Watch & listen

### Controls in action

<p align="center"><a href="media/video/IMG_2967.mp4"><img src="media/previews/controls-demo.gif" alt="Animated excerpt showing hands adjusting the breadboard controls" width="320"></a></p>
<p align="center"><strong>Turn the controls. Observe the LEDs. Explore the recordings.</strong><br>The GIF is a silent, five-second excerpt. Open the full video for its recorded audio.</p>

| Breadboard demonstration | Control experiment | Close-up demonstration |
| :---: | :---: | :---: |
| [![Two breadboards, LEDs and a speaker](media/previews/F5FD7321-8B4E-42B4-98F9-2C26B623B50A.jpg)](media/video/F5FD7321-8B4E-42B4-98F9-2C26B623B50A.mp4) | [![Adjusting the potentiometers](media/previews/IMG_2965.jpg)](media/video/IMG_2965.mp4) | [![Hands on the breadboard controls](media/previews/IMG_2967.jpg)](media/video/IMG_2967.mp4) |
| **39.3 s** · [Watch video](media/video/F5FD7321-8B4E-42B4-98F9-2C26B623B50A.mp4) | **13.0 s** · [Watch video](media/video/IMG_2965.mp4) | **16.5 s** · [Watch video](media/video/IMG_2967.mp4) |
| [Listen / download audio](media/audio/F5FD7321-8B4E-42B4-98F9-2C26B623B50A.m4a) | [Listen / download audio](media/audio/IMG_2965.m4a) | [Listen / download audio](media/audio/IMG_2967.m4a) |

The audio files are the original AAC tracks extracted from the supplied videos, without added sound or processing. They are recordings of the surrounding scene, not calibrated electrical measurements or direct line-output recordings. If a media file does not play in the repository viewer, download it to play locally.

## Breadboard experiments

The photographs document two visible arrangements: a compact setup with a light-dependent resistor, LED and speaker, and a longer breadboard with several rotary controls. The exact circuit revision associated with each recording remains to be matched to the hand-drawn and TinkerCAD diagrams below.

### 01 · Compact prototype

<img src="media/photos/IMG_2961.jpg" alt="Compact breadboard with a photoresistor, illuminated LED, external potentiometer and small speaker beside an Arduino Mega ADK" width="760">

A photoresistor, illuminated LED, external potentiometer and small speaker are visible. An Arduino Mega ADK is also present in the setup; no firmware is supplied, so its exact role is not asserted here.

### 02 · Adjustable controls

<img src="media/photos/IMG_2962.jpg" alt="Breadboard with several rotary potentiometers, jumper wires and illuminated LEDs" width="760">

The larger prototype exposes multiple potentiometers for hands-on adjustment. This photograph records the physical arrangement of the controls and wiring.

### 03 · Circuit detail

<img src="media/photos/IMG_2963.jpg" alt="Close view of a breadboard integrated circuit, electrolytic capacitors, jumper wires and a potentiometer" width="760">

A closer view records the integrated circuit and capacitor area. Component values and connections should be read from the design files and circuit diagrams, rather than inferred from the photograph alone.

## Circuit documentation

| Document | Status | Location |
| --- | --- | --- |
| Hand-drawn circuit diagram | Included | [Hand-drawn circuit](docs/hand-drawn/Hand-drawn.jpeg) |
| TinkerCAD breadboard diagram | Included | [Breadboard diagram](docs/tinkercad/breadboard.png) |
| TinkerCAD simulation video | Included | [Watch simulation](docs/tinkercad/Tinkercad_test595.mp4) |
| KiCad schematic | Included | [Editable schematic](hardware/kicad/AlienSound.kicad_sch) · [SVG preview](docs/exports/AlienSound.svg) |


### TinkerCAD simulation

[![TinkerCAD breadboard circuit with LEDs, potentiometers and speaker](docs/tinkercad/breadboard.png)](docs/tinkercad/breadboard.png)

The breadboard diagram documents the simulated wiring and component arrangement.

**[▶ Watch the TinkerCAD test video](docs/tinkercad/Tinkercad_test595.mp4)**

The supplied simulation recording is separate from the recordings of the physical breadboard. Download the MP4 if it does not play in the GitHub viewer. The generated TinkerCAD schematic is still to be added.

### Hand-drawn circuit

[![Hand-drawn schematic of the AlienSound circuit: five 74HC14 relaxation oscillators, a 74HC595 with LEDs, and an LM386 audio stage](docs/hand-drawn/Hand-drawn.jpeg)](docs/hand-drawn/Hand-drawn.jpeg)


The drawing shows three blocks:

- **Clock and data oscillators (top right):** two 74HC14 Schmitt-trigger inverters (pins 1→2 and 3→4),
  each set up as a relaxation oscillator with a 10 kΩ potentiometer in the feedback path and a 10 µF
  capacitor to ground. One output goes to the SER input of the 74HC595, the other to its clock
  inputs (SRCLK and RCLK, tied together). OE is grounded and SRCLR is held at 5 V.
- **LED register (centre):** the 74HC595 drives LEDs to ground from its outputs. Three outputs
  are also connected through diodes to the inputs of the audio oscillators below.
- **Audio oscillators and amplifier (bottom):** three more 74HC14 inverters (pins 11→10, 13→12, 9→8),
  each again an RC oscillator with a 10 kΩ potentiometer and a 10 µF capacitor. Their outputs are mixed
  through three 1 kΩ resistors, passed through a 10 µF coupling capacitor to the LM386 (5 V supply),
  and sent to the speaker through a 220 µF capacitor.

## Soldered synth

### Assembled circuit

<img src="docs/soldered/IMG_3243.jpeg" alt="Soldered synth on perfboard with three potentiometers, integrated circuits and LEDs, alongside a speaker and Arduino board" width="760">

The component-side photograph shows the synth assembled on perfboard, with three rotary controls and a row of LEDs.

### Powered setup

<img src="docs/soldered/IMG_3244.jpeg" alt="Powered perfboard synth with several illuminated LEDs and a hand adjusting a control" width="760">

Several LEDs are illuminated while a control is being adjusted. This documents the powered setup; an audio/video demonstration of the soldered synth and a photograph of the solder side remain to be added.

## KiCad design

### Editable source files

- [AlienSound.kicad_pro](hardware/kicad/AlienSound.kicad_pro) — KiCad project.
- [AlienSound.kicad_sch](hardware/kicad/AlienSound.kicad_sch) — schematic, including embedded symbols.
- [AlienSound.kicad_pcb](hardware/kicad/AlienSound.kicad_pcb) — placed components, copper routing and board outline.
- [Component inventory](hardware/bom.csv) — references, values and footprints exported from the supplied schematic.

The files were created with **KiCad 10.0** and the previews were exported using **KiCad CLI 10.0.6**. Open the `.kicad_pro` file in KiCad 10 or a compatible later version, then launch the schematic or PCB editor.

### Schematic

[![AlienSound schematic exported directly from KiCad](docs/exports/AlienSound.svg)](docs/exports/AlienSound.svg)

The source design contains three main ICs:

| Reference | Component | Position in the design |
| --- | --- | --- |
| U2 | 74HC14 | Several inverter sections connected to resistor/capacitor networks and the adjustable branches |
| U1 | 74HC595 | Eight outputs connected to LEDs; three also connect through diodes to adjustable branches |
| U3 | LM386 | Audio-stage IC, with output connected through C7 to the speaker connector LS1 |

This is a structural reading of the supplied schematic, not a statement that every connection has been electrically validated. The [design notes](docs/design-notes.md) record specific points to review before fabrication.

### 3D board previews

These KiCad 3D views show the component placement and overall appearance of the designed PCB.

**Top view**

![KiCad 3D top view showing the eight LEDs, integrated circuits, capacitors and three trimmers](docs/exports/pcb-3d-top.png)

**Perspective view**

![KiCad 3D perspective view showing the PCB and through-hole component arrangement](docs/exports/pcb-3d-perspective.png)

### Physical layout

[![Routed PCB layout with copper, component markings and board outline](docs/exports/pcb-layout.svg)](docs/exports/pcb-layout.svg)

| Property | Supplied PCB |
| --- | --- |
| Board outline | **70 × 50 mm**, measured between the Edge.Cuts centre lines |
| Nominal thickness | **1.6 mm** |
| Copper layers | **2** — F.Cu and B.Cu |
| Footprints | **30** |
| IC packages | DIP-16, DIP-14 and DIP-8, each with 7.62 mm row spacing |
| Controls | Three Bourns 3296W vertical trimmer footprints |
| Speaker connection | Two-pin header, 2.54 mm pitch |

The layout uses real component footprints. The trimmer footprints in the PCB are different from the large rotary potentiometers visible in the breadboard photos; the final component choice and mechanical fit therefore need confirmation.

### Version 2 development

The supplied KiCad project includes an eight-LED output section and three diode-connected adjustable branches. Its schematic and physical layout are available above.

**The version 2 comparison is to be completed.** This section is reserved for the baseline soldered circuit, the version 2 feature description, the corresponding circuit changes and demonstration.

## Repository map

```text
AlienSound/
├── README.md
├── hardware/
│   ├── kicad/          Editable project, schematic and PCB
│   └── bom.csv         Component inventory from the schematic
├── media/
│   ├── photos/         Three breadboard photographs
│   ├── video/          Full demonstrations with their audio
│   ├── audio/          Audio-only versions of the recordings
│   └── previews/       Video stills and animated excerpt
└── docs/
    ├── exports/        KiCad schematic, PCB preview and title graphic
    ├── hand-drawn/     Hand-drawn circuit documentation
    ├── soldered/       Assembly photographs and operating proof
    ├── tinkercad/      Breadboard diagram and simulation video
    └── design-notes.md
```

---

*AlienSound — Making our own musical instrument. Project credits follow the supplied KiCad title block: Clarisse / Raphael / Zoé.*
