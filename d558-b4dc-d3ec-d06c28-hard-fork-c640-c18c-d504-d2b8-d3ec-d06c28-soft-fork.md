# 하드포크\(Hard Fork\)와 소프트포크\(Soft Fork\)

하드포크\(hard fork\)와 소프트포크\(soft fork\)의 차이점은 하드포크는 _유효하지 않았던\(not valid\)_ 거래나 블록을 _유효\(valid\)하게_ 하도록 합의규칙\(consensus rules\)을 변화시키는 반면 소프트포크는 이전에는 유효했던 거래나 블록이 더 이상 유효하지 않도록 합의규칙을 변화시킨다. 따라서 하드포크는 거래나 블록이 유효한지에 대한 규칙을 느슨하게 하여 유효한 거래 혹은 블록의 범위를 확대시키는 반면 소프트포크는 유효성에 대한 규칙을 엄격하게 적용하여 유효한 거래 혹은 블록의 범위를 축소시킨다.

| 하드포크\(hard fork\) | 소프트포크\(soft fork\) |
| :---: | :---: |
| 유효하지 않았던 것을 유효하게 | 유효한 것을 유효하지 않게 |
| **느슨한** 규칙의 적용 | **엄격한 **규칙의 적용 |
| 유효한 거래 및 블록의 범위를 **확대** | 유효한 거래 및 블록의 범위를 **축소** |

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

