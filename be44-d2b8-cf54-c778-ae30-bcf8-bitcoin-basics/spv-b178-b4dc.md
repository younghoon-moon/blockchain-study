### SPV\(Simplified Payment Verification\) 노드

SPV는 Simplified Payment Verification의 약자로 전체 블록체인을 다운받지 않고도 노드를 운영할 수 있도록 해주어 저장공간에 제한이 있는 기기\(e.g. 스마트폰, IoT 기기 및 임베디드 시스템 등\) 혹은 비트코인 지갑\(wallet\) 등에 많이 사용된다. SPV 노드는 블록에 포함된 거래내역은 다운받지 않고 블록헤더\(block header\)만을 다운받기 때문에 전체 블록체인 저장공간의 약 1,000분의 1 정도만을 차지한다.

SPV 노드는 전체 블록체인을 저장하지 않기 때문에 풀 노드\(full node\)와는 다른 방식으로 거래를 검증한다. 풀 노드 같은 경우 예를 들어 높이가 300,000인 블록에 포함된 거래를 검증한다고 하면 블록체인에서 해당 거래의  [코인베이스 거래\(coinbase transaction\)](https://bitcoin.org/en/glossary/coinbase-transaction)에 이르기까지의 모든 거래역사\(transaction history\)에 포함된 거래들의 유효성\(validity\)를 검증함으로써 해당 거래의 유효성을 검증한다. 반면 SPV 노드는 해당 거래가 포함된 블록의 깊이\(depth\)를 참조하여 그 유효성을 검증한다. 예를 들어 SPV 노드가 높이 300,000인 블록에 포함된 거래를 검증한다고 한다면 첫째로 해당 거래의 [머클경로\(merkle path\)](https://bitcoin.stackexchange.com/questions/10479/what-is-the-merkle-root)를 검증함으로써 거래가 해당 블록에 포함되어 있음을 증명한다. 이후 SPV 노드는 해당 블록 위에 높이 300,001부터 300,006까지의 블록이 쌓이는 것을 확인하면 해당 블록의 깊이가 6 이상임을 확인하고 이를 통해 거래의 유효성에 대해 확신할 수 있다.

하지만 여기서 문제가 될 수 있는 점은 SPV 노드는 특정 거래가 존재하는 것은 확인할 수 있지만 특정 거래가 존재하지 않는다는 것은 검증할 수 없다는 것이다. 예를 들어 SPV 노드는 이중지불\(double-spend\) 거래가 없다는 것을 증명할 수 없기 때문에 이중지불 공격과 유효하지 않은 거래들을 지속적으로 전송하는 DoS\(denial-of-service\) 공격에 취약할 수 있다.

#### Reference

[Chapter 8. Mastering Bitcoin \(2nd Ed.\) by Andreas Antonopoulos](https://github.com/bitcoinbook/bitcoinbook/blob/second_edition/ch08.asciidoc)

