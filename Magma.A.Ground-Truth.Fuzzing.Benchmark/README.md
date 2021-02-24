# [Magma.A.Ground-Truth.Fuzzing.Benchmark](https://dl.acm.org/doi/10.1145/3428334)

## Summary

Magma proposed a new benchmark to replace LAVA.

The problem with LAVA is that it measures exploration, but Magma measures exploitation.
Also, Magma covers more types of bugs while LAVA only covers magic bytes.
Besides, Magma use forward porting to insert real bugs, but LAVA use synthetic ones.

It's surprising to find that honggfuzz and MOPT perform better than AFL++ in this benchmark.

It would be necessary to study Appendix A for all the bugs inserted.

## bib

```
@article{10.1145/3428334,
    author = {Hazimeh, Ahmad and Herrera, Adrian and Payer, Mathias},
    title = {Magma: A Ground-Truth Fuzzing Benchmark},
    year = {2020},
    issue_date = {December 2020},
    publisher = {Association for Computing Machinery},
    address = {New York, NY, USA},
    volume = {4},
    number = {3},
    url = {https://doi.org/10.1145/3428334},
    doi = {10.1145/3428334},
    abstract = {High scalability and low running costs have made fuzz testing the de facto standard for discovering software bugs. Fuzzing techniques are constantly being improved in a race to build the ultimate bug-finding tool. However, while fuzzing excels at finding bugs in the wild, evaluating and comparing fuzzer performance is challenging due to the lack of metrics and benchmarks. For example, crash count---perhaps the most commonly-used performance metric---is inaccurate due to imperfections in deduplication techniques. Additionally, the lack of a unified set of targets results in ad hoc evaluations that hinder fair comparison. We tackle these problems by developing Magma, a ground-truth fuzzing benchmark that enables uniform fuzzer evaluation and comparison. By introducing real bugs into real software, Magma allows for the realistic evaluation of fuzzers against a broad set of targets. By instrumenting these bugs, Magma also enables the collection of bug-centric performance metrics independent of the fuzzer. Magma is an open benchmark consisting of seven targets that perform a variety of input manipulations and complex computations, presenting a challenge to state-of-the-art fuzzers. We evaluate seven widely-used mutation-based fuzzers (AFL, AFLFast, AFL++, FairFuzz, MOpt-AFL, honggfuzz, and SymCC-AFL) against Magma over 200,000 CPU-hours. Based on the number of bugs reached, triggered, and detected, we draw conclusions about the fuzzers' exploration and detection capabilities. This provides insight into fuzzer performance evaluation, highlighting the importance of ground truth in performing more accurate and meaningful evaluations.},
    journal = {Proc. ACM Meas. Anal. Comput. Syst.},
    month = nov,
    articleno = {49},
    numpages = {29},
    keywords = {fuzzing, benchmark, software security, performance evaluation}
}
```