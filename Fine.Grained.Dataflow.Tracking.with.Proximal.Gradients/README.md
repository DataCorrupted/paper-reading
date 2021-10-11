# [Fine.Grained.Dataflow.Tracking.with.Proximal.Gradients](https://www.usenix.org/conference/usenixsecurity21/presentation/ryan)

## Summary

This paper propose to use gradient instead of boolean to track dataflow.
The idea is not hard except that they have to model non-smooth operations.
They propose chain rules and proximal gradients.

The cons with this paper is that they have (unstated) high time overhead.
Each variable in the program have a partial gradient as long as the input, thus it's not feasiable in memory.
Therefore, they decides to do taint tracking for each byte, which made time overhead infeasiable for large inputs.

In their evaluation, they avoided all time related topics.
For fuzzing test, they used number of mutation instead of time.
In time overhead evaluation, they used ONE taint tracking time.
In the "side channel" they find in jpeg, it shows that their high overhead grows as cjpeg size change, which is the problem we had.

However, it's worth learning how they hide their disadvanges and pose them as an advantage.

## bib

```
@inproceedings{ryan2021fine,
  title={Fine Grained Dataflow Tracking with Proximal Gradients},
  author={Ryan, Gabriel and Shah, Abhishek and She, Dongdong and Bhat, Koustubha and Jana, Suman},
  booktitle={30th $\{$USENIX$\}$ Security Symposium ($\{$USENIX$\}$ Security 21)},
  year={2021}
}
```