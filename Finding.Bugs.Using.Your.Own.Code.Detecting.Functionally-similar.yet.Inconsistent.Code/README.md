# [Finding.Bugs.Using.Your.Own.Code.Detecting.Functionally-similar.yet.Inconsistent.Code](https://www.usenix.org/conference/usenixsecurity21/presentation/ahmadi)

## Summary

This paper works in the following steps(Fig 3):

1. Compile
2. Data Dependency Graph extration
3. _Construct_ extraction. _Construct_ somewhat like per-variable DDG.
4. Abstraction, simplify _Construct_.
5. Bag-of-nodes to coarse grained classifier.
6. Deviation analysis to find grained find anomoly code in it's class.

This work is somewhat similar to [Path-Based.Function.Embedding.and.Its.Application.to.Error-Handling.Specification.Mining](https://web.cs.ucdavis.edu/~rubio/includes/fse18.pdf). 
Except that they work on a more fine-grained _Construct_, but later works on a function directly.

```
@inproceedings {263838,
title = {
    Finding Bugs Using Your Own Code: Detecting Functionally-similar yet Inconsistent Code},
    booktitle = {30th {USENIX} Security Symposium ({USENIX} Security 21)},
    year = {2021},
    address = {Vancouver, B.C.},
    url = {https://www.usenix.org/conference/usenixsecurity21/presentation/ahmadi},
    publisher = {{USENIX} Association},
    month = aug,
}
```