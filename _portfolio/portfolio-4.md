---
title: "Servo Motor Controller Circuit"
excerpt: "Self-Correcting Speed Servo Motor Circuit  <br/><img src='/images/finalBreadboard.png'>"
collection: portfolio
order: 4
---

Below is a drawing I made of the entire circuit. 
<img src='/images/CircuitSketchFull.jpg' alt='Full Servo Motor Circuit Sketch'>

## Circuit Logic Overview

We need to read the speed at which the motor is turning and based off that data, to control its new
input. 

Firstly, we start with the phototransistor circuit attached to the motor, every time the disk spins, and a slit in
the disk cross the light it creates a pulse creating a clock.

This clock goes through one of the Schmitt inverters to prevent the effect of random noise and into the clock of the counter.
The counter is composed of two 8-bit counters to create a count by 256. The count keeps count of the clock pulses within a time frame which is essentially
keeping track of something proportional to the current motor speed. 

Then from there the DLATCH latches this
number from the clock to keep track of our current count while we start the new count. The latch is latching the
values at the latch frequency which is just the input frequency; a square wave oscillating between 0 and 5V, that is
inverted twice. However, we don’t want to count forever, we want to count in periods so we can keep altering the
speed. We do this using the reset pulse generator, which sends a delayed pulse some small time after the latch
signal, to reset the clock. 

Now we have a digital signal representing our count we want to translate this to an analog
signal. We use the R2R ladder as a DAC to convert this signal to analog by assigning each bit a weight and
summing. We have a buffer connected to the output of the DAC, so the load on the R2R does not effect the current
its drawing. The buffer does this since it has very high input impedance. From there this analog signal enters into
the error amplifier. The voltage at the inverting input is compared to the setpoint voltage (the non inverting input
voltage). The error amplifier output gives a result that is proportional and integrated compared to the input.
Essentially, based on how high or low the input is compared to the setpoint it will either output a lower or higher
voltage to try to keep the output at the desired point (decided by the setpoint).

After the error amplifier the output goes into the Base terminal of the BJT, this is a small current, the BJT will amplify this current so the current
through the collector is 100 times larger, this is important since the collector current is what is driving the motor to
spin. There is also a diode which is typically in reverse bias but when we turn off the motor, the coils of the motor
which acts as an inductor causes a back emf, the diode will be in forward bias now and will allow a safe loop for
the current


## Circuit Pictures

### Latch Circuit Diagram and Breadboard
<div style="display:flex; gap:1rem; flex-wrap:wrap; align-items:flex-start;">
  <img src="/images/LatchCircuit.png" style="max-width:48%; height:auto; flex:0 0 auto;">
  <img src="/images/Latch_Circuit.png" style="max-width:48%; height:auto; flex:0 0 auto;">
</div>

---

### Pulse & Timing Oscilloscope Outputs
<div style="display:flex; gap:1rem; flex-wrap:wrap; align-items:flex-start;">
  <img src="/images/Delay_Pulse.png" style="max-width:48%; height:auto; flex:0 0 auto;">
  <img src="/images/Reset_Pulse.png" style="max-width:48%; height:auto; flex:0 0 auto;">
</div>

---

### Clock – DLatch Circuit Breadboard
<div style="display:flex; gap:1rem; flex-wrap:wrap; align-items:flex-start;">
  <img src="/images/DlatchBreadboard.jpg" style="max-width:32%; height:auto; flex:0 0 auto;">
  <img src="/images/DLatchLogic.png" style="max-width:32%; height:auto; flex:0 0 auto;">
</div>

---

### DLatch – R2R – Buffer Circuit Diagram, Breadboard
<div style="display:flex; gap:1rem; flex-wrap:wrap; align-items:flex-start;">
  <img src="/images/Buffer.jpg" style="max-width:32%; height:auto; flex:0 0 auto;">
  <img src="/images/BufferBreadboard.jpg" style="max-width:32%; height:auto; flex:0 0 auto;">
</div>

---

### Amplifier
<div style="display:flex; gap:1rem; flex-wrap:wrap; align-items:flex-start;">
  <img src="/images/ErrorAmplifier.jpg" style="max-width:48%; height:auto; flex:0 0 auto;">
  <img src="/images/Error_Amplifier.jpg" style="max-width:48%; height:auto; flex:0 0 auto;">
</div>

