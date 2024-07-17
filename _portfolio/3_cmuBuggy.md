---
title: "CMU Buggy"
excerpt: "Implemented various control techniques on a racecar simulation. <br/><img src='/images/buggy_plots.png'>"
collection: portfolio
---

[[GitHub]](https://github.com/SahilTChaudhary/Modern-Control-Theory)[[Report]](http://sahiltchaudhary.github.io/files/CMUBuggy.pdf)

* <b>Tech Stack:</b> Python, Webots
* <b> Summary </b>
    -  <p style="text-align: justify;">Implemented and tuned a PID controller for a Tesla Model 3, using Webots simulator.</p>
    -  <p style="text-align: justify;">Used Pole Placement to generate an optimal Gain matrix, and analyzed the controllability and stability of the system.</p>
    -  <p style="text-align: justify;">Developed an LQR controller for the same system, as a comparison to the PID controller, and performed EKF-SLAM.</p>

* <b>In-Depth</b>
    *  <p style="text-align: justify;"><b>Introduction</b><br>This project was completed as part of the Modern Control Theory (24-677) course at CMU. Various control techniques and algorithms were implemented by applying them in a simulation of the CMU tradition of Buggy race. Various algorithms like PID with Pole Placement, LQR and EKF SLAM were applied by ensuring the desired performance criteria.</p>
  
    * <p style="text-align: justify;"><b>Motivation</b><br>The aim was to learn various control techniques and algorithms by applying them in a simulation of the CMU tradition of Buggy race. This would also help students participating in the Buggy race that is held annualy, as the track and data match the actual race.</p>

    * <p style="text-align: justify;"><b>Methodology</b><br> For the puposes of the sim, we modeled a Tesla Model 3 using the Kinematic Bicycle Model. The first step was to start with the simplest controller - the PID (Proportional Integral Derivative) controller. The next step was to tune the Gains of the lateral controller by using Pole Placement. Next, we delved into the realm of Optimal Control and implemented the LQR (Linear Quadratic Regulator) and compared it with the PID implementation. Finally, since in all the methods above we assumed that we had perfect measurements of the state, we implemented EKF-SLAM (Extended Kalman Filter SLAM) to account for uncertainty in the state estimate.</p>

* <b>Results</b>
    <p>With PID, the time taken to complete the track was 243.776 s.</p>

    <div style="text-align:center">
    <img src="/images/buggy_pid_plots.png" alt="buggy_pid_plots" style="width:500px;height:400px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-1 Performance plots of the PID Controller</em></u></figcaption>


    <p>With LQR, the time taken to complete the track was 152.96 s. Hence, it was significantly faster than the PID.</p>

    <div style="text-align:center">
    <img src="/images/buggy_lqr_plots.png" alt="buggy_lqr_plots" style="width:500px;height:400px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-2 Performance plots of the LQR Controller</em></u></figcaption>

    <p>EKF-SLAM was integrated with the LQR controller implemented previously, to get a track completion time of 158.368 s.</p>

    <div style="text-align:center">
    <img src="/images/buggy_ekf_plots.png" alt="buggy_ekf_plots" style="width:500px;height:400px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-3 Performance plots with EKF-SLAM</em></u></figcaption>