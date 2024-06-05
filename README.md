---
datapackage:
  title: Cross section scattering of H2 - Ar and H2 - Xe
  description: Numerical simulation of cross-section based on "Molecular beam scattering studies of orbiting resonances and the determination of van der Waals potentials for H–Ne, Ar, Kr, and Xe and for H2–Ar, Kr, and Xe"
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
      - name: x
        type: number
      - name: y
        type: number
      - name: z
        type: number

  - path: h2xe/resultado.csv
    title: Cross section scattering
    name: cross-section
    format: csv
    schema:
      fields:
      - name: x
        type: number
      - name: y
        type: number
      - name: z
        type: number

                                                                                                                                                                                                                                                                                                
---

Simulation result (H2+ - Ar):

<PlotlyLineChart
  data={{
    url: 'https://raw.githubusercontent.com/LuisVCSilva/cross_section_scattering/main/h2ar/resultado.csv'
  }}
  title="Cross section"
  xAxis="x"
  yAxis="y"
/>


H2 + Xe:
<PlotlyLineChart
  data={{
    url: 'https://raw.githubusercontent.com/LuisVCSilva/cross_section_scattering/main/h2xe/resultado.csv'
  }}
  title="Cross section"
  xAxis="x"
  yAxis="y"
/>


Cannot plot multiple series in the same plot :|


