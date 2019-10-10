# [Understanding.Integer.Overflow.in.C.C++](https://www.cs.utah.edu/~regehr/papers/tosem15.pdf)

## Summary

This paper systematically studied all integer overflow errors in C/C++. The authors wrote a library Integer Overflow Checker(IOC), which has been merged to LLVM since LLVM 3.5. In the experiment IOC is used to check SPEC CINT 2006 as well as open source libraries including SQLite, SafeInt, LLVM, etc.

## Pros

- The first paper to systematically study integer overflow.
- Solid tool IOC(Later became UBSan) wrote.
- Real world bugs found in experiment.

## Cons

- In experiment, all the test cases are based on given test code of that library. The author could have take a step further and use fuzzing.

## bib
```
@article{dietz2015understanding,
  title={Understanding integer overflow in C/C++},
  author={Dietz, Will and Li, Peng and Regehr, John and Adve, Vikram},
  journal={ACM Transactions on Software Engineering and Methodology (TOSEM)},
  volume={25},
  number={1},
  pages={2},
  year={2015},
  publisher={ACM}
}
```