# [SANRAZOR.Reducing.Redundant.Sanitizer.Checks.in.C.C++.Programs](https://www.usenix.org/conference/osdi21/presentation/zhang)

## Summary

This paper introduces a method to reduce redundent checks introduced by sanitizer, i.e. ASan & UBSan.
The idea is to combine static & dynamic profile.

### Static profile

For each check inserted by sanitizer, collect all data dependencies into a set. 
Whether the check is instrumented by the sanitizer can be determined by the branch destination, i.e. if the block jumped to has a sanitizer function call.

Constants in a set can be removed from the check depending L0, L1, or L2.
L2 trims all constants and thus can be inaccurate. This is discussed in Sec 4.3.2. 
One example is shown in Sec 7.1.
The evaluation confirms that L2 can miss some predicates.

### Dynamic profile

Dynamic profile runs provided tests to count each check's coverage, true/false coverage.
If the total coverage and true/false coverage is the same, it is considered the same.

Evaluation is done two fold. First, how much overhead can be lowered by the method. 
Then given the reduced check, how much CVE can be reproduced from the provided POC.

The first result is shown in Table 1. UBSan has more overhead reduce than ASan, expecially when L1 or L2 is used.
The second is shown in Table 2. With all 38 bug reproduced using L0, 37 L1, and 22 L2.

The authors also argue that they are fundementally different than ASAP and can be used together.

## Related work

- [High System-Code Security with Low Overhead](https://ieeexplore.ieee.org/document/7163065)

## bib

```
@inproceedings {273757,
    author = {Jiang Zhang and Shuai Wang and Manuel Rigger and Pinjia He and Zhendong Su},
    title = {{SANRAZOR}: Reducing Redundant Sanitizer Checks in {C/C++} Programs},
    booktitle = {15th USENIX Symposium on Operating Systems Design and Implementation (OSDI 21)},
    year = {2021},
    isbn = {978-1-939133-22-9},
    pages = {479--494},
    url = {https://www.usenix.org/conference/osdi21/presentation/zhang},
    publisher = {USENIX Association},
    month = jul,
}
```
