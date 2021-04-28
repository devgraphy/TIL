# 목표

AWS 람다를 이용해서 편하게 EC2 인스턴스 생성하기

![SmartSelect_20210222-000833_Samsung Notes](images/SmartSelect_20210222-000833_Samsung%20Notes.jpg)

# 용어

lambda function (AWS Lambda)

역할(role)

정책(policy)





# 작업



## 1. Lambda function 생성

![image-20210221222641461](images/image-20210221222641461.png)

![image-20210221222653096](images/image-20210221222653096.png)



### 2. IAM > 역할 > 정책 변경

<img src="images/image-20210221223546508.png" alt="image-20210221223546508" style="zoom:50%;" />

![image-20210221223708370](images/image-20210221223708370.png)

![image-20210221223754777](images/image-20210221223754777.png)

![image-20210221223817887](images/image-20210221223817887.png)

```json
{
  "Version": "2012-10-17",
  "Statement": [{
      "Effect": "Allow",
      "Action": [
        "logs:CreateLogGroup",
        "logs:CreateLogStream",
        "logs:PutLogEvents"
      ],
      "Resource": "arn:aws:logs:*:*:*"
    },
    {
      "Action": [
        "ec2:RunInstances"
      ],
      "Effect": "Allow",
      "Resource": "*"
    }
  ]
}
```

![image-20210221223843594](images/image-20210221223843594.png)







### 3. lambda 함수 코드 변경



![image-20210221224429778](images/image-20210221224429778.png)

```python
import os
import boto3

AMI = os.environ['AMI']
INSTANCE_TYPE = os.environ['INSTANCE_TYPE']
KEY_NAME = os.environ['KEY_NAME']
SUBNET_ID = os.environ['SUBNET_ID']

ec2 = boto3.resource('ec2')


def lambda_handler(event, context):

    instance = ec2.create_instances(
        ImageId=AMI,
        InstanceType=INSTANCE_TYPE,
        KeyName=KEY_NAME,
        SubnetId=SUBNET_ID,
        MaxCount=1,
        MinCount=1
    )

    print("New instance created:", instance[0].id)
```



### 4. 환경 변수 편집

<img src="images/image-20210221225552052.png" alt="image-20210221225552052" style="zoom: 67%;" />

![SmartSelect_20210221-234725_Samsung Notes](images/SmartSelect_20210221-234725_Samsung%20Notes.jpg)



## 5. 테스트 및 인스턴스 생성 확인

![image-20210222001236080](images/image-20210222001236080.png)

![image-20210222001306172](images/image-20210222001306172.png)



## 6. ssh 연결



# 궁금한점

