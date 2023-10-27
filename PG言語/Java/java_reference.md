- [ファクトリ](#ファクトリ)
- [ストリーム](#ストリーム)
- [コレクション Collection](#コレクション-collection)
- [繰り返し](#繰り返し)
- [ラムダ式](#ラムダ式)
- [ジェネリクス](#ジェネリクス)
- [メタアノテーション ･･･アノテーションにアノテーションをつけるアノテーション](#メタアノテーション-アノテーションにアノテーションをつけるアノテーション)
- [型](#型)
- [クラス](#クラス)
- [便利機能](#便利機能)


## ファクトリ

## ファイル、ディレクトリ操作
java.nio.Path を用い、インスタンスとして読み込む。

### Pathのインスタンス化
```
Path p1 = Paths.get("c:/hoge/fuga");
```

### カレントディレクトリの決まり方
例えば、 Windowsの場合、 デスクトップのアイコンをダブルクリックして起動したプログラムは、デスクトップフォルダがカレントディレクトリになります。
Javaプログラムでも、対象のクラスを起動した時、アクセスしていたフォルダがカレントディレクトリになります。JavaプログラムはJDKのjavaコマンド (java.exe) を使って起動するので、正確には、 java コマンドを実行した時、アクセスしていたディレクトリがカレントディレクトリです。


## ファイルI/O
### ストリーム
    データの流れとその通り道
    データの受け渡しを抽象化したものです。あらゆるデータの入出力における基本的な概念です。

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
========
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
