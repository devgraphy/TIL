# 질문

## 1.

1조와 다르게 external IP가 없음

host01은 뭘까??

1조에서 expose 할 때 cluster ip 로 함.

지금은 nodeport를 줌.

1조했던 것처럼 external ip로 오픈한게없음

1조에서는 cluster ip 이기 때문에 외부에서 접근이 안되었음

cluster ip는 expose를 해줘야만 다른 노드에서 접근할 수 있게 됨

2조에서는 hos01 과 맵핑되는 ip를 찾게 되는데, host01로 외부에서 접근하면 접근되지 않음

근데 내부에선 왜 접근이 가능할까? nodeport와 일치하는 값을 찾은 것임(포트가지고 찾은것)

노드가 여러개 있을 수 잇는데, 노드포트로 오픈해놓으면 노드 중에서 해당되는 포트를 찾아서 들어감

host01은 어디에도 준게 없음. 여기서 host01은 큰 의미가 없음.



cluster ip는 외부 접근 불가

노드 포트이지만 expose 하지 않았기 때문에 접근 불가



## 2. apply, create 차이

똑같음











컨테이너 배포 방법 2가지 : kubectl, yaml 정의 후 `kubelctl deploy`





Deploy containers using yaml



1. deployment 생성하기
2. service 생성하기
3. deployment 스케일링하기