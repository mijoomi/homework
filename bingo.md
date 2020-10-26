# 나 혼자하는 빙고게임 만들기

>학원쌤이 내주신 숙제 였던 혼자하는 빙고게임 만들기 ,

```java
import java.util.*;
public class Main {
        public static void bingoprint(int[][] arr) { // 빙고판프린트 .
                for (int i = 0; i < arr.length; i++) {
                        for (int j = 0; j < arr.length; j++) {
                                System.out.print(arr[i][j] + "\t");
                        }
                        System.out.println();
                }
        }

        public static boolean bingonum(int[][] a, int num) { 
            //빙고번호 중복확인 메서드 
                for (int i = 0; i < a.length; i++) {
                        for (int j = 0; j < a.length; j++) {
                                if (num == a[i][j]) {
                                        return false;
                                }
                        }
                }
                return true;
        }

        public static void main(String[] args) {
                Scanner sc = new Scanner(System.in);
                Random random = new Random();

                int[][] arr = new int[5][5]; //빙고판 생성


                System.out.println("빙고판을 생성합니다.");

                for (int i = 0; i < arr.length; i++) {        
                    //빙고판 번호 생성
                        for (int j = 0; j < arr.length; ) {
                                int num = random.nextInt(45) + 1;
                                while (bingonum(arr, num)) {
					 //중복확인 메서드를 사용하여 중복이 없을경우
                   //true를 반환해서 while문 실행 후 배열에 변수 대입.
                                        arr[i][j] = num;
                                        j++;
                                }
                        }
                }

                bingoprint(arr);


                while (true) {

                        int bingocont =0; // 빙고 줄 카운트 변수 
                     	int count1 = 0;  // 왼쪽 대각선 체크
                    	int count2 = 0; // 오른 대각선 체크 

                        System.out.println("숫자를 입력해 주십시오 : ");


                        int mynum = sc.nextInt(); // 입력받을 숫자 

                        if (bingonum(arr, mynum)==true) {
                            // 빙고판에 숫자가 없을경우 .
                                System.out.println("입력한 숫자는 빙고판에 없습니다.");
                        }

                        if (bingonum(arr, mynum) == false) {
                                //입력받은 숫자가 빙고판에 있다면 0으로 지워줌
                                for (int i = 0; i < arr.length; i++) {
                                        for (int j = 0; j < arr.length; j++) {
                                                if (mynum == arr[i][j]) {
                                                        arr[i][j] = 0;
                                                }
                                        }
                                }
                        }
                        for(int i=0;i<arr.length;i++){ //가로 빙그체크
                                int count = 0;
                                for(int j=0; j<arr.length;j++) {
                                        if (arr[i][j] == 0) {
                                                count += 1;
                                                if (count == 5) {
                                                        bingocont += 1;
                                                }
                                        }

                                }
                        }
                        for(int i=0;i<arr.length;i++){ //세로빙고체크
                                int count = 0;
                                for(int j=0; j<arr.length;j++){
                                        if(arr[j][i]==0){
                                                count +=1;
                                                if(count==5){
                                                        bingocont+=1;
                                                }
                                        }


                                }
                        }

                        for(int i=0;i<arr.length;i++){ //왼쪽대각선 빙고체크
                                        if(arr[i][i]==0) {
                                                count1 += 1;
                                                if (count1 == 5) {
                                                        bingocont += 1;
                                                }
                                        }

                                }       

                        for(int i=0;i<arr.length;i++){
                                int j = 4-i ;//오른대각선 빙고체크
                                if(arr[i][j]==0) {
                                        count2 += 1;
                                        if (count2 == 5) {
                                                bingocont += 1;
                                        }
                                }
                         }
                        bingoprint(arr);

                        if(bingocont ==5){
                            // 빙고 5개 달성시 반복문 종료 .
                                System.out.println(bingocont+"개의 빙고 !");
                                break;
                        }
                        }
                System.out.println("빙고게임 끝");

                }
        }

```

# 실행결과

> 한번 숫자를 입력할때마다 빙고판을 출력하는데 , 모두 실행결과에 입력하기엔 너무 길어서 생략하고 , 최종 프린트 된 결과만 가져왔습니다 .

```java
0	35	8	0	0	
42	0	0	0	45	
26	30	0	0	19	
0	0	0	0	0	
0	0	0	0	0	
5개의 빙고 !
빙고게임 끝
```

# 주관적인 이모저모.

```
최근 했던 코딩중에서는 제일길다 ..; 
난이도가 높진 않았지만 100줄 넘어가는 코드는 처음 짜본거같다 . 
(빙고 검사는 복붙해서 시간이 오래걸리진 않았지만 ;;) . 
메서드로 만들어 쓸까했는데 , 
((주관적으로 )) 그냥 쓰는게 더 가독성이 편할거같아서 그냥 .. 
```

