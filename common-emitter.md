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
	\\[0.5em]
	I_{\mathrm{c}} &= I_{\mathrm{s}}\left(\mathrm{e}^{\frac{V_{\mathrm{eb}}}{NV_{\mathrm{t}}}} - 1\right) - I_{\mathrm{s}}\frac{\beta_{\mathrm{r}} + 1}{\beta_{\mathrm{r}}}\left(\mathrm{e}^{\frac{V_{\mathrm{eb}} - V_{\mathrm{ec}}}{NV_{\mathrm{t}}}} - 1\right).
\end{align}
</div>

Extracting the circuit component parameters:
<div>
\begin{equation}
	\theta = [R_1,\;\; R_2,\;\; R_3,\;\; R_4,\;\; C_1,\;\; C_2,\;\; C_3,\;\; I_\mathrm{s},\;\; N, \;\; \beta_\mathrm{f},\;\; \beta_\mathrm{r}]
\end{equation}
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
	V_\mathrm{in} = V_1\\
	V_\mathrm{cc} = V_3
\end{align}
</div>

### Simplified

Here equations that feature the current through the voltage sources have been removed as the currents are undetermined. Voltage sources have been subsituted for nodal voltages where applicable.

<div>
\begin{align}
	\frac{V_2}{R_2} - \frac{V_\mathrm{cc} - V_2}{R_1} - C_1\frac{d}{dt}(V_\mathrm{in} - V_2) &= -I_\mathrm{b}\tag{2}\\
	C_3\frac{d}{dt}(V_4 - V_6) - \frac{V_\mathrm{cc} - V_4}{R_4} &= -I_\mathrm{c}\tag{4}\\
	\frac{V_5}{R_3} + C_2 \frac{dV_5}{dt} &= I_\mathrm{b} + I_\mathrm{c}\tag{5}\\
	\color{red}{\frac{V_6}{R_\mathrm{out}}} - C_3\frac{d}{dt}(V_4 - V_6) &= 0\tag{6}
\end{align}
</div>

This version of the common-emitter model can be simplified by one parameter *if* the value of $$R_\mathrm{out}$$ is considered a parameter. If not, when multiplying/dividing through by another parameter, it combines with $$R_\mathrm{out}$$, ensuring that it stays within the exhaustive summary.

### Moving known voltages to RHS

<div>
\begin{align}
	\frac{V_2}{R_2} + \frac{V_2}{R_1} + C_1\frac{d}{dt}V_2 &= C_1\frac{d}{dt}V_\mathrm{in} + \frac{V_\mathrm{cc}}{R_1}-I_\mathrm{b}\tag{2}\\
	C_3\frac{d}{dt}(V_4 - V_6) + \frac{V_4}{R_4} &= \frac{V_\mathrm{cc}}{R_4}-I_\mathrm{c}\tag{4}\\
	\frac{V_5}{R_3} + C_2 \frac{dV_5}{dt} &= I_\mathrm{b} + I_\mathrm{c}\tag{5}\\
	\frac{V_6}{R_\mathrm{out}} - C_3\frac{d}{dt}(V_4 - V_6) &= 0\tag{6}
\end{align}
</div>

## Matrix form

### Simplified

Known values are substituted into the LHS for brevity.

