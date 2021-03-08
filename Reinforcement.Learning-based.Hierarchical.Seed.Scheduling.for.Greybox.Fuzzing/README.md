# [Reinforcement.Learning-based.Hierarchical.Seed.Scheduling.for.Greybox.Fuzzing](https://www.ndss-symposium.org/ndss-paper/reinforcement-learning-based-hierarchical-seed-scheduling-for-greybox-fuzzing/)

## Motivation & background

This paper has high correlation with its ancestor _[Be sensitive...](../Be.Sensitive.and.Collaborative.Analyzing.Impact.of.Coverage.Metrics.in.Greybox.Fuzzing/README.md)_, by the same authors.
The core idea is to use **hierarchical branch counting**.

Hardships(see _[Be Sensitive...](../Be.Sensitive.and.Collaborative.Analyzing.Impact.of.Coverage.Metrics.in.Greybox.Fuzzing/README.md)_) is that if branch counting is to sensitive, we catch more interesting seeds, but we impose much overhead to seed scheduling too, as there are way too many seeds.
If we are less sensitive, we can't find interesting things.
_Be sensitive..._ formulated a mathmatical expression of how do we measure sensitiveness of branch counting methods, via a **lattice**.
Finally they came to a conclusion that this is a tradeoff.

## Method

In this paper, they proposed a solution to this tradeoff: use **hierarchical branch counting** to catogrize seeds. 
If two seeds can't be distinguished by current methods, use more sensitive ones so they appear clustered in a less sensitive method, but seperated in more sensitive one.

### [Multi-Armed Bandit Model (MAB)](https://en.wikipedia.org/wiki/Multi-armed_bandit) & [UCB1](https://lilianweng.github.io/lil-log/2018/01/23/the-multi-armed-bandit-problem-and-its-solutions.html#ucb1)

The problem in hierarchical is that how to do scheduling.
They borrowed a similar problem in reinforcement learning: MAB.
This model balances the need to explore(less sensitive measures) and the need to exploit(more sensitive measures).

_Empirically_, they decided to use UCB1 to solve their model. 
Trying to reason about UCB1: this model do not assume any prior on the reward distribution, which is exactly the case of fuzzing: You never know which seed is rewarding, or how rewarding.

### Seed scoring

To use UCB1, they have to score how good a seed is.
Using Eqn & Def in Sec IV.B, they used seed rareness as main metric.
However, Eqn(4) seems off, not sure why they are using sum.

### Branch counting methods

They used three-level hierarchical (Fig 2). \
The root level be a virtual one ruling every nodes identical. 
The first level is function coverage, second edge coverage. 
The leaf level is the hamming distance of comparison operands, see the details in Pg. 6 top right column. 

## Evaluation

They used [DARPA Cyber Grand Challenge (CGC)](https://github.com/CyberGrandChallenge) as their benchmark and compared against AFL and AFL++
The evaluation is extensive and shows promise.

However, it's somewhat disappointing that the baseline is only AFL and AFL++.
