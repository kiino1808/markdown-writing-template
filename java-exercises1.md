
# Java章末問題（演算子～条件分岐）

## 課題1 奇数の和、偶数の和を求める

1からコマンドライン引数に与えられた整数までの和を、偶数と奇数で分けてそれぞれ表示してください。<br>
（ファイル名はCalcParity.javaとします）

※入力される数が負の場合や、文字の場合は考慮しなくて大丈夫です。

### コンパイル
```java
javac -encoding UTF-8 CalcParity.java
```

### 実行例
```java
java CalcParity 0
1から 1 までの偶数の合計は、0です.
1から 1 までの奇数の合計は、0です.

java CalcParity 1
1から 1 までの偶数の合計は、0です.
1から 1 までの奇数の合計は、1です.

java CalcParity 10
1から 10 までの偶数の合計は、30です.
1から 10 までの奇数の合計は、25です.

java CalcParity 100
1から 100 までの偶数の合計は、2550です.
1から 100 までの奇数の合計は、2500です.
```

### テンプレート
```java
public class CalcParity{
	public static void main(String args[]){
        // Enter your code here.
    }
}
```

### プログラム内でやること

#### 1. コマンドライン引数を読み込む
→ そのままだと<span style="color: red; ">文字列（String）として読み込まれてしまうの</span>で注意<br><br>
例えば、コマンドライン引数をそのまま読み込もうとすると、以下のように書けそうです。
```java
int num = args[0];
```
しかし、コンパイルしようとすると以下のようなエラーになります。
```java
javac -encoding UTF-8 CalcParity.java
CalcParity.java:6: エラー: 不適合な型: Stringをintに変換できません:
                int num = args[0];
                              ^
エラー1個
```

文字列を整数型に変換するには、Integer.parseIntメソッドを使用する必要があります。
```java
int num = Integer.parseInt(args[0]);
```
<br>

#### 2. 偶数と奇数で場合分けする
繰り返し処理の中に偶数か奇数かを場合わけする処理が必要になります。偶数であるかどうかは以下で判断が可能です。
```java
if(i % 2 == 0){
				// iが偶数の時の処理
			}else{
				// iが偶数ではないときの処理
			}
```
偶数（2で割ったあまりが0）かどうかで場合分けすることをお勧めします。

---
<br>

## 課題2 四則演算を実行する

コマンドライン引数に入力される数と演算子を用いて、四則演算の結果を表示してください。
（ファイル名はCalcInputs.javaとします）

※入力される数が負の場合や、文字の場合は考慮しなくて大丈夫ですが、<span style="color: red; ">演算子が正しくない場合</span>（+, -, ×, / 以外）には「演算子が正しくありません」という旨を表示してください。

### コンパイル
```java
javac -encoding UTF-8 CalcInputs.java
```

### 実行例
```java
java CalcInputs 100 + 2
100 + 2 = 102です.

java CalcInputs 100 - 2
100 - 2 = 98です.

java CalcInputs 100 × 2
100 * 2 = 200です.

java CalcInputs 100 / 2
100 / 2 = 50です.

java CalcInputs 100 1 2
演算子が正しくありません.

java CalcInputs 100 [ 2
演算子が正しくありません.
```
### プログラム内でやること

#### 1. String型の同値判定を行う
整数型の変数が同値かどうかを判断するには以下のように記述します。
```java
int a = 100;
int b = 100;
if(a == b){
    //条件がtrueのときの処理
}else{
    //条件がfalseのときの処理
}

String c = 'おはよう';
String d = 'おはよう';
if(c == d){
    //条件がtrueのときの処理
}else{
    //条件がfalseのときの処理
}
```
一見するとString型の変数も上のように同様の処理ができそうですが、実際に動かすとif(c == d)は<span style="color: red; ">必ずfalseとして扱われて</span>しまいます。
<br>

文字列が同一

---
<br>

## 課題3 九九の表を表示する
かけ算の九九の表を表示するプログラムを作成してください。<br>
（ファイル名はTimesTable.javaとします）

