### 블룸필터\(Bloom Filter\)

블룸필터는 확률적 검색 필터\(probabilistic search filter\)로서 찾는 정보가 무엇인지 정확히 명시하지 않고도 원하는 패턴에 부합하는 정보를 찾을 수 있도록 도와준다. SPV 노드의 경우 블룸필터를 사용하여 사생활\(privacy\)을 보호하면서도 필요한 거래내역을 요청 및 획득할 수 있다. 

블룸필터는 길이 N의 이진 배열\(binary array\)과 1부터 N까지의 출력값을 갖는 M개의 해시함수\(hash function\)로 이루어져있다. 아래의 그림은 3개의 해시함수 $$K_1, K_2, K_3$$와 16비트 배열로 구성된 블룸필터를 나타낸다.

 ![](/assets/mbc2_0808.png)





N과 M값을 조절함으로써 사용자는 정확도\(precision\)와 사생활\(privacy\) 보호 수준을 조절할 수 있도록 한다.

#### Reference

[Chapter 8. Mastering Bitcoin \(2nd Ed.\) by Andreas Antonopoulos](https://github.com/bitcoinbook/bitcoinbook/blob/second_edition/ch08.asciidoc)

