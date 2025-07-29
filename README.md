#  FrozenLake Navigation using Reinforcement and Machine Learning

This project presents a data-driven strategy to navigate the FrozenLake-v1 environment using a combination of **Reinforcement Learning (RL)** and **Machine Learning (ML)** techniques.

>  *Mini Project Report - DSC4173: Machine Learning | Author: H.S.B. Deshapriya (S/19/350)*

---

##  Overview

The **FrozenLake-v1** environment is a slippery 4×4 grid where the agent must reach a goal while avoiding holes. Due to its stochastic nature, it poses a challenge for traditional RL agents. This project leverages:
- Data collection through random exploration
- Importance-based scoring of actions
- Supervised ML (Random Forest) to guide decisions
- Exploration–exploitation strategy using ε-greedy approach

---

##  Objectives

- Simulate FrozenLake-v1 environment
- Collect 10,000 episodes of random exploration data
- Calculate **action importance** using reward and proximity to goal
- Train a **Random Forest Regressor** to predict action importance
- Build a **guided agent** using predictions
- Implement an **improved agent** using ε-greedy exploration
- Compare performances of random, guided, and improved agents

---

##  Methodology

###  Environment Setup
- Environment: `FrozenLake-v1` (`4x4`, `is_slippery=True`)
- 16 discrete states (0 to 15), 4 possible actions (Left, Down, Right, Up)

###  Data Collection
- Random agent ran for 10,000 episodes
- Collected: state, action, reward, goal proximity (via Manhattan distance), etc.

###  Action Importance Score
Custom score encouraging actions closer to the goal or producing a reward:
        importance = (reward + (1 / (goal_proximity + ε)))


###  Machine Learning Model
- **Model**: `RandomForestRegressor` from scikit-learn
- **Input Features**: state, action, goal proximity
- **Output**: importance score

###  Guided Agent
- At each step, predicts importance scores for all actions
- Chooses action with highest predicted importance

###  Improved Agent with ε-Greedy
- ε = 0.1: 10% chance to explore (random action), 90% to exploit model prediction

---

##  Results & Findings

- **Random Policy**: ~1.45% success rate (very poor)
- **Guided Agent**: Significant improvement by learning useful patterns
- **Improved Agent**: Even better performance with ε-greedy exploration

###  Key Takeaways

- ML models like Random Forest can enhance decision-making in RL environments
- Action importance allows leveraging unsuccessful but informative episodes
- ε-greedy helps avoid local optima and improves learning

---





