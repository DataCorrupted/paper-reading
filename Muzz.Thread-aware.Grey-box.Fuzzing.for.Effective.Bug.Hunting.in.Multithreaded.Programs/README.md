# [Muzz.Thread-aware.Grey-box.Fuzzing.for.Effective.Bug.Hunting.in.Multithreaded.Programs](https://www.usenix.org/conference/usenixsecurity20/presentation/chen-hongxu)

## Summary

This paper focus on multi-threaded fuzzing. However, of all the methods it proposed, it's mainly an update on branch-counting.
It added thread context to AFL and createcd a new tool Muzz.

## Design

### Static analysis

**Interleaving scope extraction**: gives you a set of instructions `L_m` that may be interleaving. Thus 3 requirements has to be met

1. After fork, before join
2. No lock
3. Read/write shared memory: through point to analysis. (Comment 1)

**Coverage instrumentation**

Cyclomatic complexity: `M = E - N + 2`. `E` beging the # of the edges, `N` being the # of the nodes(i.e. basic blocks)
The higher `M` is, the more complex is a CFG.
10 is fairly complex according to the person invented this.

Base probablity: `P = min(M/10, 1)`, base probablity is calculated for every function.

For a basic block, 
- if any instruction in `L_m`, instrument entry
- if no instruction in `L_m`, instrument entry with probability `min(0.5, P)`, i.e. at most half of "non-multithreading" basic blocks are instrumented.

For each instruction in `L_m`, instrumented it with probablity `min(P * Nm / Nb, 1/3)`. `Nm` and `Nb` means the the memory related instructions and total instructions in current basic block. Justification: racing results from memory access, so the attention it gets is based on frequency of the memory access.(Last sentence above Sec 4.2.2)

**Threading context**: For `lock`, `unlock`, `join`, maintain a sequence of tuple (callsite, thread id).

### Dynamic fuzzing

**Seed selection**

- Seed has new threading context is always selected.
- Seed has new path but no new threading context are seleted with probablity of 0.95.
- Other seeds are selected with 0.01. If no seed is interesting, select anything with probablity of 0.15.

**Repeated execution**: Repeat more for a seed with more threading context.

## Evaluation

- Can we find more seeds? Tbl 2
- Can we find bugs? Tbl 3
- Can we re-produce bugs? Tbl 4
  - Round robin execution for each seeds.
  - Repeat execution for a certain time.

## Comment

- Point to analysis is not accurate. Yet to do multi threading analysis you must know whether a pointer is pointing at a shared memory. This is one hard part to do multithreading fuzzing.
- Using cyclomatic complexity is interesting. It gave us a hint some places are just not worth fuzzing.
- Indeed, if we don't instrument all instructions we reduce overhead, but using probablities is not justified in terms of correctness. 
- Thread scheduling is not explored. Instead it repeated execute the program on PoC file for multiple times to prove the bug exists, yet no scheduling PoC is provided.

## bib
```
@inproceedings{chen2020muzz,
  title     = {$\{$MUZZ$\}$: Thread-aware Grey-box Fuzzing for Effective Bug Hunting in Multithreaded Programs},
  author    = {Chen, Hongxu and Guo, Shengjian and Xue, Yinxing and Sui, Yulei and Zhang, Cen and Li, Yuekang and Wang, Haijun and Liu, Yang},
  booktitle = {29th $\{$USENIX$\}$ Security Symposium ($\{$USENIX$\}$ Security 20)},
  pages     = {2325--2342},
  year      = {2020}
}
```