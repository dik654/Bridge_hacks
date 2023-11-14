## 사용된 취약점
컨트랙트 별로 이벤트 리스닝을 구분하지 않았다


해당 공격 관련 글
https://medium.com/pnetwork/pnetwork-post-mortem-pbtc-on-bsc-exploit-170890c58d5f
<br/><br/>

## 공격 방법
공격 컨트랙트는 selfdestruct되어 확인이 불가능한 상태이다.

relayer가 브릿지 컨트랙트의 이벤트를 리스닝하는게 아니라<br/>
유저의 모든 트랜잭션의 이벤트를 리스닝하고 있어<br/>
relayer가 감지하는 이벤트와 동일한 이벤트를 발생시키는 공격 컨트랙트를 생성,<br/>
이벤트를 발생시켜 relayer를 속인다

<img width="562" alt="image" src="https://github.com/dik654/Bridge_hacks/assets/33992354/21fb80a4-ee0b-425b-8e39-af0d3eb69cf3">

<br/><br/>
## 해결책
생성된 이벤트가 spoofing될 수 있다는 생각을 항상 가지고 relayer의 로직을 짜야한다.
