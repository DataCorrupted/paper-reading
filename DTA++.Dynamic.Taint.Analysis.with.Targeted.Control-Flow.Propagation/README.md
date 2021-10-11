# [DTA++.Dynamic.Taint.Analysis.with.Targeted.Control-Flow.Propagation](http://bitblaze.cs.berkeley.edu/papers/dta++-ndss11.pdf)

## Summary

DTA++ works on implicit flow.
Kinda sad it was published so long ago.
The general idea is the same as we proposed, to identify PHI Node.
Though PHI Node is a LLVM term, the idea is the same.
Track the data who can accept multiple values and track the values control flow.
However, DTA++ implemented it as an offline service, the trace of the program has to be dumped first.

## bib
```
@inproceedings{kang2011dta++,
  title={Dta++: dynamic taint analysis with targeted control-flow propagation.},
  author={Kang, Min Gyung and McCamant, Stephen and Poosankam, Pongsin and Song, Dawn},
  booktitle={NDSS},
  year={2011}
}
```