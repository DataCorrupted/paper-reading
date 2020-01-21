# [Fidelius.Protecting.User.Secrets.from.Compromised.Browsers](https://trouge.net/papers/fidelius_2018.pdf)

This is a paper in ECS251(winter 20) reading list.

## Summary

This paper described an interesting setting where both browser and the OS are compromised. 
It propose Fidelius, which is a tool that protects privacy in that extreme situation.

Fidelius assumes that I/O devices are not compromised, i.e. there is no keyboard logger nor monitor recorder.
It also assumes that the server is honest and does not do anything irresponsible to the sensitive data, i.e. there is no fishing sites whatsoever.

Fidelius uses extra devices that are independent to the system, it has it's own memory to prevent the system from spoofing.
The input devices sends encrypted message and output device synthesis sensitive information image to prevent from system screen shot.
The device also has two LEDs to tell the user if the system is engaged.

In evaluation, the authors argue that the latency is acceptable and it is long mainly because of rendering.

## Pro

- In Sec VIII A/B the authors argue that the the threats are mitigated.

## Con

- Unrealistic assumption. 

## Comment

This work is interesting to read but the assumption is just too hard. 
How often do you run into totally compromised OSes? 
Yet I believe fishing sites or key loggers are more easy to spot.
So even this paper solves the problem it claim to have, what do we learn from it?

Also, I find this paper lacks novelty.
Anyone, faced with the same problem, would have come up with this idea. 
No one published it before probably because the assumptions are too hard.

## Discussion

### Can we use VM or hypervisor to implement this idea? 

This question is asked in the conference. I believe not. 
As a totally compromised system can spoof the memory in the VM and read whatever it want, this approach is not safe.

## [Video](https://www.youtube.com/watch?v=Dr14zTNCHzU)

## bib
```
@inproceedings{eskandarian2019fidelius,
  title={Fidelius: Protecting user secrets from compromised browsers},
  author={Eskandarian, Saba and Cogan, Jonathan and Birnbaum, Sawyer and Brandon, Peh Chang Wei and Franke, Dillon and Fraser, Forest and Garcia, Gaspar and Gong, Eric and Nguyen, Hung T and Sethi, Taresh K and others},
  booktitle={2019 IEEE Symposium on Security and Privacy (SP)},
  pages={264--280},
  year={2019},
  organization={IEEE}
}
```