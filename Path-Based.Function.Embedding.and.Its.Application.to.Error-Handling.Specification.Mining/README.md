# [Path-Based.Function.Embedding.and.Its.Application.to.Error-Handling.Specification.Mining](https://web.cs.ucdavis.edu/~rubio/includes/fse18.pdf)

## Summary
This paper introduced a new technique _Func2vec_ to identify function synonyms. 
The authors realized 3 difficulties(semantically and syntically dissimilar; similar name but not synonyms; and vice versa) in this task and decided to encode functions using random walk and then trained an NN to model function encoding to a vector and use K-means to cluster them. 
Experiments in Sec 4 used two data set prepared manually that demonstrates _Func2vec_ has the ability to cluster synonyms with high true positive rate.

The authors also proposed an application for function synonyms: specification mining. 
The authors pointing out that the support for error handling specification is low in normal cases. 
But by clustering functions together, the support boosted. 
Sec 6 showed experiment on 48 drivers and 10 Linux FS, the result showed that _Func2vec_ can be used to mine specifications with different context(Tbl 4, Col 1&2), semantically dissimilar functions(Tbl 4, Col 3), and event found bugs in error handling(Fig 8).

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
In general this paper is easy to read and the idea is quite interesting, although not groundbreaking. 
The authors focused on error-handling, yet more application can be explored. 
One application of function synonyms paring is plagiarism checking. 
Is it possible if we change the encoder in Sec 3.1 then we can use _Func2vec_ for something else? 

## Discussion with the Author
1. 
**Why cluster specifications?**  
Or else we would have tons of low-support specifications that are basically saying the same thing.

2. 
**What if there are low labels in a sentence?**  
There is going to be at least one label because you started from a node with label. 
Tried to throw away sentences with low amount labels(threshold = 2), the result is not affected much.

3. 
**Why k steps instead of k labels for the length of the random walk?**  
The intuition is that the labels are close to each other in the sense of instructions and therefore the sentence reflects what's shortly followed by that label. 
k labels may take the path too far away.

4. 
**Sec 4 last Paragraph: "it is possible that Func2vec will perform differently for classes of function synonyms we are unaware   of." Why saying that?**  
No experiment has been done on code besides the Linux kernel by the time of the paper writing. 
Trying OpenSSL, no results for now.

5. 
**How do specifications get clustered?**  
(Without getting too much math)  Functions in Context(Ctx) and Response(Rsp) are synonyms or the same. 
For two specifications, if the Ctx set or Rsp set is the same, things can be simple. 
If both sets are different, the matching algorithm needed to match functions between two Ctx sets and Rps sets, respectively. 
Didn't explain the matching algorithm in detail and not satisfied with the answer XD.

6. 
**How was the bug found when the response is missing?(Fig 7) Chances are that this function cannot be clustered, nor the   specification.**  
The function is still clustered because one missing function call wouldn't affect that much.(As we suspected) However, the specification didn't match. 
They got the specification first and then did an extra static analysis to check for each function "With this Ctx do you have this Rsp" and found one response missing.
 
7. 
**Why did the paper look like two parts(Func2vec and specification mining) that are weakly connected?**  
This paper actually started off by mining specifications, that's the main goal. 
But as they revise the paper along the way, function synonymy(Func2vec) grows from a paragraph to two sections(Sec 3 & 4). 


8. 
**Justification for the random walk? Why randomly step into functions?**  
We want to capture what's inside a function as well as the following instructions because we believe there are many wrappers in the kernel. 
For example:
```c
    { a0; b0; c0; }

    f1() { b1; c1;}
    { a1; f1(); }  

    f2() { b2; c2;}
    { a2; f2() }
```
Such a structure can be captured by the random walk.
(Still not satisfied, somehow Aditya believes this random walk is the highlight of this paper)

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