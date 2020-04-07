## 第八章　例外の処理

 - Exception クラス図  
      1. 非検査例外　try/catchで例外ハンドリングする必要がない
      1. 検査例外　try/catchで例外ハンドリングする必要あり
      ![Exception クラス図](https://github.com/tom0125/java/blob/master/image/Exception%20%E3%82%AF%E3%83%A9%E3%82%B9%E5%9B%B3.jpg)

1. ○
2. ☓
    #### ■ point
    - 起動パラメータを渡さずにプログラムを実行した場合、mainメソッドのString型配列変数には、要素数0の配列インスタンスへの参照が渡される。
3. ☓
    #### ■ point
    - 複数のcatchブロックがある場合、どちらの例外が先にキャッチされるのか確認。到達可能なコードでなければ、コンパイルエラーになる。
4. ○
5. ○△
    #### ■ point
    - carchブロック内でreturnされていても、returnによって呼び出し元のメソッドに制御が戻る前に、finallyブロックは必ず実行される。
      finallyブロックが終了してから制御が戻される。
    - finallyブロックが実行されないのは、tryブロックやcatchブロック内で、System.exitメソッドを呼び出して、アプリケーションを強制終了したときか、JVMやOSがクラッシュしたときだけ
6. 　☓　catchブロックと、finallyブロックの両方がreturnで値を戻す場合、どちらの値が戻されるか
    
7. ☓
    #### ■ point
    - return で戻り値を戻すときに使われる変数が存在する。
8. ○　
9. ○
10. ○
     #### ■ point
     - Javaにおけるプログラムの実行中に発生するトラブルには、大きくわけて2つの種類がある。
      1. 実行環境のトラブルなど、プログラムからは対処しようのない**エラー**
      1. プログラムが対処できる**例外**
     - 例外はさらに、検査例外と非検査例外にわけられる
      1. 検査例外とは、例外処理を記述したかどうかをコンパイラが検査する例外
      1. 非検査例外とは、例外処理を記述したかどうかコンパイラが検査しない例外
     - Exceptionクラスのサブクラスは、RuntimeExceptionとそのサブクラスを除いて、全て検査例外。
      そのため、Exceptionクラスを継承している例外クラスはtry-catchしているか、もしくはthrow句で宣言しているかのどちらかを強制される。
11. 　○　
    #### ■ point
    - エラーの場合、例外と違ってプログラムで対処することを求められない。
      そのため、try-ctachしたりthrowsで宣言する必要がない。
12. ○
13. ☓
     #### ■ point
     - 配列や文字列、コレクションで存在しない要素を取り出そうとするとIndexOutOfBoundsExceptionが発生
     - public class ArrayIndexOutOfBoundsExceptionextends IndexOutOfBoundsException
      不正なインデックスを使って配列がアクセスされたことを示すためにスローされます。つまり、インデックスが負または、配列のサイズ以上の場合です。
     - **IndexOutOfBoundsException**は、ArrayIndexOutOfBoundsException,StringIndexOutOfBoundsExceptionのスーパークラス
14. ○クラスキャストと例外クラスに関する問題
    #### ■ point
    - 継承関係や実現関係にないクラスにキャストしようとすると、**ClassCastException**が発生する
    
15. ○ IllegalArgumentException
    #### ■ point
    - public class IllegalArgumentException extends RuntimeException
    - 不正な引数、または不適切な引数をメソッドに渡したことを示すためにスローされます。
    - 利用される側のオブジェクトが不正な引数を渡されたことを、利用する側のオブジェクトに通知するための例外

16. ○
    ```java
    public class Person {
      private String name;

      public void setName(String name) {
        this.name = name;
      }

      public void introdue(String address){
                    // 引数のチェック
        if(address == null){
          throw new NullPointerException("addressがnullです。");
        }
        if(address.length() > 16){
          throw new IllegalArgumentException("addressが16桁を超えています。");
        }
        System.out.printf("私の名前は%sです。住所は%sです。", name, address);
      }

      public void introdue(String address){
        // 引数のチェック
        if(address == null){
          throw new NullPointerException("addressがnullです。");
        }
        if(address.length() > 16){
          throw new IllegalArgumentException("addressが16桁を超えています。");
        }
        
        // 状態のチェック
        if(name == null){
          throw new NullPointerException("nameが正しく初期化されていません。");
        }
        if(name.length() > 8){
          throw new IllegalStateException("nameが8桁を超えています。");
        }

        System.out.printf("私の名前は%sです。住所は%sです。", name, address);
      }
        }
    ```
    #### ■ point
    - IllegalStateException ---オブジェクト自身の状態(フィールド,属性,プロパティ(Beans setter/getter))が適切でない場合にスローする例外

17. ○
    ```java
    String str = null;
    //nullPointExceptionを発生させる可能性のある書き方
    if(str.equals("")){
      System.out.println("blank");
    }
    //安全な書き方
    if("".equals(str)){
      System.out.println("blank");
    }


    ```
18. △
    #### ■ point
    - public class NumberFormatException extends IllegalArgumentException ---アプリケーションが文字列を数値型に変換しようとしたとき、文字列の形式が正しくない場合にスローされます。
19.  ☓
    #### ■ point
    - staticイニシャライザは、クラスを利用するときに一度だけ呼び出させる初期化ブロックです。
    - staticイニシャライザを処理している間に何らかのトラブルが発生したときには、そのことを通知する相手がいないため
      JVMはExceptionInitializerErrorを発生させ、プログラムを強制終了させる
20. ○
    #### ■ point
    - メソッドが呼び出されると、メソッドの実行に必要な情報がメモリのスタック領域に配置される。
    - そのため再帰呼び出しを行っていると、スタック領域が足りなくなった場合、JVMはそのことを検知すると**StackOverflowException**をスローしプログラムを強制終了させる。
21. ○
    #### ■ point
    - JVMが実行対象のクラスファイルを発見できなかった場合にスローする例外は、**NoClassDefFoundError**
22. ○
    #### ■ point
    - ヒープメモリとはインスタンスを保存したり、クラスの定義情報を保存したりするためのメモリ領域。
      大量のインスタンスを作りガベージコレクションが行われないと、この領域がいっぱいになってしまい新しいインスタンスが作れなくなってしまう。
      このような自体を検知するとJVMは**OutOfMemoryError**を発生させる。