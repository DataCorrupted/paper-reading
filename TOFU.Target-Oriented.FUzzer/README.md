# [TOFU.Target-Oriented.FUzzer](https://arxiv.org/abs/2004.14375)

## Summary

This paper presents TOFU, a target oriented fuzzer. 
The main goal is to give some target location in the source code and craft a set of inputs that can cause these locations to be reached.

The authors calculated the distance in ICFG between blocks. 
It also use `protobuf` to ask the tester to pre-define the input structure of the input and use `protobuf-mutator` to do the mutation.
A command line mutator is also included so that command line related code can also be fuzzed.
In prioritization the authors defined a new set of rules to calculate the priority.

In the experiment the authors showed that TOFU has 28% faster than AFLGo and reaches 45% more targets.

## Pros

- Using `protobuf` to ask the user to define the input structure.

## Cons

- Design is more of an engineering approach instead of scientific one. The paper title boosts about target oriented, but it is only a method to help with priority.
- Acquires user input.
- The experiment is shallow, only two binaries are tested.

## bib
```
@article{wang2020tofu,
  title={TOFU: Target-Orienter FUzzer},
  author={Wang, Zi and Liblit, Ben and Reps, Thomas},
  journal={arXiv preprint arXiv:2004.14375},
  year={2020}
}
```