# [Binary.Rewriting.without.Control.Flow.Recovery](https://dl.acm.org/doi/pdf/10.1145/3385412.3385972)

## Summary

This paper propose binary rewrite using jump to replace target instruction.
The idea is to use a jump instruction to transfer control flow to other places, add patched code and replay the target instruction.
However, this may bring problem.

Jump can be a 5-byte instruction, (`e9 xx xx xx xx`, `e9` being opcode, the rest is relative address.), but the target instruction may be less than 5 bytes.
For example, `mov` is a 3-byte instruction, `push` is one-byte.
In this case, we would treat the first two bytes in the next instruction as part of relative address.
This constitude the base line approach(B1/B2).

However, they are times when B2 won't work as the first two bytes of the next instruction may not be ideal(negative, too large, occupied address, etc.).
Based on this, the author proposed new methods

- T1: Padding. Add padding bytes before `e9` to move the instruction a bit. The available space may reduce, but it may be feasible.
- T2: Evict next instruction. Using two jumps, the first(using target instruction space) jumps to patch code, the second(slightly overlap with first jump) jumps to evicted code.
- T3: Evict neighbour instruction. Using `eb xx` to jump to a neighbour, change that neighbour to a jump and fix code. (example in Fig 2)

A memory management detail is that the patched code may scatter around(due to address limitations introduced), the authors merged all patches to some memory pages, then map these memory to intended address.

The experiment shows that whiel B1/B2 can fix 70% to 80% of the patches, T1/T2/T3 filled the gap. 
Most binaries have a 100% success rate due to T1/T2/T3. 
Runtime overhead ranges from 1.07x to 4.6x, average 2x.
The author also tried to instrument chrome and firefox.

## Pro

The pro of this paper is it has few assumptions about the binary.


## bib

```
@inproceedings{duck2020binary,
  title={Binary rewriting without control flow recovery},
  author={Duck, Gregory J and Gao, Xiang and Roychoudhury, Abhik},
  booktitle={Proceedings of the 41st ACM SIGPLAN Conference on Programming Language Design and Implementation},
  pages={151--163},
  year={2020}
}
```