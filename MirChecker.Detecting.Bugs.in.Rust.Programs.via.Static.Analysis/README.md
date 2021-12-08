# [MirChecker.Detecting.Bugs.in.Rust.Programs.via.Static.Analysis](https://dl.acm.org/doi/abs/10.1145/3460120.3484541)

## Summary

This work is based on MIR, Rust Middle IR. It used an old fix point static analysis method to try to find a runtime panic and lifetime problems.
It found real-world bugs.

## bib

```
@inproceedings{10.1145/3460120.3484541,
    author = {Li, Zhuohua and Wang, Jincheng and Sun, Mingshen and Lui, John C.S.},
    title = {MirChecker: Detecting Bugs in Rust Programs via Static Analysis},
    year = {2021},
    isbn = {9781450384544},
    publisher = {Association for Computing Machinery},
    address = {New York, NY, USA},
    url = {https://doi.org/10.1145/3460120.3484541},
    doi = {10.1145/3460120.3484541},
    abstract = {Safe system programming is often a crucial requirement due to its critical role in system software engineering. Conventional low-level programming languages such as C and assembly are efficient, but their inherent unsafe nature makes it undesirable for security-critical scenarios. Recently, Rust has become a promising alternative for safe system-level programming. While giving programmers fine-grained hardware control, its strong type system enforces many security properties including memory safety. However, Rust's security guarantee is not a silver bullet. Runtime crashes and memory-safety errors still harass Rust developers, causing damaging exploitable vulnerabilities, as reported by numerous studies.In this paper, we present and evaluate MirChecker, a fully automated bug detection framework for Rust programs by performing static analysis on Rust's Mid-level Intermediate Representation (MIR). Based on the observation of existing bugs found in Rust codebases, our approach keeps track of both numerical and symbolic information, detects potential runtime crashes and memory-safety errors by using constraint solving techniques, and outputs informative diagnostics to users. We evaluate MirChecker on both buggy code snippets extracted from existing Common Vulnerabilities and Exposures (CVE) and real-world Rust codebases. Our experiments show that MirChecker can detect all the issues in our code snippets, and is capable of performing bug finding in real-world scenarios, where it detected a total of 33 previously unknown bugs including 16 memory-safety issues from 12 Rust packages (crates) with an acceptable false-positive rate.},
    booktitle = {Proceedings of the 2021 ACM SIGSAC Conference on Computer and Communications Security},
    pages = {2183–2196},
    numpages = {14},
    keywords = {static analysis, rust, abstract interpretation},
    location = {Virtual Event, Republic of Korea},
    series = {CCS '21}
}
```