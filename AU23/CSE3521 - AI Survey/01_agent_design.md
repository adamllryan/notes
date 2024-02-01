## Artificial Intelligence

In terms of this course, the definition of AI can be left as *the science of making machines that: (think, act)$\times$(like people, rationally)*. 

## Turing Test

The **Turing Test** is old, outdated, and does not work (it's popular though). To conduct the test, you take a human judge and an "unknown entity" and put them in two different rooms. The rooms have two chat terminals, and both must converse for 5 minutes. The AI passes if the judge thinks it is a human. 

The test is flawed. It doesn't show understanding, thinking, ability to learn, interaction with the world, sensory input processing, knowledge, or much else. 

## Rationality

We define **rationality** to be exactly this:
- Achieve predefined goals to the highest extent
- No evaluation on thought process, only results/decisions
- Evaluate on utility of outcome
- Maximize expected utility  
Rational behavior is essentially doing the "right" thing, without consideration of the thought process behind it. 

## Areas of Focus

**Speech technologies** refer to the subjects of automatic speech recognition, text-to-speech synthesis, and dialog systems. **Language processing technologies** refer to the topics of question answering, machine translation, web search, and text classification.  
These is expanded upon in the [[12_modern_neural_networks#Text and Language|text and language]] section. 

**Computer vision** focuses on object/facial recognition, scene segmentation, and image classification. More can be found [[12_modern_neural_networks#Computer Vision|here]].  
**Robotics** are more mechanical engineering, but are much harder because we need to incorporate more rigorous testing. We won't focus on this in this class. 

We can also use AI for **logic** applications, like theorem provers, NASA fault diagnoses, question answering, deduction systems, constraint satisfaction, and satisfiability solvers. Similarly, we can have AI play games. 

**Decision making** is also important, covering the sections of scheduling, route planning, medical diagnosis, web search engines, spam classifiers, automated help desks, fraud detection, product recommendations, and more. 

## Agent Design

The main focus of AI is regarding *agents* in an *environment*. An **agent** is an entity that can perceive its environment through sensors and act in the environment through effectors. The **environment** is our problem setting. 

A **percept** is an agent's perceptual inputs at a given instant, and a **percept sequence** is the complete history of everything that an agent has perceived. 

We use **PEAS** to flesh out our understanding of a setting. Peas is defined as:  
Performance - measuring the agent's success.  
Environment - what populates the problem's world?  
Actuators - what can the agent act with?  
Sensors - how can the agent perceive the world?

A **rational agent** must act to maximize its expected performance given the current percept or state. Note that rationality is NOT omniscience, because there is always uncertainty in the environment. 

## Agent Types

A **reflex agent** (IS) chooses actions based on *current* percept and memory.  
Alternatively, a **planning agent** (WOULD) chooses actions based on a set of *hypothesized* consequences of all possible actions. It needs a model of how the world changes in response to actions it takes. 

A **goal-based agent** chooses actions (in a sequence) in order to get from the current state to its goals.  
We'll talk about [[learing agents]] later. There are also utility-based agents and logical agents. 

## Environment Types

An environment can be fully or partially observable. **Fully** observable means that the agent can see the complete state, and **partially** observable means there exists noise, inaccuracy, or incomplete sensors. 

There may also be single or multiple agents. **Single** agent means there is only one agent, and **multi**-agent means that the task has multiple agents, each with their own performance measure. It may be competitive or cooperative, or nothing at all sometimes. 

Environments may be deterministic or stochastic. To be **deterministic** means that the next world state is only determined by current state and agent action, whereas **stochasticism** means that there can be a degree of randomness involved. For example, an environment is stochastic if the same action with the same state can result in two different states. Not injective!!!

The next pair is episodic and sequential environments. **Episodic** refers to each state being independent of other states. **Sequential** means that every state can affect a later one (Pacman moving and eating pellets). 

Next, we have static and dynamic. **Static** environments do not change while the agent is thinking. **Dynamic** means that the environment is changing as time passes. 

Finally, environments can be **discreet** or **continuous**. To be **discreet** just means states and actions must be distinct and to be **continuous** means that they can take on continuous values. This is like tic-tac-toe vs. driving. 

When approaching a problem, certain environments require decisions. Here are the areas of focus:
- Static: go for high accuracy
- Dynamic: trade accuracy or some utility for speed
- Episodic: use a reflex agent
- Sequential: use a goal or planning agent
- Stochastic: go for robustness to uncertainty and failure
- Deterministic: go for efficiency and exactness