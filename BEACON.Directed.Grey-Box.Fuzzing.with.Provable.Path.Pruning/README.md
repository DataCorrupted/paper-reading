# [BEACON:.Directed.Grey-Box.Fuzzing.with.Provable.Path.Pruning]

## Summary

The paper is an improvement over directed grey box fuzzing with static analysis engine.
It can be applied to all fuzzers since its staic analysis, but HBACON is developed over [AFLGo](../Directed.Greybox.Fuzzing/README.md).

The analysis consist of the following parts;

1. Remove blocks that can't reach target. This can be done doing a reversed DFS starting from the target. ("... applying a graph reachability analysis on the interprocedural control flow graph (ICFG) of the program.")
2. Backward interval analysis. Starting from the target, aggrigate all intervals as a sound conditions, Algo 2 is another reversed DFS.
3. Optimization. Step 2 may have  huge time and memory overhead, here they trim them:
   1. Relationship Preservation, i.e. static evaluation of variable relations. Fig 5 derive the rules.
   2. Bounded Disjunctions. When there are too many sets of conditions, merge the new coming set with a existing set. They calculate the distance between sets to decide which set to use for merging and to minimize the precision loss.

However, I am not convinced for some of the designs for following reasons.

In step 1, paths are trimmed using `assert(false)`, I wonder how much this would help. The paper didn't specify this.

In step 2, one has to replace variable for assignments(Algo 1, Ln 3, 5, 7), but when memory load/store appears(Ln 5, 7), there is a point to analysis and it can be in accurate. The paper cite [another work](https://dl.acm.org/doi/10.1145/2535838.2535888) saying it can be solved, but that work is on integer overflows.

## Evaluation

They selected 51 known CVEs trying to reproduce them.
Comparasion with AFLGo(Table III) shows that they can reproduce all bugs while AFLGo can only reproduce 26 in 120 hrs fuzzing time.
It showed that ~87% of paths are early terminated using their design.
However, I still wonder of all the paths that are early terminated, how many can be contributed to 1?
Other evaluation shows BEACON can work on top of AFL, AFL++, Mopt and improve reproducibility too.

Overall, BEACON found 14 imcomplete fixes and 8 new bugs with 10 CVEs assigned.


