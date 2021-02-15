# 목표

클라우드 네트워크 엔지니어가 되어서 회사의 어떤 이벤트로 인해 엄청난 트래픽을 감당할 수 있는 서비스를 구축하려 한다. 즉, 웹 사이트가 다운되지 않고 모든 요청을 효율적으로 처리할 수 있도록 하는 것이다.

이를 위해 Elastic Load Balancer와 Auto Scaling group의 두가지 강력한 AWS 서비스를 통합한다.

1. 특히 웹 서버로 동작하는 EC2 인스턴스의 Auto Scaling 그룹을 생성한 다음 해당 Auto Scaling 그룹 내부의 인스턴스간 load balancing을 수행하도록 Application Load Balancer를 구성한다.
2. 모든 것이 설정되면 EC2 인스턴스에서 stress test를 시뮬레이션하여 Auto Scaling 그룹이 예상대로 작동하는지 확인한다.



# 용어

`Load Balancer`: 안정적인 서비스를 위해 사용자의 요청 부하를 분산하는 역할

`AMI`

`Healthy threshold`

`Scale out`: 인스턴스를 신축성있게 늘리고 줄이는 것

`Scale up` : 하나의 서버 용량 크게 잡는 것



# 작업

1. Application Load Balancer 생성
2. Launch Template 생성
3. Auto Scaling Group 생성
4. Horizontal Scaling 테스트

# 문제



# 개선 방향

- CloudWatch로 특정 임계점에서 알람을 보내고 이에 맞는 auto scaling