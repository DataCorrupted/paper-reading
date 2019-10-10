# [Evaluating.Fuzz.Testing](https://www.cs.umd.edu/~mwh/papers/fuzzeval.pdf)

## Summary

This paper recognized the evaluation problem in fuzzing papers. 
It argues that different settings and configurations can lead to different conclusion. 
To demonstrate such difference, the authors did extensive experiments on 32 current available tools and proposed a meaningful way of doing experiments on fuzzers.

## Pros

- First to recognize the problem
- Did a extensive study on all fuzzers and demonstrated that different settings can lead to different conclusion

## Cons

- The idea itself lacks novelty. The idea that experiment can lead to different results is not new but a common sense among fuzzer researchers. This paper merely brought this problem to people's attention
- The author didn't argue the correctness of his experiment method, but more like another heuristic.

## Comments

This paper is rather interesting to read. 
The authors put a lot efforts in the experiments. 
The result that different timeout, seed can lead to different conclusion. 

However, I find limited novelty and contribution. 
Even thought the citation of this paper may be very high(Every fuzzing paper need to cite it in experiment section from now on), I failed to see a long term impact of this paper.

## bib
```
@inproceedings{klees2018evaluating,
  title={Evaluating fuzz testing},
  author={Klees, George and Ruef, Andrew and Cooper, Benji and Wei, Shiyi and Hicks, Michael},
  booktitle={Proceedings of the 2018 ACM SIGSAC Conference on Computer and Communications Security},
  pages={2123--2138},
  year={2018},
  organization={ACM}
}
```