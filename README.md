# Project Kingfisher: ring-wing VTOL airframe CFD

I ran CFD in SimScale on two coaxial ring-wing airframes, MK2 and MK3, designed by the project lead at NIRO Lab (NSU Intelligent Robotics Lab), to see which one has less drag in forward flight. MK3 came out 19% lower, but most of that comes from it being smaller. Per unit of frontal area it is slightly worse than MK2.

## Setup

| | MK2 | MK3 |
|---|---|---|
| Solver | SimScale incompressible | SimScale incompressible |
| Inflow | 15 m/s along -y | 15 m/s along -y |
| Angle of attack | 0° | 0° |
| Flow box (cube side) | 0.885 m | 0.796 m |
| Airframe width x height (facing the flow) | 195 x 175 mm | 173 x 149 mm |
| Airframe length (along the flow) | 135 mm | 135 mm |

The airframe CAD (designed by the project lead) is in `geometry/` as STEP files. Dimensions above were measured from those files.

## Results

| | MK2 | MK3 |
|---|---|---|
| Drag (total force y) | 0.68 N | 0.55 N |
| Pressure / viscous drag | 0.58 / 0.10 N | 0.50 / 0.06 N |
| Side forces (x, z) | under 0.03 N | under 0.02 N |
| Frontal envelope area | 0.0342 m² | 0.0257 m² |
| Drag coefficient (envelope area) | 0.145 | 0.156 |

Drag coefficient uses air density 1.225 kg/m³ and the frontal envelope area (width x height).

Forces are averaged over iterations 500 to 1000, where both runs have settled (drag varies by less than 0.01 N there). Raw force data and plots are in `results/`.

MK3 has 19% less drag, but it also presents 25% less frontal area. Normalised by size, MK2 is the cleaner shape. Lift and side forces are near zero for both, which is expected for a symmetric ring wing pointed straight into the flow.

## Limitations

- The two flow boxes are different sizes, and both are small: about 2 to 3 body widths of space upstream. Wall effects probably push both drag values up. The comparison between the two designs is more reliable than the absolute numbers.
- Only one speed and one angle (0°). No lift-to-drag comparison is possible without runs at an angle of attack.

## Next steps

- Re-run both airframes in the same, larger flow box.
- Add runs at 5° and 10° angle of attack to get lift.

## Links

- MK2 SimScale project: [add link]
- MK3 SimScale project: [add link]
