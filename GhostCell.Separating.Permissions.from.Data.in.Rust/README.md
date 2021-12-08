# [GhostCell.Separating.Permissions.from.Data.in.Rust](https://dl.acm.org/doi/10.1145/3473597)

GhostCell provides a new data structure for internal mutability.
It solves the problem that it is hard to get multiple mut ref, where it would be necessary in graph.
The paper proves that the structure is safe.

## bib

```
@article{10.1145/3473597,
    author = {Yanovski, Joshua and Dang, Hoang-Hai and Jung, Ralf and Dreyer, Derek},
    title = {GhostCell: Separating Permissions from Data in Rust},
    year = {2021},
    issue_date = {August 2021},
    publisher = {Association for Computing Machinery},
    address = {New York, NY, USA},
    volume = {5},
    number = {ICFP},
    url = {https://doi.org/10.1145/3473597},
    doi = {10.1145/3473597},
    abstract = {The Rust language offers a promising approach to safe systems programming based on the principle of aliasing XOR mutability: a value may be either aliased or mutable, but not both at the same time. However, to implement pointer-based data structures with internal sharing, such as graphs or doubly-linked lists, we need to be able to mutate aliased state. To support such data structures, Rust provides a number of APIs that offer so-called interior mutability: the ability to mutate data via method calls on a shared reference. Unfortunately, the existing APIs sacrifice flexibility, concurrent access, and/or performance, in exchange for safety. In this paper, we propose a new Rust API called GhostCell which avoids such sacrifices by separating permissions from data: it enables the user to safely synchronize access to a collection of data via a single permission. GhostCell repurposes an old trick from typed functional programming: branded types (as exemplified by Haskell’s ST monad), which combine phantom types and rank-2 polymorphism to simulate a lightweight form of state-dependent types. We have formally proven the soundness of GhostCell by adapting and extending RustBelt, a semantic soundness proof for a representative subset of Rust, mechanized in Coq.},
    journal = {Proc. ACM Program. Lang.},
    month = {aug},
    articleno = {92},
    numpages = {30},
    keywords = {Rust, type systems, separation logics}
}
```