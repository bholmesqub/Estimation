---
layout: default
title: "E-Appendix: Common-emitter parameter redundancy analysis"
---

# E-Appendix: Common-emitter parameter redundancy analysis

![Common-emitter amplifier](../images/common-emitter.png)
(*Above*) The common-emitter amplifier.


The PNP BJT can be modelled using the Ebers-Moll model:
<div>
\begin{align}
	I_{\mathrm{b}} & = \frac{I_{\mathrm{s}}}{\beta_{\mathrm{f}}}\left(\mathrm{e}^{\frac{V_{\mathrm{eb}}}{NV_{\mathrm{t}}}} - 1\right) + \frac{I_{\mathrm{s}}}{\beta_{\mathrm{r}}}\left(\mathrm{e}^{\frac{V_{\mathrm{eb}} - V_{\mathrm{ec}}}{NV_{\mathrm{t}}}} - 1\right)
	\\[0.9em]
	I_{\mathrm{c}} &= I_{\mathrm{s}}\left(\mathrm{e}^{\frac{V_{\mathrm{eb}}}{NV_{\mathrm{t}}}} - 1\right) - I_{\mathrm{s}}\frac{\beta_{\mathrm{r}} + 1}{\beta_{\mathrm{r}}}\left(\mathrm{e}^{\frac{V_{\mathrm{eb}} - V_{\mathrm{ec}}}{NV_{\mathrm{t}}}} - 1\right).
\end{align}
</div>

## Nodal Equations

### Initial model

Let the convention for this derivation be that current exiting a node is positive. The potentiometer is fixed at having the maximal resistance between nodes 3 and 4. The nodal equations are then given by:
<div>
\begin{align}
	C_1\frac{d}{dt}(V_1 - V_2) - I_\mathrm{in} &= 0\tag{1}\\
	 \frac{V_2}{R_2} - \frac{V_3 - V_2}{R_1} - C_1\frac{d}{dt}(V_1 - V_2) &= -I_\mathrm{b}\tag{2}\\
	\frac{V_3 - V_2}{R_1} + \frac{V_3 - V_4}{R_4} - I_\mathrm{cc} &= 0\tag{3}	\\
	C_3\frac{d}{dt}(V_4 - V_6) - \frac{V_3 - V_4}{R_4} &= -I_\mathrm{c}\tag{4}\\
	\frac{V_5}{R_3} + C_2 \frac{dV_5}{dt} &= I_\mathrm{b} + I_\mathrm{c}\tag{5}\\
	\frac{V_6}{R_\mathrm{out}} - C_3\frac{d}{dt}(V_4 - V_6) &= 0\tag{6}\\
\end{align}
</div>

And the connections of the voltage sources to the respective nodes
<div>
\begin{align}
	V_\mathrm{i} &= V_1\\
	V_\mathrm{c} &= V_3
\end{align}
</div>

### Simplified

Here equations that feature the current through the voltage sources have been removed as the currents are undetermined.

<div>
\begin{align}
	\frac{V_2}{R_2} - \frac{V_\mathrm{3} - V_2}{R_1} - C_1\frac{d}{dt}(V_\mathrm{1} - V_2) &= -I_\mathrm{b}\tag{2}\\
	C_3\frac{d}{dt}(V_4 - V_6) - \frac{V_\mathrm{3} - V_4}{R_4} &= -I_\mathrm{c}\tag{4}\\
	\frac{V_5}{R_3} + C_2 \frac{dV_5}{dt} &= I_\mathrm{b} + I_\mathrm{c}\tag{5}\\
	\color{red}{\frac{V_6}{R_\mathrm{out}}} - C_3\frac{d}{dt}(V_4 - V_6) &= 0\tag{6}
\end{align}
</div>

This version of the common-emitter model can be simplified by one parameter *if* the value of $$R_\mathrm{out}$$ is considered a parameter. If not, when multiplying/dividing through by another parameter, it combines with $$R_\mathrm{out}$$, ensuring that it stays within the exhaustive summary.

## Matrix form

### Simplified

Resistor admittances are expressed as $$ G_{\mathrm{R}x} = R_x $$
<div>
\begin{equation}
	\mathbf{N}_\mathrm{R} \mathbf{G}_\mathrm{R} \mathbf{N}_\mathrm{R} \mathbf{v} + \mathbf{N}_\mathrm{C} \mathbf{G}_\mathrm{C} \mathbf{N}_\mathrm{C} \mathbf{v}' = \mathbf{I}