### コンパイル
```java
javac -encoding UTF-8 TimesTable.java
```
### 実行例
```java
java TimesTable
1  2  3  4  5  6  7  8  9
2  4  6  8  10  12  14  16  18
3  6  9  12  15  18  21  24  27
4  8  12  16  20  24  28  32  36
5  10  15  20  25  30  35  40  45
6  12  18  24  30  36  42  48  54
7  14  21  28  35  42  49  56  63
8  16  24  32  40  48  56  64  72
9  18  27  36  45  54  63  72  81
```
---
<br>

## 課題4 約数を表示する
(1) コマンドライン引数で与えられた数字の約数と総数を表示するプログラムを作成してください。<br>
（ファイル名はDisplayDivisor.javaとしています）

```java
javac -encoding UTF-8 DisplayDivisor.java
```

### 実行例
```java
java DisplayDivisor 120
1 2 3 4 5 6 8 10 12 15 20 24 30 40 60 120
約数の個数は 16 です.
java DisplayDivisor 25
1 5 25
約数の個数は 3 です.
java DisplayDivisor 7
1 7
約数の個数は 2 です.
```

(2) 余裕があれば、積が入力した数になるような約数も組合せで表示するようにプログラムを改良してみてください。
```java
java DisplayDivisor 120
(1, 120)
(2, 60)
(3, 40)
(4, 30)
(5, 24)
(6, 20)
(8, 15)
(10, 12)
120 の約数の個数は 16 です.
java DisplayDivisor 25
(1, 25)
(5, 5)
25 の約数の個数は 3 です.
java DisplayDivisor 7
(1, 7)
7 の約数の個数は 2 です.
```
---
<br>

## 課題5 実数を読み込む
実数（double型）を1つ読み込み、「<span style="color: red; ">18.5以上28.5未満でない</span>」数が入力されるまで、再び実数を読み込むプログラムを作成してください。<br>
（ファイル名はEvaluateDoubleNum.javaとしています）

### コンパイル
```java
javac -encoding UTF-8 EvaluateDoubleNum.java
```
### 実行例
```java
java EvaluateDoubleNum
実数を入力してください
18.5
実数を入力してください
20
実数を入力してください
17.99
17.99 が入力されたため脱出します.
```
※余裕があれば、否定演算子(!)を用いる条件分岐と用いない条件分岐の2通りで実装してみてください。

---
<br>

## 課題6 2科目の点数から評価を決める
英語、数学の2科目の点数（各100点満点）によってSからCまでの4段階評価を決定するプログラムを作成してください。点数はコマンドライン引数によって入力されるものとし、評価の基準は以下の通りとします。<br>
```
S -> 合計点が180点以上かつ両科目90点以上
A -> 合計点が160点以上179点以下 または 合計点が180点以上だがいずれかの科目が89点以下
B -> 合計点が120点以上159点以下
C -> 合計点が119点以下
```
（ファイル名はEvaluateScore.javaとしています）

### コンパイル
```java
javac -encoding UTF-8 EvaluateScore.java
```

### 実行例
```java
java EvaluateScore 90 90
評価は Sです.
java EvaluateScore 100 89
評価は Aです.
java EvaluateScore 85 85
評価は Aです.
java EvaluateScore 59 60
評価は Cです.
```

## 解答例
### 課題1
```java
public class CalcParity{
	public static void main(String args[]){
		// 1からnまでの奇数のみの和、偶数のみの和をそれぞれ求める
		int num = Integer.parseInt(args[0]);
		
		//Enter your code here.
		int evenSum = 0;
		int oddSum = 0;
		int i = 1;
		while(i <= num){
			if(i % 2 == 0){
				evenSum += i;
			}else{
				oddSum += i;
			}
			i++;
		}
        /*
        while文部分をfor文で書く場合の例
        for(i=1; i<=num; i++){
            if(i % 2 == 0){
                evenSum += i;
            }else{
                oddSum += i;
            }
        }
        */
		System.out.println("1から " + num + " までの偶数の合計は、" + evenSum + "です.");
		System.out.println("1から " + num + " までの奇数の合計は、" + oddSum + "です.");
	}
}
```