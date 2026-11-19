# Prompts and changes

- **Asked:** Set up the single-file web app project layout with the required root files and numbered folders.
  **Changed:** Documented the layout and file-placement rule in `AGENTS.md`; added this log, a specification placeholder, a minimal root `index.html`, and a README in each numbered folder.
  **Worked:** Yes; the requested files and folders are present.
- **Asked:** Review the initial beam designer plan and suggest improvements without writing code.
  **Changed:** Reviewed `spec.md`; no specification or app code was changed.
  **Worked:** Yes; recommendations are provided in the review response.
- **Asked:** Identify the remaining questions and list answer options.
  **Changed:** Collected choices for a curated property library, preliminary screening, bending and shear checks, multiple point/partial uniform loads with self-weight, configurable deflection limits, and US customary units. No app or specification code was changed.
  **Worked:** Yes; the implementation direction is clearer, with exact catalog contents and material assumptions still to be selected.
- **Asked:** Put the agreed recommendations and choices into `spec.md`.
  **Changed:** Rewrote `spec.md` to specify the curated property library, simplified preliminary bending/shear/deflection checks, loads and self-weight, units, outputs, validation, and exclusions. No app code was written.
  **Worked:** Yes; the specification now reflects the selected direction.
- **Asked:** If beam data cannot be found, include 20–30 sample beam specifications.
  **Changed:** Added a 24-entry starter catalog to `spec.md`: 12 W-shapes and 12 species/grade/size lumber combinations, with authoritative property sources and a rule against invented numeric properties.
  **Worked:** Yes; the official AISC Shapes Database v16.0 and AWC 2024 NDS sources are identified.
- **Asked:** Put the beam specification list under the data folder.
  **Changed:** Added `01_data/beam-catalog.csv` with the 24 candidate entries and pending-verification status; updated `spec.md` and the data-folder README to reference it.
  **Worked:** Yes; the catalog list is in the requested folder and contains no unverified numeric properties.
- **Asked:** Let me see the app.
  **Changed:** Replaced the empty `index.html` with a responsive visual prototype for the beam model, loads, diagrams, and checks. It clearly blocks analysis while catalog properties remain unverified.
  **Worked:** Yes; browser preview loaded and support, span, and load inputs update the schematic. Analysis remains intentionally disabled.
- **Asked:** Fix the load arrows so they point down.
  **Changed:** Reoriented the SVG arrowhead marker so the load arrows follow the downward line direction.
  **Worked:** Verified in the browser preview.
- **Asked:** Calculate and report design results.
  **Changed:** Implemented the W12x26 preliminary analysis with reactions, shear and moment, deflection, and bending/shear/deflection checks. Added support and load inputs, self-weight, and explicit limitations.
  **Worked:** Yes; browser results match the hand calculation for the default case: 10.26 kip reactions, 51.30 kip-ft maximum moment, 0.624 in deflection, 18.43 ksi bending, and 3.90 ksi average web shear. A stricter L/480 limit correctly fails.
- **Asked:** Show a beam cross-section with its width, height, components, and loads.
  **Changed:** Added a dimensioned W12x26 section drawing with labeled flanges and web; the load arrows are shown on the beam elevation, with the corresponding section dimensions and properties beside the drawing.
  **Worked:** Yes; browser checks confirm the cross-section, flange/web labels, width, and depth are visible.
- **Asked:** Automatically commit changes from now on.
  **Changed:** Added the validated-change auto-commit rule to `AGENTS.md`.
  **Worked:** This initial project commit completes the request for the current uncommitted project; future validated requested changes should be committed as documented.
- **Asked:** Provide an update.
  **Changed:** Reported the implementation and validation status while completing the calculator and cross-section work.
  **Worked:** Yes; continued through final validation.
- **Asked:** Finish up and publish the app as a public GitHub repository and GitHub Pages site at `Dax/beam`.
  **Changed:** Committed the validated app locally and checked the requested repository. No GitHub remote or CLI authentication is configured, and the browser requires GitHub sign-in; no remote repository or publication settings were changed.
  **Worked:** Local work is complete; publication is pending GitHub authentication.
