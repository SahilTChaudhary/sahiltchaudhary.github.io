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

<figure>
  <img src="/images/sbpl_logo.png" alt="SBPL Logo" style="width:250px;height:100px;">
</figure>
* <h2>Search-Based Planning Lab, Pittsburgh, PA</h2>
  <!-- <h3>Intern (May 2025 - Present)</h3> -->
  * <b>Core Skills:</b> Isaac Lab, Reinforcement Learning, Python, Git, Linux
  * <h3>Blind Manipulation</h3>
    * The aim of this project is to enable **robotic manipulation in unknown environments using contact-based observations**. This work aims to bypass assumptions regarding the world model and representation by directly mapping contact observations to actions by using Reinforcement Learning.
    * The project can be divided into the following subtasks:
      * Train an RL policy to reach the goal in an unknown environment with obstacles and only contact sensors.
      * Having reached the goal, train a policy for manipulating the target, e.g., inserting a peg in a hole, turning on a switch or valve etc. The goal is to train a 'meta-RL' policy to generalize across tasks.
      * Combine the policies into one hierarchical system.
    * My contribution is the entire **last-mile manipulation** policy, i.e., manipulating objects having reached their vicinity.
    * Currently, I have setup individual tasks in Isaac Lab, and trained baseline policies for the same, achieving **94% success rate**.

  <div style="text-align:center">
  <video src="/images/peg_insertion.webm" controls="peg_in_hole" style="max-width: 500px;"></video>
  </div>
  <figcaption style="text-align: center;"><u><em>Policy trained for inserting a peg in a hole</em></u></figcaption>

  <div style="text-align:center">
  <video src="/images/switch_manipulation.webm" controls="switch_manipulation" style="max-width: 500px;"></video>
  </div>
  <figcaption style="text-align: center;"><u><em>Policy trained for turning on a switch</em></u></figcaption>

<figure>
  <img src="/images/biorobotics_logo.png" alt="Biorobotics Logo" style="width:200px;height:200px;">
