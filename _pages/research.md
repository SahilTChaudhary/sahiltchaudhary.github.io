---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
redirect_from:
  - /research
---

{% include base_path %}

<figure>
  <img src="/images/robotics_institute.png" alt="RI Logo" style="width:200px;height:200px;">
  </figure>
* <h2>Biorobotics Lab, Pittsburgh, PA</h2>
  <h3>Graduate Research Assistant (August 2023 - Present)</h3>
  * <b>Core Skills:</b> C++, Python, ROS, Git, Linux, Gazebo, SolidWorks
  * <h3>About the project as a whole</h3>
    * This project comes under the domain of **Field Robotics**. The mission of the project is to develop a **fully autonomous system of heterogeneous robots** from the ground up, for search and rescue applications. 
      * As the number of robots grow, it becomes difficult for a single user to keep track and manage all of them. Hence, the aim is to make the system such that increasing the number of robots does not increase the burden on the user.
      * The way to achieve that is to make the **robots fully autonomous and decentralized**.

    In this project, the bulk of my work and contributions are as follows:

  * <h3>Comms-Aware Planning</h3>
    * Developed a **novel algorithm to maintain communication fidelity among robots** in a convoy, by extending off an existing work.
      * The aim is to ensure that all robots in the field, irrespective of whether they are in a convoy or not, must be able to communicate with the Basestation, i.e., the user.
      * Each robot communicates via proprietary radios, and each radio has the capability to act as a **comms relay**.
      * <h3>The existing approach</h3>
        * **Peeling off** refers to a robot in a convoy exiting the convoy and acting as a stationary comms relay for the other robots.
        * The approach involves mapping out all the possible connections between all nodes (in this case, the radios) and **generating a graph**.
        * Then using that graph, the algorithm **generates a Max-Min Spanning Tree** such that, for each radio, out of all possible connections to the **central node, i.e., the root of the tree** (which is the Basestation), the connection route chosen is such that the **strongest of the weakest links is chosen**.
        * Hence, the **algorithm essentially gives the best possible connection**. This connection is then monitored to track which robot goes out of comms, and then the appropriate behaviour is chosen.
    * Formulated a **modified Max-Min Spanning Tree to optimize the distance the robots travel before peeling off**.
      * My modification to the above algorithm involves **optimizing the connection to multiple nodes of interest, i.e., multiple central nodes**.
      * The assumption is that connecting to any central node ensures connection with the basestation. **Hence, for each robot in the network, the algorithm finds the best route to the nearest central node**.
      * Furthermore, if a central node (which is a critical node to maintain comms) is moved or drops out, all the central nodes dependent on it are **recursively rewired**.
      * If after the rewiring process a robot is left stranded out-of-comms, an **intelligent back-to-comms behaviour is autonomously triggered**.
    * Validated the algorithm through successful deployment on robots using proprietary radios.
      * I created a test-bed to simulate radio connectivity in simulation.
      * **Extensive simulation testing** in Gazebo has been conducted.
      * **Field testing on physical robots has also been conducted, demonstrating the feasibility of the algorithm**.

    <div style="text-align:center">
    <img src="/images/maxmin_tree.png" alt="maxmintree" style="width:800px;height:300px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Max-Min Tree generation from Graph</em></u></figcaption>
  
    <div style="text-align:center">
    <video src="/images/Multi_convoy_comms_peeloff.mp4" controls="controls" style="max-width: 750px;"></video>
    </div>
    <figcaption style="text-align: center;"><u><em>Multi-Convoy Comms-Peeloff demonstration in simulation</em></u></figcaption>

  * <h3>Convoy</h3>
    * Developed a **Decentralized Heterogeneous Convoy framework** comprising RC Cars and Quadruped Robots.
      * Each robot has its own autonomy for navigation. Furthermore, each robot makes decisions relates to convoy order, waypoints etc. individually. This ensures consistency among robots, and hence enables a **decentralized convoy structure**.
      * The **Heterogeneous Convoy** framework incorporates RC cars and Quadruped robots such that the ordering, waypoints and leader-follower mechanisms do not slow the convoy down, as quadrupeds are significantly slower than the RC cars. Alternatively, there is an option to ensure that the quadruped stays with the convoy, resulting in the convoy slowing down significantly.
    
      <div style="text-align:center">
      <video src="/images/hetero_convoy.mp4" controls="controls" style="max-width: 750px;"></video>
      </div>
      <figcaption style="text-align: center;"><u><em>Heterogeneous Convoy demonstration</em></u></figcaption>

    * **Designed an algorithm enabling rendezvous at intersections and coordinated return as a convoy**.
      * The algorithm finds the nearest common intersection (individually on each robot to ensure a **decentralized algorithm**) for all robots in a convoy based off of Backtracking waypoints, and then enables the robots to then move to a desired location as a convoy.
    
      <div style="text-align:center">
      <video src="/images/rendezvous.mp4" controls="controls" style="max-width: 750px;"></video>
      </div>
      <figcaption style="text-align: center;"><u><em>Rendezvous feature demonstration</em></u></figcaption>

  * <h3>Payload Redesign</h3>
    * Redesigned the payload of RC Cars and Quadruped Robots that are part of a heterogenous convoy to improve performance and **serviceability**.
      * The goal was to make the electronics more **accessible for each replacement**, and to make the **I/O ports easily reachable**.
    * **Made the payload 10% lighter, more compact, and easily accessible** to ensure serviceability by using Delrin and making the payload modular.
      * Made the payload using Delrin (instead of sheet metal like the previous payload) to reduce weight.
    * **Reduced Centre of Gravity by 15%** by decreasing the height of the payload, hence improving cornering performance of the RC cars.
      * Placed the payload closer to the chassis, reducing the overall height and hence the COG.
    * Incorporated sensors, including LiDAR, IMU, and two cameras, along with the on-board computer, motor controller, and circuit boards while ensuring optimal field of view and sensor placement.
      * LiDAR and cameras placed such that they have optimal **Field-of-View**.
      * LiDAR and IMU placed closed by and with similar orientation to ease **extrinsics calibration**.


    <div style="text-align:center">
    <img src="/images/mmpug_payload.png" alt="payload" style="width:500px;height:400px;">
    </div>
    <figcaption style="text-align: center;"><u><em>The payload</em></u></figcaption>

    <div style="text-align:center">
    <img src="/images/mmpug_payload_with_rollcage.png" alt="payload_with_rollcage" style="width:500px;height:400px;">
    </div>
    <figcaption style="text-align: center;"><u><em>The payload with Rollcage</em></u></figcaption>
---