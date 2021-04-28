# 목표

- stack 생성, 업데이트, 삭제 다뤄보기

# 용어

- stack : 컴퓨팅 리소스 집합
- template: `stack`이 생성할 리소스들을 정의해놓은 틀(json, yaml)
- logical volume: ?
- bucket:



# stack 업데이트

CloudFormation에서

stack 선택 - 업데이트 - 현재 템플릿 교체 - 템플릿 파일 업로드



# stack 생성

CloudFormation에서

stack 생성 - 새 리소스 사용(표준) - 준비된 템플릿 - 템플릿 파일 업로드

```
<ERROR: `ROLLBACK_COMPLETE`>
표시: cfnlab2 `ROLLBACK_COMPLETE` 상태
발생 이유: 같은 이름을 가진 S3버킷(같은 유형의 리소스 이름)을 가질 수 없다. (volume 이름은 상관없음)
```



# stack 삭제

CloudFormation에서

stack 선택 - 삭제