# [FuzzGen.Automatic.Fuzzer.Generation](https://www.usenix.org/conference/usenixsecurity20/presentation/ispoglou)

## Summary

This paper focus on generating binary blobs that can be used to fuzz libraries. 
Previously the job of writing fuzz-able binary executables has to be done by human experts of certain library, this work automates that process.

## Design

1. API for a number of projects that used this library(consumer).
2. Abstract API Dependence Graph(AADG) generation.
   1. For each consumer it genrates an AADG(Algo 1). Use call stack(Cd) to prevent inf loop.
   2. Merge AADGs one by one using common APIs.
   3. Flat AADG, group different nodes based on a topology sort.
3. Analysis argument flow.(Suffers from im-precise static analysis.)
   1. Not everything should be fuzzed.
   2. Same type doesn't equal same thing.(Tbl 1)
4. Binary blob generation.

## Evaluation

- Tbl 3
  - Only tested on video/audio libraries.
  - Don't necessarily outperform human written binary. 
- Fig 5 / Fig 6
  - Edge coverage.
  - Reaches peak quickly.
- Appx. A
  - Static analysis fails from time to time and cause AADG to be inconsistant.
- Appx. B / Tbl 4
  - It's not more customer better. 
  - More customer brings complexity to AADG without bring extra APIs. 
  - Emperical number of customers is 4.
- Appx. C
  - 17 real-world previously unknown bugs found
  - 6 CVEs assigned.

## Comment


### Pros

- Increased edge coverage, though not by much, but it's a fully automated process.
- A brand new approach to deal with library binaries which can't be a stand-along executable.
- Real world bugs found.

### Cons

- The impact of static analysis is not discussed in detail.

## bib
```
@inproceedings {251548,
  author = {Kyriakos Ispoglou and Daniel Austin and Vishwath Mohan and Mathias Payer},
  title = {FuzzGen: Automatic Fuzzer Generation},
  booktitle = {29th {USENIX} Security Symposium ({USENIX} Security 20)},
  year = {2020},
  isbn = {978-1-939133-17-5},
  pages = {2271--2287},
  url = {https://www.usenix.org/conference/usenixsecurity20/presentation/ispoglou},
  publisher = {{USENIX} Association},
  month = aug,
}
```