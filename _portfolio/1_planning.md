---
title: "Quadruped Path Planner for Dynamic Environments"
excerpt: "Implemented a global path planner for a quadruped robot moving in dynamic environments. <br/><img src='/images/planning_path.png' style='width:150;height:100;'>"
collection: portfolio
---

[[GitHub]](https://github.com/RedTorus/quad-sdk-PlanningProject)[[Report]](http://sahiltchaudhary.github.io/files/Planning_Final_Report.pdf)

* <b>Tech Stack:</b> C++, ROS, Git, Gazebo
* <b> Summary </b>
    -  <p style="text-align: justify;">Demonstrated a global path planner for a quadruped robot using C++ and ROS, that accounts for dynamic obstacles and the z-height of the robot.</p>
    -  <p style="text-align: justify;">Executed a Lazy-PRM with D* planner with kinodynamic constraints and state space comprising x, y, z, yaw, and velocity components.</p>
    -  <p style="text-align: justify;">Benchmarked against an existing KD-RRT-Connect planner, demonstrating that the Lazy PRM-D* approach generated lower cost paths with comparable planning times.</p>
    -  <p style="text-align: justify;">My role: Implemented the z-height controller, and helped implement PRM-D*.</p>

* <b>In-Depth</b>
    *  <p style="text-align: justify;"><b>Introduction</b><br>This project was completed as part of the Planning and Decision Making (16-782) course at CMU. The aim of this project was to implement a Lazy PRM-D* global path planner, and compare its performance with an existing KD-RRT-Connect planner. The existing planner struggled with dynamic environments and complex terrrains. To overcome these drawbacks, we implemented Lazy PRM-D* and compared it with the same. Experimental validation showed that our planner generated lower cost paths while maintaining comparable planning times with the existing RRT-Connect approach.</p>

    <div style="text-align:center">
    <img src="/images/spirit.png" alt="spirit" style="width:500;height:300px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-1 Project Spirit Quadruped Robot</em></u></figcaption>
  
    * <p style="text-align: justify;"><b>Motivation</b><br>The existing planner, although fast, struggled with dynamic environments because of having to replan repeatedly. Furthermore, it assumed the z-height of the robot to be constant based off a terrain map. As a result the planner did not account for the z-dimension, and hence performed suboptimally where taking z into consideration was necessary, like going under a table. To overcome these drawbacks, we implemented Lazy PRM-D* while considering z as part of the state.</p>

    * <p style="text-align: justify;"><b>Lazy PRM with D* and Kinodynamic constraints</b><br>The state vector of the planner is &lt;x, y, z, v<sub>x</sub>, v<sub>y</sub>, v<sub>z</sub>&gt;. This section will give a brief overview of our planner.</p>

        * <p style="text-align: justify;"><b>PRM Overview</b><br>The PRM (Probabilistic Roadmap) serves as a representation of feasible motion paths through the environment. With a generated map and a given start and goal state, a search-based planner like A* can be used in conjunction to retrieve a path, if it exists. However, the PRM generation process is computationally expensive and hence performed offline. The advantage lies in the fact that once generated, the graph can be used to find paths to any combination of start and goal states. Typically, while generating the PRM, sampled nodes that lie in obstacles are rejected, ensuring that the graph represents only collision-free paths. However, this approach is only effective in static environments, as any changes in the environment will necessitate regeneration of the PRM.</p>

        * <p style="text-align: justify;">To address this limitation, a modification to PRM for dynamic environments is called Lazy PRM. Unlike traditional PRM, this approach does not reject nodes that lie within obstacles. Instead, it retains them in the graph, but with an infinite cost. This modification ensures that the roadmap remains valid even if the environment changes. When an obstacle moves or disappears, the cost of the corresponding nodes can be dynamically updated rather than requiring a complete regeneration of the graph. This small modification enables PRMs to be used in dynamic environments.</p> 

        * <p style="text-align: justify;"><b>A* Search Overview</b><br>The cost updation and re-planning is handled by the A* search, or for a faster and more optimal re-planning algorithm, D*. D* is a modification on A* that reuses and leverages information gained during previous searches, hence making the search faster, as replanning is not done from scratch, unlike in A*. Furthermore, since it is A*, the path obtained is optimal, given the map. As long as we can create a very dense PRM, which is feasible since it's done offline, A* can find the most optimal path, unlike RRT-Connect. If speed is a priority, weighted-A* can be used instead.<p> 

        <div style="text-align:center">
        <img src="/images/planning_path.png" alt="planner_paths" style="width:300;height:600;">
        </div>
        <figcaption style="text-align: center;"><u><em>Fig-2 Visualization of the path generated by the planner</em></u></figcaption>

        * <p style="text-align: justify;"><b>Kinodynamic Constraints</b><br>Additionally, the existing RRT-Connect implementation (and hence also ours) incorporates kinodynamic constraints into its re-planning framework. These constraints ensure that the transitions between states adhere to the physical and dynamic limitations of the system. Metrics such as stance time, accelerations, and ground reaction forces (GRFs) are calculated to validate the feasibility of motion between states. This integration guarantees that the paths generated during re-planning are not only efficient but also physically realizable, which is critical for applications such as quadruped locomotion or other systems requiring adherence to dynamic constraints.<p> 

        * <p style="text-align: justify;"><b>Planning in z</b><br>One of the main objectives was to add a third dimension, z (height), to the planner to enable height-aware navigation. However, instead of directly sampling z, which would significantly increase the state space size and planning complexity, a 'lazy' approach has been implemented to improve the planning speed. The way this is done is by first checking if the nominal z of the robot collides with obstacles for a given x and y location. If it clears the obstacle check, that is, no collision is detected, z is left unchanged. However, if it collides, the minimum z (the lowest height at which the robot can successfully walk) is checked against the obstacle. If it passes the check, the robot height is set to z minimum, effectively allowing crouching. But if even that fails, it means that the state is invalid, as the robot cannot fit through it despite crouching.</p>

        <div style="text-align:center">
        <img src="/images/z_demo.png" alt="z_demo" style="width:300;height:600;">
        </div>
        <figcaption style="text-align: center;"><u><em>Fig-3 Traversing under a table: Planning in z-dimension</em></u></figcaption>

* <b>Results</b>
    <p>We compared the results of planning time and other metrics between the existing RRT-Connect and our PRM-A* and its variants.</p>

    <div style="text-align:center">
    <img src="/images/planning_times.png" alt="planning_times" style="width:400px;height:100px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Table-1 Comparison of the different approaches</em></u></figcaption>

    <p>Overall, our results indicate that the weighted-A* approach is faster than RRT-Connect, but is suboptimal. If path cost and quality are a priority, then A* should be used, which will be slower than RRT-Connect. Hence, to create a balance between planning time and path cost, D* is the right choice.</p>