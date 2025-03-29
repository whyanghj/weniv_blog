## introduction

MoE(Mixture of Exprts)는 multi-task learning에서 높은 확장성을 보인다. 하지만 비효율적이고 많은 계산량이라는 단점을 갖고있다. 그렇기에 본 논문에서는 MoFME를 설명하고있다. MoFME는 expert의 개수를 줄이고 다양한 필터를 이용한다. 라우터는 UaR(uncertainty-aware Router)를 사용한다.

MOE의 단점에 대해서 알아보겠다.
1. 여러개의
 FFN(Feed Forward Network) expert를 가져서 너무 크고 무겁다.
그래서 성능이 저하되고, 연산량은 늘어나고, 메모리사용량도 크다. 특히 자율주행자동차에 사용되는 작은 컴퓨터에는 MOE를 사용할 수 없다.  

2. 기존에는 단순한 Linear Router를 사용하여 expert를 선정하였다. 
그랬기에 라우터 가중치가 잘 조정되지 않았다. 이를 해결하기 위해 Multi-gate MoE는 추가 게이팅 네트워크를 도입했다.
하지만 계산비용이 더 늘어나는 단점이 존재했다.

기존 MOE
: 입력 -> Linear Layer -> sofrmax -> expert 선택

Multi-gate MOE
: 입력 -> gate 선택 -> 각 gate에 맞는 expert 실행

입력이 아래와 같은 경우에 Multi-gate MOE가 좋은 성능을 보였다.
-   비오는날 날씨 탐지
-   안개낀 도로 차선 탐지
-   눈 오늘 날 객체 탐지

위와 같이 입력이 복잡할 경우에는 Multi-gate MOE를 통해 gate에서 expert를 지정해주면 기존의 MOE보다 특징을 잘 찾아낼 수 있다.
하지만 위에서 말한 것 처럼 많은 연산량과 과도한 메모리 사용량으로 인한 단점이 존재한다.
그렇기에 성능이 개선되고 계산 효율을 가진 MOE가 필요하다.  
