# Notes on the supplied KiCad design

## Geometry and component fit

- Edge.Cuts runs from x = 120 to 190 mm and y = 70 to 120 mm: the nominal outline is 70 × 50 mm. Including the drawn 0.05 mm outline stroke yields a 70.05 × 50.05 mm graphics bounding box; that is not the nominal board size.
- Board thickness is 1.6 mm and two copper layers are defined.
- The PCB contains 30 footprints, 211 track segments and one via.
- Three controls use Bourns 3296W vertical trimmer footprints. Confirm these against the intended physical controls.
- The component inventory preserves the source fields. Some references encode resistance (for example `10k4`) while their value fields are generic (`R2`). Do not use the inventory as a purchasing BOM without resolving those fields and confirming diode types, capacitor ratings and polarities.


