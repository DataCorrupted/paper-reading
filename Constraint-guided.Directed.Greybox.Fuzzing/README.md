# Constraint-guided.Directed.Greybox.Fuzzing

## Summary

This paper focused on doing directed greybox fuzzing with constraint in mind (CDGF).
Unlike DGF, when thinking about distance, it also calculates the constraints' distance. 
Much like the difference in gradient descend, it's called distance here.

The distance of a basic block to another is the data constraint distance and the target summed.
In a path, the distance is the min distance of all the blocks to the target.

They proposed three templates. 
- nT, they can focus on n targets at the same time. Used on double-free, use-after-free.
- 1T+D, they have a data constraint. Used on div-by-zero.
- 2T+D, data constraint to check buffer usage. Used for buffer/stack-overflow

Templates needs to be written and compiled with the program.
They automatically generated templates using changelogs.
But is sounds like cheating to me because they basically told the fuzzer where the bug is.

In evaluation, they compared with AFLGo, as Hawkeye is not available.
It showed that they can find bugs faster than AFLGo.

However, this tool works on known bugs only. 
To find new bugs, it would require human interaction to generate a template file describe where you want fuzzer put efforts to.

The core contributions in this paper is 

1. Using data distance.
2. Use template file to force a path for fuzzer.