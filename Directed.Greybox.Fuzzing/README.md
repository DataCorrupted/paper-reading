# [Directed.Greybox.Fuzzing](https://mboehme.github.io/paper/CCS17.pdf)

## Summary

The paper develops a way to calculate the distance from one block/function(target block/function) to a set of blocks/functions across ICFG and CG. 
It uses a "set" so a seed's distance can be calculated.
Then it uses simulated annealing to schedule the seeds.

It found 39 bugs with 17 CVEs assigned.

# bib

```
@inproceedings{bohme2017directed,
  title={Directed greybox fuzzing},
  author={B{\"o}hme, Marcel and Pham, Van-Thuan and Nguyen, Manh-Dung and Roychoudhury, Abhik},
  booktitle={Proceedings of the 2017 ACM SIGSAC Conference on Computer and Communications Security},
  pages={2329--2344},
  year={2017}
}
```
