---
layout: default
title: "Common-emitter noise floor analysis"
---

# Common-emitter noise floor

To provide context to the frequency spectrum of the Common-Emitter amplifier in the results, this pages contains illustrations of the noise floor of the Common-Emitter amplifier. This enables further intuition about how accurate the spectrum is matched by knowing the limitations, and provides clarity about what may be signal distortion and not noise.

The same measurement script was used as for performing the circuit measurements but with input signal amplitudes set to 0. The sample rate is 1 MHz, measurement duration of 1 second, and 30 averages were performed.

## Supply Voltage -5V
![Supply voltage = -5V, C2 = 1uF](../../images/noise/ce-noiseErr--5V-1.0s-1uF.png)

Noise properties:
  - DC offset = 24.2 µV
  - Standard deviation = 210 µV

## Supply Voltage -9V
![Supply voltage = -9V, C2 = 1uF](../../images/noise/ce-noiseErr--9V-1.0s-1uF.png)

Noise properties:
  - DC offset = 28.4 µV
  - Standard deviation = 777 µV

## Signal distributions

![Frequency distributions](../../images/noise/ce-noiseErr-Dist-1.0s-1uF.png)

## Analysis

First, inspecting the noise distributions it can be seen that with a -9 V supply voltage there is more white noise present in the system. With a -5 V supply voltage the distributions moves towards the sum of two normal distributions, indicating more dominance of the sinusoidal 50 Hz factor.

The residual of the modelled signal is not equivalent to the noise floor at any point in the spectrum for either supply voltages. There are regions in the spectrum where the residual does follow the trend of the noise floor.

Finally, there is a noticeable bump past the upper frequency limit of the low-amplitude signal indicating significant distortion. This factor is not clear in the article illustrations but does indicate that while the low-amplitude signal is better at capturing near-linear behaviour, it is difficult to design a signal with a high SNR over the audio range with low distortion.
