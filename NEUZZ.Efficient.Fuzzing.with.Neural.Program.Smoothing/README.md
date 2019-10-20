# [NEUZZ.Efficient.Fuzzing.with.Neural.Program.Smoothing](https://arxiv.org/pdf/1807.05620.pdf)

## Summary

This paper proposed to use NN to model a program. Consider input as a vector _x_, what we want to optimize is the number of bugs found. However, this function can be discrete, therefore what we do is using the number of branch coverage as the function and use NN to model it.

## Pros

- The idea is quite new and it did reach higher branch coverage

## Further reading

[S&P19 Slides](https://www.ieee-security.org/TC/SP2019/SP19-Slides-pdfs/Dongdong_She.pdf)

## bib
```
@article{she2018neuzz,
  title={Neuzz: Efficient fuzzing with neural program learning},
  author={She, Dongdong and Pei, Kexin and Epstein, Dave and Yang, Junfeng and Ray, Baishakhi and Jana, Suman},
  journal={arXiv preprint arXiv:1807.05620},
  year={2018}
}
```