---
title: "Compact Foldable Treadmill"
excerpt: "Designed and developed a Compact and Foldable Treadmill in SolidWorks. <br/><img src='/images/Treadmill.png'>"
collection: portfolio
---

[[GitHub]](https://github.com/SahilTChaudhary/Compact-Foldable-Treadmill.git)

* <b>Tech Stack:</b> SolidWorks, Ansys, GitHub
* <b> Summary </b>
    -  <p style="text-align: justify;">Developed a CAD model and designed the folding mechanism of the Treadmill using SolidWorks.</p>
    -  <p style="text-align: justify;">Conducted Static Structural Analysis and Rigid Body Dynamics study using Ansys to optimize the materials used.</p>

* <b>In-Depth</b>
    *  <p style="text-align: justify;"><b>Introduction</b><br>The idea behind the project was to design a compact and foldable treadmill which can easily be stored under the bed or inside a cupboard, hence eliminating the problem of space and transportation. The feasibility of the design was validated by performing analyses and simulation using Ansys. Furthermore, analyses were performed on two materials, namely Carbon Steel and Aluminium Alloy, to optimize the materials used.</p>

    <div style="text-align:center">
    <img src="/images/Treadmill.png" alt="Treadmill" style="width:600px;height:400px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-1 Rendered Image of the Treadmill</em></u></figcaption>

    <div style="text-align:center">
    <img src="/images/TreadmillFolded.png" alt="Treadmill_Folded" style="width:600px;height:400px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-2 Rendered Image of the Treadmill after folding</em></u></figcaption>
  
    * <p style="text-align: justify;"><b>Motivation</b><br>During the age of COVID’19, with the onset of social distancing and lockdowns, people had been restricted to their homes for months at a stretch. This had led to a sedentary lifestyle and a lack of daily exercise. It is proven that running and even walking is one of the most efficient methods of exercise. Unfortunately, most treadmills are very bulky, take up a lot of space, and are very difficult to transport from one place to another. Thus, this motivated us to design a Treadmill that is compact and can be folded to facilitate easy storage and transport.</p>
    
       
    * <p style="text-align: justify;"><b>Mechanical Design</b><br>The components of the Treadmill include standard Treadmill Bearings, 28 Steel Rollers, a plastic Handlebar, and the Base and Frames made of Aluminium. The Treadmill is a manual one, i.e., there are no motors. Hence, it is only for walking. An incline of 15° has been given to ease movement. The base is split into three parts - front, middle and rear. There are two pairs of hinge joints in the middle, to enable folding.</p>

    <div style="text-align:center">
    <img src="/images/ArmStressAnalysis_vonMises.png" controls="StressAnalysis" style="max-width: 750px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-3 Stress Analysis - Von Mises</em></u></figcaption>

    <div style="text-align:center">
    <img src="/images/ArmStressAnalysis_Displacement.png" controls="StressAnalysis" style="max-width: 750px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-4 Stress Analysis - Displacement</em></u></figcaption>

    * <p style="text-align: justify;"><b>Topology Optimization</b><br>Topology Optimization was done to reduce the material used. The criteria used were to minimise mass by 30%, and ensure that the displacement does not increase by more than 1.2 times. The forearm and the hand were optimized, as they were the largest and most promiment components of the arm, and were also the main load bearing parts of the arm. The total mass reduction was 17.35%.</p>

    <div style="text-align:center">
    <img src="/images/Forearm_Topo.png" controls="Topo" style="max-width: 750px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-5 The Forearm after Topology Optimization</em></u></figcaption>

    <div style="text-align:center">
    <img src="/images/Hand_Topo.png" controls="Topo" style="max-width: 750px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-6 The Hand after Topology Optimization</em></u></figcaption>

* <b>Results</b>
    <p>Topology Optimization was successfully used to reduce the material cost of the arm. However, considering that the arm has been 3-D Printed using ABS, it is relatively weak, and can only be utilized for manipulating light objects like soda cans, stationery etc. Strength can be improved by either changing the material, or changing the manufacturing method, both of which will increase cost.</p>