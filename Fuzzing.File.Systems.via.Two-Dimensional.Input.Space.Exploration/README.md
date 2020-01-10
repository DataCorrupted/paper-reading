# [Fuzzing.File.Systems.via.Two-Dimensional.Input.Space.Exploration](https://taesoo.kim/pubs/2019/xu:janus.pdf)

## Summary

This paper focus on file system fuzzing. 
It identified the challenges: file systems are huge and under active development; binary blob is way larger than the suggested size in AFL(and most bytes are not worth mutating); missing context-aware workloads and reproducablity.

The authors designed JANUS to tackle with all these challenges.
JANUS takes metadata(abstracted from binary blob), a series of syscalls and spculated status.
JANUS mutates both in an order and use a libOS to execute it, assemble the corpus and starts next iteration.

JANUS would mutate metadata first and see if it triggered new path, if no new path it would mutate or add syscalls to it.(Sec III, E)

The paper did experiments on 8 file systems(And write parser on all of them). They found 90 bugs and 43 has been fixed andf 32 has assigned CVE.

## Pros

- Solid workload
- Realworld bugs found and CVEs assigned.

## Cons

- The work is basically an update, or an adapter of AFL so that it works on file system.
- It would be better if the metadata mutation is not randomly based.

## Video

[S&P19](https://www.youtube.com/watch?v=UbzZDjk2lsI)

## bib
```
@inproceedings{xu2019fuzzing,
  title={Fuzzing file systems via two-dimensional input space exploration},
  author={Xu, Wen and Moon, Hyungon and Kashyap, Sanidhya and Tseng, Po-Ning and Kim, Taesoo},
  booktitle={2019 IEEE Symposium on Security and Privacy (SP)},
  pages={818--834},
  year={2019},
  organization={IEEE}
}
```