</figure>
* <h2>Biorobotics Lab, Pittsburgh, PA</h2>
  <h3>Graduate Research Assistant (August 2023 - Present)</h3>
  * <b>Core Skills:</b> C++, Python, ROS, Git, Linux, Gazebo, SolidWorks
  * <h3>The MMPUG Project</h3>
    * This project comes under the domain of **Field Robotics**. The mission of the project is to develop a **fully autonomous system of heterogeneous robots** from the ground up, for search and rescue applications. 
    * As the number of robots grow, it becomes difficult for a single user to keep track and manage all of them. Hence, the aim is to make the system such that increasing the number of robots does not increase the burden on the user.
    * The way to achieve that is to make the **robots fully autonomous and decentralized**.

    In this project, the bulk of my work and contributions are as follows:

  * <h3>Comms-Aware Planning and MANET framework</h3>
    * Spearheaded the development of a **MANET framework** using DDS and ROS to ensure communication fidelity in heterogeneous robot convoys, perform network topology repair and recovery behaviors, and enforce a communication boundary. Submitted a [paper](http://sahiltchaudhary.github.io/files/GVSETS25_CommsAwarePlanning_compressed.pdf) to GVSETS 2025. The various features and behaviors of this framework are as follows:

    * <h3>Network Construction and Comms Peeloff</h3>
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
      <video src="/images/Comms_Peeloff.mp4" controls="commsPeeloff" style="max-width: 750px;"></video>
      </div>
      <figcaption style="text-align: center;"><u><em>Comms Peel Off hardware demonstration</em></u></figcaption>
    
      <div style="text-align:center">
      <video src="/images/Multi_convoy_comms_peeloff.mp4" controls="commsPeeloff_sim" style="max-width: 750px;"></video>
      </div>
      <figcaption style="text-align: center;"><u><em>Multi-Convoy Comms-Peeloff demonstration in simulation</em></u></figcaption>
    
    * <h3>Communication Recovery</h3>
      * This behavior handles scenarios wherein robots go out of comms. It is a fully **decentralized** algorithm that sequentially explores all known locations where Central Nodes existed or exist, till comms is regained.
      * Uses a **Global Planner** based on A* to find paths.
      * Guarantees comms recovery as long as there is a path, as the robot will keep exploring till it reaches the Basestation.

      <div style="text-align:center">
      <img src="/images/CommsRecovery.png" alt="CommsRecovery" style="width:800px;height:300px;">
      </div>
      <figcaption style="text-align: center;"><u><em>Communication Recovery algorithm</em></u></figcaption>

      <!-- <div style="text-align:center">
      <video src="/images/BackToComms_demo_sim.mp4" controls="commsRecovery" style="max-width: 750px;"></video>
      </div>
      <figcaption style="text-align: center;"><u><em>Back-To-Comms behavior for Comms Recovery</em></u></figcaption> -->

      <div style="text-align:center">
      <video src="/images/Comms_Recovery_final.mp4" controls="commsRecovery" style="max-width: 750px;"></video>
      </div>
      <figcaption style="text-align: center;"><u><em>Communication Recovery hardware demonstration</em></u></figcaption>


    * <h3>Communication Boundary</h3>
      * This feature acts like an invisible wall at the perimeter of the network topology. It prevents any robot from crossing that boundary, effectively ensuring that it stays within comms.
      * The boundary itself varies for each robot, based on the network topology and nearest Central Node.

      <div style="text-align:center">
      <video src="/images/Comms_Boundary.mp4" controls="commsBoundary" style="max-width: 750px;"></video>
      </div>
      <figcaption style="text-align: center;"><u><em>Enforcing the Comms Boundary</em></u></figcaption>

    * <h3>Network Topology Optimization based on an Inverse Kinematics approach</h3>
      * The Central Nodes and the signal strengths between them are modeled as links of a **serial manipulator**.
      * Given a desired location for a robot, an **optimization problem** is solved for the locations of the Central Nodes. This enables the Central Nodes to **dynamically adapt the comms topology** based on need.

  * <h3>Convoy</h3>
    * Developed a **Decentralized Heterogeneous Convoy framework** comprising RC Cars and Quadruped Robots (like Boston Dynamics' Spot).
      * Each robot has its own autonomy for navigation. Furthermore, each robot makes decisions relates to convoy order, waypoints etc. individually. This ensures consistency among robots, and hence enables a **decentralized convoy structure**.
      * The **Heterogeneous Convoy** framework incorporates RC cars and Quadruped robots such that the ordering, waypoints and leader-follower mechanisms do not slow the convoy down, as quadrupeds are significantly slower than the RC cars. Alternatively, there is an option to ensure that the quadruped stays with the convoy, resulting in the convoy slowing down significantly.
    
      <div style="text-align:center">
      <video src="/images/hetero_convoy.mp4" controls="heteroConvoy" style="max-width: 750px;"></video>
      </div>
      <figcaption style="text-align: center;"><u><em>Heterogeneous Convoy demonstration</em></u></figcaption>

    * **Designed an algorithm enabling rendezvous at intersections and coordinated return as a convoy**.
      * The algorithm finds the nearest common intersection (individually on each robot to ensure a **decentralized algorithm**) for all robots in a convoy based off of Backtracking waypoints, and then enables the robots to then move to a desired location as a convoy. This feature is a part of the exploratory nature of the project.
    
      <div style="text-align:center">
      <video src="/images/rendezvous.mp4" controls="rendev" style="max-width: 750px;"></video>
      </div>
      <figcaption style="text-align: center;"><u><em>Rendezvous feature demonstration</em></u></figcaption>

  * <h3>Local Planner</h3>
    * Enhanced the operational efficiency of the **Local Planner by up to 29%**, through **waypoint optimization and trajectory smoothing**, reducing unnecessary deceleration between waypoints and improving overall robot speed and motion continuity

  * <h3>Payload Redesign</h3>
    * Redesigned the payload of RC Cars and Quadruped Robots that are part of a heterogenous convoy to improve performance and **serviceability**.
      * The goal was to make the electronics more **accessible for each replacement**, and to make the **I/O ports easily reachable**.
    * **Made the payload 7% lighter, more compact, and easily accessible** to ensure serviceability by using Delrin and making the payload modular.
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