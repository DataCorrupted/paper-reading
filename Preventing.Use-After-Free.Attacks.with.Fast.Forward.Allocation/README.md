# [Preventing.Use-After-Free.Attacks.with.Fast.Forward.Allocation](https://www.usenix.org/conference/usenixsecurity21/presentation/wickman)

## Summary

This paper targets use after free problem.
First it identified three UAF cases(Tbl 1):

1. Memory inaccessablke, UAF leads to crash
2. Memory accessible but never used. Not likely to exploitable.
3. Accessable and used. Can exploit by changing contens and lead jump execution to anywhere(Fig 1)

The paper targets 3.
The method is to create a new malloc that guarantees no memory is reused.
However, this leads to high memory overhead if not freed frequently and time overhead if it does.

The authors proposed two methods.

1. (Sec 3.1) Batch allocation/free for large memory chunks
2. (Sec 3.2) Forward binning for small memory pieces.

However, they admitted that if there are plenty realloc, the time overhead would be high again.

In evaluation, they find this tool has lower overhead and prevents all UAF exploits.

## bib

```
@inproceedings {263880,
    title = {Preventing Use-After-Free Attacks with Fast Forward Allocation},
    booktitle = {30th {USENIX} Security Symposium ({USENIX} Security 21)},
    year = {2021},
    address = {Vancouver, B.C.},
    url = {https://www.usenix.org/conference/usenixsecurity21/presentation/wickman},
    publisher = {{USENIX} Association},
    month = aug,
}
```