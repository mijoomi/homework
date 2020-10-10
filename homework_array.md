# homework_array

> **문자열을 거꾸로 출력하기**

- 문자열을 입력받고 이를 거꾸로 출력하는 프로그램을 제작한다. 아래의 조건을 만족해야 한다.
  문자열을 입력받아 char 배열에 저장 문자열을 거꾸로 만드는 메소드 구현` (메소드 명: reverseArr)`
- 배열의 원소들이 거꾸로 배치되도록 코딩하기 문자열을 출력해주는 메소드 구현` (메소드 명: printArr)` 아래와 같이 입출력이 이루어져야 함

> 입력예시

```
show me the money
```

> 출력예시

```
yenom eht em wohs
```

> 문제풀이 

```java
package aa;

import java.util.Scanner;

public class Bul {
	 public static void reverseArr(char [] a, int idx1,int idx2){
		 char t = a[idx1];
		 a[idx1] = a[idx2];
		 a[idx2] = t;
	 } // 배열의 순서를 바꾸어 주는 메서드 
	 public static void  printArr(char []a){
		 for(int i=0;i<a.length/2;i++) {
			 reverseArr(a,i,a.length-i-1);
		 } // 배열의 순서를 바꾸어 주는 메서드2
		 for(int i=0;i<a.length;i++) {
			 System.out.print(a[i]);
		 } // 배열 원소를 출력하는 메서드 
	 }
	 public static void main (String[]args) {
		 Scanner sc = new Scanner(System.in);
         System.out.println("문자열을 입력해주세요 :");
		 String str = sc.nextLine(); // 문자열을 입력받음 
		 char [] data = str.toCharArray(); // 문자열을 한글자씩 문자배열에 저장
		System.out.println("배열원소 :");
		 printArr(data);

	 }
}
```

> 주관적인 코드리뷰

- 배열의 순서를 바꾸어주는 메서드 2를 어디에 넣어야 하지 고민하다가 아무곳에 넣었다 .
  메인스레드 안으로 뺄걸그랬나싶다 . 그래서 수정 해보았다 . ( 큰 차이는 없다 .) 
- 개인적으로 수정한 부분이 조금더 보기가 좋은거같다 .

```java
public class Bul {
	 public static void reverseArr(char [] a, int idx1,int idx2){
		 char t = a[idx1];
		 a[idx1] = a[idx2];
		 a[idx2] = t;
	 }
	 public static void  printArr(char []a){
		 for(int i=0;i<a.length;i++) {
			 System.out.print(a[i]);
		 }
	 }
	 public static void main (String[]args) {
		 Scanner sc = new Scanner(System.in);
		 System.out.println("문자열을 입력해주세요 :");
		 String str = sc.nextLine();
		 char [] data = str.toCharArray();
		 
		 for(int i=0;i<data.length/2;i++) {
			 reverseArr(data,i,data.length-i-1);
		 }
		 printArr(data);

	 }
}
```

