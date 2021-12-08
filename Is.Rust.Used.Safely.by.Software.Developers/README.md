# [Is.Rust.Used.Safely.by.Software.Developers](https://dl.acm.org/doi/10.1145/3377811.3380413)

This work did extensive research on current rust crates and summarized how developers use rust `unsafe`.
Here are some of their findings:

- How much do developers use Unsafe Rust? 29%  crates directly includes unsafe.
- How much of the Rust code is Safe Rust? 
- What Unsafe Rust operations are used? Tbl 4.
- What type of unsafe functions are called? Fig 6.
- Does the use of Unsafe Rust chagne over time? No.

## bib

```
@inproceedings{10.1145/3377811.3380413,
    author = {Evans, Ana Nora and Campbell, Bradford and Soffa, Mary Lou},
    title = {Is Rust Used Safely by Software Developers?},
    year = {2020},
    isbn = {9781450371216},
    publisher = {Association for Computing Machinery},
    address = {New York, NY, USA},
    url = {https://doi.org/10.1145/3377811.3380413},
    doi = {10.1145/3377811.3380413},
    abstract = {Rust, an emerging programming language with explosive growth, provides a robust type system that enables programmers to write memory-safe and data-race free code. To allow access to a machine's hardware and to support low-level performance optimizations, a second language, Unsafe Rust, is embedded in Rust. It contains support for operations that are difficult to statically check, such as C-style pointers for access to arbitrary memory locations and mutable global variables. When a program uses these features, the compiler is unable to statically guarantee the safety properties Rust promotes. In this work, we perform a large-scale empirical study to explore how software developers are using Unsafe Rust in real-world Rust libraries and applications. Our results indicate that software engineers use the keyword unsafe in less than 30% of Rust libraries, but more than half cannot be entirely statically checked by the Rust compiler because of Unsafe Rust hidden somewhere in a library's call chain. We conclude that although the use of the keyword unsafe is limited, the propagation of unsafeness offers a challenge to the claim of Rust as a memory-safe language. Furthermore, we recommend changes to the Rust compiler and to the central Rust repository's interface to help Rust software developers be aware of when their Rust code is unsafe.},
    booktitle = {Proceedings of the ACM/IEEE 42nd International Conference on Software Engineering},
    pages = {246–257},
    numpages = {12},
    location = {Seoul, South Korea},
    series = {ICSE '20}
}
```