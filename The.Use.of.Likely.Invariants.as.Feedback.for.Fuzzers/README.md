# [The.Use.of.Likely.Invariants.as.Feedback.for.Fuzzers](http://s3.eurecom.fr/docs/usenixsec21_fioraldi.pdf)

## Summary

This paper propose the use likely invariants as fuzzer feedback.  

The core idea is to use a dynamic invariant detection to mine invariants, the fuzzer is rewarded(in the sense of branch counting) when the invariant is broken.
However, the mined invariant can be huge, but it's not much for each basic block. 
Still, the author employed three methods to reduce the invariants: 

1. Some are impossible to violate. For example, unsigned integer are greater equal than 0.
2. Unrealted variables.
3. Overlapping conditions, i.e. nested conditions.

Each invariant has an id, whenever an invariant is violated, it is xor-ed with blcok id.
See Listing 4 for details.               


## bib
```
@article{fioraldiuse,
  title={The Use of Likely Invariants as Feedback for Fuzzers},
  author={Fioraldi, Andrea and D’Elia, Daniele Cono and Balzarotti, Davide}
}
```