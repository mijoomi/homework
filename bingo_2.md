#  빙고게임 _ 2 ( 컴퓨터와 하는 빙고게임)

> 전에 했던 빙고게임을 이용해서 컴퓨터와 하는 빙고게임을 만들었다 .
>
> 중간에 무한루프의 늪에 빠져서 고생했다 .

```java
package com.company;

import java.util.Scanner;

public class BingoMain {
    public static void main (String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("닉넴");
        String nickname = sc.next();
        Player p1 = new Player(nickname);
        ComPuter c1 = new ComPuter();



        p1.playerReade();
        c1.computerReade();
        System.out.println("플레이어의 보드판 입니다 ");
        p1.print();
        System.out.println();
        System.out.println("컴퓨터의 보드판 입니다.");
        c1.print();

        while (true) {
            System.out.println(p1.getNickname()+"의 순서입니다 .");
            int num = sc.nextInt();
            if (p1.setNumber(num) == false) {
                continue;
            }
            else {
                p1.setNumber(num);
            }
                if(p1.getbingo()==1) {
                    System.out.println(p1.getNickname() + " 승리");
                    break;
                } else {
                    c1.setNumber(num);
                    if (c1.getbingo()==1) {
                        System.out.println(c1.getNickname() + "의 승리");
                        break;
                    }
                }
            p1.print();
            System.out.println(p1.getbingo());
            System.out.println();

            System.out.println(c1.getNickname()+"의 순서입니다 .");

            int num2 = c1.setNumber();
            System.out.println(num2);

            if (c1.getbingo() == 1) {
                System.out.println(c1.getNickname() + "승리");
                break;
            } else {
                c1.setNumber(num2);
                if (c1.getbingo() == 1) {
                    System.out.println(p1.getNickname() + "승리");
                    break;
                }
            }
            c1.print();

        }
    }
}
```

```java
package com.company;

import java.util.Random;

public class Bingo {
    private int [][] board;
    private int count;

    public Bingo(){
        board = new int[5][5];
        count = 0;
    }


    public void creatBoard() {
        Random random = new Random();
        for (int i = 0; i < board.length; i++) {
            //빙고판 번호 생성
            for (int j = 0; j < board.length; ) {
                int num = random.nextInt(45) + 1;
                while (bingonum(num)) {
                    //중복확인 메서드를 사용하여 중복이 없을경우
                    //true를 반환해서 while문 실행 후 배열에 변수 대입.
                    board[i][j] = num;
                    j++;
                }
            }
        }
    }

    public int getbingo(){
        return count;
    }

            boolean bingonum (int num) {
                //빙고번호 중복확인 메서드
                for (int i = 0; i < board.length; i++) {
                    for (int j = 0; j < board.length; j++) {
                        if (num == board[i][j]) {
                            return false;
                        }
                    }
                }
                return true;
    }


    public boolean selectNum(int num) {
        if (bingonum(num) == false) {
            //입력받은 숫자가 빙고판에 있다면 0으로 지워줌
            for (int i = 0; i < board.length; i++) {
                for (int j = 0; j < board.length; j++) {
                    if (num == board[i][j]) {
                        board[i][j] = 0;
                        bingocheck();
                        return true;
                    }
                }
            }
        }
        return false;
    }
    public void bingocheck(){
        this.count =0;
        for(int i=0;i<board.length;i++){ //가로 빙그체크
            int count1 = 0;
            for(int j=0; j<board.length;j++) {
                if (board[i][j] == 0) {
                    count1 += 1;
                    if (count1 == 5) {
                        this.count += 1;
                    }
                }

            }
        }
        for(int i=0;i<board.length;i++){ //세로빙고체크
            int count2 = 0;
            for(int j=0; j<board.length;j++){
                if(board[j][i]==0){
                    count2 +=1;
                    if(count2==5){
                        this.count += 1;
                    }
                }


            }
        }
        int count1 =0 ;
        for(int i=0;i<board.length;i++){ //왼쪽대각선 빙고체크
            if(board[i][i]==0) {
                count1 += 1;
                if (count1 == 5) {
                  this.count += 1;
                }
            }

        }
        int count2=0;

        for(int i=0;i<board.length;i++){
            int j = 4-i ;//오른대각선 빙고체크
            if(board[i][j]==0) {
                count2 += 1;
                if (count2 == 5) {
                   this.count += 1;
                }
            }
        }
    }

    public void printbingo(){
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board.length; j++) {
                System.out.print(board[i][j] + "\t");
            }
            System.out.println();
        }
    }

}

```

```java
package com.company;

public class Player {
    private Bingo bingo;
    private String nickname;
    public Player(){
        this("Player");
    }

    public Player(String nickname){
        this.nickname = nickname;
        bingo = new Bingo();
    }

    public void playerReade(){
        bingo.creatBoard();
    }
    public boolean setNumber(int num){
        return bingo.selectNum(num);
    }
    public void print(){
        bingo.printbingo();
    }
    public int getbingo(){
     return bingo.getbingo();
    }
    public String getNickname(){
        return nickname;
    }

}

```

```java
package com.company;

import java.util.Random;

public class ComPuter {
    Random ram = new Random();
    private Bingo bingo;
    private String nickname;

    public ComPuter(){
        nickname = "computer";
        bingo = new Bingo();
    }

    public void computerReade(){
        bingo.creatBoard();
    }
    public int setNumber() {
        while (true) {
            int num = ram.nextInt(45) + 1;
            boolean num2 = bingo.bingonum(num);
            if (num2 == false) {
                return num;
            }
        }
    }
    public void setNumber(int number) {
        bingo.selectNum(number);
    }
    public void print(){
        bingo.printbingo();
    }
    public int getbingo(){
        return bingo.getbingo();
    }
    public String getNickname(){
        return nickname;
    }

}

```

