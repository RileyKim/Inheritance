# 상속 Inheritance
-------------------

객체 지향 프로그램에서 부모 클래스의 멤버를 자식 클래스에게 물려줄 수 있다.

부모 클래스 = 상위 클래스, 자식 클래스 = 하위 클래스 또는 파생 클래스

상속은 이미 잘 개발된 클래스를 재사용해서 새로운 클래스를 만들기 때문에 코드의 중복을 줄여준다.

###클래스 상속
---------------
자식 클래스를 선언할 때 어떤 부모 클래스를 상속받을 것인지를 결정하고 선택된 부모 클래스는 다음과 같이 extends 뒤에 기술한다.


```
class 자식 클래스 extends 부모 클래스 {
//필드
//생성자
//메소드
}
```

**다른 언어와는 달리 자바는 다중 상속을 허용하지 않는다.**

###부모 생성자 호출
-------------------------------

자바에서 자식 객체를 생성하면, 부모 객체가 먼저 생성되고 자식 객체가 그 다음에 생성된다.

```
//부모 객체 : CellPhone
//자식 객체 : DmbCellPhone

DmbCellPhone dmbCellPhone = new DmbCellPhone();

```

모든 객체는 클래스의 생성자를 생성해야만 생성된다. 
부모 객체는 자식 생성자의 맨 첫줄에서 생성할 수 있다.

```
Public DmbCellPhone(){
	super();
}
```

super()는 부모의 기본 생성자를 호출한다.


```
// 예시
// [부모클래스] People.java

public class People{
	public String name;
	public String ssn;
	
	public people(String name, String ssn){
		this.name = name;
		this.ssn = name;
	}
}
```


```
// 예시
// [자식클래스] Student.java

puublic class Student extends People{
	public int studentNo;
	
	public Student(String name, String ssn, int studentNo){
		super(name, ssn); // 부모 생성자 호출
		this.studentNo = studentNo;
	}
}
```
	

###메소드 재정의
--------------------
부모 클래스의 모든 메소드가 자식 클래스에게 맞게 설계되어 있다면 가장 이상적인 상속이지만, 어떤 메소드는 자식 클래스가 사용하기에 적합하지 않을 수도 있다. 이 경우 상속된 일부 메소드는 자식 클래스에서 다시 수정해서 사용해야한다.

**메소드 재정의(@Override)**

**메소드 오버라이딩**은 상속된 메소드의 내용이 자식 클래스에 맞지 않을 경우, 자식 클래스에서 동일한 메소드를 재정의하는 것이다.

```
//부모 클래스
class parent{
	void method1{}
}
```

```
//자식 클래스
class child extends parent{
	void method1{} // 재정의
}
```

**부모 메소드의 호출**

자식 클래스에서 부모 클래스의 메소드를 오버라이딩하게 되면, 부모 클래스의 메소드는 숨겨지고 오버라이딩된 자식 메소드만 사용된다. 그러나 자식 클래스 내부에서 오버라이딩된 부모 클래스의 메소드를 호출해야 하는 상황이 발생한다면 명시적으로 super 키워드를 붙여서 부모 메소드를 호출할 수 있다.

```
//부모 클래스
class parent{
	void method1{}
}
```

```
//자식 클래스
class child extends parent{
	void method1{} // 재정의
	super.method1(); // 부모 메소드 호출
}
```

**final 클래스는 상속할 수 없으면, final 메소드는 오버라이딩을 할 수 없다.**

