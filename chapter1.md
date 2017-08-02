Sharding

현재 대부분의 개방형\(public\) 블록체인은 모든 노드\(node\)가 모든 상태\(state\)를 저장하고 모든 거래\(transaction\)을 처리하는 높은 중복성을 지닌다. 이러한 중복성으로 인해 현재의 블록체인은 높은 수준의 보안을 제공할 수 있는 반면 확장성\(scalability\)에 제한이 있다 \(e.g. 비트코인은 초당 3-5개, 이더리움은 7-15개의 거래 처리 가능\).

### 샤딩\(sharding\)의 기본원리

샤딩은 블록체인의 상태\(state\)를 "샤드\(shard\)"라 불리는 k개의 구획\(partition\)으로 나눈다. 기본적인 형태의 샤딩의 경우 각 샤드\(shard\)는 각자의 거래내역을 지니며 샤드에서 이루어지는 거래의 효과는 해당 샤드 내로 제한된다. 좀 더 복잡한 형태의 샤딩의 경우에는 샤드간 통신\(cross-shard communication\)을 통해 하나의 샤드에서의 거래가 다른 샤드의 상태를 변화시킬 수 있다.

Collator라 불리는 노드는 특정 샤드 A 내의 거래를 인정하고 collation을 생산한다. Collation은 collation header를 포함하는데 이는 "샤드 A 내에서 일어나는 거래의 collation이다"라는 메세지이다. 이전 state root 값과 해당 collation의 거래의 merkle root 값, 그 거래들을 처리한 후 상태의 state root 값을 명시한다.

블록은 각 샤드에 대한 collation header를 포함해야 하며 다음의 조건을 만족시키는 경우에만 유효\(valid\)하다.

* 각 collation에 포함된 pre-state root가 해당 샤드의 현재 state root와 일치\(match\)한다
* 모든 collation의 모든 거래들이 유효\(valid\)하다
* Collation의 post-state root가 주어진 pre-state root를 갖는 상태에 거래를 적용한 후의 결과값과 일치한다
* Collation이 해당 샤드에 등록된 collator들의 2/3 이상에 의해 서명된다

이 때 다음과 같은 다양한 수준\(level\)의 노드들이 존재한다

* Super-full node: 모든 collation의 거래를 처리하며 모든 샤드에 대한 상태를 저장 및 유지
* Top-level node: 모든 상위 수준\(top-level\) 블록을 처리하지만 각 collation 내의 거래를 처리 혹은 저장하지 않음. 해당 샤드의 collators의 2/3 이상이 서명하면 이를 유효한 것으로 받아들인다
* Single-shard node: top-level node로 활동하면서 특정 샤드의 모든 거래를 처리하며 샤드의 상태를 저장 및 유지한다 

### Reference

[Sharding FAQ](https://github.com/ethereum/wiki/wiki/Sharding-FAQ)

