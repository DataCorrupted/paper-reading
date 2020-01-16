# [ShortCut.Accelerating.Mostly-Deterministic.Code.Regions](https://dl.acm.org/doi/pdf/10.1145/3341301.3359659)

This is a paper in ECS251(winter 20) reading list.

## Summary

This paper propose ShortCut, a system that aims at accelerating codes. 
It does so by identifies "mostly deterministic code" and skip the execution by copying and modifying memory/register states.

ShortCut would profile a binary first by feeding it some inputs. 
It classifies each byte as _predicate_ or _taint_ where _predicate_ means that in these inputs the byte seems to be the same.
Then ShortCut generates slices where it can skip execution. 
It also handles data flow and control flow divergences.
Once it is generated, during execution the slice gets skipped until certain predicate fails and then it would roll back to do evaluation.

The experiment shows that ShortCut can break even, i.e. won't hurt performance, as long as 1/4 "hit rate". 
It even reached a huge performance gain on certain evaluations.

## Pros

- Performance gain
- Don't rely on source code(Intel pin used)

## Cons

- Too much heuristics, especially on taint tracking.
- Didn't mention how profiling is done in evaluation, yet it affects the result greatly.
- Break even part is only mentioned in the talk but not in the paper.

## [Video](https://sosp19.rcs.uwaterloo.ca/videos/D3-S3-P2.mp4)

## bib
```
@inproceedings{dou2019shortcut,
  title={ShortCut: accelerating mostly-deterministic code regions},
  author={Dou, Xianzheng and Chen, Peter M and Flinn, Jason},
  booktitle={Proceedings of the 27th ACM Symposium on Operating Systems Principles},
  pages={570--585},
  year={2019}
}
```