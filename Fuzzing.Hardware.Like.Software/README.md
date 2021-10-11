# [Fuzzing.Hardware.Like.Software](https://arxiv.org/abs/2102.02308)

## Summary

This paper propose fuzzing hardware. 
It uses hardware simulator Verilator to compile a hardware Design Under Test(DUT) to a software.
Compared to pure random verfication and formal verication, this methods stands in between.
The key challenge here is the following:

1. How to represent test cases (what's input?)
2. How to represent crash/branch coverage (what's interesting?)

The paper used a digital lock to do both evaluation and design. (Sec V. Evaluation Part 1)
It justified the design choices by evaluation result.

In the second part of evaluation, it tested google's OpenTitan. (Fig 12)

## Key take away

While I am not familar with fuzzing and thus can't evaluate how effective is their second part of evaluation,
I realize that fuzzing is an idea instead of a tool. 
As long as input, interesting, crash, etc. is properly defined, any system should be fuzz-able.

The other take away is that when it comes to heuristic choices, putting them in evaluation is better than design.
Let's the data talk.

## bib

```
@article{trippel2021fuzzing,
  title={Fuzzing Hardware Like Software},
  author={Trippel, Timothy and Shin, Kang G and Chernyakhovsky, Alex and Kelly, Garret and Rizzo, Dominic and Hicks, Matthew},
  journal={arXiv preprint arXiv:2102.02308},
  year={2021}
}
```