\end{equation}
</div>
<div>
\begin{equation}
	\begin{split}
	\begin{bmatrix}
		0 & 0 & 0 & 0 & 0 & 0\\[0.9em]
		0 & G_\mathrm{R1} + G_\mathrm{R2} & -G_\mathrm{R1} & 0 & 0 & 0\\[0.9em]
		0 & -G_\mathrm{R1} & G_\mathrm{R1} + G_\mathrm{R4} & -G_\mathrm{R4} & 0 & 0\\[0.9em]
		0 & 0 & -G_\mathrm{R4} & G_\mathrm{R4} & 0 & 0\\[0.9em]
		0 & 0 & 0 & 0 & G_\mathrm{R3} & 0 \\[0.9em]
		0 & 0 & 0 & 0 & 0 & G_\mathrm{Rout}
	\end{bmatrix}
	\begin{bmatrix}
		V_1 \\[0.9em] V_2 \\[0.9em] V_3 \\[0.9em] V_4 \\[0.9em] V_5 \\[0.9em] V_6
	\end{bmatrix}
	\\[0.9em]+
	\begin{bmatrix}
		C_1 & -C_1 & 0 & 0 & 0 & 0 \\[0.9em]
		-C_1 & C_1 & 0 & 0 & 0 & 0 \\[0.9em]
		0 & 0 & 0 & 0 & 0 & 0 \\[0.9em]
		0 & 0 & 0 & C_3 & 0 & -C_3 \\[0.9em]
		0 & 0 & 0 & 0 & C_2 & 0 \\[0.9em]
		0 & 0 & 0 & -C_3 & 0 & C_3
	\end{bmatrix}
	\begin{bmatrix}
		V_\mathrm{1}' \\[0.9em] V_2' \\[0.9em] V_\mathrm{3}' \\[0.9em] V_4' \\[0.9em] V_5' \\[0.9em] V_6'
	\end{bmatrix}
	=
	\begin{bmatrix}
		0 \\[0.9em] -I_\mathrm{b} \\[0.9em] 0 \\[0.9em] -I_\mathrm{c} \\[0.9em] I_\mathrm{b} + I_\mathrm{c} \\[0.9em] 0
	\end{bmatrix}
	\end{split}
\end{equation}
</div>

## Exhaustive summary and redundancy

Extracting the circuit component parameters:
<div>
\begin{equation}
	\theta = [R_1,\;\; R_2,\;\; R_3,\;\; R_4,\;\; C_1,\;\; C_2,\;\; C_3,\;\; I_\mathrm{s},\;\; N, \;\; \beta_\mathrm{f},\;\; \beta_\mathrm{r}]
\end{equation}
</div>

An exhaustive summary can now be found from the elements of the matrices and the additional parameter information from the Ebers-Moll model. There are many repeated elements which have no effect on redundancy, so can be removed. Again, polarity does not change the redundancy so each element can be represented by its absolute value. Assuming that $$R_\mathrm{out}$$ is a known value and not a parameter, the exhaustive summary is given by:
<div>
\begin{align}
	\kappa = [G_\mathrm{R1} + &G_\mathrm{R2},\;\; G_\mathrm{R1},\;\;G_\mathrm{R1} + G_\mathrm{R4},\;\;G_\mathrm{R4},\;\;G_\mathrm{R3},
	\\
	& C_1,\;\; C_3,\;\; C_2,\;\; I_\mathrm{s}/\beta_\mathrm{f} ,\;\; I_\mathrm{s}/\beta_\mathrm{r},\;\; I_\mathrm{s},\;\; I_\mathrm{s}(\beta_\mathrm{r} + 1)/\beta_\mathrm{r},\;\; 1/N]
\end{align}
</div>

Which results in the derivative matrix:

<div>
\begin{equation}
	\frac{\partial\mathbf{\kappa}}{\partial\mathbf{\theta}} =
	\left[
	\begin{smallmatrix}
		-G_\mathrm{R1}^2 & -G_\mathrm{R2}^2 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
		-G_\mathrm{R1}^2 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0\\
		-G_\mathrm{R1}^2 & 0 & 0 & -G_\mathrm{R4}^2 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
		0 & 0 & 0 & -G_\mathrm{R4}^2 & 0 & 0 & 0 & 0 & 0 & 0 & 0\\
		0 & 0 & -G_\mathrm{R3}^2 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0\\
		0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0\\
		0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0\\
		0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0\\
		0 & 0 & 0 & 0 & 0 & 0 & 0 & 1/\beta_\mathrm{f} & -I_\mathrm{s}/\beta_\mathrm{f} & 0 & 0\\
		0 & 0 & 0 & 0 & 0 & 0 & 0 & 1/\beta_\mathrm{f} & -I_\mathrm{s}/\beta_\mathrm{f} & 0 & 0\\
		0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0\\
		0 & 0 & 0 & 0 & 0 & 0 & 0 & (\beta_\mathrm{r} + 1)/\beta_\mathrm{r} & 0 & 0 & I_\mathrm{s}/\beta_\mathrm{r} - I_\mathrm{s}(\beta_\mathrm{r} + 1)/\beta_\mathrm{r}^2\\
		0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & -1/N^2 & 0 & 0\\
	\end{smallmatrix}
	\right]
\end{equation}
</div>
