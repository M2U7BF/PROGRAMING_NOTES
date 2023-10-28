- [ファイル、ディレクトリ操作](#ファイルディレクトリ操作)
  - [Pathのインスタンス化](#pathのインスタンス化)
  - [カレントディレクトリの決まり方](#カレントディレクトリの決まり方)
- [ファイル入出力](#ファイル入出力)
  - [ストリーム](#ストリーム)
  - [テキストデータの読み取り（Reader）](#テキストデータの読み取りreader)
    - [簡単なリーダーの初期化方法](#簡単なリーダーの初期化方法)
    - [リソース付きtry文 (try-with-resources文)](#リソース付きtry文-try-with-resources文)
  - [文字列を解析する](#文字列を解析する)
  - [テキストデータの書き込み（Writer）](#テキストデータの書き込みwriter)
- [オブジェクトの入出力（バイナリストリーム）](#オブジェクトの入出力バイナリストリーム)
- [文字列入出力](#文字列入出力)
  - [各手法の概説](#各手法の概説)
  - [高速な方法](#高速な方法)
- [コレクション Collection](#コレクション-collection)
  - [ArrayList](#arraylist)
    - [初期化](#初期化)
  - [LinkedList](#linkedlist)
  - [Collection系クラスの使い方](#collection系クラスの使い方)
    - [配列をListに変換する。](#配列をlistに変換する)
    - [配列をListに変換する。(不変リスト)](#配列をlistに変換する不変リスト)
- [繰り返し](#繰り返し)
- [ラムダ式](#ラムダ式)
- [ジェネリクス](#ジェネリクス)
- [メタアノテーション ･･･アノテーションにアノテーションをつけるアノテーション](#メタアノテーション-アノテーションにアノテーションをつけるアノテーション)
- [オブジェクト型の標準型](#オブジェクト型の標準型)
  - [String](#string)
    - [文字列操作を行う。](#文字列操作を行う)
      - [String](#string-1)
      - [StringBuffer](#stringbuffer)
      - [StringBuilder](#stringbuilder)
- [型](#型)
- [クラス](#クラス)
- [便利機能](#便利機能)


-----


## ファイル、ディレクトリ操作
java.nio.Path を用い、インスタンスとして読み込む。

### Pathのインスタンス化
```
Path p1 = Paths.get("c:/hoge/fuga");
```

### カレントディレクトリの決まり方
例えば、 Windowsの場合、 デスクトップのアイコンをダブルクリックして起動したプログラムは、デスクトップフォルダがカレントディレクトリになります。
Javaプログラムでも、対象のクラスを起動した時、アクセスしていたフォルダがカレントディレクトリになります。JavaプログラムはJDKのjavaコマンド (java.exe) を使って起動するので、正確には、 java コマンドを実行した時、アクセスしていたディレクトリがカレントディレクトリです。


## ファイル入出力
### ストリーム
    データの流れとその通り道
    データの受け渡しを抽象化したものです。あらゆるデータの入出力における基本的な概念です。

### テキストデータの読み取り（Reader）
java.ioパッケージの場合、Readerクラスを用いる。

#### 簡単なリーダーの初期化方法
java.nioパッケージを用いると、Buffer機能を追加したリーダーを簡単に初期化できる。
```
BufferedReader br = Files.newBufferdReader();
```

旧来の方法は、ブラウザ参照。

#### リソース付きtry文 (try-with-resources文)
Readerクラスでは最後にメモリを開放するclose()を実行する。
旧来はfinallyブロックが必要であったが、try-with-resource文で不要となった。
```
try(BufferedReader br = Files.newBufferdReader();){
    // 処理
}
catch(){ // 例外処理
    // ...
}
```

リソースへアクセスするオブジェクトを()内に書くので、try-with-resourceと呼ばれる。

### 文字列を解析する
単純に読み取るのではなく、数字か文字列かなどを解析する必要がある場合、
Scannerクラスを用いる。

Scannerクラスはデフォルトで、全角空白も区切り文字と判定する。


### テキストデータの書き込み（Writer）
BufferedWriterを用いる。
```
try(BufferedWriter bw = Files.newBufferdWriter(path);) {
    // 処理
}
catch(){ // 例外処理
    // ...
}
```

StandardOpenOptionで上書き、追記など、オプション指定できる。


## オブジェクトの入出力（バイナリストリーム）



## 文字列入出力
Javaにおける入出力の方法は以下である。
1. Scannerの利用
2.
### 各手法の概説
1.Scannerの利用
コード量は少ない。
    Scannerが遅い理由
         Scanner クラスでは、7 つの nextXXX() メソッドの後に nextLine() メソッドを呼び出すと、nextLine() はコンソールから値を読み込まず、カーソルはコンソールに表示されません。

### 高速な方法

## コレクション Collection
配列
    プリミティブ型を格納する

リスト
    オブジェクトを格納する
        Java.util.ArrayList();
        追加
            array.add(obj)
            array.add(index,obj)

Set
Map


### ArrayList
#### 初期化
初期化時はより汎用的なList型に格納する。
```
List<String> list = new ArrayList<>();
```

ArrayListやLinkedListはListインタフェースを実装しているので、インスタンスはList型変数に代入できる。
こうしておけば、ArrayListからLinkedListなど、他の型への変更が簡単になる。
将来の変更を容易にするための書き方だ。


### LinkedList
要素を参照するシーンではArrayListが適している。
挿入や削除が多いシーンではLinkedListが適している。


### Collection系クラスの使い方
Collectionは様々なクラスのオブジェクトに対応するために、ジェネリクス型（総称型）で定義されている。
使用時はジェネリクス型に対し、クラスを宣言し用いる必要がある。
```
ArrayList<String> list = new ArrayList<>();
HashSet<String> set = new HashSet<>();
HashMap<Integer, String> map = new HashMap<>();
```

右辺で型を指定しなくても良い。
型推論という機能で、コンパイル時に自動で補完される。


#### 配列をListに変換する。
Arrays.asList()を用いる。
配列をListのように扱うことができる。
```
String[] str = { "Windows", "Linux", "macOS" };
List<String> list = Arrays.asList(str);
```

#### 配列をListに変換する。(不変リスト)
List.of()で作成したリストは、要素の追加、削除ができない。
```
List<String> list = List.of("hoge", "fuga");
```


## 繰り返し
    拡張for文
        for (型 変数: リスト) {
            処理
        }
        for (WebElement element: allElements) {
            System.out.println(element.getText());
        }

## ラムダ式
    関数型インターフェイスを実装したクラスのインスタンスを、ごく短いコーディング量でとても簡単に作れてしまう文法

出力
    配列
        Arrays.toString(arr1)
        Arrays.deepToString(week)

クラス
    ジェネリッククラス
        ジェネリッククラスでは <T> のような型パラメータを使用して定義します。
        ここで T は仮の型引数を表し、実際の使用時に具体的な型（例えば、Integer、Stringなど）で置き換えられます。
        これにより、複数のデータ型に対応するクラスを一度に定義できます。

        ```
        // 通常のクラスの例
        public class NormalResult {
            private Object data;

            public NormalResult(Object data) {
                this.data = data;
            }

            public Object getData() {
                return data;
            }
        }

        // ジェネリッククラスの例
        public class CommonResult<T> {
            private T data;

            public CommonResult(T data) {
                this.data = data;
            }

            public T getData() {
                return data;
            }
        }

        // 使用例
        NormalResult normal = new NormalResult("Hello");
        CommonResult<String> generic = new CommonResult<>("Hello");

        String normalData = (String) normal.getData(); // キャストが必要
        String genericData = generic.getData();        // キャスト不要で使える
        ```

ジェネリクス
## ジェネリクス
    型パラメータ Type parameter
    class ClassSample<T>{...
    どの型にも対応できる

    型パラメータの表記    https://programmer-life.work/java/generics-type
    E - Element（要素）(Javaのコレクション フレームワークで多用されている)
    K - Key（キー）
    N - Number（数値）
    T - Type（タイプ）
    V - Value（値）
    S,U,V etc. - 2番目、3番目、4番目... types
    P パラメータ
    R return 戻す型

    境界型パラメータ bounded type parameter
    適用される型を継承したクラスで使用されている型に制限している
    <E extends Number>

    多数の境界 multiple bounds
    継承するクラスを複数記述している
    <E extends Class1 & Class2>

    非境界ワイルドカード型 unbounded wildcard type
    なんらかの型を持つ
    List<?>

    上限境界ワイルドカード型 bounded wildcard type
    指定した型と同じ、またはその型を継承するサブクラス(サブインターフェース)を表す
    List<? extends Number>

    下限境界ワイルドカード
    指定した型と同じ、またはその型のスーパークラスを表す
    List<? super Integer>

## メタアノテーション ･･･アノテーションにアノテーションをつけるアノテーション

    @Target
        アノテーションを適用できるプログラム要素宣言のタイプ（クラス、インターフェース、コンストラクターなど）を指定する。
        定数であるElementType enumeration(列挙) を引数とする。

    @Documented
        Documented はメタアノテーションです。
        アノテーションを定義するときに@Documentedを適用すると、そのアノテーションを使ったクラスが生成されるJavaDocにそのことが表示されるようになります。
        私はこの使い方をあまり見たことがないのですが、ここに例があります。以前の質問で、Eclipseでは自動的に機能しないことが示唆されていましたが、Eclipse 3.6でテストしたところ、@Documentedアノテーションを付けるかどうかにかかわらず、私のアノテーションはJavaDocのポップアップに表示されました。

        javadoc ･･･プログラムを説明するドキュメント

    @Retention
        保持ポリシーに付属するメタアノテーションでもあります。
        アノテーションが破棄される時点を示す。
        RetentionPolicy.SOURCE： 実行時に破棄されます。
        RetentionPolicy.CLASS： .classファイルに記録されますが、実行時に破棄されます。CLASSは、Javaのデフォルトの保持ポリシーです。
        RetentionPolicy.RUNTIME： 実行時に保持され、実行時にプログラムでアクセスできます。
## オブジェクト型の標準型
### String
#### 文字列操作を行う。
文字列操作には、以下のクラスがある。
1. String
2. StringBuffer
3. StringBuilder

目的に応じて使い分けられる。
##### String

##### StringBuffer
マルチスレッド処理において、便利である。

##### StringBuilder
多くの実装において、最も高速である。
通常はこのクラスを使用するとよい。



## 型
    型変換
        Stringへ変換
            int → String
                str = int.toString
            Date → String
                String str = new SimpleDateFormat("yyyy-MM-dd hh:mm:ss").format(dateObj);

        intへ変換
            int num = Integer.parseInt(str);

        timestampへ変換
            str → timestamp
                SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
                Date date = new Date();
                try {
                    date = sdf.parse(stringTradeDate);
                } catch (ParseException e) {
                    throw new RuntimeException(e);
                }
                Timestamp tradeDate = new Timestamp(date.getTime());

            calendar → Date → timestamp
                Date nextDate = nextDateCalendar.getTime();

                Timestamp timestamp = new Timestamp(date.getTime());

        Calendarへ変換
            timestamp → calendar
                Calendar calendar = Calendar.getInstance();
                calendar.setTimeInMillis(timestamp.getTime());


## クラス
    コンストラクタ
        自分自身にすでに定義されているコンストラクタを呼び出す
            this(引数);
        親クラスのコンストラクタを呼び出す
            super(); //Objectクラスの継承の際に明示的に呼び出すことがあるっぽい

System.out.println
    ArrayListを出力
    Arrays.toString(some_array)

## 便利機能
    recordクラス    https://kamoqq.info/post/java-record-cheat-sheet/
    recordをつけるとコンストラクタの 自動生成,finalなフィールドの自動生成などを行う
    public final class User {... を記述したことと同じになる。 レコードクラスを使うと記述がシンプルになる。

    public record User(String name, int age) {
    }

    lombokライブラリを使う
