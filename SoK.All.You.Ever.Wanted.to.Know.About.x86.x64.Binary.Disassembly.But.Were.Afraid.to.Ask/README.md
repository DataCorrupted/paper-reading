# [SoK.All.You.Ever.Wanted.to.Know.About.x86.x64.Binary.Disassembly.But.Were.Afraid.to.Ask](https://www.computer.org/csdl/proceedings-article/sp/2021/893400a194/1mbmHyBd1Dy)

## Summary

This paper summarized current available tools in disassembly. 
It carefully analysised methods, including algorithms and heuristics used in them.
Then the authors did large scale experiments and comes to some conclusion(Section V: Findings):

1. Complex constructs are common and heurisitics ar eindispensable to handle them
2. Heurisitics inherently introduce converage-correctness trade-offs
3. Tools complement each other.
4. ...

## Thoughts

Disassembly is hard. 
All the works mentioned in the paper made few assumptions: striped, heavily optimized, etc.

However, inorder to use disassembly to help fuzzing, we have these assumptions.
We can ask the user to compile the code with `O0` and `-g`. 

One concerns is almost no tools can find function entries properly. (Table X)
This is a daunting problem for context sensitive fuzzing.

## bib

```
@INPROCEEDINGS {,
    author = {C. Pang and R. Yu and Y. Chen and E. Koskinen and G. Portokalidis and B. Mao and J. Xu},
    booktitle = {2021 2021 IEEE Symposium on Security and Privacy (SP)},
    title = {SoK: All You Ever Wanted to Know About x86/x64 Binary Disassembly but Were Afraid to Ask},
    year = {2021},
    volume = {},
    issn = {2375-1207},
    pages = {194-212},
    keywords = {binary-disassembly;binary-security;knowledge-systematization},
    doi = {10.1109/SP40001.2021.00012},
    url = {https://doi.ieeecomputersociety.org/10.1109/SP40001.2021.00012},
    publisher = {IEEE Computer Society},
    address = {Los Alamitos, CA, USA},
    month = {may}
}
```