# [Datalog.Disassembly](https://www.usenix.org/conference/usenixsecurity20/presentation/flores-montoya)

## Summary

This paper introduced a new way of doing disassembly.
They use [Datalog](https://en.wikipedia.org/wiki/Datalog) to first derive facts about the binary.
Certain facts include address A can't be an instructon(_invalid(A)_) or address is an instructor with size, opcode, etc.(_instruction(A, size, ...)_).

First backward traversal(Sec 4.1) cancels any instruction using facts _invalid(A)_. 
For example, if _A_ is invalid, the "instruction" after _A_ can't be valid.
Using forward traversal(Sec 4.2) we can get a superset of all basic blocks.
These basic blocks can overlap, thus (Sec 4.3) tries to solve this using scores.
Sec 5 and 6 further analysises data flow and thus symbolize bytes.

In evaluation, they disassemblied coreutil, real world, and CGC and assembled them back.
Their tool _Ddisasm_ showed 99+% dissam rate and assemble rate, outperforming benchmark Ramblr.

# bib

```
@inproceedings {251538,
    author = {Antonio Flores-Montoya and Eric Schulte},
    title = {Datalog Disassembly},
    booktitle = {29th {USENIX} Security Symposium ({USENIX} Security 20)},
    year = {2020},
    isbn = {978-1-939133-17-5},
    pages = {1075--1092},
    url = {https://www.usenix.org/conference/usenixsecurity20/presentation/flores-montoya},
    publisher = {{USENIX} Association},
    month = aug,
}
```
