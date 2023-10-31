## 사용된 취약점
폴리곤 sidechain에서 Merkle Patrica Tree의 decoding 과정에서 중복을 이용한 double spending 공격 

해당 내용에 대한 블로그 글

https://medium.com/immunefi/polygon-double-spend-bug-fix-postmortem-2m-bounty-5a1db09db7f1

## 공격 방법
branch mask란 trie 구조에서 특정 값에 도달하기 위한 경로를 나타내는데 사용하는 값인데, 
폴리곤에서는 burn 트랜잭션의 receipt의 위치에 branch mask로 도달할 경우 verify에 성공하여 withdraw를 할 수 있다.

그런데 디코딩 과정에서의 시작 nibble이 1 또는 3이면 첫 nibble을 읽지않고 넘어가고,

0으로 시작하면 첫 byte를 읽지않고 넘어간다

이 로직에 의해 여러 인코딩된 branch mask가 디코딩 이후 동일한 값을 나타내게 되었고, 한 트랜잭션에 여러번 verify가 가능하게 되는 문제가 생겼다.
![image](https://github.com/dik654/Bridge_hacks/assets/33992354/8067ca3b-1d18-4f98-9718-09c0a28e2b51)



## 해결책
검증 중 branch mask의 시작 byte가 0이면 revert되도록 하여 중복되는 케이스들을 막았다.
<img width="811" alt="image" src="https://github.com/dik654/Bridge_hacks/assets/33992354/23e0c1b7-96a6-4a01-9c13-078d3ca5fc58">
