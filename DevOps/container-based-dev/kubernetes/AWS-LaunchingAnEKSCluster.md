- 



클라우드 의존성을 덜기 위해서 도커 이미지를 활용해야 한다.

오픈소스를 이용한 배포(vs. aws에서 제공하는 파이프라인, 클라우드 스타)



로드밸런서 직접 핸들링 -> AWS 빈스톡 자동화서비스로 대체할 수 있음

- 동작원리는 이해할 필요 있음. 그래서 EC2 기반으로 했었음
- 대부분의 클라우드 서비스는 유사하다. 그러나 표준인 쿠버네티스은 왜 사용할까???







# Admin 권한을 가진 IAM 사용자 생성

Set the following values:

- *User name*: **k8-admin**
- *Access type*: **Programmatic access**

AKIAW3LJ6MSMGPZTVMXU

rPiXHjjX8bU5QsUtQAh1YrNIeFvxl/JTlSEozz0R





CLI 명령어 업데이트

```
sudo ./aws/install --bin-dir /usr/bin --install-dir /usr/bin/aws-cli --update
```





![image-20210222141320645](images/image-20210222141320645.png)

![image-20210222141239115](images/image-20210222141239115.png)



![image-20210222141502626](images/image-20210222141502626.png)

현재까지는 권한등록한 것임



# cubectl 설치

```
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.16.8/2020-04-16/bin/linux/amd64/kubectl
```



Apply execute permissions to the binary:

```
chmod +x ./kubectl
```



Copy the binary to a directory in your path:

```
mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin
```

- kubectl을 어디서 실행가능하도록 환경변수 잡아주는 것
- ![image-20210222141902176](images/image-20210222141902176.png)

Ensure `kubectl` is installed:

```
kubectl version --short --client
```

- ![image-20210222142003520](images/image-20210222142003520.png)



# eksctl 설치

Download `eksctl`:

```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
```

- kubectl과 마찬가지로 설치하는 방법은 여러가지가 있음
- 파이프라인, & 구분
  - 파이프라인은 앞에 명령어 성공 상관없이 뒤에 명령어 수행
  - &: 앞에 명령어 성공하면 뒤에 명령어 수행
- -C: 압축 경로 지정





Move the extracted binary to `/usr/bin`:

```
sudo mv /tmp/eksctl /usr/bin
```

옮겨놨으니 eksctl 명령어도 어디서든 수행 가능하게 되었다.

- ![image-20210222142656759](images/image-20210222142656759.png)
- 여기서 --version이 아닌 version인거는 스펙문서를 참고해야 함



# EKS 클러스터

이제는 명령어로 인스턴스 생성할 수 있게 되었다.

Provision an EKS cluster with three worker nodes in `us-east-1`:

```
eksctl create cluster --name dev --version 1.16 --region us-east-1 --nodegroup-name standard-workers --node-type t3.micro --nodes 3 --nodes-min 1 --nodes-max 4 --managed
```

- 클러스터 생성
- 노드그룹 이름 지정
- 노드 타입 지정 = 인스턴스 타입
- 디폴트 노드 개수 3개
- 부하가 심해지면 4개
- 최소 노드 1개
- --managed : AWS eks에서 관리가 되도록 지정
- ![image-20210222143903738](images/image-20210222143903738.png)
- [rollback error]: 공간이 부족해서 발생하는 문제일 수 있음

In the AWS Management Console, navigate to CloudFormation and take a look at what’s going on there.

- 산출물 2개
  - <img src="images/image-20210222145220480.png" alt="image-20210222145220480" style="zoom: 67%;" />

>ECS: 쿠버네티스 이전 서비스
>
>EKS: 쿠버네티스 현재
>
>ECR: 이미지 관리해주는 레포지토리



- auto scaling 만들어져 있음
  - 우리는 이를 구성하기 위해서 시작 템플릿을 했어야 했는데, 확인해보면 템플릿이 만들어져 있음을 확인할 수 있음



In the CLI, check the cluster:

![image-20210222150857736](images/image-20210222150857736.png)

Enable it to connect to our cluster:

```
aws eks update-kubeconfig --name dev --region us-east-1
```



# git 설치

git에서 git clone 하여 yml 파일을 가져오기 위함

Install Git:

```
sudo yum install -y git
```

Download the course files:

```
git clone https://github.com/ACloudGuru-Resources/Course_EKS-Basics
```

Change directory:

```
cd Course_EKS-Basics
```

Take a look at the deployment file:

```
cat nginx-deployment.yaml
```

Take a look at the service file:

```
cat nginx-svc.yaml
```

클러스터 IP는 내부에서 쓰이는 것이므로 공개되지 않음



Create the service:

```
kubectl apply -f ./nginx-svc.yaml
```

Check its status:

```
kubectl get service
```

![image-20210222151922005](images/image-20210222151922005.png)

Create the deployment:

```
kubectl apply -f ./nginx-deployment.yaml
```

Check its status:

```
kubectl get deployment
```

View the pods:

```
kubectl get pod
```

View the ReplicaSets:

```
kubectl get rs
```

View the nodes:

```
kubectl get node
```





Access the application using the load balancer, replacing `<LOAD_BALANCER_EXTERNAL_IP>` with the IP you copied earlier:

```bash
curl "<LOAD_BALANCER_EXTERNAL_IP>"
```

![image-20210222152608899](images/image-20210222152608899.png)

![image-20210222152708661](images/image-20210222152708661.png)





yml파일 세부 내용을 다 이해하면서 하면 러닝커브가 높아짐

yml 스펙문서 보면서 yml 작성법 익힐 수 있음

어느 부분을 수정하면 내가 내 입맛에 맞게 쓸 수 있는지 알아야 함

[쿠버네티스 오브젝트 이해하기 | Kubernetes](https://kubernetes.io/ko/docs/concepts/overview/working-with-objects/kubernetes-objects/)

k8 문서를 본다고 다 이해되진 않을 것임



volume이 적용되면 하나의 pod에 여러 컨테이너가 들어가야하는 경우가 발생



와이드한 학습 내용은 예제 중심의 튜토리얼로 빠르게 학습하는 것이 학습 팁!