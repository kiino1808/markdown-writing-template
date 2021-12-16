
# Java章末問題（配列）

## 課題1 最大値を探す

(1)int型の配列a[]が、

```
int a[] = {21, 6, -10, 0, 31, -99};
```

で与えられているとき、最大値と最大値化格納されている配列の添字を表示するプログラムを作成してください。最大値が複数ある場合、
<span style="color: red; ">添字が小さいほう</span>を出力するようにしてください。また、aの中身を書き換えて、正常にプログラムが動いているかを確認してみてください。<br>
（ファイル名はSearchMax.javaとしています）

<br>

### コンパイル

```java
javac -encoding UTF-8 SearchMax.java
```

### 実行例

```java
java SearchMax
最大値の添え字は 4です
最大値は 31です
```

<br>

(2)余裕があれば、最大値をとる添字が配列内に複数ある場合は
<span style="color: red; ">すべての添字</span>を出力するようにしてください。

---

## 課題2 最頻値を探す

(1)int型の配列array[]が、

```
int array[] = {5, 6, 5, 8, 7, 5, 9, 7, 3, 4};
```

で与えられているとき、配列内の最頻値とその値が何個格納されているかを表示するプログラムを作成してください。<br>
（ファイル名はSearchMode.javaとしています）
<br>

### コンパイル

```java
javac -encoding UTF-8 SearchMode.java
```

### 実行例

```java
java SearchMode
最頻値は 5です
個数は 3です
```

<br>
(2)余裕があれば、最頻値が配列内に複数ある場合に
<span style="color: red; ">すべての最頻値</span>を出力するようにしてください。

---

## 課題3 BMIを計算する

&ensp;
生徒のデータから肥満の疑いのある生徒を探し出すことを考えます。方法はBMI(Body Mass Index)という数値を算出する方法です。BMIは次の式で与えられます。

```
BMI ＝ 体重[kg] ÷ (身長[m])2
```

2次元配列に格納されている、各々の生徒の体重と身長の情報からBMIを算出し、25以上の生徒の学籍番号（順に1,2,3,...とする）とBMIの値を画面に出力するプログラムを作成してください。（ファイル名はCalculateBmi.javaとしています）<br>なお、以下の点に留意してください。<br>

* 肥満の疑いのある生徒がいない場合は、”該当なし”と出力して終了する
* BMIを表示する際は、小数第2位まで表示させる

<br>

2次元配列は以下のものを使用してください。

```java
double[][] studentsInfo = 
{
    {152.1, 182.0, 185.6, 165.7, 152.3, 140.4, 150.8, 166.1, 160.0, 172.5},
    {47.3, 82.7, 71.9, 58.4, 44.5, 39.9, 57.1, 69.9, 45.1, 83.1}
};
//1行目は生徒の身長(cm)を、2行目は生徒の体重(kg)を表す
```

<br>

### コンパイル

```java
javac -encoding UTF-8 CalculateBmi.java
```

### 実行例

```java
java CalculateBmi
出席暗号7 の生徒は BMI = 25.11 で肥満の疑いがあります.
出席暗号8 の生徒は BMI = 25.34 で肥満の疑いがあります.
出席暗号10 の生徒は BMI = 27.93 で肥満の疑いがあります.
```

フォーマット

```
"%.2f".formatted(bmi)
```

---

## 課題4 配列をソートする

配列の中身を昇順/降順に入れ替える手法の１つとしてバブルソートというものがあります。泡が浮かび上がってくるかの如くデータが徐々に先頭へ集まってくるのが特徴で、

* 端から順に隣り端から順に合う要素を順番に比較して入れ替え
* 全体がソート完了になるまで交換操作を繰り返す

の操作で構成されています。バブルソートを昇順で実行し、ソート前とソート後の配列を表示するプログラムを作成してください。<br>

例えば、ソート対象の配列が
```
int a[] = {23, -6, 12, 0, 1, 100, -92, 4, 77};
```
とすると、ソート実行後は

```
{-92, -6, 0, 1, 4, 12, 23, 77, 100}
```
となります。<br>
（ファイル名はBubbleSort.javaとしています）

<br>

### コンパイル

```java
javac -encoding UTF-8 BubbleSort.java
```

### 実行例

```java
java BubbleSort
[23, -6, 12, 0, 1, 100, -92, 4, 77]
[-92, -6, 0, 1, 4, 12, 23, 77, 100]
```
<br>

