# [Firmalice.Automatic.Detection.of.Authentication.Bypass.Vulnerabilities.in.Binary.Firmware](https://www.ndss-symposium.org/wp-content/uploads/2017/09/11_1_2.pdf)

## Summary

This paper proposed an approach to analysis authentication bypass in IoT binary blobs. 
It is hard as some of the bianry blobs has no underline OS and thus hard to fuzz.
Also, for IoT devices, the source code is offten not avaliable.

The process can be devided into:

1. Firmware loading. The binary has to be loaded. 
	- Disassembly
	- Base address: find jump address, consecutive address whose value ends with 00.
	- Entry point: find those functions that no one cass.
2. Security policy: determine which point of the program is privilaged
3. Static program analysis: Find a slice(subset) of the program that only concerns authentication.
4. Symbolic execution: execute the path to collect all the constraints
5. Bypass check: Bypass is considered as a optimization problem.

## Pros

- How they dealed with binary blobs that don't have underline OSes.
- Tackled with programs that can't easily run

## Cons

- Security policy relies on human expert, the approach does not scale. Beside, it's hard to work on bugs unknown.
- Evaluation is weak, only 3 binary analysised and all backdoor are known. 

## Comment

One might consider symbolic execution is not good enough, but in this case it's actually a good choice given that binary blobs are hard to execute.

## bib
```
@inproceedings{shoshitaishvili2015firmalice,
  title={Firmalice-automatic detection of authentication bypass vulnerabilities in binary firmware.},
  author={Shoshitaishvili, Yan and Wang, Ruoyu and Hauser, Christophe and Kruegel, Christopher and Vigna, Giovanni},
  booktitle={NDSS},
  year={2015}
}
```