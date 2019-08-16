## Kotlinの魅力
* 簡潔
    * 文末セミコロン、型の指定の省略
    * if-elseが式
    * 型推論
* 安全
    * Nullぽ対策（Null安全）
* JVM言語
    * Javaの資産そのまま使える
* 静的型付け
    * Javaバイトコードにコンパイル
    * バグを早い段階で見つけることができる
* オブジェクト指向
    * プリミティブ型（int, charなど）がなく、すべてがオブジェクト（Rubyぽい？）
    * プロパティ、オブジェクト宣言、拡張関数などがある（Javaにはない）
* 関数型プログラミング
    * 第一級オブジェクトとしての関数がある
    * 関数を文字列や数値、関数の引数として渡したり、戻り値として受け取ったりできる

Javaでは、関数やクラスはクラスに属さなくてはならない
→ Kotlinではクラスに属さなくていい

演算子オーバーロード
* +とか、-とかをオーバーロードして、func + funcとかでplusメソッドが呼べる
* operator識別子
* operator fun plus

lazyキーワードなんだ？

### 拡張関数
既存のクラスやインターフェースに持っていない関数を作って、拡張して使いやすくすることができる


```kotlin
## 配列
arrayOfNulls<Int>(5)
fun <reified T> arrayOfNulls(size: Int): Array<T?>


trimMargin
fun String.trimMargin(marginPrefix: String = "|"): String
トリプルクォーテーション（\"\"\"\）で囲った文字列を、marginPrefixで指定した文字列（目印）以外を文字列として出力

intArrayOf
fun intArrayOf(vararg elements: Int): IntArray


charArrayOf
fun charArrayOf(vararg elements: Char): CharArray
```

```
## コレクション
複数の値のコンテナとなるオブジェクト
リスト、セット、マップ
基本的にイミュータブル
mutableListOf, mutableSetOf

### リスト
順序付きのコレクション
listOf
fun <T> listOf(vararg elements: T): List<T>
listはイミュータブル, varで宣言しても変更不可能
mutableListOfを使えば、変更可能なリストを宣言することができる
fun <T> mutableListOf(): MutableList<T>

レンジオブジェクトはtoListを使うことでリストに変換することができる
(1..5).toList()

### セット
集合を表すコレクション
要素の重複がない
val ints: Set<Int> = setOf(1,2,1,3)
val chars: MutableSet<Char> = mutableSetOf('a', 'b', 'a')
要素の順番を保証しないので、リストや配列のようにインデックスで要素にアクセスすることはできない
→ キーとバリューが同一な配列のイメージ（集合）
→ set.indexOfをやると、存在すれば要素のインデックスが返る

### マップ
キーと値のペアを持っているコレクション
val numberMap: MutableMap<String, Int> = mutableMapOf("one" to 1, "two" to 2)

## 条件分岐
ifは式
kotlinではswitchではなくwhen式
when式を使ったときに、条件分岐に関数や範囲などを指定できる（Javaではできない）
isを使って型チェックもできる（is String）


## ループ
### while
### for
イテレータを提供するオブジェクトに対する繰り返し
→ next と hasNextを持つオブジェクト

indices
リストや配列に定義されているプロパティで、全要素分のインデックスをrangeとして返す
```

## 第二部
### 関数

基本型
```
fun succ(i: Int): Int = i + 1
```

引数に名前をつけると、順番に依存しなくなる→ バラバラでもおｋ
