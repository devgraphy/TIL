# 클래스 변수, 인스턴스 변수

jave 스타일

```java
class Service{
	List<Student> students;				// 멤버 변수
	//static List<Student> students;	// 클래스 변수 - 공유되는 변수!	
	Service(students){
		this.students = students;
	}
}

Service s1 = new Service(students)
Service s2 = new Service(students)

//Service.students 						// 클래스 로드되는 시점에 딱 한번 초기화
										// 다시 new하더라도 초기화되지 않음
```

python 스타일

```python
class ClassTest:
    class_var = 0
    def __init__(self, instance_var):
        self.instance_var = instance_var

# 인스턴스 변수 조작(인스턴스 이름으로 접근)
c1 = ClassTest(10)
c2 = ClassTest(20)
print("c1 instance var:{}, c2 instance var:{}".format(c1.instance_var, c2.instance_var))

# 클래스 변수 조작(클래스 이름으로 접근)
ClassTest.class_var += 1 
print("c1 class var:{}, c2 class var:{}".format(c1.class_var, c2.class_var))

```





## 클래스 변수

* 인스턴스들의 전역 변수

* static 변수 = 메모리에 한 번 할당되어 프로그램이 종료될 때 해제되는 것을 의미한다.

* 클래스명으로 값 조작

* 다른 언어에서는 `static` 키워드를 명시함. 다른 언어에서는 `인스턴스명.` 으로 접근해도 클래스 변수처럼 적용된다.

  

  

## 인스턴스 변수

* 객체 안에서만 레퍼런스되는 변수
* 생성될때마다 초기화되는 변수
* 생성자를 통해서 선언하는 변수
* 객체명으로 값 조작







## Python vs 다른 언어

* python은 예를 들어 자바에 비해 문법적으로 유연하다.

* java에서는 클래스 변수는 명시적으로 static으로 명시를 해두고 `인스턴스명.` 으로 접근하여도 클래스 변수로 동작한다.

* 하지만 python 에서는 static으로 명시해두지 않고 클래스 변수는 `클래스명.`으로 접근하고 인스턴스 변수를 사용할 의도라면 `인스턴스명.`으로 사용자에게 책임 권한이 있다.

* 따라서, python은 문법이 엄격하지 않아 표준이 잘 되지 않을 가능성이 크다.

* 장단점이 존재한다.
  * 유연성이 있으면 쉽게 배울 수 있다.
  * 규모 큰 회사 (여러 개발자, 여러 회사들이 협업하는 곳)는 표준이 중요하다. 타입, 문법이 엄격한 것이 표준이 따르기 편하다.
* JavaScript는 ECMA6부터 `use strict` 를 명시하면 엄격하게 문법을 지키면서 사용 가능해졌다.
* 이를 위해 MS 의 typescript는 타입까지 명시해서 쓰게 하도록 하고 있다.
* JavaScript는 과거 프론트 단에서 드로잉, 이벤트 처리 역할에만 집중되었을 때는 굳이 엄격한 문법이 필요하진 않았다.
* 하지만  서버로부터 API형태로 데이터를 받아 모든 로직을 프론트단에서 처리하는 등 역할이 확대되면서 엄격한 문법이 중요하게 되었다. 또한 역할별로 MVC 패턴 적용하게 되었다.
* 유연성으로 인해 컴파일 타임에 발생 안 되니 테스트하는 게 많아지게 되었다.
* 그래서  `use strict` 를 통해 컴파일 타임에 syntax 에러를 잡고 로직은 테스트를 통해서 확인하게 되었다.



