# [SAVIOR.Towards.Bug-Driven.Hybrid.Testing](https://arxiv.org/pdf/1906.07327.pdf)

By the time of this review, this paper is not published yet and it's a preprint version on arxiv. 
Please add a valid bib when it's published.

## Summary

This paper combines fuzz testing and comcolic execution. The main contribution in this paper is that the authors formulized a new approach to pritorize seeds. 

SAVIOR is composed of 3 parts: AFL, coordinator, and KLEE.
Coordinator will prioritize seeds according to the potential basic blocks that can be reached and potential bugs(with the help of UBSan).
The priority algorithm also took number of trials into account.
KLEE is used to do bug guided verification, i.e. given a seed and a basic block with potential bug, KLEE is used to solve the constrain to trigger that bug.

Two set of experiments are done. SAVIOR has been able to find more bugs than LAVA-M listed. It outperformed other hybrid fuzzers(DRILLER and QSYM) even with verifier helping them. In 8 real-world open source programs, SAVIOR found tens of unique bugs compared to the other tools. SAVIOR also found 102 Out of Bound(OOB) errors and 141 logic errors in total.

## Pros

- Prioritize. The paper identified that all seeds are not the same. Those who have more un-covered basic blocks and potential bugs are more worth investigating.
- Bug directed. KLEE is used to help verify bugs in a seed.
- Dramatically improvement compared to DRILLER and QSYM.
- Error classification. This is also mentioned in IntEgrity, as errors can be classified as crash(crash), harmful(logic error), and benign.
- Experiment analysis. The authors did a careful analysis of all numerical results.

## bib
```
@article{chen2019savior,
  title={SAVIOR: Towards Bug-Driven Hybrid Testing},
  author={Chen, Yaohui and Li, Peng and Xu, Jun and Guo, Shengjian and Zhou, Rundong and Zhang, Yulong and Lu, Long and others},
  journal={arXiv preprint arXiv:1906.07327},
  year={2019}
}
```