---
title : "변수의 scope와 static"
categories : JAVA
date : "2021-01-31"
---

[7번째 포스트]

프로그램상에서 변수들은 각자 사용 가능한 범위를 가진다.

그 범위를 **변수의 스코프**라고 한다.



### 변수의 종류

* 인스턴스변수

  클래스 내에서 선언되는 변수. 생성된 객체마다 각각 다른 값을 가질 수 있다. ---(1)

* 클래스변수

  클래스 내에서 선언되면서 앞에 static 키워드가 붙는다. 이 변수는 값을 **공유**하는 변수로서, 객체마다 값이 변하지 않는다. ---(2)

  (인스턴스변수와 클래스변수를 멤버변수라 한다.)

* 지역변수

  메소드나 생성자 내부에 선언되는 변수로서,  해당 메소드/생성자 안에서만 사용 가능하다. ---(3)



모든 멤버변수(인스턴스변수,클래스변수)는 defalut 값을 가진다. 즉, 초기화가 필요없다.

이 변수들은 힙 메모리에 올라가는데, 힙 메모리에서는 자동으로 초기화해준다.

지역변수는 초기화를 무조건 해줘야 한다. 이 변수는 스택 메모리에 올라가는데, 스택 메모리는 자동으로 초기화해주지 않는다.



### static 키워드는 무엇인가?

* 메소드, 필드 등에 키워드 static을 사용하면 해당 클래스를 인스턴스화(객체로 변환)하지 않아도 사용 가능하다. ---(4)

* static 메소드에서는 static 필드, 메소드만 사용 가능하다. 그 외에는 인스턴스화 후 사용해야 한다. ---(5)

  그동안 메인메소드에서 static 키워드가 항상 있었던 것을 볼 수 있다. 

  메인메소드에서 해당 클래스의 필드, 메소드를 호출할 때 항상 인스턴스화 시킨 이유를 여기서 알 수 있다.

* static키워드가 붙은 클래스 변수는 값을 공유한다. ---(6)

* 클래스변수는 인스턴스화하지 않으므로 참조변수.속성이 아닌 클래스명.클래스변수로 접근 가능하다. ---(7)



앞선 정리를 코드로 다시 정리해보면...

```java
public class ScopeAndStatic {
    int globalscope = 10; //인스턴스변수 (멤버변수) (1)
    static int staticVal = 7; //클래스변수 (멤버변수) (2)
    
    public void scopeTest(int value) {
        int localScope = 20; //지역변수 (3)
        System.out.println(globalScope); //클래스영역에서 선언된 변수이므로 사용 가능
        System.out.println(localScope); //해당 메소드의 지역변수는 당연히 사용 가능
        System.out.println(value); //메소드의 매개변수도 사용 가능
    }
    
    public void scopeTest2(int value2) {
        System.out.println(globalScope);
//      System.out.println(localScope); 다른 메소드의 지역변수는 사용 불가
//		System.out.println(value); 해당 메소드의 매개변수가 아니므로 사용 불가
        System.out.println(value2);
    }
    
    public static void main(String[] args) { //메인메소드는 static메소드!
//		System.out.println(globalScope); 인스턴스변수는 static메소드에서 인스턴스화 후 실행해야만 함! (5)
        System.out.println(staticVal); //클래스변수는 인스턴스화 하지 않는다 (4)
        
        ScopeAndStatic a = new ScopeAndStatic(); //객체 생성
        System.out.println(a.globalScope); //인스턴스화했으므로 정상 실행
        
        ScopeAndStatic a2 = new ScopeAndStatic();
        a.globalScope = 10;
        a2.globalScope = 20;
        System.out.println(a.globalScope); //10 출력
        System.out.println(a2.globalScope); //20 출력
        //인스턴스변수는 생성된 객체마다 각각 다른 값을 가질 수 있다. (1)
        
        a.staticVal = 50;
        a2.staticVal = 100;
        System.out.println(a.staticVal); //100 출력
        System.out.println(a.staticVal); //100 출력
        //클래스변수는 단지 하나의 값만 가진다. 값을 공유하는 특성. (2,6)
        
        System.out.println(ScopeAndStatic.staticVal);
        //클래스변수는 인스턴스화가 필요 없으므로 클래스명.클래스변수로 접근 가능 (7)
    }
}
```



