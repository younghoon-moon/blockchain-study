# 크립토노트\(CrpytoNote\)

### 0. 개요\(Overview\)

크립토노트\(CryptoNote\)는

### 1. 비트코인의 사생활\(privacy\) 보호의 문제

사생활\(privacy\) 보호와 익명성\(anonymity\)은 전자화폐의 가장 중요한 요소 중 하나. 전자화폐가 완전한 익명성을 지니기 위해서는 다음과 같은 조건을 만족시켜야 함.

* **추적 불가능성\(Untraceability\)**: 들어오는 거래\(incoming transaction\)의 가능한 발신인\(sender\)들이 해당 거래를 보낼 확률이 모두 동일\(equiprobable\)하다.
* **연결 불가능성\(Unlinkability\)**: 나가는 거래\(outgoing transaction\) 2개가 동일한 사람에게 보내는 것인지 증명\(prove\)할 수 없다.

비트코인의 경우 추적 불가능성을 지니지 못한다. 모든 비트코인 거래는 투명하게 공개되므로 해당 거래의 발신인이 누군지 명확하게\(unambiguously\) 식별할 수 있기 때문이다. [크립트노트 백서](https://cryptonote.org/whitepaper.pdf)에 의하면 비트코인은 연결 불가능성도 지니고 있지 않다는 지적이 나오고 있는데 엄밀한 블록체인 분석\(blockchain analysis\)을 통해 비트코인 사용자와 그들의 거래의 연관성을 찾을 수 있다는 내용을 담은 논문도 많음.

#### 연결 불가능한 결제\(Unlinkable Payments\)

1. 철수가 영희에게 지불을 하는 경우를 가정하자. 영희는 자신의 표준주소\(standard address\)를 공개하고 철수는 해당 주소를 통해 영희의 공개키 \(A, B\)를 확보한다.
2. 영희는 무작위\(random\)로 $$r ∈ [1,l−1]$$을 생성한 후 일회성 공개키\(one-time public key\) $$P = H_s(rA)G+B$$를 계산한다.
3. 철수는 P를 목표키\(destination key\)로 사용하여 \([디피 헬만 키 교환](https://ko.wikipedia.org/wiki/%EB%94%94%ED%94%BC-%ED%97%AC%EB%A7%8C_%ED%82%A4_%EA%B5%90%ED%99%98)의 일부로서\) $$R = rG$$를 거래에 포함시킨다. 

#### 일회성 링 시그니처\(One-time Ring Signatures\)

### Reference

[https://cryptonote.org/](https://cryptonote.org/)

