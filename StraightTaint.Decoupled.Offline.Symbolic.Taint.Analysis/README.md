# [StraightTaint.Decoupled.Offline.Symbolic.Taint.Analysis](https://faculty.ist.psu.edu/wu/papers/StraightTaint-ASE16.pdf)

## Summary

This paper aims at lowering the overhead of Dynamic Taint Analysis(DTA) by lightweight online logging and allow offline taint analysis.

### Design

**Online logging**

Trace profiling. 2 byte id for each block, split to H tag and L tag, two bytes each. When the H tag are the same it's emitted, or 0x0000 added to change H tag. This design explores spacial locality and saves log space. (Why not adding a special tag for rewind to explore time locality? - To hard to implement)

e.g. 
```
Log 	Block

0x12	(H tag)
0x34 	0x1234
0x35 	0x1235
0x00    (0x0000 to change H tag)
0x00 
0x13 	(New H tag)
0x23 	0x1323
0x24 	0x1324
```

Async logging. A (local) buffer is provided, when buffer runs out, a worker thread switches local buffer and dumps the filled buffer to global buffer.

**Offline DTA**

This work is based on Intel Pin and works on directly binary code, so no need to extract IR, using block trace is enough.

Then create an abstract processor `s = (pc, V, M)` where `pc` is program counter, `V` is symbolic register value, `M` is memory context(in fuzzer2's sense, range tree).

For dynamic memories, use `malloc` to get an actual non-conflicting memory.

### Evaluation

- **Speed**: Runtime overhead lower than libdft/FlowWalker(Fig 9/10)
- **Accuracy**: Able to taint know bugs(Table 1)

## Comments

- Moving taint analysis from online to offline has the same idea as fuzzer2, decoupling is done nicely, and the runtime overhead drop is impressive.
- Weak accuracy measurement. In fact this is an interesting academic problem: How do we measure taint analysis? 

## bib
```
@inproceedings{ming2016straighttaint,
  title={Straighttaint: Decoupled offline symbolic taint analysis},
  author={Ming, Jiang and Wu, Dinghao and Wang, Jun and Xiao, Gaoyao and Liu, Peng},
  booktitle={2016 31st IEEE/ACM International Conference on Automated Software Engineering (ASE)},
  pages={308--319},
  year={2016},
  organization={IEEE}
}
```