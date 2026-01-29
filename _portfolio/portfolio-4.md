---
title: "Servo Motor Controller Circuit"
excerpt: "Self-Correcting Speed Servo Motor Circuit  <br/><img src='/images/finalBreadboard.png'>"
collection: portfolio
order: 4
---

## Circuit Overview

Below is a drawing of the complete servo motor controller circuit.

<img src="/images/CircuitSketchFull.jpg" alt="Full Servo Motor Circuit Sketch">

---

## Speed Sensing & Clock Generation

The motor speed is measured using a phototransistor attached to a slotted disk. Each time a slit passes through the light beam, a pulse is generated, creating a clock signal proportional to motor speed.

To reduce noise, this signal is passed through a Schmitt inverter before being used by the counter.

---

## Counting & Latching the Speed

The cleaned clock signal feeds into two cascaded 8-bit counters, producing a 16-bit count over a fixed time window. This value represents the current motor speed.

A D-latch captures the count so it can be processed while the next measurement begins.

### Latch Circuit
<div style="display:flex; gap:1rem; flex-wrap:wrap;">
  <img src="/images/LatchCircuit.png" style="max-width:48%; height:auto;">
  <img src="/images/Latch_Circuit.png" style="max-width:48%; height:auto;">
</div>

---

## Timing & Reset Control

To prevent continuous counting, a reset pulse generator sends a delayed reset shortly after the latch event. This ensures the speed is measured in discrete intervals.

### Pulse Timing
<div style="display:flex; gap:1rem; flex-wrap:wrap;">
  <img src="/images/Delay_Pulse.png" style="max-width:48%; height:auto;">
  <img src="/images/Reset_Pulse.png" style="max-width:48%; height:auto;">
</div>

---

## Digital-to-Analog Conversion

The latched digital value is converted into an analog voltage using an R-2R ladder DAC. Each bit contributes a weighted voltage, producing a signal proportional to motor speed.

A buffer follows the DAC to prevent loading effects due to its high input impedance.

### DLatch → R2R → Buffer
<div style="display:flex; gap:1rem; flex-wrap:wrap;">
  <img src="/images/Buffer.jpg" style="max-width:32%; height:auto;">
  <img src="/images/BBREADBOARD.jpg" style="max-width:32%; height:auto;">
</div>

---

## Error Amplification & Motor Drive

The analog speed signal is compared to a setpoint voltage using an error amplifier. The resulting output adjusts motor drive voltage to correct speed deviations.

This signal drives a BJT, amplifying current to power the motor. A flyback diode protects against back EMF when the motor is switched off.

### Error Amplifier
<div style="display:flex; gap:1rem; flex-wrap:wrap;">
  <img src="/images/ErrorAmplifier.jpg" style="max-width:48%; height:auto;">
  <img src="/images/Error_Amplifier.jpg" style="max-width:48%; height:auto;">
</div>
