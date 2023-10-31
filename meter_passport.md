## 사용된 취약점
브릿지 컨트랙트에 wETH를 사용하는 로직이 추가되면서 depositETH()라는 함수가 추가되었는데,
전체적인 브릿지 처리 과정에서 wETH의 예외처리를 하던 도중
기존에 있던 deposit()함수를 통하면 wETH의 예외처리 때문에 토큰을 실제로 deposit하지않고도 withdraw가 가능하였다

해당 공격 관련 글

https://coincodecap.com/meter-io-hacked-around-4-3m-lost

<br/><br/>
## 공격 방법
<img width="511" alt="image" src="https://github.com/dik654/Bridge_hacks/assets/33992354/24a9f8f6-9564-430d-9a64-21dcf1dd3cf1">
<br/><br/><br/><br/><br/><br/>
<img width="1037" alt="image" src="https://github.com/dik654/Bridge_hacks/assets/33992354/2db31740-ab4c-4c6e-a93b-c0d937826998">
<br/><br/><br/><br/><br/><br/>
<img width="934" alt="image" src="https://github.com/dik654/Bridge_hacks/assets/33992354/48f83fc5-aa4c-4fcb-93d2-e8fa49afad99">
<br/><br/><br/><br/>

## 해결책
새로운 기능이 추가되었을 때, 기존에 있던 요소들과의 상호관계도 꼼꼼히 따져봐야한다

