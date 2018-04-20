---
layout: default
title: "E-Appendix: Fuzz-face parameter redundancy analysis"
---

# E-Appendix: Fuzz-face parameter redundancy analysis

![Fuzz-face schematic](../images/fuzz-face.png)

## Ebers-Moll BJT model

The PNP BJT can be modelled using the Ebers-Moll model:
<div>
\begin{align}
	I_{\mathrm{b1}} & = \frac{I_{\mathrm{s1}}}{\beta_{\mathrm{f1}}}\left(\mathrm{e}^{\frac{V_1 - V_3}{N_1V_{\mathrm{t}}}} - 1\right) + \frac{I_{\mathrm{s1}}}{\beta_{\mathrm{r1}}}\left(\mathrm{e}^{\frac{- V_3 - V_4}{N_1V_{\mathrm{t}}}} - 1\right)
	\\[0.5em]
	I_{\mathrm{c1}} &= I_{\mathrm{s1}}\left(\mathrm{e}^{\frac{V_1 - V_3}{N_1V_{\mathrm{t}}}} - 1\right) - I_{\mathrm{s1}}\frac{\beta_{\mathrm{r1}} + 1}{\beta_{\mathrm{r1}}}\left(\mathrm{e}^{\frac{- V_3 - V_4}{N_1V_{\mathrm{t}}}} - 1\right)
  \\[0.5em]
  I_{\mathrm{b2}} & = \frac{I_{\mathrm{s2}}}{\beta_{\mathrm{f2}}}\left(\mathrm{e}^{\frac{V_6 - V_4}{N_2V_{\mathrm{t}}}} - 1\right) + \frac{I_{\mathrm{s2}}}{\beta_{\mathrm{r2}}}\left(\mathrm{e}^{\frac{- V_4 -V_7}{N_2V_{\mathrm{t}}}} - 1\right)
	\\[0.5em]
	I_{\mathrm{c2}} &= I_{\mathrm{s2}}\left(\mathrm{e}^{\frac{V_6 - V_4}{N_2V_{\mathrm{t}}}} - 1\right) - I_{\mathrm{s2}}\frac{\beta_{\mathrm{r2}} + 1}{\beta_{\mathrm{r2}}}\left(\mathrm{e}^{\frac{- V_4 - 12V_7}{N_2V_{\mathrm{t}}}} - 1\right)
\end{align}
</div>

## Nodal equations
Let the convention for this derivation be that current exiting a node is positive. Current enters the PNP BJT from the emitter and exits at the base and collector. The volume potentiometer is fixed at having the maximal resistance. The nodal equations are then given by:
<div>
\begin{align}
  \color{gray}{\frac{V_1 - V_5}{fR_\mathrm{fuzz}} - I_\mathrm{cc}} &= \color{gray}{-(I_\mathrm{b1} + I_\mathrm{c1})}\tag{1}\\
  \color{gray}{C_3 \frac{d}{dt}(V_2 - V_3) - I_\mathrm{vi}} &= \color{gray}{0}\tag{2}\\
  \frac{1}{R_3}(V_3 - V_6) - C_3 \frac{d}{dt}(V_2 - V_3) &= I_\mathrm{b1}\tag{3}\\
  \frac{V_4}{R_4} &= I_\mathrm{c1} - I_\mathrm{b2}\tag{4}\\
  C_1 \frac{dV_5}{dt} + \frac{V_5 - V_6}{(1-f)R_\mathrm{fuzz}} - \frac{V_1 - V_5}{fR_\mathrm{fuzz}} &= 0\tag{5}\\
  -\frac{V_5 - V_6}{(1-f)R_\mathrm{fuzz}}-\frac{1}{R_3}(V_3 - V_6) &=-(I_\mathrm{b2} + I_\mathrm{c2})\tag{6}\\
  \frac{1}{R_1}(V_7 - V_8) &= I_\mathrm{c2}\tag{7}\\
  C_2\frac{d}{dt}(V_8 - V_9) + \frac{V_8}{R_2} - \frac{1}{R_1}(V_7 - V_8) &= 0\tag{8}\\
  \frac{V_9}{R_\mathrm{vol}} - C_2\frac{d}{dt}(V_8 - V_9) &= 0\tag{9}
\end{align}
</div>

And the voltage source connections:
<div>
\begin{align}
  V_1 &= V_\mathrm{cc}\\
  V_2 &= V_\mathrm{in}
\end{align}
</div>

## Condensed form

