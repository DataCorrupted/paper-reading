# [Scale.and.Performance.in.the.Denali.Isolation.Kernel](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.58.4705&rep=rep1&type=pdf)

This is a paper in ECS251(winter 20) reading list.

## Summary

This paper Denali, an isolated kernel that focuses on performance and scalability to tackle Internet services.

It first identified the cases where isolated kernel is needed:

- Dynamic content is CDN
- Push service to host
- Internet measurement and experiment
- Mobile code

and the design principles(Sec 2.1):

- Expose low-level resources
- Prevent direct sharing by exposing only private virtualized namespaces.
- Need for scale.
- Simplicity.

Denali designed a new instruction set ISA to be a subset of x86 instruction set. It gives every VM a virtualized memory address space. I/O interrupt is also designed.

The evaluation shows that Denali showed little overhead compared to BSD when doing TCP and HTTP requests(Fig 3). 
Yet the LoC in core kernel is fewer than Linux 2.4.16.
Further experiments(including the one on game server) showed that scalability is also addressed.

## Pro

- Scalability

## Con

- Backward compatibility

## bib
```
@article{whitaker2002scale,
  title={Scale and performance in the Denali isolation kernel},
  author={Whitaker, Andrew and Shaw, Marianne and Gribble, Steven D},
  journal={ACM SIGOPS Operating Systems Review},
  volume={36},
  number={SI},
  pages={195--209},
  year={2002},
  publisher={ACM}
}
```