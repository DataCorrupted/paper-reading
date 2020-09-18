# [KRACE.Data.Race.Fuzzing.for.Kernel.File.Systems](https://www.cc.gatech.edu/~mxu80/pubs/xu:krace.pdf)

## Background

This paper looks awfully alike [Fuzzing.File.Systems.via.Two-Dimensional.Input.Space.Exploration(S&P19)](../Fuzzing.File.Systems.via.Two-Dimensional.Input.Space.Exploration/README.md). 
Turns out it's the same group([Meng XU](https://www.cc.gatech.edu/~mxu80/), [Taesoo KIM](https://taesoo.kim/))
It seems that it is a group focused on OS, distributed systems, and storage.

Unlike our fuzzing work where inputs are considered an array of bytes, Fuzzing FS considered two dimensions of inputs: FS itself, i.e., the data in the FS(array of bytes) and syscalls.
In this work, they stopped thinking about the bytes, and input is solely (multi-threading) syscalls.

## Summary

KRACE introduced a new way of detecting racing bugs in kernels, file systems to be specific. 
It consists of the following parts:

### Coverage

Code coverage that is generally used in AFL, Angora, etc. is not useful when detecting racing bugs. 
A racing bug and a normal execution may have the same coverage but different scheduling. 
On another hand, it's impossible to search all possible scheduling schemes.
Considering that only memory access are worth fuzzing, the author proposed _alias coverage_:

- All memory access(with it's location) is labelled `i1, i2, ..., in`.
- **Dynamically**, for all memory, keep track of `<i_x, thread_x>`.
- When a piece of memory gets updated by `<i_y, thread_y>`, have a path from `<i_x, thread_x>` to `<i_y, thread_y>` unless `thread_x == thread_y`.

### Mutation

The seed in this work is a multi-threading syscall sequence.

- Mutate: Change parameter.
- Add: Add new syscalls.
- Delete: Delete syscalls.
- Merge: Instead of attaching, interweavingly join.

### Runtime delay injection

Scheduling is an input space(as specified in previous paper), so they try to use delay to make all threads deterministic.

- Random number ring generated before fuzzing.
- After a memory operation wait `x` memory operations, `x` is the first element of the ring.

### Bug analysis

Two memory access is a race if:

1. they access the same memory location,
2. they are issued from different contexts tx and ty,
3. at least one of them is a write operation.

There are two possible cases it's not:

1. The memory is locked. The authors looked for all locks.
2. One memory access happened before the other can happen.	

Manual selection.

## Experiment

- Clean state kernel, slow but expr shows that it will catch up. Mainly for re-producablity.
- 23 Races in ext4, btrfs and VFS. 11 confirmed harmful.
- Known benign races.

## Pros

- New design regarding _alias coverage_
- Merge method.

## Cons

- Little bugs found.
- Benign races and heuristic based separation method.(P.g 10)

## bib
```
@INPROCEEDINGS{9152693,
  author={M. {Xu} and S. {Kashyap} and H. {Zhao} and T. {Kim}},
  booktitle={2020 IEEE Symposium on Security and Privacy (SP)},
  title={Krace: Data Race Fuzzing for Kernel File Systems},
  year={2020},
  volume={},
  number={},
  pages={1643-1660},
}
```