---
layout: default
title: "E-Appendix: Fuzz-face parameter redundancy analysis"
---

# E-Appendix: Fuzz-face parameter redundancy analysis

![Common-emitter amplifier](../images/fuzz-face.png)

## Nodal equations
Let the convention for this derivation be that current exiting a node is positive. Current enters the PNP BJT from the emitter and exits at the base and collector. The volume potentiometer is fixed at having the maximal resistance. The nodal equations are then given by:
<div>
\begin{align}
  \frac{V_1 - V_5}{fR_\mathrm{fuzz}} - I_\mathrm{cc} &= -(I_\mathrm{b1} + I_\mathrm{c1})\tag{1}\\
  C_5 \frac{dV_\mathrm{in}}{dt} + C_3 \frac{d}{dt}(V_\mathrm{in} - V_3) - I_\mathrm{vi} &= 0\tag{2}\\
  \frac{1}{R_3}(V_3 - V_6) - C_3 \frac{d}{dt}(V_\mathrm{in} - V_3) &= I_\mathrm{b1}\tag{3}\\
  \frac{V_4}{R_4} &= I_\mathrm{c1} - I_\mathrm{b2}\tag{4}\\
  C_1 \frac{dV_5}{dt} + \frac{V_5 - V_6}{(1-f)R_\mathrm{fuzz}} - \frac{V_1 - V_5}{fR_\mathrm{fuzz}} &= 0\tag{5}\\
  -\frac{V_5 - V_6}{(1-f)R_\mathrm{fuzz}}-\frac{1}{R_3}(V_3 - V_6) &=-(I_\mathrm{b2} + I_\mathrm{c2})\tag{6}\\
  \frac{1}{R_1}(V_7 - V_8) &= I_\mathrm{c2}\tag{7}\\
  C_2\frac{d}{dt}(V_8 - V_9) + \frac{V_8}{R_2} - \frac{1}{R_1}(V_7 - V_8) &= 0\tag{8}\\
  \frac{V_9}{R_\mathrm{vol}} - C_2\frac{d}{dt}(V_8 - V_9) &= 0\tag{9}
\end{align}
</div>

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
