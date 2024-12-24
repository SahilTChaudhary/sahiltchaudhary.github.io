---
title: "Point-LiDAR Inertial Odometry"
excerpt: |
    Implemented Point-LIO from scratch to overcome the drawbacks of frame-based LiDAR processing.  
    ![Point-LIO](/images/point_lio_cover.png){:width='500px' height='250px'} 
collection: portfolio
---

[[GitHub]](https://github.com/taylorpool/point_lio)[[Report]](http://sahiltchaudhary.github.io/files/Point_LIO_Final.pdf)

* <b>Tech Stack:</b> C++, ROS, Git, GTSAM
* <b> Summary </b>
    -  <p style="text-align: justify;">Implemented the Point-LIO algorithm using C++ and GTSAM, addressing the limitations of scan-based LiDAR processing.</p>
    -  <p style="text-align: justify;">Modeled IMU saturation as part of the state vector within an Extended Kalman Filter (EKF) framework, improving state estimation during aggressive maneuvers.</p>
    -  <p style="text-align: justify;">Handled time synchronization between LiDAR and IMU data by using separate buffers and timestamped LiDAR points, identifying challenges in implementation.</p>
    -  <p style="text-align: justify;">My role: Implemented the EKF.</p>

* <b>In-Depth</b>
    *  <p style="text-align: justify;"><b>Introduction</b><br>This project was completed as part of the Robot Localization and Mapping (16-833) course at CMU. This project presents Point-LIO, a novel filtering based approach to LiDAR-Inertial Odometry. The algorithm treats inputs from Inertial Measurement Units (IMUs) and LiDAR sensors as proper measurement updates within an Extended Kalman Filter (EKF) framework. Our objective was to evaluate the performance of the Point-LIO system on data collected on ground vehicles navigating through long, narrow corridors. Given the necessity for real-time processing, we implemented the algorithm in C++. Furthermore, we enhanced the algorithm's accuracy further by incorporating an extension based on the Unscented Kalman Filter (UKF) - demonstrating the capability to estimate robot state during aggresive motion. </p>

    <div style="text-align:center">
    <img src="/images/point_lio_cover.png" alt="point_lio_cover" style="width:600px;height:300px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-1 Taken from the Point LIO paper</em></u></figcaption>
  
    * <p style="text-align: justify;"><b>Motivation</b><br>LiDAR is a sensor that samples at discrete points in time and returns the range and azimuth associated with the points in question. However, a common practice is to accumulate these points into a scan. Even though this aggregation aids in data processing, it introduces motion distortion, specifically when the LiDAR is in motion at high speeds. This distortion can compromise the accuracy of spatial measurements and pose challenges for navigation and mapping tasks. In addition to increasing lag, the low frame rate restricts the available bandwidth.</p>

        * <p>We take inspiration from Point-LIO, a framework that entirely circumvents the motion distortion problem because it processes each LiDAR point sequentially on its own. This sequential processing of points also enables an odometry rate in the range of kHz, whereas, in traditional scan-based methods, it is typically 10 Hz. This enables the LiDAR odometry rate to be even faster than the IMU odometry rate, which is around 100 Hz.</p>

    * <p style="text-align: justify;"><b>Methodology</b><br>This section gives a brief overview of the algorithm and approach used.</p>
    
        * <p style="text-align: justify;"><b>Point-based LiDAR processing</b><br>Our methodology involves the use of point-wise processing of LiDAR points by checking the plane correspondence of the given LiDAR point with its five nearest neighbors, as part of the measurement model. If the point does not lie in the plane, we add it to the map by assuming that it is a new point. This essentially encompasses the addition of new information to the map. If it lies in the plane, measurement update proceeds without any changes to the map. In order to enable fast insertion of points to the map as well as fast querying of the five nearest neighbors for the plane correspondence, we represent the points of the point cloud map using a variation of the KD-Tree known as the incremental KD-Tree. This tailored approach contributes to the robustness and overall effectiveness of our methodology.</p>

        * <p style="text-align: justify;"><b>Addressing IMU Saturation</b><br>Another significant issue that arises is that IMUs can become saturated in aggressive and fast motions, as the robot's angular velocity and linear acceleration might exceed the IMU's measuring range. This can yield the IMU to be useless during those time-steps. In order to overcome this, we use a stochastic process-augmented kinematic model, in which the IMU measurements, which are angular velocity and linear acceleration, are modeled as outputs of the system. This means that they are part of the state vector and are used in the update stage. Doing this enables us to estimate the angular velocity and linear acceleration as part of the state, and then correct the estimate using a filtering approach such as the Extended Kalman Filter (EKF) or the Unscented Kalman Filter (UKF). If during a certain maneuver or time-step the actual IMU reading becomes saturated, we just skip the measurements from those saturated channels, and use the current estimate of the angular velocity and linear acceleration from the propagate model during that time. This ensures that the system is more robust during aggressive and fast motion, as the system can continue to operate effectively and maintain functionality even when the IMU measurements are saturated. Thus, overall reliability and performance is enhanced.</p>

        <div style="text-align:center">
        <img src="/images/point_lio_algo.png" alt="pointLIO_algorithm" style="width:500;height:600px;">
        </div>
        <figcaption style="text-align: center;"><u><em>Fig-2 Point-LIO algorithm (taken from the Point-LIO paper)</em></u></figcaption>

* <p style="text-align: justify;"><b>Challenges</b><br>The major challenge was achieving the time syncing between LiDAR and IMU data. Unfortunately, due to the fact that LIDAR measurements arrive in a packet of 30,000 points every tenth of a second, their distribution across any given time window is non-uniform. The result is that we can no longer assume that all LIDAR measurements have been received prior to a given IMU measurement. And vice versa. We decided to overcome this issue by allocating individual buffers for both IMU and LIDAR points. When a IMU measurement was received, we processed all LIDAR points before the IMU measurement. Similarly, when a LIDAR point was received, we processed all IMU measurements prior to the time stamp associated with the LIDAR point. Unfortunately, this still resulted in negative time differences between the current state of the filter, and the time stamp associated with the current measurement being processed.</p>

* <b>Results</b>
    <p>The results for IMU dead reckoning and IMU data modeled as output of the system are shown in the figures below.</p>

    <div style="text-align:center">
    <img src="/images/pointlio_traj_plot.png" alt="pointLIO_traj_plot" style="width:600px;height:300px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-3 Trajectory and landmark visualization</em></u></figcaption>

    <div style="text-align:center">
    <img src="/images/pointlio_traj_plot-2.png" alt="pointLIO_traj_plot-2" style="width:600px;height:300px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-4 Trajectory and landmark visualization</em></u></figcaption>

    <p>We have presented our findings implementing Point-LIO: an algorithm for LiDAR-Inertial Odometry that seeks to replace scan registration with point-by-point registration. We implemented our approach in C++ from scratch with a significant amount of effort dedicated towards mapping, processing LiDAR points, and also forming the Extended and Unscented Kalman Filters on-manifold. We found that Point-LIO is unsuitable for real-time computation given the inherently sequential nature of the processing requirements. Furthermore, we found that the time synchronization between each individual LiDAR point and IMU measurement to be difficult to implement properly and wholly non-intuitive.</p>