### 블룸필터\(Bloom Filter\)

블룸필터는 확률적 검색 필터로서 찾는 정보가 무엇인지 정확히 명시하지 않고도 원하는 패턴에 부합하는 정보를 찾는 방법으로서 사생활을 보호하면서도 원하는 정보를 찾을 수 있도록 도와준다. SPV 노드의 경우 원하는 거래의 모든 정보를 공개하지 않으면서도 해당 거래를 찾을 수 있도록 해준다.

블룸필터는 길이 N의 이진 배열\(binary array\)과 1부터 N까지의 출력값을 갖는 M개의 해시함수\(hash function\)로 이루어져있다. 해시함수는 결정적으로\(deterministically\) 생성되기 때문에 블룸필터를 구현하는 노드들은 모두 똑같은 해시함수를 갖는다. N과 M값을 조절함으로써 사용자는 정확도\(precision\)와 사생활\(privacy\) 보호 수준을 조절할 수 있도록 한다.

#### Reference

[Chapter 8. Mastering Bitcoin \(2nd Ed.\) by Andreas Antonopoulos](https://github.com/bitcoinbook/bitcoinbook/blob/second_edition/ch08.asciidoc)

