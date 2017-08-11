# 플라즈마\(Plasma\)

플라즈마\(Plasma\)는 일련의 스마트 컨트랙트를 통해 최상위 블록체인\(root blockchain\) 위에 하위 블록체인\(child blockchain\)을 구현하는 프레임워크\(framework\)이다. 하위 블록체인이 대부분의 연산을 독립적으로 실시하고 주기적으로 그 결과를 최상위 블록체인에 기록함으로써 연산력의 중복을 줄이고 대량의 연산을 가능하게 한다. 하위 블록체인들은 독립적으로 실시하는 연산의 유효성이 최상위 블록체인으로부터 파생\(derive\)되기 때문에 최상위 블록체인은 주로 대법원\(Supreme Court\)에 하위 블록체인들은 대법원으로부터 정당성을 물려받는 하위 법원들에 비교되기도 한다. 



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

