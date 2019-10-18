# [KLEE.Unassisted.and.Automatic.Generation.of.High-Coverage.Tests.for.Complex.Systems.Programs](https://hci.stanford.edu/cstr/reports/2008-03.pdf)

## Summary

This paper presents a symbolic execution tool KLEE. 

KLEE used several techniques to reduce the time for symbolic execution, including 1) compact state representation, 2) query optimization, 3) state scheduling. 
Compact state representation basically used copy-on-write object level to reduce the objects in memory. 
Query optimization used some techniques including _Expression Rewriting_, _Constraint Set Simplification_, _Implied Value Concretization_, _Constraint Independence_, _Counter-example Cache_. 
Result shows that the time used by solver can be reduced to 1/15. 
In state scheduling, two states are given priority: those who are high in branch tree and those who are like to cover new code.

What's more, KLEE also models environment including file system, environment variable, etc.

In experiment, KLEE show more code coverage than user provided test cases or random testing. 
It also found real-world bugs.

## Pros

- State-of-art symbolic execution.
- Real bugs found.

## Cons

- Compare with manual testing is trivial. Also the authors didn't mention how they did random test.

## bib
```
@inproceedings{cadar2008klee,
  title={KLEE: Unassisted and Automatic Generation of High-Coverage Tests for Complex Systems Programs.},
  author={Cadar, Cristian and Dunbar, Daniel and Engler, Dawson R and others},
  booktitle={OSDI},
  volume={8},
  pages={209--224},
  year={2008}
}
```