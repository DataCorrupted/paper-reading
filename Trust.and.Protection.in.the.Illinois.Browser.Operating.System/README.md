# [Trust.and.Protection.in.the.Illinois.Browser.Operating.System](http://www.cse.psu.edu/~trj1/cse597-s11/docs/Tang_osdi10.pdf)

This is a paper in ECS251(winter 20) reading list.

## Motivation

- Browsers are widely used and become an app platform
- Browsers are plagued with vulnerabilities

## Summary

The paper propose IBOS, a microkernel that focus on browser security. Unlike other approaches that put OS concept into browsers, IBOS put broser into account when writing kernel.

The paper propose a shinked trust computing base(TCB). The kernel puts drivers out and enforces 12 security invariants, including architecture, driver, storage, network and UI. [Same origin policy](https://en.wikipedia.org/wiki/Same-origin_policy) is also enforced.

## Pros

- Security taken into account and invariants enforced.

## Cons

- Didn't prevent all the vulnerabilitys as they are expected to.
- Compare LoC didn't seem fair since this is a micro kernel.

## bib
```
@inproceedings{tang2010trust,
  title={Trust and Protection in the Illinois Browser Operating System.},
  author={Tang, Shuo and Mai, Haohui and King, Samuel T},
  booktitle={OSDI},
  pages={17--32},
  year={2010}
}
```