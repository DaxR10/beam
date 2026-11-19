# Beam Designer

## Purpose

A single-file web app for preliminary analysis of a simply supported beam or
cantilever. It visualizes reactions, shear, moment, and deflection, and screens
the selected beam for bending, shear, and deflection.

Results are preliminary checks, not code-compliance approval or a complete
structural design. The app must identify the checks it performs and the
important checks it omits.

## Platform and units

- Keep the app in the root `index.html` so GitHub Pages can serve it.
- Support US customary units in the initial version: ft, in, lb, kip, ksi, and
  kip/ft, with labels shown on inputs and results.
- Convert units consistently for calculations; show the units used in results.
- Bundle the curated property data with the app so the property library works
  without a backend or network request.

## Beam and material data

- Offer a curated, offline starter library of steel W-shapes and selected
  lumber sizes, species, and grades.
- Record the source and version for each property dataset. Use published
  section properties for steel shapes and published design values for lumber;
  do not invent or silently substitute missing properties.
- Seed the catalog with the 24 candidate specifications listed in
  `01_data/beam-catalog.csv`: 12 steel W-shapes and 12 lumber
  species/grade/size combinations.
- Source steel shape properties and weights from the
  [AISC Shapes Database v16.0](https://www.aisc.org/aisc/publications/steel-construction-manual/shapes-database-v160/).
  Pair the initial steel examples with ASTM A992 steel (`Fy = 50 ksi`,
  `E = 29,000 ksi`), and identify that grade in the UI rather than implying it
  is guaranteed by the shape designation.
- Source lumber design values from the applicable tables in the
  [AWC 2024 National Design Specification](https://awc.org/resources/2024-nds/)
  and its supplement. Use the actual dimensions and size-specific values for
  each species, grade, and nominal size.
- Steel records need the shape designation, flange width `bf`, section modulus
  `Sx`, moment of inertia `Ix`, depth `d`, web thickness `tw`, flange
  thickness `tf`, and nominal self-weight. Material selection supplies `E`
  and yield strength `Fy`.
- Lumber records need the species, grade, actual dressed dimensions, `E`,
  published allowable bending stress `Fb`, published allowable shear stress
  `Fv`, and unit weight. Derive section properties from the actual dimensions.
- For the preliminary screen, use steel bending allowable stress `0.66 Fy` and
  shear allowable stress `0.40 Fy`; use published lumber `Fb` and `Fv` without
  adjustment factors. Show these assumptions in the results.
- If an entry's numeric properties cannot be verified against its cited
  source, do not make up values or allow it to produce a Pass result; omit or
  disable that entry until verified.
- The initial calculated example is W12x26 in ASTM A992 steel. Until further
  catalog rows are verified, other entries remain unavailable for calculation.
- If required data is unavailable for a selection, explain which value is
  missing and do not report a pass.

## Inputs

- Support condition: simply supported or cantilever.
- Span length.
- Beam family and a shape/material entry from the curated library.
- Any number of vertical point loads, each with a magnitude and position.
- Any number of uniform loads, each with a magnitude and start/end positions;
  a full-span uniform load is a load whose range is the full span.
- Include the selected beam's self-weight automatically as a uniform load.
- Allow the user to set the deflection limit, defaulting to `L/360`, and choose
  which applied loads are included in that deflection check.

## Calculations and checks

- Calculate support reactions, shear, and moment from static equilibrium.
- Calculate elastic deflection for an ideal, prismatic beam using the selected
  material's `E` and section properties.
- Calculate bending stress as `fb = M/Sx` for steel W-shapes and from the
  section modulus derived from lumber dimensions. Compare with the selected
  simplified allowable bending stress.
- For a steel W-shape, screen average web shear as `fv = V / (tw * (d - 2tf))`.
  For rectangular lumber, screen maximum shear as `fv = 1.5V / (b*d)`. Compare
  each with its simplified allowable shear stress.
- Compare the selected maximum deflection with the user-selected span-based
  limit. The initial limit is `L/360`.
- Show the numerical demand, allowable or limit, and utilization for each
  check. Mark each check Pass or Fail; report an overall Pass only when all
  three checks pass.
- Clearly state that passing these checks does not establish code compliance
  or address the excluded failure modes, including lateral-torsional, local,
  and shear buckling.

## Outputs and presentation

- Show the beam, supports, loads, and reactions.
- Show a dimensioned cross-section for each available beam, including width,
  overall height/depth, web, and flange dimensions. Show applied loads on the
  longitudinal beam view.
- Show shear, moment, and deflection diagrams with axes, units, and key
  maximum values.
- Show bending, shear, and deflection check results and their assumptions.
- Open with a representative example beam and load case.
- Use a clean, professional layout.

## Validation

- Verify equilibrium and expected reactions, shear, and moment for simply
  supported and cantilever cases.
- Include point-load, full-span uniform-load, and partial-span uniform-load
  cases, including self-weight.
- Example: a 20 ft simply supported W12x26 with a user-applied full-span load
  of 1 kip/ft. With nominal self-weight of 26 lb/ft, total uniform load is
  1.026 kip/ft, maximum moment is 51.3 kip-ft, and maximum shear is 10.26 kip.
  For A992 steel with `E = 29,000 ksi`, `Fy = 50 ksi`, `Sx = 33.4 in^3`,
  `Ix = 204 in^4`, `d = 12.2 in`, `tw = 0.23 in`, and `tf = 0.38 in`,
  bending stress is 18.43 ksi versus 33.00 ksi allowable, and average web
  shear is 3.90 ksi versus 20.00 ksi allowable. Maximum deflection is about
  0.624 in versus the default `L/360` limit of 0.667 in. All three preliminary
  checks pass; this is not a code-compliance result.

## Out of scope

- Continuous beams and other support conditions.
- Lateral-torsional, local, and shear buckling.
- Axial or lateral loading, load combinations, dynamic analysis, and connection
  design.
- Full code-compliant design or certification.
