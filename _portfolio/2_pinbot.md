---
title: "PinBot – Reinforcement Learning on a Pinball Machine"
excerpt: |
    Developed a reinforcement learning agent using Proximal Policy Optimization (PPO) to play the pinball game Total Nuclear Annihilation.  
    ![Total Nuclear Annihilation](/images/tna.png){:width='350px' height='200px'}
collection: portfolio
---

[[GitHub]](https://github.com/RichaaM/Pinbot)[[Report]](http://sahiltchaudhary.github.io/files/IRL_Final_Project_Report.pdf)

<i>September 2024 - Present</i>

* <b>Tech Stack:</b> Python, PyTorch, Unity, Git
* <b> Summary </b>
    -  <p style="text-align: justify;">Developed a reinforcement learning agent using Proximal Policy Optimization (PPO) to play the pinball game Total Nuclear Annihilation.</p>
    -  <p style="text-align: justify;">Trained the agent in a simulated environment using the Gymnasium framework, outperforming a randomized baseline agent by 67%.</p>
    -  <p style="text-align: justify;">Applying transfer learning to adapt the agent for a physical pinball machine (ongoing work).</p>
    -  <p style="text-align: justify;">My role: Helped setup the simulation framework, and also worked on implementing PPO.</p>

* <b>In-Depth</b>
    *  <p style="text-align: justify;"><b>Introduction</b><br>This project was completed as part of the Introduction to Robot Learning (16-831) course at CMU. The aim of this project was to apply reinforcement learning to play the classic arcade game of pinball. Two settings were considered - simulation and physical hardware. The performance of this agent was evaluated against human players.</p>

    <div style="text-align:center">
    <img src="/images/tna.png" alt="tna" style="width:500;height:300px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-1 The physical setup of the Pinball game of Total Nuclear Annihilation (TNA)</em></u></figcaption>
  
    * <p style="text-align: justify;"><b>Motivation</b><br>Reinforcement learning has been successfully applied to games like Go, Pong, and Dota 2. Games serve as ideal learning environments due to their defined boundaries, clear objectives, and opportunities for strategic decision making. Pinball is a classic arcade game in which a player uses two flippers to keep a ball on the playfield while attempting to hit various targets. Pinball is dynamic and requires highly reactive game play and control. The objective is to maximize the score of the game over the course of three balls (turns). This makes pinball an ideal candidate for training an RL agent, because the rewards and actions are very clearly defined.</p>

    * <p style="text-align: justify;"><b>Methodology</b><br>A digital version of TNA was sourced from the Visual Pinball X project, and was trained in a simulation environment using the Unity ML-Agents framework. After training in sim, the goal was to use the learned weights and implement transfer learning for the physical game, as this would speed up training drastically. The RL model used for the same was Proximal Policy Optimization (PPO).</p>

    * <p style="text-align: justify;"><b>PPO</b><br>The details of the training and model parameters are given below.</p>
    
        * <p style="text-align: justify;"><b>State Space</b><br>The state/observation space is continuous, and includes five state observations: a downsampled image of the playfield; the ball’s x and y position; and the ball’s x and y velocity.</p> 

        * <p style="text-align: justify;"><b>Action Space</b><br>The action space is discrete, and includes a vector of four discrete actions. The first action, idle, releases the flippers. The second and third actions activate the left and right flippers, respectively. The fourth action activates both flippers simultaneously. The agent samples one action 20 times per second.</p>
        
        * <p style="text-align: justify;"><b>Reward Function</b><br>The reward function is calculated by factoring in the score, play time, ball position, and ball loss. The score is the raw game score tracked by the machine, and it is the direct metric we seek to increase. A large penalty when a ball is lost to encourage the agent from prematurely ending a game. Furthermore, to encourage activity in the typically sparse environment, a small reward is added whenever the ball is on the field above the flippers, and detracted when at or below. This position-based reward is necessary, as a simple time-based award would reach a local minima where the agent simply traps the ball on the flipper. We sum these three components to get the reward function as shown in Fig-2.</p>

        <div style="text-align:center">
        <img src="/images/reward_formulation.png" alt="reward" style="width:300;height:200px;">
        </div>
        <figcaption style="text-align: center;"><u><em>Fig-2 Reward formulation</em></u></figcaption>

        * <p style="text-align: justify;"><b>Model Architecture</b><br>The current model is set relatively small, featuring 1 layer and 128 hidden units. Experimentation with more layers and units is needed, but a compact network was initially favored to prevent overfitting and reduce training time. A recurrent neural network (RNN) is used to give the agent a short-term memory of 35 frames (about 1.5 seconds). This allows the agent to better factor in the game dynamics, as a single game frame does not convey ball velocity or acceleration. For the game frame image, a simple encoder with two convolutional layers is used to transform frames to the agent’s space. The agent’s reward signals are influenced by a gamma γ of 0.99, encouraging the agent to care about long-term rewards. To update the model, an epsilon ϵ of 0.2 was used, which will keep the updates more stable, but slow the training process slightly. A learning rate of 3e − 4 is implemented, with a linear schedule.</p>

        <div style="text-align:center">
        <img src="/images/training_framework.png" alt="training" style="width:300;height:600;">
        </div>
        <figcaption style="text-align: center;"><u><em>Fig-3 An overview of the training framework</em></u></figcaption>

* <b>Results</b>
    <p>After training for 90k steps, the model was evaluated against three baselines: a human player, a randomized agent, and no agent. 10 cases were run for each scenario, with aggregated results below.</p>

    <div style="text-align:center">
    <img src="/images/training_results.png" alt="results" style="width:600px;height:130px;">
    </div>
    <figcaption style="text-align: center;"><u><em>Table-1 Performance of the trained agent compared against baselines</em></u></figcaption>

    <div style="text-align:center">
    <img src="/images/pinbot_violin.png" alt="results_plot" style="width:600px;height:500;">
    </div>
    <figcaption style="text-align: center;"><u><em>Fig-4 Violin plot of agent performance</em></u></figcaption>

    <div style="text-align:center">
    <video src="/images/Pinbot_Gameplay_Demo.mp4" controls="pinbot_demo" style="width:400px;height:480;"></video>
    </div>
    <figcaption style="text-align: center;"><u><em>The AI in action - The agent had locked two balls, and was one shot away from getting a multi-ball</em></u></figcaption>

    <p>In this work, we developed a reinforcement learning model to play pinball in simulation, showing heightened performance to random actions, and near-comparable performance to a human player.</p>