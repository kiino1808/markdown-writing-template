# Java章末問題（コレクション）
## 課題1 Listの速度比較
for文と拡張for文の速度比較をするプログラムを考えます。
## 課題2 HashMap
コマンドライン引数で指定された食品の料金を出力するプログラムを作ってください。<br>
食品の名前と料金は以下のように、適当に決めてください。
```java
this.price = new HashMap<>();
price.put("もやし", 30);
price.put("にんじん", 70);
price.put("長ねぎ", 80);
price.put("ピーマン", 100);
price.put("野菜炒めパック", 100);
price.put("大根", 150);
price.put("リンゴ", 160);
price.put("にんにく", 200);
price.put("ゆず", 210);
price.put("ドラゴンフルーツ", 250);
```

また、プログラム中でfor文を書く際は、拡張for文を用いるようにしてください。<br>

テンプレート
```java
import java.util.HashMap;

public class FoodPrice{
	public static void main(String[] args){
        // Enter your code here.

    }
	
    HashMap<String, Integer> price; // HashMap初期化
    // Enter your code here.

}
```

### コンパイル

```java
javac -encoding UTF-8 FoodPrice.java
```

### 実行例

```java
java FoodPrice もやし
もやし: 30円
java FoodPrice もやし　にんじん　長ねぎ　ピーマン　にんにく
もやし: 30円
にんじん: 70円
長ねぎ: 80円
ピーマン: 100円
にんにく: 200円
java FoodPrice にんじん　卵　ピーマン　白菜
にんじん: 70円
卵: 在庫がありません
ピーマン: 100円
白菜: 在庫がありません
```

<br>

---
## 解答例

### 課題1
```java
import java.util.LinkedList;
import java.util.List;

public class ListSpeed{

    public static void main(String[] args) {
        compareSpeed_ms(100);
    	compareSpeed_ms(1000);
    	compareSpeed_ms(10000);
    	compareSpeed_ms(100000);

    }
	public static void compareSpeed_ms(int n){
		List<Integer> list = new LinkedList<>();
        for (int i = 0; i < n; i++) {
            list.add(i);
        }

        //開始
        long start = System.currentTimeMillis();
        for (int i = 0; i < list.size(); i++) {
            int tmp = list.get(i);
        }
        //終了
        long end = System.currentTimeMillis();
        System.out.println("for文(size: " + n + "): " + (end - start) + " ms");

        //開始
        start = System.currentTimeMillis();
        for (Integer i : list) {
            int tmp = i;
        }
        //終了
        end = System.currentTimeMillis();
        System.out.println("拡張for文(size: "+ n + "): " + (end - start) + " ms");
	}

}
```

### 課題2
```java
import java.util.HashMap;

public class FoodPrice{
	public static void main(String[] args){
        FoodPrice food = new FoodPrice();
        food.showPrice(args);
    }
	
    HashMap<String, Integer> price; // HashMap初期化
	
	/** 食品の値段を表示する*/
    void showPrice(String[] args){
        this.initialize();
        for(String food: args){
            this.searchAndPrint(food);
        }
    }
	
	/** 食品の料金表を作成する*/
	void initialize(){
        this.price = new HashMap<>();
        price.put("もやし", 30);
    	price.put("にんじん", 70);
        price.put("長ねぎ", 80);
        price.put("ピーマン", 100);
    	price.put("野菜炒めパック", 100);
        price.put("大根", 150);
    	price.put("リンゴ", 160);
        price.put("にんにく", 200);
        price.put("ゆず", 210);
        price.put("ドラゴンフルーツ", 250);
    }
	
	/** 料金を検索する．*/
    void searchAndPrint(String foodName){
        
        Integer price = this.price.get(foodName);
        if(price == null){ // 該当するものが見つからなかった．
            System.out.println(foodName + ": 在庫がありません");
        }
        else{
            // 食品の料金を出力する．
            System.out.println(foodName + ": " + price + "円");
        }
    }
}
```