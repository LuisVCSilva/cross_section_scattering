---
datapackage:
  title: Dataset Template
  description: A template for a dataset to publish on DataHub. Uses the Data Package metadata.
  licenses:
  - path: http://opendatacommons.org/licenses/pddl/
    title: Open Data Commons Public Domain Dedication and License v1.0
  resources:
  - path: h2ar/resultado.csv
    title: Cross section scattering
    name: cross-section
    format: csv
    schema:
      fields:
---

Simulation result:

<LineChart
  data="./h2ar/resultado.csv"
  title="H2+ - Ar Cross-Section scattering"
  xAxis="eV"
  yAxis="Cross Section"
/>

