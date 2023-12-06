In terms of this course, AI can be 



# Introduction

## Definition

AI is difficult to define. We can narrow it down to 4 goals: think like people, think rationally, act like people, and act rationally.

### Turing Test

The most popular test of AI success is the Turing Test, that requires a human judge and unknown entity (either a person on an AI). They must converse for 5 minutes and if the entity can fool the judge into thinking that it is a human, it passes the test.

#### Issues with the Turing Test

This is kind of flawed though. It fails to address understanding, thinking, ability to learn, interaction with an unconstrained world, sensory input processing, having knowledge, and basically anything besides being able to trick a person into thinking it has thought.

## Rational Thinking

`Rational` means to behave in a very specific way:

- maximize achieving pre-defined goals
- only consider decisions, not the thought process behind them
- goals expressed in terms of utility of outcomes
- maximizing your expected utility

# Research areas related to AI

## Speech processing & Natural language processing

Speech technologies like Siri and Alexa. Encapsulates [automatic speech recognition] (ASR), [text-to-speech synthesis] (tts), and [dialog systems].

Language processing technologies like [question answering], [machine translation], [web search], and [text classification].

## Computer vision

Object and face recognition, scene segmentation, and image classification.

## Robotics

Part mechanical engineering, part AI. Much harder than simulations.
Technologies like vehicles, rescue, soccer, and lots of automation.
No mechanical aspects in this class!

## Logic

Logical systems like [theorem provers], [NASA fault diagnosis], [question answering].
Methods like [deduction systems], [constraint satisfaction], and [satisfiability solvers].

## Game playing

Plays games lol

## Decision making

Applied AI for automation like [scheduling], [route planning], [medical diagnosis], [web search engines], [spam classifiers], [automated help desks], [fraud detection], [product recommendations], etc.

# Start to Agent Design

## AI

Much of AI is concerned with AI acting in [environments]. An [environment] is the problem setting and the [agent] is an entity that _perceives_ its environment through _sensors_ and _acts_ upon that environment through _actuators_.

[Percept]: An agent's perceptual inputs at any given instant
[Percept Sequence]: Complete history of everything an agent has perceived

## PEAS

`P`erformance - measuring the agent's success
`E`nvironment - what populates the problem's world?
`A`ctuators - what can the agent act with?
`S`ensors - how can the agent perceive the world?

## Rational Agent

A [rational agent] always acts to maximize its expected performance measure given current percept/state
NOTE: Rationality /= omniscience!!! There is always uncertainty in the environment and the agent cannot know everything (sometimes)

## Types of agents

### Reflex agent

Chooses action based on current percept and maybe memory. Does not consider future consequences of actions!!!

NOTE: A state is a representation of the environment with only elements that are relevant to the problem. A percept is what the agent can perceive from the environment

### Planning agent

Asks what if and makes desicions based on presumed consequences of performed actions. Must have a model of how the world evolves in response to actions and must formulate a long-term goal.

### Goal-based agent

Chooses an action from current state in order to achieve a goal

### Learning agents, utility-based agents, logical agents

not here?? confused

## Types of environments

### Observable

[Fully observable]: agent can see everything (chess game or like a fully visible board game)
[Partially observable]: agent must deal with noise, inaccuracy, or incomplete sensors (poker game with hidden cards)

### Number of agents

[Single agent]: the only agent is controlled by the AI
[Multiagent]: task involves more than one agent, each with its own performance measure and may be competitive or cooperative.

### Repeatability

[Deterministic]: next state is based on current state and agent action. EXACT RESULT FOR INPUTS
[Stochastic]: incorporates randomness. If repeated, results could be different despite the same scenario `UNCERTAINTY`

### Relations

[Episodic]: each step is independent of previous ones. (checking emails. each email is independent)
[Sequential]: each step's state affects later ones. (pacman)

### Environment

[Static]: world does not change while agent is choosing an action.
[Dynamic]: decision time matters. (such as driving a car)

### Liquidity/Freedom

[Discrete]: possible states and actions are distinct. Like an integer
[Continuous]: states and actions take on continuous values. Like a double

**Static**: focus on getting high accuracy
**Dynamic**: trade some utility for higher efficiency (speed)
**Episodic**: reflex agent
**Sequential**: goal based/planning agent
**Stochastic**: robustness to uncertainty/failure
**Deterministic**: efficiency and exactness
