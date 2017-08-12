# 라이트닝 네트워크\(Lightning Network\)

### 1. 비트코인의 확장성\(scalability\) 문제

현재 비트코인은 가십\(gossip\) 프로토콜을 사용하여 모든 노드들이 모든 상태의 변화를 서로에게 전파하고 이를 통해 합의에 이르는 시스템이다. 하지만 이는 모든 참가자가 비트코인 네트워크에서 일어나는 모든 거래내역들을 확인해야 하기 때문에 글로벌 금융 거래를 처리하기에는 상당한 걸림돌로 작용한다. 예를 들어 비자\(Visa\)의 경우 2013년 연휴 당시 [초당 최대 47,000건의 거래를 처리](http://www.visa.com/blogarchives/us/2013/10/10/stress-test-prepares-visanet-for-the-most-wonderful-time-of-the-year/index.html)하였고 현재에도 하루 평균 수억건의 거래를 처리하고 있는 반면 비트코인은 1MB 블록크기의 제한으로 인해 초당 3~5개의 거래밖에 처리하지 못한다. 만약 비트코인이 비자와 같은 거래량을 처리하기 위해서는 블록의 크기가 약 10GB 이상이 되어야 하는데 이는 년간 500TB\(테라바이트\) 이상의 저장공간을 차지하게 된다.

만약 블록의 크기기 지나치게 증가되면 블록체인의 검증과 블록의 채굴에 참가하기 위해 필요한 저장공간과 연산능력 및 네트워크 성능이 급격히 높아져 네트워크에 참가할 수 있는 노드\(node\)와 채굴자\(miner\)들의 수가 크게 감소하게 된다. 그렇게 되면 네트워크가 소수의 신뢰받는 중앙화된 노드들을 중심으로 형성되어 현재 중앙화된 시스템이 앉고있는 문제점들을 그대로 답습할 우려가 있다.

### 2. 라이트닝 네트워크\(Lightning Network\)란?

라이트닝 네트워크\(Lightning Network\)는 이러한 비트코인의 확장성에 대한 문제의식에서 출발하였다. 비트코인이 비자\(Visa\)와 같이 초당 47,000개 이상의 거래를 처리하기 위해서는 비트코인 블록체인 바깥에서\(off-chain\) 거래가 이루어질 수 있도록 하는 시스템이 필요하며 이와 더불어 매우 낮은 수수료의 소액거래\(micropayment\)를 거의 무제한으로 처리할 수 있는 시스템이 있다면 더 좋을 것이다. 라이트닝 네트워크란 **블록체인의 바깥에서 대량의 소액결제\(micropayment\)를 즉시\(instant\) 처리할 수 있는 분산화 시스템**이다.

### 3. 라이트닝 네트워크의 작동원리

라이트닝 네트워크는 결제채널\(payment channel\)을 사용하여 . 두 명의 거래 당사자는 일정량의 비트코인을 다중서명\(multi-sig\) 거래에 보낸다. 양측의 동의가 있을 경우에만 현재 잔고\(balance\)는

철수와 영희가 거래채널을 만든다고 하면 다음의 절차를 거치게 된다.

1. 철수와 영희는 각각으로부터 특정량의 BTC를 입력값\(input\)으로 하고 철수와 영희 둘 모두의 서명을 사용해야 unlock 할 수 있는 2-of-2 다중서명\(multi-sig\) 스크립트를 출력값\(outpu\)으로 하는 Funding Transaction을 생성한다. 이 때 철수와 영희는 Funding Transaction에 대한 자신들의 서명을 서로 교환하지 않는다. 
2. 철수와 영희는 처음에 넣은 BTC를 각자에게 환불\(refund\)하는 최초의 Commitment Transaction을 생성. 이 때 SIGHASH\_NOINPUT

철수와 영희는 최초 채널 Funding Transaction에 대한 입력값\(input\)과 출력값\(output\)을 생성하지만 거래에 서명은 하지 않은 상태. Funding Transaction의 출력값은 2-of-2 다중서명 스크립트. 철수와 영희는 2-of-2 출력값에서 원래 금액을 자신들에게 환불하는 거래를 생성하기 전까지 첫 번째 Funding Transaction에 대한 서명을 교환하지 않는다.  거래에 서명을 하지 않는 이유는

누굴 탓할까\(ascribing blame\) 

OP CHECKSEQUENCEVERIFY

**Revocable Sequence Maturity Contract \(RSMC\)**는 특정 기간 이후\(e.g. 1,000 확인confirmations\)에 실행될 수 있지만 그 전에는 취소\(revoke\)될 수 있는 계약을 말하며







### Reference

[“The Bitcoin Lightning Network”: Paper \(PDF\) DRAFT Version 0.5.9.1](https://lightning.network/lightning-network-paper.pdf)

[SF Bitcoin Devs Seminar: Scaling Bitcoin to Billions of Transactions Per Day](https://www.youtube.com/watch?v=8zVzw912wPo&t=20m15s)

[EB80 – Joseph Poon & Tadge Dryja: Scalability And The Lightning Network](https://www.youtube.com/watch?v=fBS_ieDwQ9k)