<div>
\begin{equation}
	\mathbf{N_R G_R N_R v + N_C G_C N_C v' = I}
\end{equation}
</div>
<div>
\begin{equation}
	\begin{split}
	\begin{bmatrix}
		0 & 0 & 0 & 0 & 0 & 0\\
		0 & \frac{1}{R_1} + \frac{1}{R_2} & -\frac{1}{R_1} & 0 & 0 & 0\\
		0 & -\frac{1}{R_1} & \frac{1}{R_1} + \frac{1}{R_4} & -\frac{1}{R_4} & 0 & 0\\
		0 & 0 & -\frac{1}{R_4} & \frac{1}{R_4} & 0 & 0\\
		0 & 0 & 0 & 0 & \frac{1}{R_3} & 0 \\
		0 & 0 & 0 & 0 & 0 & \frac{1}{R_\mathrm{out}}
	\end{bmatrix}
	\begin{bmatrix}
		V_\mathrm{in} \\ V_2 \\ V_\mathrm{cc} \\ V_4 \\ V_5 \\ V_6
	\end{bmatrix}
	\\+
	\begin{bmatrix}
		C_1 & -C_1 & 0 & 0 & 0 & 0 \\
		-C_1 & C_1 & 0 & 0 & 0 & 0 \\
		0 & 0 & 0 & 0 & 0 & 0 \\
		0 & 0 & 0 & C_3 & 0 & -C_3 \\
		0 & 0 & 0 & 0 & C_2 & 0 \\
		0 & 0 & 0 & -C_3 & 0 & C_3
	\end{bmatrix}
	\begin{bmatrix}
		V_\mathrm{in}' \\ V_2' \\ V_\mathrm{cc}' \\ V_4' \\ V_5' \\ V_6'
	\end{bmatrix}
	=
	\begin{bmatrix}
		0 \\ -I_\mathrm{b} \\ 0 \\ -I_\mathrm{c} \\ I_\mathrm{b} + I_\mathrm{c} \\ 0
	\end{bmatrix}
	\end{split}
\end{equation}
</div>

### Moving known voltages to RHS

Known voltages are maintained on RHS but additional conductance matrices are created to handle the change.

<div>
\begin{equation}
\mathbf{N_{R1} G_R N_{R1} v + N_{C1} G_C N_{C1} v' = N_{nl} I + N_{R2} G_R N_{R2} u + N_{C2} G_C N_{C2} u'}
\end{equation}
</div>
<div>
\begin{equation}
	\begin{split}
	\begin{bmatrix}
		\frac{1}{R_1} + \frac{1}{R_2} & 0 & 0 & 0\\
		0 & \frac{1}{R_4} & 0 & 0\\
		0 & 0 & \frac{1}{R_3} & 0 \\
		0 & 0 & 0 & \frac{1}{R_\mathrm{out}}
	\end{bmatrix}
	\begin{bmatrix}
		V_2 \\ V_4 \\ V_5 \\ V_6
	\end{bmatrix}
	+
	\begin{bmatrix}
		C_1 & 0 & 0 & 0 \\
		0 & C_3 & 0 & -C_3 \\
		0 & 0 & C_2 & 0 \\
		0 & -C_3 & 0 & C_3
	\end{bmatrix}
	\begin{bmatrix}
		V_2' \\ V_4' \\ V_5' \\ V_6'
	\end{bmatrix}

	\\=
	\begin{bmatrix}
		0 & 0 \\ -1 & 0 \\ 0 & 0 \\ 0 & -1 \\ 1 & 1 \\ 0 & 0
	\end{bmatrix}
	\begin{bmatrix}
		I_\mathrm{b} \\ I_\mathrm{c}
	\end{bmatrix}
	+
	\begin{bmatrix}
		0 & -\frac{1}{R_1} \\ 0 & \frac{1}{R_1} + \frac{1}{R_4} \\
		0 & -\frac{1}{R_4} \\0 & 0 \\0 & 0
	\end{bmatrix}
	\begin{bmatrix}
		V_\mathrm{in} \\ V_\mathrm{cc}
	\end{bmatrix}
	+
	\begin{bmatrix}
		0 & C_1 \\ 0 & 0 \\ 0 & 0 \\ 0 & 0 \\ 0 & 0 \\ 0 & 0 \\
	\end{bmatrix}
	\begin{bmatrix}
		V_\mathrm{in}' \\ V_\mathrm{cc}'
	\end{bmatrix}
	\end{split}
\end{equation}
</div>

## Exhaustive summary and redundancy

An exhaustive summary can now be found from the elements of the matrices and the additional parameter information from the Ebers-Moll model. There are many repeated elements which have no effect on redundancy, so can be removed. Again, polarity does not change the redundancy so each element can be represented by it's absolute value. Assuming that $$R_\mathrm{out}$$ is a known value and not a parameter, the exhaustive summary is given by:
<div>
\begin{align}
	\kappa = [1/R_1 + &1/R_2,\;\; 1/R_1,\;\;1/R_1 + 1/R_4,\;\;1/R_4,\;\;1/R_3,
	\\
	& C_1,\;\; C_3,\;\; C_2,\;\; I_\mathrm{s}/\beta_\mathrm{f} ,\;\; I_\mathrm{s}/\beta_\mathrm{r},\;\; I_\mathrm{s},\;\; I_\mathrm{s}(\beta_\mathrm{r} + 1)/\beta_\mathrm{r},\;\; 1/N]
\end{align}
</div>

Which results in the derivative matrix:

<div>
\begin{equation}
	\begin{bmatrix}
		-\frac{1}{R_1^2} & -\frac{1}{R_2^2} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
		-\frac{1}{R_1^2} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0\\
		-\frac{1}{R_1^2} & 0 & 0 & -\frac{1}{R_4^2} & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
		0 & 0 & 0 & -\frac{1}{R_4^2} & 0 & 0 & 0 & 0 & 0 & 0 & 0\\
		0 & 0 & -\frac{1}{R_3^2} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0\\
		0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0\\
		0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0\\
		0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0\\
		0 & 0 & 0 & 0 & 0 & 0 & 1/\beta_\mathrm{f} & 0 & -I_\mathrm{s}/\beta_\mathrm{f} & 0 & 0\\
		0 & 0 & 0 & 0 & 0 & 0 & 1/\beta_\mathrm{f} & 0 & -I_\mathrm{s}/\beta_\mathrm{f} & 0 & 0\\
		0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0\\
		0 & 0 & 0 & 0 & 0 & 0 & (\beta_\mathrm{r} + 1)/\beta_\mathrm{r} & 0 & 0 & 0 & I_\mathrm{s}/\beta_\mathrm{r} - I_\mathrm{s}(\beta_\mathrm{r} + 1)/\beta_\mathrm{r}^2\\
		0 & 0 & 0 & 0 & 0 & 0 & 0 & -1/N^2 & 0 & 0 & 0\\
	\end{bmatrix}
\end{equation}
</div>
