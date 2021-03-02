# [REDQUEEN.Fuzzing.with.Input-to-State.Correspondence](https://synthesis.to/papers/NDSS19-Redqueen.pdf)

## Summary

This paper work on input correspondence. 
It made following heavy assumptions:

1. Input byte and usage in constraints are directly correspond. (Lst 1)
2. Bytes used in constraints are grouped together and there are few compared total number of inputs. (Algo 1)

However, whether these two assumptions is reliable is questionable.
Based on these assumptions, they designed two methods to mutate input:

1. Magic bytes. After tracing, they use different encodings and small mutations to match magic bytes. They also segment inputs sections(colorization) to mutate more bytes without changing the path.
2. Check sum. 


[Others notes](https://note.youdao.com/ynoteshare1/index.html?id=6a4b00d912eab145d1c1f32f11bde3e0&type=note)

## bib

```
@inproceedings{DBLP:conf/ndss/AschermannSBGH19,
  author    = {Cornelius Aschermann and
               Sergej Schumilo and
               Tim Blazytko and
               Robert Gawlik and
               Thorsten Holz},
  title     = {{REDQUEEN:} Fuzzing with Input-to-State Correspondence},
  booktitle = {26th Annual Network and Distributed System Security Symposium, {NDSS}
               2019, San Diego, California, USA, February 24-27, 2019},
  publisher = {The Internet Society},
  year      = {2019},
  url       = {https://www.ndss-symposium.org/ndss-paper/redqueen-fuzzing-with-input-to-state-correspondence/},
  timestamp = {Mon, 01 Feb 2021 08:42:22 +0100},
  biburl    = {https://dblp.org/rec/conf/ndss/AschermannSBGH19.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```