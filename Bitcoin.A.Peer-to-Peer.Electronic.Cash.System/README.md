# [Bitcoin.A.Peer-to-Peer.Electronic.Cash.System](https://bitcoin.org/bitcoin.pdf)

This is a paper in ECS251(winter 20) reading list.

## Summary

This white book introduced the notion of Bitcoin, a distributed, decentralized currency system that prevents double-spend problems.

Transaction is guaranteed by signature of the sender and the public key of the sendee.
However, this doesn't prevent the double-spending problem. 
To introduce a universal time stamp without a centralized server, the paper proposed the following method:

- New transactions are broadcast to all nodes
- Each node collect all transactions into their ledger
- Each node tried on WoF to add a block to the chain, the block contains all the transactions it records
- The WoF is broadcast
- A WoF is only accepted after each node verified it
- Acceptance is done by working on the next WoF after the new block

The incentive for each node is that every WoF come with a special block that the first transaction is a few bitcoins given to the solver.
This incentive helps keep the node stay honest, as attacking the chain is not as profitable as solving more blocks.

The hash for each transaction is done in a tree fashion so that the transaction details are not necessary and the block size can be small.

Not all coins needs to be tracked, it can be combined. 
But the paper is not very clear on how this is done.

In Sec 11, an interesting calculation is done. 
This calculation is based on the assumption that the attacker can solve a block before others at rate _q_ and what it might take for an attacker to chase the honest chain.
If _q_ greater or equal than _p_ then eventually(infinite time) attacker can catch up no matter the distance.
Otherwise, we can calculate and get that the distance between honest chain and attack chain is 6 when it is not likely the attacker can fake a chain.
Learn more about [51% attack](https://www.investopedia.com/terms/1/51-attack.asp)

## [Video](https://www.youtube.com/watch?v=TVlo66aOZE0)

## Other readings

[Blockchain Guide](https://bitcoin.org/en/blockchain-guide)

## bib
```
@article{nakamoto2008peer,
  title={Bitcoin: A peer-to-peer electronic cash system},
  author={Nakamoto, Satoshi},
  journal={Bitcoin.--URL: https://bitcoin.org/bitcoin.pdf},
  year={2008}
}
```