# 메소드

> **어떤 작업을 수행하기 위한 문장들을 묶어 놓은것 **
>
> **사용 방법 :**

> `접근제어자` +`반환형 `+(`매개변수`) {
>
> `실행할 내용 `
>
> `return` ( 없을경우 생략가능)
>
> }



# 메소드오버로딩

> **동일한 이름의 메소드를 매개 변수와 , 타입을 다르게하여 사용하는것**
>
> **타입이 다르거나 , 매개변수의 갯수가 달라야한다**



# 문제 및 메소드, 오버로딩 예시



> **문제 1) 사칙 연산을 하는 계산기 프로그램을 제작한다. 아래의 조건을 만족시켜야 한다.**
>
> - 더하기, 빼기, 곱하기, 나누기 기능을 하는 메소드를 제작한다.
>
> - 각 메소드들은 정수형 데이터와 실수형 데이터를 각각 받을 수 있도록 오버로딩 되어야 한다.
>
> - 메소드 호출 시 값을 직접 숫자로 넘겨 사용하며, 아래와 같은 방법으로 받게 된다.
>
> - 10 + 4= 14	10.4 + 4 = 14.4	4 + 40.4 = 44.4	52.2 + 10.0 = 62.2



```java
public class Bul {
       static int sum(int x,int y) {
    	   return x+y;
       } //int형 덧셈 
       static int add(int x,int y) {
    	   return x-y;
       }//int형 뺏셈
       static int mul(int x,int y) {
    	   return x*y;
       }//int형 곱셈
       static double div(int x,int y) {
    	   return x/y;
       }//int형 나눗셈
       static double sum(double x,double y) {
    	   return x+y;
       }//double형 덧셈
       static double add(double x,double y) {
    	   return x-y;
       }//double형 뺏셈
       static double mul(double x,double y) {
    	   return x*y;
       }//double형 곱셈
       static double div(double x,double y) {
    	   return x/y;
       }//double형 나눗셈
}
	
```





