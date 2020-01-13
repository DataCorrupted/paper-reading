# [Application.Performance.and.Flexibility.on.Exokernel.Systems](http://csl.snu.ac.kr/courses/4190.568/2019-1/exokernel-sosp97.pdf)

This is a paper in ECS251(winter 20) reading list.

## Summary

This paper described an exokernel Xok/ExOS, along with it's customized file system NX. To proof the effectiveness of Xok/ExOS, the authors also wrote Cheetah HTTP server that gained 8x performance gain.

First it introduced exokernel design principles(Sec 3.1):

- Separate protection and management
- Expose allocation
- Expose names
- Expose revocation
- Expose information

The file system they designed allows block level multiplexing and self-descriptive metadata.
Xok, on the other hand, allows wakeup predicates.

## bib
```
@article{kaashoek1997application, 
	title={Application performance and flexibility on exokernel systems}, 
	author={Kaashoek, M Frans and Engler, Dawson R and Ganger, Gregory R and Briceno, H{'e}ctor M and Hunt, Russell and Mazieres, David and Pinckney, Thomas and Grimm, Robert and Jannotti, John and Mackenzie, Kenneth}, 
	journal={ACM SIGOPS Operating Systems Review}, 
	volume={31}, 
	number={5}, 
	pages={52--65}, 
	year={1997}, 
	publisher={ACM} 
}
```