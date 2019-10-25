# [SAVIOR.Towards.Bug-Driven.Hybrid.Testing](https://arxiv.org/pdf/1906.07327.pdf)

By the time of this review, this paper is not published yet and it's a preprint version on arxiv. 
Please add a valid bib when it's published.

## Summary

This paper combines fuzz testing and concolic execution. The main contribution in this paper is that the authors formulized a new approach to prioritize seeds. 

SAVIOR is composed of 3 parts: AFL, coordinator, and KLEE.
Coordinator will prioritize seeds according to the potential basic blocks that can be reached and potential bugs(with the help of UBSan).
The priority algorithm also took number of trials into account.	
KLEE is used to do bug guided verification, i.e. given a seed and a basic block with potential bug, KLEE is used to solve the constrain to trigger that bug.

The main contribution is **Bug guided prioritization** and **Bug guided verification**.  
Prioritization is done through: <img src="http://bit.ly/2pB2k7g" align="center" border="0" alt="\frac{1}{n} \sum_{k=1}^n e^{-0.05S_k} * L_k" width="151" height="50" />  
Verification is done through KLEE.

Two set of experiments are done. SAVIOR has been able to find more bugs than LAVA-M listed. It outperformed other hybrid fuzzers(DRILLER and QSYM) even with verifier helping them. In 8 real-world open source programs, SAVIOR found tens of unique bugs compared to the other tools. SAVIOR also found 102 Out of Bound(OOB) errors and 141 logic errors in total.

## Pros

- Prioritize. The paper identified that all seeds are not the same. Those who have more un-covered basic blocks and potential bugs are more worth investigating.
- Bug directed. KLEE is used to help verify bugs in a seed.
- Dramatically improvement compared to DRILLER and QSYM.
- Error classification. This is also mentioned in IntEgrity, as errors can be classified as crash(crash), harmful(logic error), and benign.
- Experiment analysis. The authors did a careful analysis of all numerical results.

## Comment

Prioritize has being mentioned more and more in recent researches. 
Angora[[1]](https://web.cs.ucdavis.edu/~hchen/paper/chen2018angora.pdf) started off by lower priority of those who cannot be solved immediately, IntEgrity prioritize integer related bugs, this work start to prioritize seed more carefully by using UBSan. 
GREYEYE[[2]](https://www.usenix.org/system/files/sec20spring_gan_prepub.pdf) took a step further and even started to prioritize bytes in a seed and branches reached by a seed.

But directed is also mentioned a lot recently. 
Before, people assume that code coverage lead to bugs, this is a good intuition. 
But as the bug is hiding deeper and deeper due to the development of coverage-based fuzzer, this assumption may not hold and we need to start dealing with bugs more seriously. 
However, how to direct to a bug except to using priority is yet not well answered.

Except for this work, DRILLER[[3]](https://sites.cs.ucsb.edu/~vigna/publications/2016_NDSS_Driller.pdf) and QSYM[[4]](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-yun.pdf) also using hybrid fuzzing. 
However, whether they actually work remains a problem, the pain is that concolic execution is slow.
I suspect that this paper also suffer from speed issue, but they won because of prioritize.

## Further reading

[SoK: Sanitizing for Security](https://arxiv.org/pdf/1806.04355.pdf)  
[All You Ever Wanted to Know About Dynamic Taint Analysis and Forward Symbolic Execution (but might have been afraid to ask)](https://users.ece.cmu.edu/~aavgerin/papers/Oakland10.pdf)  
[KLEE: Unassisted and Automatic Generation of High-Coverage Tests for Complex Systems Programs](https://hci.stanford.edu/cstr/reports/2008-03.pdf)  

## bib
```
@article{chen2019savior,
  title={SAVIOR: Towards Bug-Driven Hybrid Testing},
  author={Chen, Yaohui and Li, Peng and Xu, Jun and Guo, Shengjian and Zhou, Rundong and Zhang, Yulong and Lu, Long and others},
  journal={arXiv preprint arXiv:1906.07327},
  year={2019}
}
```