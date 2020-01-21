# [MemLock.Memory.Usage.Guided.Fuzzing](https://wcventure.github.io/pdf/ICSE2020_MemLock.pdf)

## Summary

MemLock focuses on fuzzing memory errors. 
To be more precise, they focus uncontrolled memory error, i.e. huge recursion, huge allocation and memory leak.
MemLock is build upon AFL with certain modifications.

The approach is divided into two parts. 
First part does static analysis that not only cares about CFG but also call graph and memory allocation to track memory usage on stack and heap.
In static instrumenting, they instrumented standard library to keep track of memory related functions.
The second part does fuzzing, where extra policies are added. 
Aside from AFL's definition of "interesting seed", MemLock considers seed with higher max heap memory or higher max stack memory usage seed to be interesting.
During seed selection, interesting seed get picked at probability 1, others at probability 0.01.
Seed with higher memory usage gets updated to replace the original seed.

In evaluation, MemLock is compared with 6 state-of-art fuzzers. 
MemLock aced all of four questions proposed and found 15 CVES with 12 already patched.

## Pros

- Real world CVES found.

## Cons

- A variation based on AFL, lack of novelty.
- Comparison on state-of-art fuzzers are not fair, since these bugs needs special tuning and none of these fuzzers are built for this task.
- Hardship breaking comparasions.
- Algorithm is actually wrong and it wouldn't terminate until the queue is empty.

## bib
```
@inproceedings{wen2020memlock,
  title={Memlock: Memory usage guided fuzzing},
  author={Wen, Cheng and Wang, Haijun and Li, Yuekang and Qin, Shengchao and Liu, Yang and Xu, Zhiwu and Chen, Hongxu and Xie, Xiaofei and Pu, Geguang and Liu, Ting},
  year={2020},
  organization={ICSE}
}
```