# [Be.Sensitive.and.Collaborative.Analyzing.Impact.of.Coverage.Metrics.in.Greybox.Fuzzing](https://www.usenix.org/conference/raid2019/presentation/wang)

## Summary

This paper summarized all branch counting methods. 
It formally defined a term _sensitivity_, which is a partial order.
The authors did experiment on all popular methods and come to a conclusion that there is not a method that is strictly better than others.

they also realized that it's better to combine two methods than use only one.

## Comment

This is another paper that stated the elephant in the room: there is no perfect branch counting method.
It's about tradeoff, how much resources do you have?

However, the finding that combining is better is quite interesting.

Most results in this paper though, can't be useful for fuzzer2 as they used random mutation.

## bib
```
@inproceedings {241986,
  author = {Jinghan Wang and Yue Duan and Wei Song and Heng Yin and Chengyu Song},
  title = {Be Sensitive and Collaborative: Analyzing Impact of Coverage Metrics in Greybox Fuzzing},
  booktitle = {22nd International Symposium on Research in Attacks, Intrusions and Defenses ({RAID} 2019)},
  year = {2019},
  isbn = {978-1-939133-07-6},
  address = {Chaoyang District, Beijing},
  pages = {1--15},
  url = {https://www.usenix.org/conference/raid2019/presentation/wang},
  publisher = {{USENIX} Association},
  month = sep,
}
```