# Plasma Plant: A Minable Plasma Chain based on PoS for dApps on the Ethereum

**Plasma Plant** is a simple implementation of a minable plasma chain based on Proof of Stake. This is designed to minimize the gas costs to run a decentralized application. Using Plasma Plant, dApp can operate its own plasma chain and issue its own ERC20 token which is mined by maintaining the plasma chain. Also users can enter and exit the plasma chain in a secure way. It is inspired by Minimum Viable Plasma, Plasma Cash, and Casper.

**Plasma Plant for Community** is an extended version of Plasma Plant designed to support a token economy for community. Please check Plasma Plant Community [here](https://github.com/commitplay/plasma-plant-for-community).

**Table of Contents**

1. Introduction to Plasma Plant
  1. Plant
  1. Consensus of Plasma Chain
  1. Check Point
  1. How to deploy smart contract to the plasma
  1. Accuse & Penalty
  1. Enter & Exit
1. Progress
1. Contributing
1. License

## Terminology

## Core concepts

1. Plasma Plant aims to build a fast and secure network infra by motivating people to participate as a node as many as possible.
1. When exit a plasma chain, people need a secure way instead of a fast way.


## Plant

**Being a plant**  
Plant means a node which maintains the plasma chain. Anyone can operate a plant if they deposit 3 ETH to the Plasma Contract. The deposit can be reassigned according to the amount of transactions per a checkpoint.


**Charge up mining resource**  
Plant does a job to write plasma chain's







## Progress of the implementation

## Contributing

## License




Key features of Plasma Plant are followings:

- Proof of Stake
- Accusation
- Randomized miner & validator




# Attacks

## Case A

1. Hacker get a chance to make a check point as one of a plant
1. Hacker is in control of validators
1. Hacker create an invalid set of blocks and get signatures from validators
1. Hacker succeeded to write invalid blocks to the root chain

##### Probability to succeed the attack

- Hacker should get the top priority as a check point generator
  - If there're *N* active plants, the probability is *1/N*.
- If the hacker have a control of *s*% of the plants.

##### How to recover the damage & punish the attacker

1. 다른 노드들이 체크포인트가 실제로 합의된 것과 다른 것을 인지할 경우, 체크포인트 생성자를 고소할 수 있습니다. 고소를 진행하기 위해서는 다음 체크포인트가 생성되기 전에 고소를 위한 트랜잭션이 접수되어야 하며, 올바른 체크포인트를 담아  대체하는 트랜잭션을 보냅니다.

1. 고소당한 체크포인트 생성자는 등록한 체크포인트가 합의에 따른 결과라는 것을 입증하는 변호과정을 진행해야 합니다. 이는 해당 블록에 포함된 트랜잭션을 모두 루트체인에 기록하는 것을 통해 이루어집니다. 즉, 많은 비용을 소모하게 되는데 이 비용은 플랜트로 등록하기 위해 사용한 Proof of Stake에서 차감됩니다.
> 즉 하나의 체크포인트에 포함될 수 있는 플라즈마 트랜잭션의 총 개수는 루트블록의 평균 가스 가격을 고려하여 Proof of Stake를 통해 예치한 금액이 고소를 변호하기 충분하도록 매번 조정됩니다.

1. 하지만 고소를 당한 체크포인트가 네트워크상의 문제 등으로 변호를 제대로 못하는 상황이 발생할 수 있습니다. 이에 따라 2차 변호의 기회가 주어집니다. 2차 변호는 체크포인트생성자가 아니지만 올바른 트랜잭션 정보를 포함하고 있는 다른 플랜트들 모두가 2차 변호자로 참가할 수 있습니다.

1. 변호에 성공할 경우에는, 고소를 진행한 사람들로부터 변호 비용을 보전받습니다. 그리고 고소를 진행한 사람들은 예치금을 몰수당하고 플랜트의 자격을 잃게 됩니다.

1. 변호에 실패할 경우에는, 검증자와 체크포인트 생성자 모두 예치금을 몰수당합니다. 그리고 몰수된 예치금은 고소를 진행한 플랜트들에게 보상으로 돌아갑니다. 더불어 생성된 체크포인트는 새로이 요청된 체크포인트로 교체되며 플라즈마 체인은 해당 체크포인트로 롤백되어 다시 블록을 쌓기 시작합니다.

1. 고소를 통해 교체된 체크포인트도 마찬가지로 다시 고소를 당할 수 있습니다.

##### How to withdraw assets from Plasma

1. 플라즈마 내부에서 플라즈마 외부로 출금요청을 할 경우, 외부출금 트랜잭션이 플랜트에게 전송됩니다. 플랜트는 플라즈마 상에서 출금처리를 완료합니다.

1. 체크포인트 생성자는 출금 내역을 모아 체크포인트에 포함시킵니다.

1. 해당 체크포인트가 고소당하지 않았다면, 다음 체크포인트가 생성될 때 체크포인트에 포함된 출금내역이 실행되어 출금이 진행됩니다.
