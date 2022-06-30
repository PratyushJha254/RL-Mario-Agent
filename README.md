# RL-Mario-Agent
Training an RL Agent in Super Mario Bros environment for level 1 using OpenAI Gym and pyTorch.

For using the Super Mario game environment, we imported <code>gym_super_mario_bros</code>

https://pypi.org/project/gym-super-mario-bros/

<h3>Theory:</h3>
Reinforcement Learning involves training an agent to learn a good strategy through a process of exploration and exploitation.<br>
In this project, we have implemented Double Deep Q Learning to train our Agent.<br>
Deep Q Learning is used so that rapid changes in Q does not cause it to diverge. Hence, we use two nets to provide stability:<br>
<ol>
<li>The Q Network is updated regularly</li>
<li>The target network is an older version of the Q network updated occasionally.</li>
</ol>
However, it happens that the value of Q* gets overestimated. To solve this issue, Double Deep Q Learning is used. In Double Deep Q- Learning, we train two independent Q networks on disjoint subsets of experience. In this, the Q Network being trained is used to select the actions and the other Q Network is used to evaluate the actions and we keep alternating between the two.<br>

<h3>Modules/Libraries used:</h3>
The following modules/libraries have been imported:
<ul>
<li><code>torch</code>: For using tensors in our program which can be executed on GPU</li>
<li><code>torch.nn</code>: For Neural Networks</li>
<li><code>pickle</code>: For saving and loading files</li>
<li><code>matplotlib.pyplot</code>: For plotting Episodes trained vs Average Rewards Graph</li>
<li><code>numpy</code>: Python's library for working with arrays</li>
<li><code>cv2</code>: It is the module name for OpenCV-python</li>
</ul>

<h3>Hyper-parameters:</h3> 
The model has been trained for 10000 epochs with the following hyper-parameters:
<ul>
<li>Learning rate: <code>lr=0.00025</code></li>
<li>Discount Factor: <code>gamma=0.9</code></li>
<li>Exploration decay: <code>exploration_decay=0.99</code></li>
</ul>

<h3>Result</h3>
After training the model, the following graph is observed for Episodes Trained vs Average Rewards (per 500 episodes):
<picture>
  <source media="(prefers-color-scheme: light)" srcset="https://user-images.githubusercontent.com/108410048/176499258-0609ee71-69e0-4cdc-9d29-e9d4e022e0b5.jpeg">
</picture>

