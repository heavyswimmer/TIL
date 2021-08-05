# 싱글턴 패턴(Singleton pattern)

## 정의
싱글턴 패턴은 인스턴스가 사용될 때에 매번 새로운 인스턴스를 만들어 내지 않고 동일한 인스턴스 1개만을 사용하도록 하는 것이다.<br>
따라서 생성자가 여러 차례 호출되더라도 실제로 생성되는 객체는 하나 뿐이며, 최초 생성 이후에 호출된 생성자는 최초의 생성자가 생성한 객체를 리턴해준다.<br>
다시 말해, 싱글턴 패턴을 따르는 클래스란 인스턴스가 사용될 때마다 새로 생성할 필요 없이 최초로 생성한 인스턴스 하나를 계속 참조해서 재사용하는 클래스를 말한다.<br>
이러한 방식은 프로그램 상에서 계속 동일한 문법을 가진 인스턴스를 반환해야 할 때 유용하게 사용된다.


## 사용방식
1. private 변수로 자기 자신의 클래스 인스턴스를 갖도록 한다. 이 때 접근제한자는 private 이므로, 외부 클래스에서는 접근이 불가능하다. 또한 static 변수로 지정하여 클래스를 사용할 때 객체생성은 딱 1번만 생성되도록 해야 한다.
2. 생성자에 접근제한자를 private 로 지정하여 외부에서는 인스턴스를 생성하지 못하도록 한다.
3. static 메소드를 생성하여 외부에서 해당 클래스의 객체를 사용할 수 있도록 해준다.

<br>

```java
package jdbc.day04.singletonPattern;

public class SingletonNumber {
	
	// field, attribute, property 속성 정의 (첫번째)
	private static SingletonNumber singleton = null;
	
	// 인스턴스 변수
	private int cnt = 0;
	

	// ==> static 초기화 블럭  <== //
	static {
	    // static 초기화 블럭은 해당 클래스가 객체로 생성되기전에 먼저 실행되어지며,
	    // 딱 1번만 호출되어지고 다음번에 새로운 객체(인스턴스)를 매번 생성하더라도
	    // static 초기화 블럭은 호출이 안되어진다.
		
		singleton = new SingletonNumber();
		
		System.out.println(">>> SingletonNumber 클래스의 static 초기화 블럭 호출됨. <<<");
	
	}
	
	private SingletonNumber() {}


	public static SingletonNumber getInstance() {
		return singleton;
	}
	
	///////////////////////////////////////////////////////////////////////////////
	// 인스턴스 메소드
	public int getNextNumber() {
		return ++cnt;	// 인스턴스 변수
	}
}
```
