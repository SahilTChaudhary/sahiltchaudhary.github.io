---
title: "Re-Sizeable Autonomous Cleaning Robot"
excerpt: |
    Designed and developed a Floor Cleaning Robot that can adjust its size depending on need.  
    ![Re-Sizeable Robot](/images/resizeableRobotRender.png){:width='600px' height='300px'}
collection: portfolio
---

[[GitHub]](https://github.com/SahilTChaudhary/Re-Sizeable-Autonomous-Cleaning-Robot)[[Report]](http://sahiltchaudhary.github.io/files/resizeableRobReport.pdf)

* <b>Tech Stack:</b> Python, CoppeliaSim (V-REP), Fusion 360, Ansys, Raspberry Pi 4
* <b> Summary </b>
    -  <p style="text-align: justify;">Developed a CAD model of a Floor Cleaning Robot that can adjust its size depending on need, as a team lead of three students. The actuation mechanism utilised a Ball Screw Linear Actuator.</p>
    -  <p style="text-align: justify;">Conducted a Simulation study using V-REP, and also developed a Functional Prototype using Raspberry Pi 4 and various sensors to demonstrate the efficacy of the system.</p>
    -  <p style="text-align: justify;">My role: Team lead, built the physical robot along with the wiring and low level code, helped with CAD.</p>

* <b>In-Depth</b>
    *  <p style="text-align: justify;"><b>Introduction</b><br>The idea behind the project was to design and create a Re-Sizeable Floor Cleaning Robot. Automated floor cleaning robots are commonly employed in smart homes, residential, and office spaces to clean the floors. According to a world market study, there is a strong demand for the application of these robots in domestic settings with fully automated functionalities and the least amount of human assistance, and while these robots still account for a small percentage of the global vacuum cleaner market, their recognition and implementation is growing at a rapid rate. The robots are small and execute the cleaning operation without the need for human participation. These robots use motion planning algorithms to cover a large area while cleaning, such as spiral motion, backtracking spiral motion, boustrophedon motion (back and forth), and basic zig-zag motion patterns.</p>

    <div style="text-align:center">
    <img src="/images/resizeableRobotRender.png" alt="Robot_Render" style="width:600px;height:300px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-1 Rendered Image of the robot</em></u></figcaption>

    <div style="text-align:center">
    <img src="/images/resizeableRobot_Prototype.png" alt="Functional_Prototype" style="width:600px;height:300px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-2 Functional Prototype of the robot</em></u></figcaption>
  
    * <p style="text-align: justify;"><b>Motivation</b><br>The goal of the project was to design a re-sizeable cleaning robot that can extend its length, allowing it to cover a larger area in a single sweep, and can also reduce its size to reach inaccessible areas. Cleaning robots are available in a variety of sizes and can clean a specific area in a single sweep. However, the cleaning efficiency and effectiveness can be improved. In open places with little impediment, such as broad halls and living rooms, cleaning can be done quickly by sweeping a larger area in a single sweep. Furthermore, by reducing its length, the robot can clean otherwise inaccessible areas, for example between two pieces of furniture that are close to each other.</p>
    
       
    * <p style="text-align: justify;"><b>Mechanical Design</b><br>The robot comprises three hollow cuboid compartments that overlap and can linearly actuate with the help of the ball screw mechanism. The vacuum system comprises a set of rigid concentric pipes, and there will be a slit along the length of the pipe which will make the vacuum opening. The ends of these pipes will be attached to the walls of the robot on both sides. Hence, whenever the pipes will move further away from each other the slit opening will also increase making it more efficient to collect dust. These pipes will be connected to a storage compartment via a connecting pipe.</p>

        * <p style="text-align: justify;">Increasing the area of the vacuum opening will reduce the suction power so to overcome this problem a motor will be inserted which will adjust the suction power based on the largest opening. For example, when the robot is fully extended it will be powerful enough to absorb dust at the largest opening and when the opening size reduces i.e., when the robot contracts, the vacuum motor voltage will automatically be reduced using a buck converter in order to maintain a constant suction pressure.</p>

        <div style="text-align:center">
        <img src="/images/resizeableRobot_Mechanism.gif" alt="Actuation_Mechanism" style="width:550px;height:300px;">
        </div>
        <figcaption style="text-align: center;"><u><em>Fig-3 Actuation Mechanism</em></u></figcaption>


    * <p style="text-align: justify;"><b>Circuit Design</b><br>The components used are Ultrasonic sensors, camera, four wheel motors, a Ball Screw Actuator, and the Raspberry Pi 4. Representative circuit diagrams are given below.</p>

    <div style="text-align:center">
    <img src="/images/UltrasonicCircuit.png" alt="US_Circuit" style="width:550px;height:300px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-4 Ultrasonic Sensor Circuit</em></u></figcaption>

    <div style="text-align:center">
    <img src="/images/WheelCircuit.png" alt="Wheel_Circuit" style="width:550px;height:300px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-5 Wheel Motors Circuit</em></u></figcaption>

    <div style="text-align:center">
    <img src="/images/LinearActuatorCircuit.png" alt="LA_Circuit" style="width:550px;height:300px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-6 Linear Actuator Circuit</em></u></figcaption>
  

    <div style="text-align:center">
    <video src="/images/resizeableRobot_working_model.mp4" controls="controls" style="max-width: 750px;"></video>
    </div>
    <figcaption style="text-align: center;"><u><em>Functional Prototype demonstration</em></u></figcaption>

* <b>Results</b>
    <p>A simulation study has been demonstrated to verify the efficacy of the system. Further, a functional prototype has been developed as a proof of concept to test the system in the real world. The results above show that the robot can effectively adjust its size depending on need, without affecting mobility and structural integrity of the chassis. Several iterations were required to attain a chassis that was performing well. Earlier iterations of the functional prototype suffered from bending of the chassis and loss of traction to the wheels. Having identified the problem areas, necessary modifications were made to the chassis to ensure compliance.  Future work will involve integrating SLAM using LIDAR, for more efficient and systematic cleaning.</p>