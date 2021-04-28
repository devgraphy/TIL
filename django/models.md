해당 문서의 목표

- ORM 역할
- model 수정 방법



# ORM(Object-Oriented-Mapping)

python으로 작성된 class 기반의 모델을 SQL 데이터베이스(SQLITE)에 저장할 수 있게 자동으로 바꾸어 주는 역할을 한다.

시스템 2개가 있다고 생각해보자. 각 시스템은 다른 언어를 쓰고 있기 때문에 데이터를 주고 받을 때 문제가 생긴다. 마찬가지로 django에서는 python 언어를 사용하고, SQL에서는 SQL문을 사용하기 때문에 문제가 생길 수 있다. 하지만 django는 이 문제를 해결하기 위해 ORM이라는 기술을 사용한다.



# model 수정

1) 필드를 추가하는 경우

- 필드를 추가

- `python manage.py makemigrations`

  - non-nullable 속성에 대한 처리
  - models.DateTimeField의 경우, default=`timezon.now` 와 같은 값을 설정해준다.

- `python manage.py migrate`

  

2) 필드 삭제 또는 속성을 변경하는 경우

