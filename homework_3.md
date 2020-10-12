# homework_3

> 주사위 확률구하기

- 주사위 한 개를 던졌을 때 3보다 클 확률과 주사위 두 개를 던졌을 때 6보다 클 확률을 각각 비교해본다. 아래와 같은 조건으로 프로그램을 작성한다.

- 주사위를 3개 생성주사위 변수는 배열로 생성하고 배열의 크기는 1000으로 설정1~6까지 숫자를 생성하는 랜덤객체를 생성하고 각 주사위 변수에 값을 넣는다 - random.nextInt(6) + 1

-  1000번을 실행하여 각 조건에 맞을 경우 카운트를 진행주사위 rol1값: 3보다 클 경우주사위 rol2, rol3의 합: 6보다 클 경우> 결과를 %로 표시

> 문제풀이

```java
import java.util.Random;
import java.util.Scanner;

public class Bul {
	public static void main(String[]args) {
	Scanner sc= new Scanner(System.in);
	Random  random = new Random();
	int num = 0; // 1개의 확률을 카운트 하기 위한 변수 
	int num2 = 0;	// 2개의 확률을 카운트 하기 위한 변수 
	int [] dice = new int [1000]; //주사위 변수 배열생성
	int [] dice1 = new int [1000];
	int [] dice2 = new int [1000];
	
	for(int i =0;i<1000;i++) { // 주사위하나를 던졌을때 3이상이 나올확률을 구하는 반복문
		dice[i] = random.nextInt(6)+1;
		if(dice[i]>3) { //배열 dice[i]가 3이상 일경우 카운트 
			num++;
		}
		
	}
	System.out.println("주사위 한개 확률"+num*0.1+"%"); //퍼센트 출력
	
	for(int i =0;i<1000;i++) { // 주사위하나를 던졌을때 3이상이 나올확률을 구하는 반복문
		dice1[i] = random.nextInt(6)+1;
		dice2[i] = random.nextInt(6)+1;
		if(dice1[i]+dice2[i]>6) { //배열 dice1[i]+ dice2[i]가 6이상 일경우 카운트
			num2++;
		}
		
	}
	System.out.println("주사위 두개 확률"+num2*0.1+"%"); //퍼센트 출력
}

}
```

> 주관적인 코드리뷰 

나.. 나쁘지 않은 코드 였다 . 오늘 풀었던 문제중에 제일 깔끔하다 . ~~( 난이도가 쉬운걸지도)~~