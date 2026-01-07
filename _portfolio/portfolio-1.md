---
title: "Autonomous Robot"
excerpt: "Building an autonomous robot for a pet rescue competition<br/><img src='/images/Robot_1.jpg'>"
collection: portfolio
---

## Overview
This project involved designing and building an autonomous  robot to compete in a pet rescue competition from a hypothetical burning building
The robot was programmed to navigate an obstacle course, identify stuffed pets, and  transport them to the safe area. The playing surface is shown below: 


<br/><img src='/images/Surface_Assembly_2025.png'>


There were three ways to approach the competition. Either you collect the pets in a basket, drive them back and forth, collect them in a basket and zipline to safety at the end, or lastly, you could also throw the pets through the hoop. Out of 15 teams, only our team and one other decided to try throwing the pets, as it was the most challenging option. However, we decided to go for it, thinking it would be a fun challenge. 


I mainly worked on the chassis, the claw for picking up pets, and the ramp design to hold the throwing arm. I also worked on some side projects such as mounting different components, such as the IR sensors, and worked on line following PID tuning. 

## Summary of Contributions
- **3D modelling in Onshape:** I finalized designs for the claw, chassis and more in onshape, also did assembly integration for others components in the model.
- **Autonomous Navigation:** Worked on line following and creating mounts to ensure consistent results.  
- **Mechanical Design:** Custom-built chassis using laser cutter, 3D printer, waterjet cutter, and other sheet metal tools.  
- **Teamwork:** Collaborated with 3 teammates for software, electronics, and testing integration.

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
The claw was built modularly with all 3d printed parts, allowing for customization of individual parts and trying different designs, such as different gear ratios and claw pincer designs, without having to re-print everything. This modularity was very useful since, as can be seen in the map, one pet was inside a hollow pillar, so it took some fine-tuning of different parameters to make sure the claw could pick up all the pets on the map.

<br/><img src='/images/claw_2.png'>



