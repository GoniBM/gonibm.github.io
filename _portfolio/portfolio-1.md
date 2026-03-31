---
title: "Autonomous Robot"
excerpt: "Building an autonomous robot for a pet rescue competition<br/><img src='/images/Robot_1.jpg'>"
collection: portfolio
order: 1
---

## Overview
This project involved designing and building an autonomous robot to save pets from a burning building. The scenario was emulated by an 8 square foot surface that included a ramp, debris, and other obstacles, with stuffed animals scattered throughout that needed to be brought to safety.

Each team built an autonomous robot programmed to navigate the obstacle course, identify stuffed pets, and transport them to the safe area. The playing surface is shown below:

<div style="display: flex; gap: 20px; justify-content: center;">
  <img src="/images/Surface_Assembly_2025.png" width="45%">
  <img src="/images/mapTop.png" width="45%">
</div>

There were three ways to approach the competition: collect the pets in a basket and drive them back and forth, collect them in a basket and zipline to safety at the end, or throw the pets through the hoop as seen in the map above. Out of 15 teams, only our team and one other decided to try throwing — it was the hardest option, but we thought it would be a fun challenge.

My main contributions were the chassis, the claw for picking up pets, and the structural base for the throwing arm. I also worked on some side projects: designing and soldering our line-following circuit, mounting the IR sensors, and tuning the line-following PID. I also helped develop our state machine.

## Technologies Used
- **Hardware:** ESP32, Time of Flight sensors, ultrasonic sensors, servo motors, IR sensors, DC motors  
- **Software:** C++  
- **Tools:** Onshape, 3D printer, soldering station, waterjet cutter, laser cutter, lathe, drill press  

## Claw Design 

### Design

The claw is driven by a servo motor through a gear reduction to increase torque — picking up pets reliably mattered more than picking them up quickly. It was built modularly with all 3D-printed parts, which made it easy to swap in different gear ratios and pincer designs without reprinting everything. This modularity was especially useful because one pet was hidden inside a hollow pillar, so it took some fine-tuning to make sure the claw could handle every pickup on the map.

<br/><img src='/images/claw.png'>
<br/><img src='/images/Claw_Image.png'>

### Animation 
<div align="center">
  <video width="80%" controls>
    <source src="/images/Claw_Actuation.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
</div>

## Chassis Design 

I designed the chassis from laser-cut hardboard using the tab and slot feature in Onshape, which lets you build a structure that connects similarly to LEGO, held together with wood glue. I went with this approach because of how quickly you can iterate with cardboard early on — short turnaround made it easy to spot problems fast, which was essential given the tight timeline.

My very first prototype was a simple box. It helped me gauge the tolerances of the laser cutter, test the strength of the hardboard structure, give the team a visual reference for component placement, and serve as a first testbed for wheel mounting.

There were a few options to consider for the drivetrain. Rear-wheel drive with a front caster allows for easy maneuverability, but a caster gets stuck easily on the 1-inch debris on the track. Four-wheel drive gives higher speeds, but requires four motors — more weight and more electrical noise near sensitive circuits. I landed on rear-wheel drive with two front omni wheels. The omnis gave us good maneuverability without the extra motors, and having two front contact points meant we didn't get stuck the way a caster would.

With the wheel configuration decided, I did some calculations on the chassis ground clearance needed to drive up the ramp without bottoming out:

<br/><img src='/images/WheelCalc.png'>

I also ran motor calculations to figure out what drive motors to source:

<br/><img src='/images/MotorCalc.png'>

These were initially unloaded calculations — our robot ended up heavier than expected, so we had to iterate and switch to higher-torque motors.

From there, I designed a custom 3D-printed motor mount (left) so I could set the ground clearance precisely, along with pillow block mounts (right) to rigidly hold the shafts for the front omni wheels. The front omnis rotated about a bearing on the far end of the shaft and were constrained axially with a simple shaft collar.

<div style="display: flex; gap: 20px; justify-content: center;">
  <img src="/images/motaA.png" width="45%">
  <img src="/images/Pillow.png" width="45%">
</div>

Going from a box to a full chassis meant thinking through a lot of layout decisions at once. We pre-planned where all the circuits would go — more robust components like the wheel drivers and power board went in the back, while the sensitive control and sensing boards went up front, away from motor noise. We also wanted the centre of mass biased toward the rear so the driven wheels would have more traction. On top of that, we needed the pet pickup arm positioned so it could hand off cleanly to the throwing arm, with enough clearance for everything to move freely. Finally, we needed a strong enough superstructure to handle the force from the throwing arm without ripping out of the chassis. With all of that in mind, the chassis came together into its final form:

<div style="display: flex; gap: 20px; justify-content: center;">
  <img src="/images/chassis_top.png" width="100%">
</div>

The throwing arm needed a dedicated support structure. To avoid shifting the centre of gravity too far back, I designed a lightweight base using two laser-cut acrylic triangles joined by two waterjet sheet metal pieces — one across the top face as the arm's resting surface, and one connecting at the bottom so the whole assembly could be bolted to the chassis.

<br/><img src='/images/ramp.png'>

## Results

The claw worked well and picked up pets reliably without dropping them. Where we struggled was getting the claw to drop the pet cleanly into the throwing arm, and getting the arm to consistently reach pets that were farther from the target. One mistake we made was mounting the throwing arm off to one side — it shifted our centre of mass more than we anticipated, which made our line following inconsistent at times.

Overall, we didn't place first, but I don't regret going for the harder approach. It pushed us to solve problems we wouldn't have faced otherwise, and I came away with a lot more than I would have playing it safe.