<div>
\begin{equation}
  \begin{split}
  &
  \begin{bmatrix}
  G_\mathrm{Rf} & 0 & 0 & 0 & -G_\mathrm{Rf} & 0 & 0 & 0 & 0\\
  0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0\\
  0 & 0 & G_\mathrm{R3} & 0 & 0 & -G_\mathrm{R3} & 0 & 0 & 0\\
  0 & 0 & 0 & G_\mathrm{R4} & 0 & 0 & 0 & 0 & 0\\
  -G_\mathrm{Rf} & 0 & 0 & 0 & G_\mathrm{Rf} - G_\mathrm{R\bar{f}} & G_\mathrm{R\bar{f}} & 0 & 0 & 0\\
  0 & 0 & -G_\mathrm{R3} & 0 & G_\mathrm{R\bar{f}} & G_\mathrm{R3} - G_\mathrm{R\bar{f}} & 0 & 0 & 0\\
  0 & 0 & 0 & 0 & 0 & 0 & G_\mathrm{R1} & -G_\mathrm{R1} & 0\\
  0 & 0 & 0 & 0 & 0 & 0 & -G_\mathrm{R1} & G_\mathrm{R1} + G_\mathrm{R2} & 0\\
  0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & G_\mathrm{Rv}
  \end{bmatrix}
  \begin{bmatrix}
    V_1 \\ V_2 \\ V_3 \\ V_4 \\ V_5 \\ V_6 \\ V_7 \\ V_8 \\ V_9
  \end{bmatrix}
  \\
  &+
  \begin{bmatrix}
    0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0\\
    0 & C_3 & -C_3 & 0 & 0 & 0 & 0 & 0 & 0\\
    0 & -C_3 & C_3 & 0 & 0 & 0 & 0 & 0 & 0\\
    0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0\\
    0 & 0 & 0 & 0 & C_1 & 0 & 0 & 0 & 0\\
    0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0\\
    0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0\\
    0 & 0 & 0 & 0 & 0 & 0 & 0 & C_2 & -C_2\\
    0 & 0 & 0 & 0 & 0 & 0 & 0 & -C_2 & C_2\\
  \end{bmatrix}
  \begin{bmatrix}
    V_1' \\ V_2' \\ V_3' \\ V_4' \\ V_5' \\ V_6' \\ V_7' \\ V_8' \\ V_9'
  \end{bmatrix}
  =
  \begin{bmatrix}
    1 & 1 & 0 & 0\\
    0 & 0 & 0 & 0\\
    0 & -1& 0 & 0\\
    -1 & 0& 0 &-1\\
    0 & 0 & 0 & 0\\
    0 & 0 & 1 & 1\\
    0 & 0 & -1& 0\\
    0 & 0 & 0 & 0\\
    0 & 0 & 0 & 0
  \end{bmatrix}
  \begin{bmatrix}
    I_\mathrm{c1} \\ I_\mathrm{b1} \\ I_\mathrm{c2} \\ I_\mathrm{b2}
  \end{bmatrix}
  \end{split}
\end{equation}
</div>

## Parameter redundancy

<div>
\begin{equation}
\begin{split}
  \mathbf{\kappa}_\mathrm{ff} = [G_\mathrm{Rf},&\;\; G_\mathrm{R3},\;\; G_\mathrm{R4},\;\; G_\mathrm{Rf} - G_\mathrm{R\bar{f}},\;\; G_\mathrm{R\bar{f}},\;\; G_\mathrm{R3} - G_\mathrm{R\bar{f}},\;\; G_\mathrm{R1},\;\; C_3,\;\; C_1,\;\; C_2,\\
  &\;\; \frac{I_{\mathrm{s1}}}{\beta_{\mathrm{f1}}},\;\; \frac{I_{\mathrm{s1}}}{\beta_{\mathrm{r1}}},\;\; I_{\mathrm{s1}},\;\; I_{\mathrm{s1}}\frac{\beta_{\mathrm{r1}} + 1}{\beta_{\mathrm{r1}}},\;\;\frac{I_{\mathrm{s2}}}{\beta_{\mathrm{f2}}},\;\;\frac{I_{\mathrm{s2}}}{\beta_{\mathrm{r2}}},\;\; I_{\mathrm{s2}},\;\; I_{\mathrm{s2}}\frac{\beta_{\mathrm{r2}} + 2}{\beta_{\mathrm{r2}}} ]
\end{split}
\end{equation}
</div>
