# [SyRust.Automatic.Testing.of.Rust.Libraries.with.Semantic-Aware.Program.Synthesis](https://dl.acm.org/doi/10.1145/3453483.3454084)

## Summary

SyRust uses compiler feedback to automatically generate use cases of a rust crate to do automated testing.
It found 4 new bugs.

## bib

```
@inproceedings{10.1145/3453483.3454084,
    author = {Takashima, Yoshiki and Martins, Ruben and Jia, Limin and P\u{a}s\u{a}reanu, Corina S.},
    title = {SyRust: Automatic Testing of Rust Libraries with Semantic-Aware Program Synthesis},
    year = {2021},
    isbn = {9781450383912},
    publisher = {Association for Computing Machinery},
    address = {New York, NY, USA},
    url = {https://doi.org/10.1145/3453483.3454084},
    doi = {10.1145/3453483.3454084},
    abstract = {Rust’s type system ensures the safety of Rust programs; however, programmers can side-step some of the strict typing rules by using the unsafe keyword. A common use of unsafe Rust is by libraries. Bugs in these libraries undermine the safety of the entire Rust program. Therefore, it is crucial to thoroughly test library APIs to rule out bugs. Unfortunately, such testing relies on programmers to manually construct test cases, which is an inefficient and ineffective process. The goal of this paper is to develop a methodology for automatically generating Rust programs to effectively test Rust library APIs. The main challenge is to synthesize well-typed Rust programs to account for proper chaining of API calls and Rust’s ownership type system and polymorphic types. We develop a program synthesis technique for Rust library API testing, which relies on a novel logical encoding of typing constraints from Rust’s ownership type system. We implement SyRust, a testing framework for Rust libraries that automatically synthesizes semantically valid test cases. Our experiments on 30 popular open-source Rust libraries found 4 new bugs.},
    booktitle = {Proceedings of the 42nd ACM SIGPLAN International Conference on Programming Language Design and Implementation},
    pages = {899–913},
    numpages = {15},
    keywords = {API Testing, Program Synthesis, Rust},
    location = {Virtual, Canada},
    series = {PLDI 2021}
}
```