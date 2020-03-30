## 第五章　ループ構造の使用
1. ○  
2. ○  
3. ○  
    #### ■ point 
    - while文やdo-while文では、中括弧を省略した場合、次の文だけが繰り返しの対象になる。  
    - do-while文で中括弧を省略した場合には、doとwhileの間には一文のみを記述できる。二文以上記述した場合にはコンパイルエラーになる。  
    - セミコロンが現れるまでが一つの文のため,中カッコを使わないwhile文の中に複数行に渡るdo-while文を記述することは問題ない。  
    ``` java
    while(条件文)
      do{
        //複数行の処理
        
      }while;
    ```
4. ☓  
    #### 問題のコード   
    ```java
    public class Main{
      public static void main(String[]args){
        for(int i = 0,long j = 2; i < 5; i++){//コンパイルエラー　初期化文で複数の変数を宣言する場合、変数は同じ型でなければならない
          system.out.println(i * j);
        }
      }
    }
    
    ```
    #### 複数の一時変数を使用したfor文
    ``` java
    for(int i = 0, j = 0; i < 3; i++ ){
      //繰り返し処理
    }
    ````
5.  
    #### 問題のコード
    ``` java
    public class Main{
      public static void main(String[] args){
        int a = 1;
        for(int b = 2, total = 0; b <= 5; b++){
          total = a + b;
        }
        System.out.println(total);//コンパイルエラー
      }
    }
    ```
    #### ■ point
    - for文の初期化分で宣言した変数は、for文のブロック外で使うことができない。
6.
7.
8.
9.
10.
11.
12.
13.
14.
15.
16.
17.