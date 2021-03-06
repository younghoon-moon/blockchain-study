# 라이트닝 네트워크\(Lightning Network\)

## 0. 개요

[라이트닝 네트워크\(Lightning Network\)](https://lightning.network/)는 [Joseph Poon](https://twitter.com/jcp)과 [Thaddeus Dryja](https://www.linkedin.com/in/thaddeus-dryja-29620b53/)에 의해 2015년 처음 소개되었으며 이후 비트코인을 비롯한 블록체인 시스템의 확장성 문제를 해결해줄 수 있는 솔루션으로 많은 각광을 받았다.

## 1. 비트코인의 확장성\(scalability\) 문제

현재 비트코인은 가십\(gossip\) 프로토콜을 사용하여 모든 노드들이 모든 상태의 변화를 서로에게 전파하고 이를 통해 합의에 이르는 시스템이다. 하지만 이는 모든 참가자가 비트코인 네트워크에서 일어나는 모든 거래내역들을 확인해야 하기 때문에 글로벌 금융 거래를 처리하기에는 상당한 걸림돌로 작용한다. 예를 들어 비자\(Visa\)의 경우 2013년 연휴 당시 [초당 최대 47,000건의 거래를 처리](http://www.visa.com/blogarchives/us/2013/10/10/stress-test-prepares-visanet-for-the-most-wonderful-time-of-the-year/index.html)하였고 현재에도 하루 평균 수억건의 거래를 처리하고 있는 반면 비트코인은 1MB 블록크기의 제한으로 인해 초당 3~5개의 거래밖에 처리하지 못한다. 만약 비트코인이 비자와 같은 거래량을 처리하기 위해서는 블록의 크기가 약 10GB 이상이 되어야 하는데 이는 년간 500TB\(테라바이트\) 이상의 저장공간을 차지하게 된다.

만약 블록의 크기기 지나치게 증가되면 블록체인의 검증과 블록의 채굴에 참가하기 위해 필요한 저장공간과 연산능력 및 네트워크 성능이 급격히 높아져 네트워크에 참가할 수 있는 노드\(node\)와 채굴자\(miner\)들의 수가 크게 감소하게 된다. 그렇게 되면 네트워크가 소수의 신뢰받는 중앙화된 노드들을 중심으로 형성되어 현재 중앙화된 시스템이 앉고있는 문제점들을 그대로 답습할 우려가 있다.

## 2. 라이트닝 네트워크\(Lightning Network\)란?

라이트닝 네트워크\(Lightning Network\)는 비트코인 확장성 문제에 대한 해결책으로 제시되었으며** 블록체인 외부에서\(off-chain\) 결제채널\(payment channels\)의 네트워크**를 통해 낮은 수수료로 다량의 소액거래\(micropayment\)를 처리할 수 있도록 시스템이다. 블록체인 바깥에서 이루어지지만 실제로 이루어지는 모든 거래는 유효한 비트코인 거래로서 중간 관리인\(custodian\) 없이 안전하게 거래를 성사시킬 수 있다.

## 3. 라이트닝 네트워크의 작동원리

### 3.1. 결제채널의 생성

철수와 영희가 결제채널\(payment channel\)을 만드는 기본적인 절차는 다음과 같다.

1. **Funding Transaction 생성**. 철수와 영희는 각자 일정량\(e.g. 철수는 3BTC를 영희는 2BTC를 보낸다고 가정하자\)의 비트코인\(BTC\)을 입력값\(input\)으로 보내는 Funding Transaction을 생성한다. 이 때 Funding Transaction의 출력값\(output\)은 2-of-2 다중서명\(multi-sig\) 스크립트로서 철수와 영희의 서명이 모두 있어야 Funding Transaction의 자금을 사용할 수 있다. 이 때 철수와 영희는 Funding Transaction에 대한 서명을 교환하지 않는데 그 이유는 서명을 교환하는 경우 Funding Transaction을 네트워크에 통보\(broadcast\)함으로써 블록체인에 기록할 수 있기 때문이다. 이렇게 되면 철수와 영희 둘 중 한 명이라도 나쁜 마음을 먹는 경우 자금을 계속 묶어두거나 묶인 자금을 인질\(hostage\)로 삼아 돈을 요구할 수 있다. 
2. **Commitment Transaction의 생성**. 이후 철수와 영희는 각자가 원래 Funding Transaction에 지불했던 비트코인을 자신에게 환불\(refund\)하는\(e.g. 철수에게 3BTC, 영희에게 2BTC을 주는\) Commitment Transaction을 생성한다. Commitment Transaction의 입력값은 1에서 만들어진 Funding Transaction의 거래 ID\(`txid`\)값이 들어갈 것이다.
3. **Commitment Transaction에 서명**. 철수와 영희는 Commitment Transaction에 서명을 한다. 이 때 위의 1에서 Funding Transaction에 서명이 되지 않았기 때문에 Commitment Transaction은 입력값\(input\)의 `txid` 필드가 정해지지 않았다. 따라서 철수와 영희 모두 입력값에 서명을 할 수 없다. 이 경우 라이트닝 네트워크는 입력값에 서명하지 않는 `SIGHASH_NOINPUT` 플래그\(flag\)를 사용하여 서명을 생성하도록 한다.
4. **Commitment Transaction 서명 교환**. 철수와 영희는 3에서 Commitment Transaction에 대한 서명을 교환한다.
5. **Funding Transaction에 서명**. Commitment Transaction에 대한 서명의 교환이 완료되면 철수와 영희는 각각 Funding Transaction에 서명한다.
6. **Funding Transaction 서명 교환**. 철수와 영희는 5의 Funding Transaction에 대한 서명을 교환한다.
7. **Funding Transaction을 블록체인 상에 공개**. 이젠 철수와 영희는 자금동결의 우려없이 Funding Transaction을 블록체인 상에 공개할 수 있다. 철수와 영희 모두 Commitment Transaction에 서명했기 때문에 마음만 먹으면 언제든지 상대방의 동의없이 Commitment Transaction을 블록체인 상에 공개함으로써 초기에 투입하였던 자금을 환불받을 수 있기 때문이다.

위의 7단계를 거쳐 Funding Transaction이 블록체인에 기록되게 되면 철수와 영희간의 결제채널이 성립된 것이다. 이 때 Commitment Transaction은 블록체인에 공개되지 않으며 거래 당사자간의 현재 잔고\(current balance\)를 나타내는데 사용된다. 철수와 영희는 Commitment Transaction을 블록체인 상에 공개함으로써 자신의 잔고를 환불받고 결제채널을 닫을 수 있다.

### 3.2. 블록체인 외부\(off blockchain\)에서의 장부 업데이트 문제

철수와 영희는 개설된 결제채널을 바탕으로 블록체인 바깥에서 장부를 업데이트해 나간다고 가정하자. 라이트닝 네트워크는 장부가 업데이트 될때마다 새로운 Commitment Transaction을 생성하여 장부를 업데이트한다. 예를 들어 철수와 영희가 Commitment Transaction을 통해 각각 3BTC, 2BTC을 보유하고 있는 상황에서 철수가 영희에게 0.5BTC을 지불한다고 하자. 철수와 영희에게 각자에게 2.5BTC씩 지불하는 새로운 Commitment Transaction을 생성하고 이에 서명한 후 서명을 교환한다. 이 때 새로운 Commitment Transaction 또한 최초에 생성된 Funding Transaction을 입력값으로 갖으며 블록체인 상에 공개되지 않고 거래 당사자들만 보관한다.

하지만 여기서 문제가 발생하는데 새로운 Commitment Transaction 뿐만 아니라 이전의 Commitment Transaction도 여전히 네트워크 상에 공개되어 블록체인에 기록될 수 있으며 이 둘은 동일한 입력값\(Funding Transaction\)을 가지고 있다. 즉 **어떠한 Commitment Transaction이 유효한 것인지에 대한 우선순위가 없어** 철수의 경우 이전의 Commitment Transaction을 블록체인에 공개하여 0.5BTC을 되돌려받는 것이 경제적으로 유리하기 때문에 결제채널 자체가 작동하지 않게 된다. 블록체인 같은 경우는 모든 거래들이 블록체인에 비가역적으로 기록되어 그 유효성이 검증되지만 블록체인 외부\(off blockchain\)에서는 이러한 비가역성이 존재하지 않기 때문에 다른 방식으로 최신 거래의 유효성을 확립해야 한다.

라이트닝 네트워크는 블록체인 외부에서 최신 거래의 유효성을 확립하기 위해 다음과 같이 크게 세 가지의 도구를 사용한다.

* 같은 내용의 거래를 **서명 순서를 달리하여** Commitment Transaction 한 쌍\(2개\)을 만들어 **특정 거래를 블록체인에 공개한 당사자를 파악**. 백서\(whitepaper\)에서는 이를 "**누구 탓인가\(ascribing blame\)**"라고 표현하고 있다.
* 거래를 일정기간 동안 유효하지 않도록 하는 **타임락\(timelock\)** 기능을 사용하여 **취소할 수 있는 거래\(revocable transactions\)**를 생성하고 이를 통해 블록체인 상에서 분쟁을 해결\(dispute resolution\)한다. 
* Breach Remedy Transaction을 통해 계약을 어기는 거래 참가자의 예치금을 몰수하는 방식으로 **벌금\(penalty\)**을 부과한다. 

### 3.3. 블록체인 외부\(off blockchain\)에서 최신 장부상태에 대한 유효성\(validity\) 확립

#### **3.3.1. 특정 거래를 블록체인에 공개한 당사자 파악**

라이트닝 네트워크에서 모든 Commitment Transaction은 각각의 거래 당사자에 의해 **반만 서명된\(half-signed\) 거래의 쌍**\(2개\)으로 이루어져있다. 예를 들어 철수가 서명한 Commitment Transaction은 영희가 보관하고 영희는 언제든지 이에 자신의 서명을 덧붙여 블록체인 상에 공개할 수 있다. 반대로 영희가 서명한 거래는 철수가 보관하고 철수 또한 언제든지 자신의 서명을 덧붙여 이를 블록체인 상에 공개할 수 있다. 따라서 특정 Commitment Transaction이 블록체인 상에 공개된 경우 철수와 영희 중 누가 거래를 공개하였는지 파악할 수 있게 되며 이는 결제채널에서 계약을 어기는\(i.e. 최신이 아닌 Commitment Transaction을 블록체인 상에 공개하는\) 참가자를 식별하고 그들에게 벌금을 부과하는 데 사용된다.

#### 3.3.2. 취소 가능한 거래\(Revocable Transaction\)의 생성

Revocable Sequence Maturity Contract \(RSMC\)

거래 당사자들은 RSMC를 이행하는

특정기간\(e.g. 1,000번의 확인confirmation\) 후부터 유효한 거래 생성\(revocable output balance\)

#### 3.3.3. 벌금의 부과

라이트닝 네트워크는 최신이 아닌 Commitment Transaction을 네트워크에 전파\(broadcast\)하는 참가자의 예치금을 몰수함으로써 최신이 아닌 Commitment Transaction들을 무효화\(invalidate\)한다.

### 3.4. 

![](/assets/Screen Shot 2017-08-13 at 3.12.43 AM.png)

### Reference

[“The Bitcoin Lightning Network”: Paper \(PDF\) DRAFT Version 0.5.9.1](https://lightning.network/lightning-network-paper.pdf)

[SF Bitcoin Devs Seminar: Scaling Bitcoin to Billions of Transactions Per Day](https://www.youtube.com/watch?v=8zVzw912wPo&t=20m15s)

[EB80 – Joseph Poon & Tadge Dryja: Scalability And The Lightning Network](https://www.youtube.com/watch?v=fBS_ieDwQ9k)

