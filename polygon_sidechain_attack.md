## 사용된 취약점
폴리곤 sidechain에서 Merkle proof의 중복을 이용한 double spending 공격 

해당 내용에 대한 블로그 글

https://medium.com/immunefi/polygon-double-spend-bug-fix-postmortem-2m-bounty-5a1db09db7f1

## 공격 방법
Merkle Patrica Tree의 decoding 방식의 헛점을 이용하여 여러 동일한 exit을 만들어 내어
한 burn transaction을 "여러 branch mask를 차례대로 이용하여" 검증하는데 성공하였다(double spending)


## 해결책
검증 중 branch mask의 시작 byte가 0이면 revert되도록 하여 중복되는 케이스들을 막았다.
<img width="811" alt="image" src="https://github.com/dik654/Bridge_hacks/assets/33992354/23e0c1b7-96a6-4a01-9c13-078d3ca5fc58">
