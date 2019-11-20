# [GRIMOIRE.Synthesizing.Structure.while.Fuzzing](https://www.usenix.org/system/files/sec19-blazytko.pdf)

## Summary

This paper presents GRIMOIRE, it aims to synthesize structural fuzzing input without help from human. It identified several pains in existing fuzzers: 1) Need human assistance, 2) Requires source code, 3) Environment model 4)  Seed 5) Format specification 6) Application limit 7) small-scale mutation. GRIMOIRE solved all of the pains. First it generalize the input and then use extension, recursive replacement and string replacement to generate new input.

Extensive experiment has been done and showed good results. GRIMOIRE has found new 11 CVEs while other only found 5.

## Pros
- Identified 7 pains in fuzzing
- Solved all 7 pains and found more bugs.

## Cons
- The proposed method only extend, but does not shrink. 

## Comment
The proposed method benefit us in that we can add bytes during fuzzing by add dummy bytes in between normal bytes.
However, we still have to think how can we reduce bytes when necessary.

## bib
```
@inproceedings {236210,
  author = {Tim Blazytko and Cornelius Aschermann and Moritz Schl{\"o}gel and Ali Abbasi and Sergej Schumilo and Simon W{\"o}rner and Thorsten Holz},
  title = {{GRIMOIRE}: Synthesizing Structure while Fuzzing},
  booktitle = {28th {USENIX} Security Symposium ({USENIX} Security 19)},
  year = {2019},
  isbn = {978-1-939133-06-9},
  address = {Santa Clara, CA},
  pages = {1985--2002},
  url = {https://www.usenix.org/conference/usenixsecurity19/presentation/blazytko},
  publisher = {{USENIX} Association},
  month = aug,
}
```