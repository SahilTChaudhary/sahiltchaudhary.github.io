---
title: "Quadruped Robot"
excerpt: "Found the stable workspace of a Quadruped Robot using Kinematic Analysis. <br/><img src='/images/QuadRobot.png'>"
collection: portfolio
---

[[Notion]](https://common-bathtub-ada.notion.site/Quadrupled-Project-5025fb31b81147499df83d656a3e7b42)[[GitHub]](https://github.com/SahilTChaudhary/Quadruped-Robot)

* <b>Tech Stack:</b> Python(PyBullet), ROS, SolidWorks, MATLAB, SIMULINK(Robotics Toolbox), GitHub
* <b> Summary </b>
    -  <p style="text-align: justify;">Created a CAD design and prototype of a quadruped walking robot and implemented yaw, pitch and roll as a team lead of four students; implemented trot, canter and pace gait to analyses the various performance and stability of different gait systems.</p>
    -  <p style="text-align: justify;">Redesigned the legs of the quadruped robot making it capable of performing backflips; conducted kinematic workspace analysis of the robot and using the kinematics, equation of motions and using Simulink and PyBullet for animation.</p>
<br>

* <b>In-Depth</b>
    *  <p style="text-align: justify;"><b>Introduction</b><br>The idea behind the project was to redesign and create a new leg design for quadruped robots, which are robots designed with four legs and have several practical applications. They can navigate difficult terrain and environments that are inaccessible to wheeled or bipedal robots, making them useful for tasks such as search and rescue operations or exploration of rough terrain. Quadruped robots can also be used for inspection and maintenance of industrial equipment or infrastructure, as well as for agricultural applications such as herding livestock or monitoring crops. In addition, the stability provided by four legs makes quadruped robots well-suited for tasks that require high precision or stability, such as carrying and manipulating heavy objects.</p>

    <div style="text-align:center">
    <img src="/images/Quad_project_render_1.png" alt="Robot_Render" style="width:700px;height:300px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-1 Render Image of the robot</em></u></figcaption>
  
    * <p style="text-align: justify;"><b>Motivation</b><br>The goal of the project was to re-create the leg design to increase the workspace of the robots legs. Legged robots, which are robots designed with legs instead of wheels, have become increasingly important in recent years. One of the main advantages of legged robots is their ability to navigate complex and uneven terrain, making them ideal for applications such as search and rescue, exploration, and inspection of hazardous environments. Additionally, legged robots can be used for tasks that require greater dexterity and mobility, such as manipulating objects or interacting with humans. Legged robots can also operate in environments where wheeled robots or other types of vehicles may be unable to operate, such as rocky or steep terrain, or in disaster-stricken areas with debris on the ground.</p>
    
    <div style="text-align:center">
    <img src="/images/Quad_project_Leg_Redesign.png" alt="Robot_Render" style="width:550px;height:300px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-2 Redesigned Leg with out of plane joints</em></u></figcaption>
    
    * <p style="text-align: justify;"><b>Mechanical Design</b><br>The figure above shows the new design of the leg used. This was done to provide the robot with a higher order of workspace. While, also maintains the capabilities of the current design. Furthermore, legged robots have the potential to significantly reduce the environmental impact of transportation. Compared to traditional wheeled vehicles, legged robots have a lower ground pressure, which means they can traverse delicate ecosystems without causing damage. They also consume less energy, making them more environmentally friendly than traditional vehicles. In the future, legged robots may be used for last-mile delivery, reducing the need for carbon-emitting trucks and vans. Overall, legged robots have a wide range of potential applications and offer a flexible and adaptable platform for various tasks. Their ability to navigate complex environments, interact with humans, and reduce environmental impact make them an important area of research and development.
    
    * <p style="text-align: justify;">The kinematic analysis and the mathematical calculations behind the robot can be found on the <b>[Notion page](https://common-bathtub-ada.notion.site/Quadrupled-Project-5025fb31b81147499df83d656a3e7b42)</b>.</p>

    <div style="text-align:center">
    <video src="/images/Quad_project_simulation_1.mp4" controls="controls" style="max-width: 750px;"></video>
    </div>
    <figcaption style="text-align: center;"><u><em>Simulation-1 Standstill movement capabilities of the Robot</em></u></figcaption>

    <div style="text-align:center">
    <video src="/images/Quad_project_simulation_2.mp4" controls="controls" style="max-width: 750px;"></video>
    </div>
    <figcaption style="text-align: center;"><u><em>Simulation-2 Motion capabilities of the Robot</em></u></figcaption>

    * <p style="text-align: justify;"><b>Results</b><br>The simulations above show to final output of the projects depicting the capabilities of the robot. It can also be observed that the robot is fully capable of dropping down to the the much lower height as the limbs are out of plane for the robot. This increase the mobility in robot in cramped quatres and low lying ares. It can also be noted that the robot is able to maintain the same functionality as before without the increase in any additional constraints due to the redesigning of the legs. </p>