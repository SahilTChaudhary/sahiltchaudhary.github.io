---
title: "Re-Sizeable Autonomous Cleaning Robot"
excerpt: "Designed and developed a Floor Cleaning Robot that can adjust its size depending on need. <br/><img src='/images/CleaningRobot.png'>"
collection: portfolio
---

[[GitHub]](https://github.com/SahilTChaudhary/Re-Sizeable-Autonomous-Cleaning-Robot)[[Report]](http://sahiltchaudhary.github.io/files/resizeableRobReport.pdf)

* <b>Tech Stack:</b> Python, CoppeliaSim (V-REP), Fusion 360, Ansys, GitHub, Raspberry Pi 4
* <b> Summary </b>
    -  <p style="text-align: justify;">Developed a CAD model of a Floor Cleaning Robot that can adjust its size depending on need, as a team lead of three students. The actuation mechanism utilised a Ball Screw Linear Actuator.</p>
    -  <p style="text-align: justify;">Conducted a Simulation study using V-REP, and also developed a Functional Prototype using Raspberry Pi 4 and various sensors to demonstrate the efficacy of the system.</p>

* <b>In-Depth</b>
    *  <p style="text-align: justify;"><b>Introduction</b><br>The idea behind the project was to design and create a Re-Sizeable Floor Cleaning Robot. Automated floor cleaning robots are commonly employed in smart homes, residential, and office spaces to clean the floors. According to a world market study, there is a strong demand for the application of these robots in domestic settings with fully automated functionalities and the least amount of human assistance, and while these robots still account for a small percentage of the global vacuum cleaner market, their recognition and implementation is growing at a rapid rate. The robots are small and execute the cleaning operation without the need for human participation. These robots use motion planning algorithms to cover a large area while cleaning, such as spiral motion, backtracking spiral motion, boustrophedon motion (back and forth), and basic zig-zag motion patterns.</p>

    <div style="text-align:center">
    <img src="/images/Quad_project_render_1.png" alt="Robot_Render" style="width:700px;height:300px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-1 Render Image of the robot</em></u></figcaption>
  
    * <p style="text-align: justify;"><b>Motivation</b><br>The goal of the project was to design a re-sizeable cleaning robot that can extend its length, allowing it to cover a larger area in a single sweep, and can also reduce its size to reach inaccessible areas. Cleaning robots are available in a variety of sizes and can clean a specific area in a single sweep. However, the cleaning efficiency and effectiveness can be improved. In open places with little impediment, such as broad halls and living rooms, cleaning can be done quickly by sweeping a larger area in a single sweep. Furthermore, by reducing its length, the robot can clean otherwise inaccessible areas, for example between two pieces of furniture that are close to each other.</p>
    
    <div style="text-align:center">
    <img src="/images/Quad_project_Leg_Redesign.png" alt="Robot_Render" style="width:550px;height:300px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-2 Redesigned Leg with out of plane joints</em></u></figcaption>
    
    * <p style="text-align: justify;"><b>Mechanical Design</b><br>The figure above shows the new design of the leg used. This was done to provide the robot with a higher order of workspace, while also maintaining the capabilities of the current design. Furthermore, legged robots have the potential to significantly reduce the environmental impact of transportation. Compared to traditional wheeled vehicles, legged robots have a lower ground pressure, which means they can traverse delicate ecosystems without causing damage. They also consume less energy, making them more environmentally friendly than traditional vehicles. In the future, legged robots may be used for last-mile delivery, reducing the need for carbon-emitting trucks and vans. Overall, legged robots have a wide range of potential applications and offer a flexible and adaptable platform for various tasks. Their ability to navigate complex environments, interact with humans, and reduce environmental impact make them an important area of research and development.
    
    * <p style="text-align: justify;">The kinematic analysis and the mathematical calculations behind the robot can be found on [[Notion]](https://common-bathtub-ada.notion.site/Quadrupled-Project-5025fb31b81147499df83d656a3e7b42).</p>

    <div style="text-align:center">
    <video src="/images/Quad_project_simulation_1.mp4" controls="controls" style="max-width: 750px;"></video>
    </div>
    <figcaption style="text-align: center;"><u><em>Simulation-1 Standstill movement capabilities of the Robot</em></u></figcaption>
---

    <div style="text-align:center">
    <video src="/images/Quad_project_simulation_2.mp4" controls="controls" style="max-width: 750px;"></video>
    </div>
    <figcaption style="text-align: center;"><u><em>Simulation-2 Motion capabilities of the Robot</em></u></figcaption>

    * <p style="text-align: justify;"><b>Results</b><br>A simulation study has been demonstrated to verify the efficacy of the system. Further, a functional prototype has been developed as a proof of concept to test the system in the real world. The results above show that the robot can effectively adjust its size depending on need, without affecting mobility and structural integrity of the chassis. Several iterations were required to attain a chassis that was performing well. Earlier iterations of the functional prototype suffered from bending of the chassis and loss of traction to the wheels. Having identified the problem areas, necessary modifications were made to the chassis to ensure compliance.  Future work will involve integrating SLAM using LIDAR, for more efficient and systematic cleaning.</p>