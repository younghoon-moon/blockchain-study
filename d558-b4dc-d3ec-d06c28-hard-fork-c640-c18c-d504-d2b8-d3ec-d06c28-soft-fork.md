# 하드포크\(Hard Fork\)와 소프트포크\(Soft Fork\)

### 정의\(definition\)

하드포크\(hard fork\)와 소프트포크\(soft fork\)의 차이점은 하드포크가 _유효하지 않았던\(not valid\)_ 거래나 블록을 _유효\(valid\)하게_ 하도록 합의규칙\(consensus rules\)을 변화시키는 반면 소프트포크는 이전에는 유효했던 거래나 블록이 더 이상 유효하지 않도록 합의규칙을 변화시킨다는 것이다. 즉 하드포크는 거래나 블록이 유효한지에 대한 규칙을 느슨하게 하여 유효한 거래 혹은 블록의 범위를 확대시키는 반면 소프트포크는 유효성에 대한 엄격한 규칙을 적용하여 유효한 거래 혹은 블록의 범위를 축소시킨다. 

| 하드포크\(hard fork\) | 소프트포크\(soft fork\) |
| :---: | :---: |
| 유효하지 않았던 것을 유효하게 | 유효한 것을 유효하지 않게 |
| **느슨한** 규칙의 적용 | **엄격한 **규칙의 적용 |
| 유효한 거래 및 블록의 범위를 **확대** | 유효한 거래 및 블록의 범위를 **축소** |

예를 들어 블록의 크기제한을 현재 1MB에서 2MB로 상향조정하는 규칙의 변화는 하드포크이다. 기존에 유효하지 않았던 1.5MB 블록이 새로운 규칙 하에서는 유효한 것이 되기 때문이다. 반면에 블록 크기제한을 현재 1MB에서 0.75MB로 하향조정하는 규칙의 변화는 소프트포크를 야기하는데 이는 이전에는 유효했던 0.8MB 블록이 새로운 규칙 하에서는 유효하지 않은 블록이 되기 때문이다. 



최근 논란의 중심에 있는 세그윗\(SegWit: Segregated Witness\)은 소프트포크 규칙변화인데, 세그윗이 적용된 거래는 기존 규칙에 부합하여 기존의 노드들에 의해 받아들여지기 때문이다.  





먼저 소프트포크를 살펴보자. 만약 소프크포크가 일어난다면 네트워크는 기존 소프트웨어를 돌리는 노드\("기존 노드"\)와 새로운 소프트웨어를 돌리는 노드\("신규노드"\)로 나눠진다.

이 때 중요하게 구분해야 하는 것이 거래와 블록의 유효성 규칙을 모두 바뀌는가 아니면 블록의 유효성 규칙만이 바뀌는가이다. 거래의 유효성 규칙이 바뀌게 되면 블록의 유효성 규칙은 자동으로 바뀌게\(i.e. 유효하지 않는 거래를 포함하는 블록은 유효하지 않으므로\) 되므로 거래의 유효성 규칙이 바뀌는데 블록의 유효성 규칙이 바뀌지 않는 경우는 없다.  



블록 또한 기존의 합의규칙에 따른 "기존블록"과 새로 적용된 엄격한 합의규칙에 따른 "신규블록"으로 나누어진다. 이 때 기존노드들은 기존블록과 신규블록을 모두 받아들이는 반면 신규노드는 신규블록만을 유효한 것으로 인정한다. 



[Let's Talk Bitcoin! \#333 - On Consensus and All Kinds of Forks](https://letstalkbitcoin.com/blog/post/lets-talk-bitcoin-333-on-consensus-and-all-kinds-of-forks)

2년전만 해도 하드포크라는 단어가 많이 쓰이지도 않았음

네트워크에 disruption을 일으키지 않는 한도 내에서 변화를 signal, activate하고 합의규칙을 바꿀 수 있는 방법을 고안 중

h vs. s signalling mechanisms, miner-activated vs. user-activated

**하드포크와 소프트 포크의 차이점**

하드포크는 expands the options\(ranges\) of the consensus rules, make previously invalid to subsequently valid

nodes follow the 1. highest-difficulty 2. valid chain

소프트포크는 previously valid is now invalid

예시 BIP66 \(1년 반\) - 서명이 validated방법, DER encoding of ECDSA signature to prevent certain class of tx malleability. valid했던 것이 새로운 규칙하에서 invalid 됨. tightening\(not loosening\) of the rules

**divergence on which is the highest-difficulty**

fork 맨날 일어남. eventual settlement \(100 blocks not redeemable\), 4-5 times a week, network latency, synchronization

**divergence on which is valid**

minority chain &gt; majority chain, wipeout \(UASF\)

[Forks, Signaling, and Activation](https://medium.com/@elombrozo/forks-signaling-and-activation-d60b6abda49a) by [Eric Lombrozo](https://medium.com/@elombrozo?source=post_header_lockup)

March 2013 chain fork

[Hard Forks, Soft Forks, Defaults and Coercion](http://vitalik.ca/general/2017/03/14/forks_and_markets.html) by Vitalik Buterin

