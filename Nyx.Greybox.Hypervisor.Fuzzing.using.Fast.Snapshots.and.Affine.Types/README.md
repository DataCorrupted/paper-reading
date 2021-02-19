# [Nyx.Greybox.Hypervisor.Fuzzing.using.Fast.Snapshots.and.Affine.Types](https://www.usenix.org/conference/usenixsecurity21/presentation/schumilo)

## Summary

This paper focuses on fuzzing hypervisors.
The motivation is that in a cloud based setting, hypervisors can ba an attack surface, given an attacker can create a host OS on this hypervisor.

Nyx solved some challenges in fuzzing hypervisor:

- Input space. The input space of a hypervisor is the _program_ that runs in the host VM. 
- Nested VM. To monitor hypervisor's code coverage, you need another VM outside it. but nested VM is not supported in the hardware level.
- Fast recovery. As hypervisor is a stateful program, every time the hypervisor and VM inside will need to be resetted. 

It used the following design:

- Affine typed input. It provided a mechanism for user to specify input grammar to generate a C program that runs in VM. This is challenging as context free grammar can't generate useful input. For example, CFG can generate use-after-free code, which crashes hypervisor while it's not hypervisor's fault.
- Fast recovery. Recover register is trivial. Memory is resetted Nyx logged all the dirty memory pages used. Devices except for disk is resetted using `memcp`. Disks is harder and they used a hash set to log all the used space.

In evaluation, they compared with HyperCube. 
The result shows that most of the cases they are the same, except for two cases they are significantly higher and in one case, lower.
They explained that it's because many device emulators' code is easy and straight forward.

They also test snapshot recovery speed.
Nyx is only a little bit slower than AFL fork server, considering they have to recover the whole hypervisor, this is promising.

They also found 44 new vulnerabilities. 5 bugs have CVE assigned already.

## Pros

- The design of fast recovery. They used one method to cover almost all device emulators. 
- They found real world bugs, and have CVE assigned.

## Cons

- They only tested QEMU and BHYVE. The scope is too small.
- The branch coverage is not significantly higher(Table 1)
- Need user interaction.

## bib
```
@inproceedings {263866,
  title = {Nyx: Greybox Hypervisor Fuzzing using Fast Snapshots and Affine Types},
  booktitle = {30th {USENIX} Security Symposium ({USENIX} Security 21)},
  year = {2021},
  address = {Vancouver, B.C.},
  url = {https://www.usenix.org/conference/usenixsecurity21/presentation/schumilo},
  publisher = {{USENIX} Association},
  month = aug,
}
```