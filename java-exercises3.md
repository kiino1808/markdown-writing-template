
# Java章末問題（例外処理）

## 課題 0除算による例外に対応しよう
以下のような四則演算を行うクラスを用意しました。
```java
public class Calc {
    
    /** 加算 */
    public int plus(int a,int b){
            return a + b;
    }
    /** 減産 */
    public int minus(int a,int b){
        return a - b;
    }
    /** 乗算 */
    public int multiply(int a,int b){
        return a * b;
    }
    /** 除算 */
    public int divide(int a,int b){
            return a / b;
    }
}
```
<br>

### 例外の確認
Calcクラスのdivide()は、0で割る計算を行うと、例外が発生してしまいます。 まずは、例外の発生を以下のコードで確認してみましょう。
```java
Calc calc = new Calc();
int result = calc.divide(100,0);
System.out.println("戻り値は"+result+"です");
```
プログラムが以下のようなエラーを出力します。
```java
Exception in thread "main" java.lang.ArithmeticException: / by zero
```
<br>

### 例外に対応する
divide()にtry-catch文を実装して、0除算が発生したら以下のメッセージを出力するように修正します。また、エラー発生時の戻り値は0を返すようにします。
```java
0除算が発生しました
```
<br>

### 確認用のソースコード
以下のコードを実行して、期待値が出力されることを確認してください。
```java
Calc calc = new Calc();
int result = calc.divide(100,0);
System.out.println("戻り値は"+result+"です");
```

```java
0除算が発生しました
戻り値は0です
```