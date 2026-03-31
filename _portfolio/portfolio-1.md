---
title: "Autonomous Robot"
excerpt: "Building an autonomous robot for a pet rescue competition<br/><img src='/images/Robot_1.jpg'>"
collection: portfolio
order: 1
---

## Overview
This project involved designing and building an autonomous  robot to compete in a pet rescue competition from a hypothetical burning building
The robot was programmed to navigate an obstacle course, identify stuffed pets, and  transport them to the safe area. The playing surface is shown below: 

<div style="display: flex; gap: 20px; justify-content: center;">
  <img src="/images/Surface_Assembly_2025.png" width="45%">
  <img src="/images/mapTop.png" width="45%">
</div>


There were three ways to approach the competition. Either you collect the pets in a basket, drive them back and forth, collect them in a basket and zipline to safety at the end, or lastly, you could also throw the pets through the hoop. Out of 15 teams, only our team and one other decided to try throwing the pets, as it was the most challenging option. However, we decided to go for it, thinking it would be a fun challenge. 


I mainly worked on the chassis, the claw for picking up pets, and the ramp design to hold the throwing arm. I also worked on some side projects such as mounting different components, such as the IR sensors, and worked on line following PID tuning. 

## Technologies Used
- **Hardware:** ESP32, Time of Flight sensors, ultrasonic sensors, servo motors, IR sensors, DC motors  
- **Software:** C++  
- **Tools:** Onshape, 3D printer, soldering station, waterjet cutter, laser cutter, lathe, drill press  

## Claw Design 

### Animation 
<div align="center">
  <video width="80%" controls>
    <source src="/images/Claw_Actuation.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
</div>

### Design

The claw is driven by a servo motor, which goes through a gear reduction to increase torque. This is because picking up the pets consistently without any drops was more important than picking them up very quickly. The claw was built modularly with all 3d printed parts, allowing for customization of individual parts and trying different designs, such as different gear ratios and claw pincer designs, without having to re-print everything. This modularity was very useful since, as can be seen in the map, one pet was inside a hollow pillar, so it took some fine-tuning of different parameters to make sure the claw could pick up all the pets on the map.

<br/><img src='/images/claw.png'>

## Chassis Design 

There were many options for mounting wheels. You can do rear wheel drive with a castor at the front which allows for easier manuverability, but not good for the 1in high debris on the track.  You can do four wheel drive which allows for higher speeds, but you need four motos which is heavy and you are more likely to induce noise in your noise sensative circuits. Because of this I decided two use rear wheel drive with two omni wheels at the front. It worked with the debris, and allowed for good enough manuervability without needing four motors. I did some calculations on the chassis height off the floor needed to clear the ramp part as a first step: 


<br/><img src='/images/WheelCalc.png'>


After I also did some motor calculations to source what motors we wanted to drive the robot: 

<br/><img src='/images/MotorCalc.png'>


Based on the motor, I designed some custom 3d printed motor mounts shown on th left, which gave us the proper ground clearance we wanted for the debris. Then I made some corresponding pillow block mounts for the non-driven front wheels shown on the right


<div style="display: flex; gap: 20px; justify-content: center;">
  <img src="/images/motaA.png" width="45%">
  <img src="/images/Pillow.png" width="45%">
</div>




The chassis was made specifically with laser-cut hardboard in mind. This material is readily available and was sufficiently strong for the robot we were making. The indiviual 2d chassis parts were connected with tab and slots. The motors driving the wheels were in the back. Therefore, a lot of the sensing circuits were designed to be in the front to avoid electrical noise contaimation those lines. 

<div style="display: flex; gap: 20px; justify-content: center;">
  <img src="/images/chassis_top.png" width="100%">
</div>


As a part of our throwing arm assembly, we needed a structure to hold the arm. Since we don't want to shift our centre of gravity too far back, this is the design I came up with to have a strong and lightweeight is a base for it. It was designed with two laser-cut acrylic triangles joined by two water-jet pieces of sheet metal, one across the top face to make the surface for the arm to lie on, and one sheet that connected on the bottom so the structure could be bolted to the chassis.

<br/><img src='/images/ramp.png'>




