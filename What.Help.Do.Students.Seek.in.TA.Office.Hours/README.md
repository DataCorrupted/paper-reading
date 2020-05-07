# [What.Help.Do.Students.Seek.in.TA.Office.Hours](https://dl.acm.org/doi/abs/10.1145/3291279.3339418)

## Summary

This paper focuses on the study of how students do(i.e. what they ask) in office hours and how they interact with TA.

The challenge is that any recording will hide students true intends as they may not ask questions they consider "silly". 
Asking TAs to write a summary for every student will introduce a huge overhead for TA.

The authors proposes a methodology _Design Recipe_ (DR) used in software engineering to ask the student and TA to classify the problems.
In this process, both TA and students try to write a form to record  their interaction.

## Methodology

The authors used DR, and classified all questions into 14 categories(See Fig 2), 6 of which are in DR and 7 of which are not and one being "Other"

In the TA form TA are required to further classify what type of the help is asked(instruction, clarification or verification), yet the student don't have to do it as students may not have any idea. B
But the student do have to classify their question into 14 caregories.
The students and TAs are asked to fill out the form after the session. 

To elimate the biases between TAs, they all host office hours and the students are free to go to anyone without pre-assignments.

Afterwards, the data are collected and evaluated.

## Results

The authors hosted a course that compresses many basic computer science knowledge and recorded all TA-student interaction using this method.
There are 67 students and most of them got A with only one failed.
12 undergraduate TAs are selected for this course.

They found that the average time of visit of students are shaped live "V" with regard to students' grade.
Another finding is that students prefer to ask questions in DR.
Specifically most of them ask about testing and function definition.

Another interesting finding is that the form between students and TAs' have certain differences.

## Comments

### Pros

- Through methodology and experiment.
- Analysis of the result is deep and brings new thinking.

### Cons

- DR approach is limited to programming related courses and is not scale to other courses that are hard to classify student questions.
- No false positive/negative analysis. How do we know the data is not affected in anyway?(For example, is it possible the process of filling a form scare away students?)
- The study is carried out with undergraduate TAs, what happens to graduate TAs and what might be the differences is not addressed.

### Improvements

- The author should've proposed a universal way to classify all the questions asked so that any professor can conduct the same research to help improve their course.
- From my perspective, I would definitely try this approach when TAing Data Structure, where such classification can be easy.

## bib
```
@inproceedings{ren2019help,
  title={What Help Do Students Seek in TA Office Hours?},
  author={Ren, Yanyan and Krishnamurthi, Shriram and Fisler, Kathi},
  booktitle={Proceedings of the 2019 ACM Conference on International Computing Education Research},
  pages={41--49},
  year={2019}
}
```