# [Breaking.Through.Binaries.Compiler-quality.Instrumentation.for.Better.Binary-only.Fuzzing](http://static1.1.sqspcdn.com/static/f/543048/28391424/1610229123433/FIBRE_USENIX_21.pdf?token=F1KXP383rJP1UWqGgPASdv5Xlkc%3D)

## Summary

This paper identified the problems in binary fuzzing:

1. Hardware assisted. Heavy overhead.
2. Dynamic binary translators. Heavy overhead.
3. Static binary rewrite.

To lower the overhead, the paper decided to use static binary rewrite. 
It invented a new IR and disassembly to that IR, then instrument the code.
To further optimize it, they optimize for register usage.
The intrumentation has an optimization, but it's similar to Valkyrie's.

Evaluation shows better performance thanks to increased throughtput.  
Another spotlight is that they can fuzz close sourced programs as well as Windows programs.
Evaluation also showed that they have low overhead if register optimization is useful, but it's often useless in Windows.
