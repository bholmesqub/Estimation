---
layout: default
title: "Common-emitter aliasing analysis"
---

# Common-emitter aliasing analysis

When optimising nonlinear models against measured data, aliasing can cause significant issues. Bias can be introduced into the modelled signal that causes for compensation in the parameter set for features that do not exist in the measurement.

Graphically this can be illustrated in the following image:

![Common-emitter aliasing example](../../images/aliasing/ce-aliasing-td-comparison.png)

Here the excitation signal from the article (with supply voltage = -9 V, and peak voltage = 3 V) has been simulated through the common-emitter amplifier model with a base sample rate of 1 MHz, and oversampled up to 16x. Each signal is compared to the 1x oversampled (not oversampled) signal for the lower plots.

While for audio frequencies a 1 MHz sample rate gives a Nyquist frequency already 25x higher than the upper limit, it is clear that only sampling at 100 kHz has caused significant artefacts. When further oversampled, these artefacts change causing error between the models, preventing complete convergence of the model parameters.
