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

\begin{document}
\noindent
\large\textbf{Rascunho} \hfill \textbf{Luis Vinicius Costa Silva} \\
\normalsize Um estudo sobre dispersão 

\subsection*{Ideia}
Busca-se compreender o fenômeno de dispersão em uma molécula qualquer através de algum procedimento, de preferência numérico. Para este exemplo escolhi a dispersão de uma partícula de Hidrogênio (mais leve) por um potencial de uma partícula de Crípton (mais pesado) no qual resultados experimentais foram publicados por \cite{toennies}. Meu objetivo foi replicar os resultados desenvolvidos no artigo de forma numérica. Para tanto, foi formulada a equação do sistema à partir da equação de Schrodinger, e esta foi resolvida numéricamente (com um potencial de Lennard-Jones para modelar a interação entre partículas) para obter as seções de choque totais e parciais (assim como função de onda, função de onda assintótica, potencial efetivo). \newline
Assim, resolveu-se a equação de Schrodinger do sistema:

\begin{equation}
H \Psi = E \Psi
\end{equation}

\begin{equation}
\left [ - \frac{\hbar^2}{2m} \Delta + V(r) \right ] \Psi (\vec{r}) = E \Psi (\vec{r})
\end{equation}

onde $V(r)$ é um potencial esférico. É sabido que neste caso todas as autofunções do sistema são também autofunções dos operadores de momento angular, ou seja estas podem ser reescritas como combinações linears de harmônicas esféricas na forma:

\begin{equation}
\Psi(\vec{r}) = \sum_{l=0}^{\infty} \sum_{m=-l}^{l} A_{lm} \frac{u_l(r)}{r} Y^{m}_{l} (\theta, \phi)
\end{equation}

Aplicando separação de variáveis, isso reduz o problema para o caso radial da equação, onde o problema fica em função da coordenada $r$ que varia de $0$ a $\infty$, m é a massa reduzida do sistema inteiro.

\begin{equation}
\left [ - \frac{\hbar^2}{2m} \frac{d^2}{dr^2} + \left ( V(r) + \frac{\hbar^2 l (l+1)}{2mr^2} - E \right ) \right ] = u_l(r) = 0	
\end{equation}

Os deslocamentos de fase $\delta_l$ (dependentes de potencial e energia) são calculado à partir do comportamento assintótico  da função de onda da seguinte forma:

\begin{equation}
\tan \delta_1 = \frac{Kj_l(kr_1)-j_l(kr_2)}{K n_l(kr_1) - n_l(kr_2)}
\end{equation}

onde $k = \sqrt{2m E \hbar^{(-2)}}$, $K = r_1 u_2 (r_2 u_1)^{-1}$ e $u_{1,2} = 
u_l(r_{r1,2})$, e onde $j_l$ e $n_l$ são funções de Bessel e $r_1 \approx r_2 \approx r_{\text{max}}$. Assim, a seção de choque total é dada por:

\begin{equation}
\sigma_{\text{total}} = \frac{4 \pi}{k^2} \sum_{l=0}^{\infty} (2l+1) \sin^2 \delta_l
\end{equation}

Utilizando o potencial de Lennard-Jones para modelar a interação entre os dois átomos têm-se:

\begin{equation}
V_{LJ}(r) = \epsilon  \left [ \left (  \frac{\sigma}{r}  \right ) ^{12} - 2 \left ( \frac{\sigma}{r}  \right )^6  \right ]
\end{equation}

onde $\epsilon = 5.9$ meV e $\sigma = 3.57$ .


\subsection*{Resultados}
O gráfico abaixo é a solução numérica do sistema apresentando as séries das variáveis de interesse do sistema, logo após ele o gráfico original no artigo experimental:

\begin{figure}[H]
\centering
\includegraphics[width=\textwidth]{geral.png}
\end{figure}

\begin{figure}[H]
\centering
\includegraphics[width=\textwidth]{original.png}
\end{figure}

No experimento foi relacionado a energia do centro de massa em eletronvolt (eV) a seção de choque total $\sigma$ em barn. O solver foi escrito em Python e foi utilizada o algoritmo de Numerov para resolução da equação do sistema, a biblioteca Scipy para a utilização das funções de Bessel, Numpy para operações em matrizes e séries e Matplotlib para plots. O arquivo ``solver.py" simula a seção de choque resultante da interação de H-Kr, sob os parâmetros especificados em ``params.json", um arquivo csv contendo as séries de interesse pode ser gerado e plotado com o script ``plot.py". Todo o procedimento pode ser executado com o arquivo ``run.sh". Foi considerado que \newline


Como dito anteriormente, o resultado numérico parece estar em concordância com os resultados experimentais realizados por \cite{toennies}.
\section*{O que pode ser explorado}
Próximas pesquisas podem explorar as seguintes áreas:

\begin{itemize}
\item explorando outros modelos que descrevem a interação intermolecular de maneira mais precisa (ao invés do Lennard Jones), por exemplo com modelos não-paramétricos gerados com aprendizado de máquina;
\item uso de outros métodos de integração além do Numerov (formulação integral do problema por exemplo);
\item malhas adaptativas;
\item paralelização do código.
\item simulação de moléculas complexas com aplicações interessantes (caracterização de materiais)
\end{itemize}

\begin{thebibliography}{9}
\bibitem{toennies}
Toennies, J. P., Welz, W., \& Wolf, G. (1979). Molecular beam scattering studies of orbiting resonances and the determination of van der Waals potentials for H–Ne, Ar, Kr, and Xe and for H2–Ar, Kr, and Xe. The Journal of Chemical Physics, 71(2), 614-642.
\end{thebibliography}
\end{document}


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


