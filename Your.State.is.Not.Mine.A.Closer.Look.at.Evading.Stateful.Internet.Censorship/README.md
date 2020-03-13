# [Your.State.is.Not.Mine.A.Closer.Look.at.Evading.Stateful.Internet.Censorship](https://conferences.sigcomm.org/imc/2017/papers/imc17-final59.pdf)

## Summary

This paper focus on Internet censorship and the evasion of it, especially Great Fire Wall(GFW) in China.

### Threat model

1. The client initiates a TCP connection with the server. 
2. The GFW establishes a shadow connection by creating a TCB and can read from and inject packets to the original connection. 
3. Meanwhile, there could be network middleboxes on the path.
4. (DNS request is sent over TCP instead of UDP, they didn't mention it.)

### Previous methods

The paper first reviews previous evasion methodologies, including:

1. TCP Control Block(TCB) creation: Send a false SYN to fool the GFW into creating a useless TCB.
2. Data reassembly: 1) Out-of-order data overlapping and 2) In-order data overlapping
3. TCB tear down: Send RST or RST/ACK to trick the GFW into tear down TCB.

### New assumptions

The experiment shows that the GFW is evolving and previous methods don't work as some previous assumptions do not stand anymore.
Based one these experiments they formulated new assumptions:

1. The GFW creates TCB upon SYN packets as well as SYN/ACK packets(Old approach 1 fails)
2. The GFW has a re-synchronizes state when it 1) sees multiple SYN packets 2) multiple SYN/ACK from server or 3) SYN/ACK with acknowledge number different from SYN.(Old approach 2 fails)
3. On RST or RST/ACK, the GFW may re-synchronization instead of tearing down TCB.(Old approach 3 fails)

### Proposed methods

Based on these new assumptions, the paper propose new evasion techniques:

- Resync + Desync: After receive SYN/ACK(Connection established), insert a out-of-order (garbage) data packet to interfere with the GFW's TCB
- TCB Reversal: Send SYN/ACK prior to connection to fool the GFW into thinking the client is the server since the GFW don't censor data from the server.

### Impl

The authors developed a tool based on old and new evasion techniques called INTANG.
Besides the approach mentioned above, ITANT also converts UDP DNS request into TCP request to re-use the technique above.
INTANG will handle everything in background and thus is transparent to the application.

Evaluation showed that INTANG has high successful evasion rate shown in Table 4. 
Also, INTANG is able to allow Tor, which has been baned in China for over 7 years.

## Pros

- A through investigation into the GFW mechanism.
- New evasion approach proposed and implemented, great result.

## Cons

- Re-sync + de-sync will fail just like previous ones as the GFW evolves.
- Un-explained data in Table 6: Why nodes Tianjing perform so bad at DNS request?

## bib
```
@inproceedings{wang2017your,
  title={Your state is not mine: a closer look at evading stateful internet censorship},
  author={Wang, Zhongjie and Cao, Yue and Qian, Zhiyun and Song, Chengyu and Krishnamurthy, Srikanth V},
  booktitle={Proceedings of the 2017 Internet Measurement Conference},
  pages={114--127},
  year={2017}
}
```