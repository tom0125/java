## 第八章　例外の処理
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
    #### ■ point
    - Exception クラス図
      ![Exception クラス図](https://github.com/yoshitaku-jp/test_doc/blob/images/dog_akitainu.png)
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
18. 　
19. 
20. 