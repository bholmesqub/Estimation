---
layout: default
title: "Common-emitter aliasing analysis"
---

# Common-emitter aliasing analysis

When optimising nonlinear models against measured data, aliasing can cause significant issues. Bias can be introduced into the modelled signal that causes for compensation in the parameter set for features that do not exist in the measurement.

Graphically this can be illustrated in the following image:

![Common-emitter aliasing example](../../images/aliasing/ce-aliasing.png)

Here the excitation signal from the article (with supply voltage = -9 V, and peak voltage = 3 V) has been simulated through the common-emitter amplifier model at two sample rates: 2 MHz and 100 kHz. While for audio frequencies a 100 kHz sample rate gives a Nyquist frequency already 2.5x higher than the upper limit, it is clear that only sampling at 100 kHz has caused significant artefacts.