## 閑話

一般にバブルソートは、実装は簡単だが遅くて非実用的という問題点があります。
<br>
（参考）ソートごとの速度比較の動画<br>
[![](https://img.youtube.com/vi/ZZuD6iUe3Pc&ab_channel=ViktorBohush/0.jpg)](https://www.youtube.com/watch?v=ZZuD6iUe3Pc&ab_channel=ViktorBohush)

また、検査対象が大きくなるほどバブルソートは計算にかかる時間も非常に大きくなることが知られています。
```java
//配列の長さによる時間比較
int b[] = new int[10000];
initializeDescending(b); // 降順に数値を代入
bubbleSort_ms(b); // バブルソートにかかる時間(ms)を計測

int c[] = new int[100000]; // bの10倍
initializeDescending(c);
bubbleSort_ms(c);

int d[] = new int[500000];// bの50倍
initializeDescending(d);
bubbleSort_ms(d);

int e[] = new int[1000000];// bの100倍
initializeDescending(e);
bubbleSort_ms(e);
```
```java
ソート時間: 63 ms
ソート時間: 4521 ms
ソート時間: 136413 ms
ソート時間: 328796 ms
```
大規模なシステム開発となればなるほど、検索する配列やデータベースの大きさも莫大なものとなり、より安定かつ高速な設計が求められるようになります。

---

## 課題5 相関係数を求める

---

## 解答例

### 課題1
```java
public class SearchMax{
	public static void main(String args[]){
		int a[] = {21, 6, -10, 0, 31, -99}; // 検索対象の配列
		int maxIndex = 0; // 暫定の最大値添字

		// Enter your code here.
		for(int i=0; i<a.length; i++){
			if(a[maxIndex] < a[i]){
				maxIndex = i;
			}
		}
		System.out.println("最大値の添字は " + maxIndex + "です");
		System.out.println("最大値は " + a[maxIndex] + "です");
	}
}
```
---
### 課題2
```java
public class SearchMode {
    public static void main(String args[]){
        //int配列から最頻値を求める.
		int array[] = {5, 6, 5, 8, 7, 5, 9, 7, 3, 4}; // 検索対象の配列
		int countMax = 0; // 最頻値登場回数
		int mode = array[0]; // 最頻値

		// Enter your code here.
        for(int i=0; i<array.length; i++){
            int count = 0;
            for(int j=i; j<array.length; j++){
                if(array[i] == array[j]){
                    count++;
                }
            }
            if(countMax < count){
                countMax = count;
                mode = array[i];
            }
        }
		System.out.println("最頻値 " + mode + "です");
		System.out.println("登場回数は " + countMax + "です");
	}
}

```
---
### 課題3
```java
public class CalculateBmi {
    public static void main(String args[]){
        // 生徒の身長(cm)&体重(kg)情報からBMI25以上を抽出 & 小数第2位までBMI表示
        double[][] studentsInfo = {
            {152.1, 182.0, 185.6, 165.7, 152.3, 140.4, 150.8, 166.1, 160.0, 172.5}, 
            {47.3, 82.7, 71.9, 58.4, 44.5, 39.9, 57.1, 69.9, 45.1, 83.1}
            };

        // Enter your code here.
    	boolean bmiFlag = false;
        for(int i=0; i<studentsInfo[0].length; i++){
            double bmi = studentsInfo[1][i]/ Math.pow((studentsInfo[0][i] / 100), 2);
            if(bmi >= 25){
                System.out.println("出席暗号" + (i + 1) + " の生徒は BMI = " + "%.2f".formatted(bmi) + " で肥満の疑いがあります.");
            	bmiFlag = true;
            }
        }
    	
    	if(!bmiFlag){
    		System.out.println("該当なし");
    	}
    }
}
```

---

### 課題4
```java
import java.util.Arrays;

public class BubbleSort {
    public static void main(String args[]){
        // バブルソートでint配列を小さい順に並び替えする
        int tmp = 0;
        int a[] = {23, -6, 12, 0, 1, 100, -92, 4, 77};
        System.out.println(Arrays.toString(a));
        for(int i=0; i<a.length; i++){
            for(int j=0; j<a.length-i-1; j++){
                if(a[j] > a[j+1]){
                    tmp = a[j];
                    a[j] = a[j+1];
                    a[j+1] = tmp;
                }
            }
        }
        System.out.println(Arrays.toString(a));
    }
}
```
