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

- 



1. EC2 인스턴스 시작

   - ubuntu 20.4
   - 보안그룹: ssh, http
   - VPC: default
   - perm: cloudmsa.pem

2. EC2 인스턴스 SSH 연결 환경 세팅

   - `sudo apt-get update`

   - `sudo apt-get install apache`

   - sudo apt-get install php

   - ```
     <?php
     	for($i=0; $i<1000000; $i++){}
     	?>
     ```

     

   - http://<ip>index.html        http://<ip>index.php 확인

3. 부하 테스트용 EC2 인스턴스 시작

   - ubuntu 20.4
   - 보안그룹:ssh
   - VPC:default
   - perm:cloudmsa.pem
   - Name: stress-test
   - sudo apt-get update
   - sudo apt-get install apache2-utils
   - ab -n 100000 -c 2 http://<webserverip>/index.php    #stress test webserver instance ssh console: top으로 cpu 확인

4. AMI 생성

   - webserver로 AMI 생성
   - Name: webserver

5. 로드밸런서 생성

   - LAB 참고

6. 시작 템플릿 생성

   - AMI: webserver

7. AutoScaling 생성

   - LAB 참조

8. 부하테스트

   - stress-test
   - ab -n request  <요청수> -c <동시사용자수> http://<로드밸런서 도메인주소/index.php>
   - 시작템플리승로 생성된 instance ssh 연결 콘솔에서 로그 확인: load balancer가 요청 전달 확인(부하분산)
   - sudo tail -f /var/log/apache2/access.log
   - Auto Scaling instance 수, desired 수 확인
   - 부하테스트 종료 후 5.로드밸런서 생성
   - LAB 참조





## CloudWatch로 특정 임계점에서 알람을 보내고 이에 맞는 auto scaling