# [IOTFUZZER.Discovering.Memory.Corruptions.in.IoT.Through.App-based.Fuzzing](https://web.cse.ohio-state.edu/~lin.3021/file/NDSS18b.pdf)

[Talk Video](https://www.youtube.com/watch?v=Ys2FBmdbdIw)

## Summary

This paper focuses on IoT fuzzing. 
It does **black box** fuzzing, which requires almost no binary analysis. 
The author used the fact that most IoT devices are controlled by mobile devices over network, thus feeding input from the mobile devices would be enough. 
This work focuses on finding memory bugs and found 15 of them in real world across 17 devices.


## Difficulties

- Hard to obtain binaries: Vender's don't publish them
- Hard to unpack: they run on different setups
- Hard to analysis: Only binary available

Recall last paper we talked: Some of them run in bare metal

## Solution

Feed input from network:

- Mutate field in network packet is hard: mutate from constants and user input(UI)
- Devices communicate encrypted: identify encryption function
- How do we know it crashed: Monitor connection(TCP) and send heart beat(UDP)

**Function hook**
For functions asking for constants(MAC address, Location, etc.), hook the function to provide any input to the message packet and thus send to the fuzzer.

**Fuzzing policy**
- Double the string or pad "A" to try trigger stack overflow.
- Change int/float

## Pro

- 15 real-world memory corruption found(Quite superising)
- Black box fuzzing

## Con

- Can't locate the bug
- Due to network connection may have false positive.
- Requires a mobile device to do the test, doesn't scale. 
- Is this fuzzing or just input.