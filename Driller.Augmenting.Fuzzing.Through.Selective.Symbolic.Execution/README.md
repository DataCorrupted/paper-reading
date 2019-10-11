# [Driller.Augmenting.Fuzzing.Through.Selective.Symbolic.Execution](https://sites.cs.ucsb.edu/~chris/research/doc/ndss16_driller.pdf)

## Summary

This paper introduced a new automated tool Driller by combining fuzzing(AFL) and symbolic execution together. 
The authors categorized inputs into _generic_ input and _specific_ input, they further partitioned a program into _compartments_ for different functionalities. 
The intuition is that fuzzers and symbolic execution can be combined to solve different _compartments_. 
In the experiment, the authors showed that Driller can found 7 more crashes than AFL along, hundreds of more basic blocks thanks to mode switching.

## Pros

- The first to combine fuzzer and symbolic execution together.
- Found more crashes and basic blocks than AFL nor symbolic execution.

## Cons

- The experiment is done on a given dataset, not real-world bug is found, therefore limited contribution.
- The switch is more of a heuristic than a principled search.

## Comment

The idea that symbolic execution and fuzzers can combine is quite attracting.
One upside mentioned in the paper is that symbolic execution can be used to solve magic numbers really quick(Although gradient descent can do that too).
I believe this idea can be extended and therefore used to solve input length problem, i.e. input is an integer _k_ followed by _k_ chars. 

## bib
```
@inproceedings{stephens2016driller,
  title={Driller: Augmenting Fuzzing Through Selective Symbolic Execution.},
  author={Stephens, Nick and Grosen, John and Salls, Christopher and Dutcher, Andrew and Wang, Ruoyu and Corbetta, Jacopo and Shoshitaishvili, Yan and Kruegel, Christopher and Vigna, Giovanni},
  booktitle={NDSS},
  volume={16},
  number={2016},
  pages={1--16},
  year={2016}
}
```