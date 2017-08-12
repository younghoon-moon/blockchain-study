# 라이트닝 네트워크\(Lightning Network\)

### 1. 비트코인의 확장성\(scalability\) 문제

현재 비트코인은 가십\(gossip\) 프로토콜을 사용하여 모든 노드들이 모든 상태의 변화를 서로에게 전파하고 이를 통해 합의에 이르는 시스템이다. 하지만 이는 모든 참가자가 비트코인 네트워크에서 일어나는 모든 거래내역들을 확인해야 하기 때문에 글로벌 금융 거래를 처리하기에는 상당한 걸림돌로 작용한다. 예를 들어 비자\(Visa\)의 경우 2013년 연휴 당시 [초당 최대 47,000건의 거래를 처리](http://www.visa.com/blogarchives/us/2013/10/10/stress-test-prepares-visanet-for-the-most-wonderful-time-of-the-year/index.html)하였고 현재에도 하루 평균 수억건의 거래를 처리하고 있는 반면 비트코인은 1MB 블록크기의 제한으로 인해 초당 3~5개의 거래밖에 처리하지 못한다. 만약 비트코인이 비자와 같은 거래량을 처리하기 위해서는 블록의 크기가 약 10GB 이상이 되어야 하는데 이는 년간 500TB\(테라바이트\) 이상의 저장공간을 차지하게 된다.

만약 블록의 크기기 지나치게 증가되면 블록체인의 검증과 블록의 채굴에 참가하기 위해 필요한 저장공간과 연산능력 및 네트워크 성능이 급격히 높아져 네트워크에 참가할 수 있는 노드\(node\)와 채굴자\(miner\)들의 수가 크게 감소하게 된다. 그렇게 되면 네트워크가 소수의 신뢰받는 중앙화된 노드들을 중심으로 형성되어 현재 중앙화된 시스템이 앉고있는 문제점들을 그대로 답습할 우려가 있다.

### 2. 라이트닝 네트워크\(Lightning Network\)란?

라이트닝 네트워크\(Lightning Network\)는 비트코인 확장성 문제에 대한 해결책으로 제시되었으며** 블록체인 바깥에서\(off-chain\) 결제채널\(payment channels\)의 네트워크**를 통해 낮은 수수료로 다량의 소액거래\(micropayment\)를 처리할 수 있도록 시스템이다. 블록체인 바깥에서 이루어지지만 실제로 이루어지는 모든 거래는 유효한 비트코인 거래로서 중간 관리인\(custodian\) 없이 안전하게 거래를 성사시킬 수 있다.

### 3. 라이트닝 네트워크의 작동원리

#### 3.1. 결제채널의 생성

철수와 영희가 결제채널\(payment channel\)을 만든다고 하면 다음의 절차를 거치게 된다.

1. **Funding Transaction 생성**. 철수와 영희는 각자 일정량의 비트코인\(BTC\)을 입력값\(input\)으로 보내는 Funding Transaction을 생성한다. 이 때 Funding Transaction의 출력값\(output\)은 2-of-2 다중서명\(multi-sig\) 스크립트로서 철수와 영희의 서명이 모두 있어야 spend 할 수 있다. 
2. 고 를 출력값\(output\)으로 하는 Funding Transaction을 생성한다. 이 때 철수와 영희는 Funding Transaction에 대한 서명을 서로 교환하지 않는다. 
3. 철수와 영희는 처음에 넣은 BTC를 각자에게 환불\(refund\)하는 최초의 Commitment Transaction을 생성. 이 때 SIGHASH\_NOINPUT

철수와 영희는 최초 채널 Funding Transaction에 대한 입력값\(input\)과 출력값\(output\)을 생성하지만 거래에 서명은 하지 않은 상태. Funding Transaction의 출력값은 2-of-2 다중서명 스크립트. 철수와 영희는 2-of-2 출력값에서 원래 금액을 자신들에게 환불하는 거래를 생성하기 전까지 첫 번째 Funding Transaction에 대한 서명을 교환하지 않는다.  거래에 서명을 하지 않는 이유는

누굴 탓할까\(ascribing blame\)

OP CHECKSEQUENCEVERIFY

**Revocable Sequence Maturity Contract \(RSMC\)**는 특정 기간 이후\(e.g. 1,000 확인confirmations\)에 실행될 수 있지만 그 전에는 취소\(revoke\)될 수 있는 계약을 말하며

### Reference

[“The Bitcoin Lightning Network”: Paper \(PDF\) DRAFT Version 0.5.9.1](https://lightning.network/lightning-network-paper.pdf)

[SF Bitcoin Devs Seminar: Scaling Bitcoin to Billions of Transactions Per Day](https://www.youtube.com/watch?v=8zVzw912wPo&t=20m15s)

[EB80 – Joseph Poon & Tadge Dryja: Scalability And The Lightning Network](https://www.youtube.com/watch?v=fBS_ieDwQ9k)

