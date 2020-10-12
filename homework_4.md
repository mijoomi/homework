# home work_4

> **문제 1 로또 1등 당첨 확률 구하기 **

- 로또 당첨 번호 생성 (7개의 숫자, 마지막 숫자는 보너스 번호, 1~45번 숫자 중 랜덤으로 선택, 숫자 중복 불가능)
- 로또 추첨 번호 생성 (6개의 숫자, 1~45번 숫자 중 랜덤으로 선택, 숫자 중복 불가능)
-  로또 1등 조건: 보너스 숫자를 제외한 6개의 숫자 모두 일치
- 자동 번호 생성기를 통해 숫자 7개 생성
-  1등 당첨 확률을 %로 표시

> 문제풀이

```java
public class Bul {
	public static void main(String[] args) {
		Random random = new Random();

		int[] num1 = new int[7]; // 1등 당첨 번호 , 마지막 숫자는 보너스 번호
		int[] num2 = new int[6]; // 1등 추첨번호
		int count = 0; // 구매횟수
		long money=0; // 구매 금액
		

		random1: while (true) {
			count += 1; // 구매횟수 증가 
			money+=1000;	// 구매 금액증가
			for (int i = 0; i < num1.length; i++) { // 당첨번호 7개 생성
				num1[i] = random.nextInt(45) + 1;
				for (int j = 0; j < i; j++) {
					if (num1[i] == num1[j]) {
						i--;
					}
				}

			}
			for (int i = 0; i < num2.length; i++) { // 추첨 번호 6개 생성
				num2[i] = random.nextInt(45) + 1;
				for (int j = 0; j < i; j++) {
					if (num2[i] == num2[j]) {
						i--;
					}
				}
			}
			int x = 0; // 번호가 일치하면 카운트할 정수 

			for (int j = 0; j < num2.length; j++) { 
                //당첨 번호와 추첨번호를 비교하는 반복문
				for (int k = 0; k < num2.length; k++) {
					if (num1[j] == num2[k]) {
						x += 1; //번호가 일치하다면 카운트 
					}
				}
			}
			if (x == 6) { //6개의 번호가 일치한다면 
				break random1; //반복문 종료 
			}
		}

		for (int i = 0; i < num1.length; i++) { //1등 당첨번호 출력
			System.out.print(" " + num1[i]);
		}
		System.out.println();
		for (int i = 0; i < num2.length; i++) { //1등 추첨번호 출력
			System.out.print(" " + num2[i]);
		}
	
		System.out.println();
		System.out.println("구매횟수 : " + count); 
		System.out.println("구매금액 : " + money );
		System.out.println("당첨 확률 : " +(double) 1/count*100);

	}
}

```

> **문제2 로또 2등 당첨 확률 구하기 **

- 로또 당첨 번호 생성 (7개의 숫자, 마지막 숫자는 보너스 번호, 1~45번 숫자 중 랜덤으로 선택, 숫자 중복 불가능)> 
- 로또 추첨 번호 생성 (6개의 숫자, 1~45번 숫자 중 랜덤으로 선택, 숫자 중복 불가능)
- 로또 2등 조건: 숫자 5개 일치 및 보너스 숫자(마지막 번호) 일치 
- 자동 번호 생성기를 통해 숫자 7개 생성
- 2등 당첨 확률을 %로 표시

```java
public class Bul {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		Random random = new Random();

		int[] num1 = new int[7]; 
		int[] num2 = new int[6];
		int count = 0; // 구매횟수
		long money = 0;

		random1: while (true) {
			count += 1;
			money += 1000;
			for (int i = 0; i < num1.length; i++) { //위에 코드랑 동일 
				num1[i] = random.nextInt(45) + 1;
				for (int j = 0; j < i; j++) {
					if (num1[i] == num1[j]) {
						i--;
					}
				}

			}
			for (int i = 0; i < num2.length; i++) { //위에 코드랑 동일 
				num2[i] = random.nextInt(45) + 1;
				for (int j = 0; j < i; j++) {
					if (num2[i] == num2[j]) {
						i--;
					}
				}
			}
			int x = 0;
			int h = 0; //보너스 숫자가 추첨번호에 포함되면 카운트 할 변수 
			for (int j = 0; j < num2.length; j++) {
				for (int k = 0; k < num2.length; k++) {
					if (num1[j] == num2[k]) {
						x += 1;
						if (x == 5) { //5개가 일치한다면 반복문 탈출 
							break;
						}
					}
				}
			}
			for (int v = 0; v < num2.length; v++) { 
                //보너스 숫자와 일치하는 숫자가 있다면 
				if (num1[6] == num2[v]) {
					h += 1; // 변수에 1 카운트
				}
			}

			if ((x == 5) && (h == 1)) {
				break random1; //5개가 일치하고 , 보너스 번호가 있다면 조건문종료
			}
		}

		for (int i = 0; i < num1.length; i++) {
			System.out.print(" " + num1[i]);
		}
		System.out.println();
		for (int i = 0; i < num2.length; i++) {
			System.out.print(" " + num2[i]);
		}

		System.out.println();
		System.out.println("구매횟수 : " + count);
		System.out.println("구매금액 : " + money);
		System.out.println("당첨 확률 : " + (double) 1 / count * 100);

	}
}

```

> *~~주관적인 코드리뷰~~*  

첫번째 문제 풀때는 num1과 num2를 헷갈려 삽질을 하는바람에 고생했다 .  

변수명뒤에 숫자 붙이는게 습관인데 , 고쳐야 겠다 ㅠㅠ .

두번째 문제는 첫번째 문제에서 살짝 수정만해서 빨리 풀었다 .

중복숫자 안받는 더 좋은방법이 있을거같은데 ,  선생님한테 여쭈어보고 수정해서 재업로드 해야겠다 .