# Notes on the supplied KiCad design

The three editable KiCad files are copied without changing the circuit or layout. These notes distinguish the supplied design from a validated manufacturing release.

## Geometry and component fit

- Edge.Cuts runs from x = 120 to 190 mm and y = 70 to 120 mm: the nominal outline is 70 × 50 mm. Including the drawn 0.05 mm outline stroke yields a 70.05 × 50.05 mm graphics bounding box; that is not the nominal board size.
- Board thickness is 1.6 mm and two copper layers are defined.
- The PCB contains 30 footprints, 211 track segments and one via.
- Three controls use Bourns 3296W vertical trimmer footprints. Confirm these against the intended physical controls.
- The component inventory preserves the source fields. Some references encode resistance (for example `10k4`) while their value fields are generic (`R2`). Do not use the inventory as a purchasing BOM without resolving those fields and confirming diode types, capacitor ratings and polarities.

## Connections to review

The schematic netlist exported by KiCad shows:

1. **U3 pin 6 (LM386 V+) is unconnected.** The amplifier supply connection needs review.
2. **The eight LEDs are connected directly between U1 outputs and GND.** No separate series resistor appears in those LED paths in the supplied netlist; review the intended current limiting.
3. **The apparent audio mix is incomplete.** `1k1` and `1k3` share a net at pin 2, whereas `1k2` pin 2 connects to C6. Confirm whether all three branches are intended to reach the audio input.
4. **One 74HC14 section has unconnected pins 5 and 6.** Review the handling of the unused input.

These are observations from the provided source, not modifications to it. The photographs and videos cannot establish that the KiCad design is electrically identical to the demonstrated breadboards.

## Verification record

- Schematic SVG export: successful with KiCad CLI 10.0.6.
- PCB SVG export: successful with KiCad CLI 10.0.6.
- Netlist export and source inspection: successful.
- Automated PCB DRC: the CLI terminated without producing a report in this environment. **No passing DRC or ERC result is claimed.** Run both checks in KiCad and resolve the relevant findings before fabrication.
- Soldered perfboard assembly and powered-LED photographs are included in `docs/soldered/`. No manufactured-PCB test or soldered-synth audio/video demonstration is included yet.
