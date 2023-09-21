>[!INFO] Stuff on test
> - Covers up to adversarial search
> - No coding or pseudocoding problems, but maybe reading code problems
> - Will cover cost/benefits of graph tree
> - This sheet must fit on one page 8.5x11 single-sided. 
# Intro Content

AI has 4 goals:

|  | Humanlike | Rationality |  
| -------- | -------- | -------- |  
| Think | Think like people | Think rationally |  
| Act | Act like people | Act rationally |

> [!INFO] Rational means the following:
> - maximize achieving pre-defined goals
> - only consider decisions, not the thought process behind them
> - goals expressed in terms of utility of outcomes
> - maximizing your expected utility

*Turing Test*: Outdated test to determine if AI is successful. A human judge converses with unknown entity (person or an AI) for 5 minutes and if it can fool the judge into thinking it's a human, it passes.  

*Agent Metrics*:
Performance (agent success), Environment (environment variables), Actuators (agent abilities), Sensors (agent perception)
`Rational` means to behave in a very specific way:

*AI Types*: Processing/NLP, Speech recognition, TTS, dialog, computer vision, recognition, scene segmentation, image classification
*Agent Types*: Reflex, planning, goal-based, learning, utility, logical agents
#### Reflex Agent
Choose action based on current percept/memory. No consideration of future consequences. 
#### Planning Agent
Plans ahead and considers future states. 
#### Goal
## Environment Types
*Fully Observable*: Agent can see everything. 
*Partially Observable*: Agent deals with noise, inaccuracy, or incomplete sensors. 
*Single Agent*: Agent plays itself. 
*Multi Agent*: Involves multiple agents. 
*Static*: The world does not change while the agent is thinking. Decision time does not matter!
*Dynamic*: The world is changing while the agent is thinking. Decision time matters!
*Discrete*: Possible states are distinct and/or the world changes discretely. Think integers. 
*Continuous*: Possible states take continuous values. Think floats. 
*Deterministic*: The next state is fully determined by current state and agent action. If sent back to the same state, you can repeat this 100% of the time. 
*Stochastic*: The next state has some element of randomness. There is some uncertainty. 
*Episodic*: Past states are independent of previous ones. 
*Sequential*: States affect later ones

# Uninformed Search
## Search Problem
*Search Problem*: Contains the following. 
*State Space*: A list of every possible state. 
*Successor Function*: Returns all successor states, along with actions and costs. 
*Start State, Goal Test*: The first state the agent starts with, and a function that checks if state is goal state. 
*Solution*: Sequence of actions which transforms the start state to a goal state. 

