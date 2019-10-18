# [FUZZIFICATION.Anti-Fuzzing.Techniques](https://www.usenix.org/system/files/sec19fall_jung_prepub.pdf)

## Summary

This paper proposed a combined methods to prevent adversary from fuzzing a binary called FUZZIFICATION. 
These techniques include BranchBump, BranchTrap and AntiHybrid. 
Extensive experiments has been done and show that the bugs found is reduced.

## Pros
- Novelty, first to deal with anti fuzzing.

## Cons
- Heuristic methods used. 
Nothing principle.
- Strong assumptions made. 
(Sec 3, para 2. 
"... 
experienced developers should have a set of test cases ...")
- Experiment is done on VUzzer and T-Fuzz, which is not state of art.

## Comment

This paper is quite fun to read, "but there is an elephant in the room", i.e. everyone knows about this issue and no one touches it because it's not worth it. 
If you don't want to get fuzzed, make sure you fuzz it first and fix all the bugs. 
That said, the justification for this paper is not well enough.

The methods are also not satisfying. 
The justification for branch bump is not mentioned, and why would you slow down cold branches? However, increasing implicit data-flow seems reasonable as this is a tough one even for state-of-art fuzzers.

There are both pros and cons in experiments. 
First I am happy to see that all three methods is tested separately. Yet, from Fig 9 & 10, there can always see AntiHybrid seems not working.

To sum up, this paper is fun to read, yet the justification, method and evaluation are all questionable.

## Further reading

[Fuzzification: Anti-Fuzzing Techniques [pdf] | Hacker News](https://news.ycombinator.com/item?id=20801168)

## bib
```
@inproceedings{jung2019fuzzification,
  title={FUZZIFICATION: anti-fuzzing techniques},
  author={Jung, Jinho and Hu, Hong and Solodukhin, David and Pagan, Daniel and Lee, Kyu Hyung and Kim, Taesoo},
  booktitle={28th $\{$USENIX$\}$ Security Symposium ($\{$USENIX$\}$ Security 19)},
  pages={1913--1930},
  year={2019}
}
```