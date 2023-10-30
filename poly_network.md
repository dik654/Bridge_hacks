## 사용된 취약점
- Function Signature Hash Collision
solidity의 함수가 실행될 때, 함수명 전체가 아닌 keccak256(함수명(타입...))의 첫 4bytes(hex 8글자)로 함수이름을 구별한다.
해시값의 전체는 다를지라도 첫 4bytes만 동일하다면 같은 함수로 판단되기에 주의해야할 취약점이다.

해당 내용 관련 openzeppelin의 게시글이 있으니 참조하면 좋다
https://forum.openzeppelin.com/t/beware-of-the-proxy-learn-how-to-exploit-function-clashing/1070

## 공격 방법

<img width="836" alt="image" src="https://github.com/dik654/Bridge_hacks/assets/33992354/48ee9823-3a2f-47ed-8def-6883b678dd38">
<img width="1456" alt="image" src="https://github.com/dik654/Bridge_hacks/assets/33992354/321a59a7-0846-44fd-a2f4-4ba7bf64a567">
