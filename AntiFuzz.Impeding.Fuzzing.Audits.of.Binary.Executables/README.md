# [AntiFuzz.Impeding.Fuzzing.Audits.of.Binary.Executables](https://www.usenix.org/conference/usenixsecurity19/presentation/guler)

## Summary

This paper identified four assumptions of fuzzers(Sec 3):

1. Coverage yields relevant feedback.
2. Crashes can be detected.
3. Many Executions per second.
4. Constraints are solvable with symbolic execution.

This paper proposed four ways of anti-fuzzing, attacking all four assumptions:

1. (Sec 4.1) Random edges. Random functions are called based on input hashes to create fake edges for all inputs, making them all interesting.
2. (Sec 4.2) Custom signal handler. This made sure that the program always exit(0) no matter what, so fuzzers don't know if it crashed or not.
3. (Sec 4.3) Malformed input slow down by 250 ms. They argue that only fuzzers generate huge amount of malformed input and it would impose little overhead to end-user.
4. (Sec 4.4) Using encrypt-decrypt cycle to overload solvers.

An example instrumentation can be found in Fig 2.

Evaluation shows that they forced branch coverage of Vuzzer, AFL, Hongg and QSYM to less than 1000 (Tbl 3).
However, they didn't introduce much overhead on SPEC CPU 2006 benchmark(Tbl 5).

[repo](https://github.com/RUB-SysSec/antifuzz)

## bib
```
@inproceedings {235499,
    author = {Emre G{\"u}ler and Cornelius Aschermann and Ali Abbasi and Thorsten Holz},
    title = {AntiFuzz: Impeding Fuzzing Audits of Binary Executables},
    booktitle = {28th {USENIX} Security Symposium ({USENIX} Security 19)},
    year = {2019},
    isbn = {978-1-939133-06-9},
    address = {Santa Clara, CA},
    pages = {1931--1947},
    url = {https://www.usenix.org/conference/usenixsecurity19/presentation/guler},
    publisher = {{USENIX} Association},
    month = aug,
}
```

