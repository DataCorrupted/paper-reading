# [Path-Based.Function.Embedding.and.Its.Application.to.Error-Handling.Specification.Mining](https://web.cs.ucdavis.edu/~rubio/includes/fse18.pdf)

## Summary
This paper introduced a new technique _Func2vec_ to identify function synonyms. The authors realized 3 difficulties(semantically and syntically dissimilar; similar name but not synonyms; and vice versa) in this task and decided to encode functions using random walk and then trained an NN to model function encoding to a vector and use K-means to cluster them. Experiments in Sec 4 used two data set prepared manually that demonstrates _Func2vec_ has the ability to cluster synonyms with high true positive rate.

The authors also proposed an application for function synonyms: specification mining. The authors pointing out that the support for error handling specification is low in normal cases. But by clustering functions together, the support boosted. Sec 6 showed experiment on 48 drivers and 10 Linux FS, the result showed that _Func2vec_ can be used to mine specifications with different context(Tbl 4, Col 1&2), semantically dissimilar functions(Tbl 4, Col 3), and event found bugs in error handling(Fig 8).

## Pros

- (Writing) This paper has clear definition of all notions and definitions and in most cases has examples followed, making it relatively easy to read
- (Writing) The authors keep reminding the readers of the novelty in Abstract, Intro, Conclusion.
- Real world bugs are found.
- The new combination of different old ideas generated something new

## Cons
- The ideas is not groundbreaking. Random walk and NLP are quite cliche. 
- The authors proposed an application, yet it didn't mention how important this application is.
- Sec 3.2 and 3.3 is too shallow. I would expect more details in it instead of some references(Sec 3.4).
- The experiment is limited to Linux code. In the last paragraph of Sec 4 the author acknowledged that the tool may perform differently, I wonder if this tool have any real-world usage besides checking Linux code.

## Comment
In general this paper is easy to read and the idea is quite interesting, although not groundbreaking. The authors focused on error-handling, yet more application can be explored. One application of function synonyms paring is plagiarism checking. Is
it possible if we change the encoder in Sec 3.1 then we can use _Func2vec_ for something else? 

## bib
```
@inproceedings{defreez2018path,
  title={Path-based function embedding and its application to error-handling specification mining},
  author={DeFreez, Daniel and Thakur, Aditya V and Rubio-Gonz{\'a}lez, Cindy},
  booktitle={Proceedings of the 2018 26th ACM Joint Meeting on European Software Engineering Conference and Symposium on the Foundations of Software Engineering},
  pages={423--433},
  year={2018},
  organization={ACM}
}
```