# 플라즈마\(Plasma\)

Similar to the Lightning Network, Plasma is a series of contracts which runs on top of an existing blockchain to ensure enforcement while ensuring that one is able to hold funds in a contract state with net settlement/withdrawal at a later date

Plasma is composed of five key components

1. An **incentive layer** for persistently computing contracts in an economically efficient manner
2. **Structure for arranging child chains** in a tree format to maximize low-cost efficiency and net-settlement of transactions
3. **MapReduce** computing framework for constructing fraud proofs of state transitions within these nested chains to be compatible with the tree structure while reframing the state transitions to be highly scalable
4. **Consensus** mechanism which is dependent upon the root blockchain which attempts to replicate the results of the Nakamoto consensus incentives
5. **bitmap-UTXO commitment structure** for ensuring accurate state transitions off the root blockchain while minimizing mass-exit costs.

### Reference

[Reading the Plasma White Paper with Ameen Soleimani](https://www.youtube.com/watch?v=jvlunzEl_so&feature=youtu.be) by [Decypher Media](https://www.youtube.com/channel/UC8CB0ZkvogP7tnCTDR-zV7g)

[Plasma in 10 minutes](https://medium.com/chain-cloud-company-blog/plasma-in-10-minutes-c856da94e339)

