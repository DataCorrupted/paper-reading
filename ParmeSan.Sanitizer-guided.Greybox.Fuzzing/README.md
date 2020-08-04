# [ParmeSan.Sanitizer-guided.Greybox.Fuzzing](https://www.usenix.org/conference/usenixsecurity20/presentation/osterlund)

## Summary

Different from coverage based fuzzer, ParmeSan uses sanitizer-based fuzzing method
The intuition is to drive fuzzer to find branches that are interesting(i.e. targets) and try to find potential bugs labelled out by sanitizers.
The experiment shows that ParmeSan find bugs more faster than state of the art. 

## Method
1. Target acquisition
   1. Use sanitizer like ASan(Address), UBSan(Undefined Behavior), TySan(Type), LSan(Leak). [`llvm-diff`](https://llvm.org/docs/CommandGuide/llvm-diff.html) to _statically_ find sanitized Basic Blocks(BB) as _targets_.
   2. Table 1 shows that many BB are redundent. You can remove up to 80% of the BB and still find a path to bug. So we need to prune some _targets_.
   3. Intuition 1(Profile-guided): _Targets_ on hot paths are not interesting. 
      1. (Similar to [ASAP](https://dslab.epfl.ch/pubs/asap.pdf): "most overhead in existing tools is due to only a few “hot” checks, whereas the checks most useful to security are typically “cold” and cheap.")
   4. Intuition 2(Complexity-based): targets in functions that are heavily modified by sanitizers are interesting.
2. Dynamic Control Flow Graph(CFG)
   1. Using statically generated CFG, add edges dynamically(to figure out _indirect call_)
   2. Distance metric, `d(c)` being the distance from a branch condition `c` to any targets. `N(c)` being `c`'s successors.
      1. See Sec 5.2's formular
      2. `1/inf = 0, 1/0 = inf`
   3. Augmenting CFG with DFA
3. Sanitizer-guided fuzer
   1. DFA for fuzzing
   2. Input prioritization. `Branch` recorded with `(runs, distance)` and prioritize by `distance`.
   3. Efficient bug detection(_lazysan_): When solving, using un-instrumented `trace` program to reach target first and then use intrumented version to trigger bug.

## Implementation

Modification based on Angora.

## Evaulation
1. Table 2, 3, 4: Shorter Time to Exposure(TTE) and less coverage to find discovered CVE.
   1. Table 2: Previously found CVEs. *Manual target selection, i.e. skip Target acquisition*
   2. Table 3: Google fuzzer-test-suite. *Target acquisition using ASan, Assertion Errors(AE) are manually targetted*, the author argued that there is using sanitizers to target AE makes little sense.
   3. Table 4: Overall improvement compare to Angora(Geomean diff) is 37% in TTE(a) and 33% in branch coverage(b). But most of the cases we see *little improvement compared to Angora,* only in some cases we see dramatically drop(50%+) in either (a) or (b), including `boringssl`(a), `pcre2`(a, b), `lcms`(a, b), `libxml2`(b), and `re2`(a).
2. Table 5: Sanitizer choices change the result dramatically.
3. Table 6: New bugs. *Little improvement compared to Angora.*
4. Table 7: Each components(_lazysan_, pruning and dynamic CFG) has a positive effect to ParmeSan.
5. Table 8: Run time / compile time overhead is low(2% / 2%). Complexity based pruning shows less targets(?), no pruning increases targets by 539%.
   1. Possible explanation: Run profile pruning first, then complexity based pruning will revive some previously pruned targets.

## Comments

- Nice writing. Though it's Angora based and the experiment shows little improvements compared to Angora, the method part seems quite impressive.
- Pruning intuition lacks justification but works: If hot paths has may not have bugs and thus you don't target hot paths, what are we fuzzing for?
- Distance metric is quite good. It greatly lowers the resource to calculate the distance(from `O(|V|^2)` times of **DFS** to a simple topological sorting.)
- Carefuly experiment over different components effects.
- _lazysan_ optimization, improved fuzzing time by 25%(Table 7).

## bib
```
@inproceedings {251544,
author = {Sebastian {\"O}sterlund and Kaveh Razavi and Herbert Bos and Cristiano Giuffrida},
title = {ParmeSan: Sanitizer-guided Greybox Fuzzing},
booktitle = {29th {USENIX} Security Symposium ({USENIX} Security 20)},
year = {2020},
url = {https://www.usenix.org/conference/usenixsecurity20/presentation/osterlund},
publisher = {{USENIX} Association},
month = aug,
}
```