# [Skyfire.Data-Driven.Seed.Generation.for.Fuzzing](https://www.ieee-security.org/TC/SP2017/papers/42.pdf)

## Summary

This paper proposed to use probabilistic context sensitive grammar (PCSG) learned from data set(thus "data-driven") to generate new seeds to increase code coverage. 
The work flow can be seen in Fig 1 and 2.

PCSG is a proposed grammar built on Context Sensitive Grammar(CSG). 
CSG is used to help pass semantics check.(Review CFG, CSG if necessary)
Provided with a CFG and data set crawled from the Internet, the authors learn a PCSG. 

**PCSG Learning**: In PCSG same derivation rules have summed probability of 1. 

**Seed Generation**: the algorithm can be seen in Algorithm 1.
Some heuristics are used:

1. Favor low-probability production rules.
2. Favor low-frequency production rules, and restrict the application number of the same production rule.
3. Favor low-complexity production rules.
4. Restrict the total number of rule applications.

**Seed selection**: based on coverage.

**Seed mutation**: randomally mutate terminals.

In experiment the authors reported 16 new memory corruption bugs and 32 DOS bugs.
They answered the following 4 questions:

1. Can Skyfire generate good seeds for a fuzzer to find bugs? 
2. Can Skyfire improve the code coverage of target programs? 
3. Are the proposed PCSG and the four heuristics used in Skyfire effective in generating seeds? 
4. How efficient is Skyfire? 

## Pros

- Real world bugs found.
- Code coverage
- In experiment, they explained heuristics' effectiveness

## Cons

- Blindly improve code coverage
- Not a huge leap compared to crawl, the base line choice is not good enough.
- Failed to produce on JS, which limit this works extendibility, i.e. it can only be used in xml and xsl, not other languages.

## Related reading

[S&P19: ProFuzzer: On-the-fly Input Type Probing for Better Zero-day Vulnerability Discovery](https://wcventure.github.io/FuzzingPaper/Paper/SP19_Profuzz.pdf)

## bib
```
@inproceedings{wang2017skyfire,
  title={Skyfire: Data-driven seed generation for fuzzing},
  author={Wang, Junjie and Chen, Bihuan and Wei, Lei and Liu, Yang},
  booktitle={2017 IEEE Symposium on Security and Privacy (SP)},
  pages={579--594},
  year={2017},
  organization={IEEE}
}
```