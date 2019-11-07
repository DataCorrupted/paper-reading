# [GREYONE.Data.Flow.Sensitive.Fuzzing](https://www.usenix.org/system/files/sec20spring_gan_prepub.pdf)

## Summary

This paper targets on data flow sensitive fuzzing. It proposed as new way of doing taint tracking(2.1 Fuzzing-driven Taint Inference, FTI), a new way of mutating seeds(2.2 Taint guided mutation) and new evolution method(2.3 Conformance guided evolution).

### 2.1 

Mutate to see if a var changes. Monitor on all variables in one path. Fast.

### 2.2
Focus on those branches who has higher priority.

W_byte(S, pos) = # of untouched branches that depend on this input _pos_ byte   
W_br(S, br) = Sum of W_byte(S, pos) of the bytes this br depends on

If this don't work, RANDOM mutate.

### 2.3 Conformance

C_br(br, S) = # of equal bits(var1, var2)  
C_BB(bb, S) = MAX C_br(bb, S) of all edges  
C_seed(S) = sum C_BB  

Seed store:
1. new seed
2. seed with higher conformance, replace original seed.
3. same conformance, difference C_BB, append this seed.

High conformance seed first.

## Pros

- Fast taint tracking and no over-taint.
- Separated evaluation on how each component performs.
- Detailed discussion and graph showing results. Especially the compassion with DFSan.

## Cons

- No explanation how much under-taint maybe out there.
- Randomness used in the end... worst than heuristics
- No justification for conformance computation

## Comments

This paper solved and didn't solve implicit taint flow. 
On the one hand, treat the program as black box does solve implicit taint since we only care about the output now(Is this var changed?).
On the other if the input is not fine tuned the black box may not provide useful information.



## bib

```
@inproceedings {244046,
  title = {{GREYONE}: Data Flow Sensitive Fuzzing},
  booktitle = {29th {USENIX} Security Symposium ({USENIX} Security 20)},
  year = {2020},
  address = {Boston, MA},
  url = {https://www.usenix.org/conference/usenixsecurity20/presentation/gan},
  publisher = {{USENIX} Association},
  month = aug,
}
```
