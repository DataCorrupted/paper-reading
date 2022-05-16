---
title:
- JIGSAW.Efficient.and.Scalable.Path.Constraints.Fuzzing
author:
- Peter Rong
theme:
- Madrid
date:
- May 16, 2022
classoption: "aspectratio=169"
header-includes: |
    \usepackage{tikz}
    \usetikzlibrary{chains,shadows.blur}
    \usetikzlibrary{shapes,shapes.geometric,backgrounds,arrows,automata,positioning,cd,}
    \tikzset{
        cfgedge/.style   = {black, ->, >=stealth},
        thickcfgedge/.style   = {black, ->, >=stealth, line width=1.1pt},
    }
---

# Motivation
```{=latex}
\begin{figure}
    \centering
    \begin{tikzpicture}[
            auto,
            box/.style = {
                    draw,rounded corners,blur shadow,fill=white,
                    align=center,text width=3cm,
                    node distance=5mm
                },
        ]
        \node [box] [minimum width=5cm, text width=5cm](source) {Source code(C, C++, ...)};
        \node [draw = none, below = 6cm of source] {\textbf{Greybox fuzzer}};
        \draw[thick,dotted] ($(source.south west)+(-0.5,-0.4)$)  rectangle ($(source.south west)+(+14.5,-6.5)$);

        \node [box] [below = of source](IR) {Intermediate representation (IR)};
        \node [box, right= 1cm of IR] (instrumentation) {Instrumentation};
        \node [box, below=of instrumentation] (P) {Testing program};
        \path (source) edge[cfgedge] node[left]{Compiler frontend}  (IR);
        \path (IR) edge[cfgedge] (instrumentation);
        \path (instrumentation) edge[cfgedge] node[right] {Compiler backend} (P);
        \node [box, below = 3cm of P] (S) {Seed store};
        \node [box, right = 1cm of S] (I) {Initial seed};
        \path (I.west) edge[cfgedge] (S.east);
        \node [box, below left = 1cm and 2cm of P] (M) {Mutation};
        \node [box, below right = 1cm and 2cm of P] (B) {Behavior observation};
        \node [above=of B] (D) {};
        \path (P.south east) edge[cfgedge, bend left] (B.north west);
        \path (B.south west) edge[cfgedge, bend left, align = left] node[above] {Has new \\ behavior} (S.north east);
        \path (S.north west) edge[cfgedge, bend left, align = left] node[above] {Seed \\ selection} (M.south east);
        \path (M.north east) edge[cfgedge, bend left, align = left] node[below] {New \\ input} (P.south west);
        \path (B.north) edge[cfgedge, bend left, align=left] node[right] {Discard if no \\ new behavior} (D.south);
    \end{tikzpicture}
\end{figure}
```

# To increase flipping rate (Fig 1)...

- Increase branch accuracy (QSYM)
- Increase throughput (AFL)

# It's hard to increase throughput...

- Program state reset, `fork()` is slow, branch is slow
- New tests are passed through FS
- Lock contention prevents large scale parallelism can be slow if cores
    - Input sync
    - Global state sharing (e.g. branch counting)

# Proposed solution: JIT'ed native function

- Native function don't need to reset state, no branch in JIT'ed function
- New tests are passed as function arguments, i.e. through memory
- Native functions are lock free from each other.

# Overview of solution

- Frontend: branch collection
- Middle end: generate native function, JIT compile it.
- Backend: Solve the native function(s).

# Frontend

- Use DFSan to collect all branches (Like Angora)
- Branches that are similar in AST are cached for later lookup.
    - e.g. `x > 10` and `y > 20` are the same from the AST perspective.
- Logical operations:
    - Or: Parse as 2 or more branches, solving either can solve the branch.
    - And: Generate a clause for each one and joint solve it.
    - Not: Use opposite operation. (e.g. `==` -> `!=`)

# Middle end

- Change comparisons to loss function (Table 1).
- Cancel optimization, it will be slow.

# Backend: Solving strategy

- GD, Prioritize satisfiability
- Joint optimization, minimize the sum of loss function.

# Parallelism

- Each thread has a solver and a JIT engine to reduce lock.
- Cache compiled AST nodes without leaves, using hash to find them.
- Async sloving, i.e. frontend and backend are async.

# Evaluation

## Single thread
- JIGSAW w/ 1M iterations, Z3 w/ 60s timeout
- JIGSAW solves 93.2% of Z3 solved nested branches, 98.81% last branch.
- Caching reduce huge amount of JIT time (9000+s -> 8s)
- 10x nested and 44.5x single branch compared to Z3

## Multi-thread

- Near linear scalability

## End-to-end

- Ranked 1 in Fuzzbench
- Better than Angora and Z3 on 5 programs.

<!-- This is a README that can be parsed by pandoc to generate a pdf -->
<!-- Try run it with `pandoc -t beamer -V theme:Madrid README.md -o README.pdf` -->
