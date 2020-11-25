# [Looking.from.the.Mirror.Evaluating.IoT.Device.Security.through.Mobile.Companion.Apps](https://www.usenix.org/conference/usenixsecurity19/presentation/wang-xueqiang)

## Summary

This paper focuses on _similarity_ between apps rather than bug finding. 
The intuition is _reuse_ of codes, thus one vulnerability leads  to another.
To tackle the scalability problem, the paper had another intuition: re-usage can be _indirectly inferred from the mobile companion apps_.

The author collected \~3,000 applications as their database. 
The result shows that there are problems in the following 4 aspects:

- Known bugs can exist in a re-branded product even though the bugs has been fixed in the original product.
- Vulnerable hardware shared by different products can suffer from the same vulnerability.
- Protocol 
- Backend service

## App analysis

The authors build a platform that "clusters" mobile applications that are used to control IoTs.

### Device interface analysis

- **Response extraction**: Track network API.
- **Pairing response and request**: Share similar call stack.
- **Reconstruct request**

Generates a set of request and response pairs.
A device is said to have a similar interface as another device if they both accept similar requests and output similar responses.

### Imprint analysis 

- device (backdoor) keywords
- certificates and keys
- non-trivial usernames and passwords
- special URLs

### [Fuzzy hash analysis](https://ssdeep-project.github.io/ssdeep/index.html)

## Cross app analysis	

- Similar software
- Similar hardware
- Similar protocol

## Findings 

- 118.2s to analysis one app.
- 2.1% apps cannot be analysised.
- Table 2 / 3
- Case study in 3.3.2 \~ 3.3.5

## Comment

### Pro

- Scalability: \~3000 apps analysised.
- New bugs found... or no new bugs found. After all, they re-found existing bugs in other apps.
- Insight into IoT industries: Small vendors take little care about their product's security. Also there are many complications due to the existence of re-branding.

### Con

- This paper seems to be a work of little impact. The problem they are solving is more like an industry malpractice rather than a research topic.


## bib
```
@inproceedings {236342,
author = {Xueqiang Wang and Yuqiong Sun and Susanta Nanda and XiaoFeng Wang},
title = {Looking from the Mirror: Evaluating IoT Device Security through Mobile Companion Apps},
booktitle = {28th {USENIX} Security Symposium ({USENIX} Security 19)},
year = {2019},
isbn = {978-1-939133-06-9},
address = {Santa Clara, CA},
pages = {1151--1167},
url = {https://www.usenix.org/conference/usenixsecurity19/presentation/wang-xueqiang},
publisher = {{USENIX} Association},
month = aug,
}
```
