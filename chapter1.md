# Sharding

현재 대부분의 개방형\(public\) 블록체인은 모든 노드\(node\)가 모든 상태\(state\)를 저장하고 모든 거래\(transaction\)을 처리하는 높은 중복성을 지닌다. 이러한 중복성으로 인해 현재의 블록체인은 높은 수준의 보안을 제공할 수 있는 반면 확장성\(scalability\)에 제한이 있다 \(e.g. 비트코인은 초당 3-5개, 이더리움은 7-15개의 거래 처리 가능\).

### 샤딩\(sharding\)의 기본원리

샤딩은 블록체인의 상태\(state\)를 "샤드\(shard\)"라 불리는 k개의 구획\(partition\)으로 나눈다. 기본적인 형태의 샤딩의 경우 각 샤드\(shard\)는 각자의 거래내역을 지니며 샤드에서 이루어지는 거래의 효과는 해당 샤드 내로 제한된다. 좀 더 복잡한 형태의 샤딩의 경우에는 샤드간 통신\(cross-shard communication\)을 통해 하나의 샤드에서의 거래가 다른 샤드의 상태를 변화시킬 수 있다.

Collator라 불리는 노드는 특정 샤드 A 내의 거래를 인정하고 collation을 생산한다. Collation은 collation header를 포함하는데 이는 "샤드 A 내에서 일어나는 거래의 collation이다"라는 메세지이다. 이전 state root 값과 해당 collation의 거래의 merkle root 값

### Reference

[Sharding FAQ](https://github.com/ethereum/wiki/wiki/Sharding-FAQ)

