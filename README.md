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

  - path: iris.csv
    title: Iris
    name: iris
    format: csv
    schema:
      fields:
      - name: sepal_length
        type: number
      - name: sepal_width
        type: number
      - name: petal_length
        type: number
      - name: petal_width
        type: number

                                                                                                                                                                                                                                                                                                
---

Simulation result (H2+ - Ar):

$$\frac{\partial f}{\partial t} + \mathbf{v} \cdot \nabla f + \mathbf{g} \cdot \nabla_{\mathbf{v}} f = Q(f, f)$$

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

Here are some notes about the problem:


# Draft

**Luis Vinicius Costa Silva**

A study on cross-section scattering

## Idea

The aim is to understand the phenomenon of scattering in a generic molecule through some procedure, preferably numerical. For this example, I chose the scattering of a Hydrogen particle (lighter) by a potential of a Krypton particle (heavier), for which experimental results were published by Toennies[1]. My goal was to replicate the results developed in the article numerically. For this, the system equation was formulated from the Schrödinger equation, and it was solved numerically (with a Lennard-Jones potential to model the interaction between particles) to obtain total and partial cross-sections (as well as wave function, asymptotic wave function, effective potential).

Thus, the Schrödinger equation of the system was solved:

$$
H \Psi = E \Psi
$$

$$
\left [ - \frac{\hbar^2}{2m} \Delta + V(r) \right ] \Psi (\vec{r}) = E \Psi (\vec{r})
$$


<PdfViewer
  data={{
    url: 'blob:https://github.com/9a929540-38ae-4b08-b370-6a78e800c9b8'
  }}
  parentClassName="h-96"
/>



<PdfViewer
  data={{
    url: 'https://github.com/LuisVCSilva/doutorado/blob/main/Se%C3%A7%C3%A3o%20de%20choque/rascunho/report.pdf'
  }}
  parentClassName="h-96"
/>

I tried to include a PDF file but couldn't, not sure why, tried the pdf url and the blob one.

Cannot plot multiple series in the same plot :|


