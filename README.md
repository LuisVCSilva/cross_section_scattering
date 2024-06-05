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
      - name: 0
        type: number
      - name: 1
        type: number
      - name: 2
        type: number
      - name: 3
        type: number
      - name: 4
        type: number
      - name: 5
        type: number
      - name: 6
        type: number
      - name: 7
        type: number
      - name: 8
        type: number
      - name: 9
        type: number
      - name: 10
        type: number
      - name: 11
        type: number
      - name: 12
        type: number
      - name: 13
        type: number
      - name: 14
        type: number
      - name: 15
        type: number
      - name: 16
        type: number
      - name: 17
        type: number
      - name: 18
        type: number
      - name: 19
        type: number
      - name: 20
        type: number
      - name: 21
        type: number
      - name: 22
        type: number                                                                                                                                                        
      - name: 23
        type: number                                                                                                                                                        
                                                                                                                                                     
---

Simulation result:

<LineChart
  data="./h2ar/resultado.csv"
  title="H2+ - Ar Cross-Section scattering"
  xAxis="eV"
  yAxis="Cross Section"
/>

