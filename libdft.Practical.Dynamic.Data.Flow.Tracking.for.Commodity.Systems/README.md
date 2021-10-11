# [libdft.Practical.Dynamic.Data.Flow.Tracking.for.Commodity.Systems](http://nsl.cs.columbia.edu/papers/2012/libdft.vee12.pdf)

## Summary

This paper works on DFT.
Instead of static rewriting/instrumentation, libdft uses IntelPin to do dynamic instrumentation.
The taint propagation rules are based on x84 instructions.
(Sec 4.3.1) Besides ALR, XREF operations, whose rules are pretty straightforward, there are other rules to deal with.

The paper also introduced some optimizations. Evaluation shows the unoptimized version has 10+x overhead, where optimized has ~4x.

## bib

```
@inproceedings{kemerlis2012libdft,
  title={libdft: Practical dynamic data flow tracking for commodity systems},
  author={Kemerlis, Vasileios P and Portokalidis, Georgios and Jee, Kangkook and Keromytis, Angelos D},
  booktitle={Proceedings of the 8th ACM SIGPLAN/SIGOPS conference on Virtual Execution Environments},
  pages={121--132},
  year={2012}
}
```