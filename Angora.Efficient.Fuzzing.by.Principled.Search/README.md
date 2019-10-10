# [Angora.Efficient.Fuzzing.by.Principled.Search](https://web.cs.ucdavis.edu/~hchen/paper/chen2018angora.pdf)

## Summary

While fuzzing is a popular technique, the performance of state-of-the-art fuzzers are poor. Angora is proposed using gradient descent to solve constraints in program and therefore mutate input bytes. In experiment, Angora found almost all LAVA bugs and 6, 52, 29, 40, and 48 new bugs in open source programs.

## Pros

- Novelty in gradient descent
- Huge leap in coverage

## Cons

- Don't have a experiment described in [Evaluating.Fuzz.Testing](../Evaluating.Fuzz.Testing/README.md)

## bib
```
@inproceedings{chen2018angora,
  title={Angora: Efficient fuzzing by principled search},
  author={Chen, Peng and Chen, Hao},
  booktitle={2018 IEEE Symposium on Security and Privacy (SP)},
  pages={711--725},
  year={2018},
  organization={IEEE}
}
```