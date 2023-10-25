- [標準API](#標準api)
- [文字列操作のクラス](#文字列操作のクラス)
      - [String](#string)
      - [StringBuffer](#stringbuffer)
      - [StringBuilder](#stringbuilder)


## 標準API
よく使われる標準APIを以下にまとめる。

java.awt
    Graphics	すべてのグラフィックコンテキストの抽象基底クラス
java.awt.image
    BufferedImage	イメージデータを保持
java.io
    → このパッケージは、データ・ストリーム、直列化、ファイル・システムによるシステム入出力用に提供されています。
    BufferedInputStream
    BufferedReader	文字型入力ストリームから効率よくテキストを読み取る手段を提供
    BufferedWriter	文字型出力ストリームに効率よくテキストを書き込む手段を提供
    File	ファイルシステム情報を保持
    FileReader	テキストファイルからの読み取り手段を提供
java.lang
    ラッパクラス	基本データ型の操作に利用（Integer、Longなど）
    Math	指数関数、対数関数、三角関数などの基本的な演算処理
    Package	パッケージ名、仕様、バージョンに関する情報を保持
    String	文字列の加工・制御手段を提供する
    StringBuffer	可変長文字列の操作手段を提供する
    System	システム全般の制御、情報の取得手段を提供
java.sql
    CallableStatement	ストアドプロシージャを実行
    Connection	データベースとの接続を管理
    DatabaseMetaData	データベースの構成情報を保持
    PreparedStatement	準備済みSQL命令を実行
    ResultSet	データベースから抽出した結果セットを操作
    ResultSetMetaData	結果セットの構成情報を保持
    Statement	静的なSQL命令を実行
    DriverManager	JDBCドライバを管理
java.text
    DecimalFormat	10進数を整形する手段を提供
    SimpleDateFormat	日付型データを整形する手段を提供
java.util
    Calendar	標準的なカレンダーを提供
    Date	日付情報を保持、また操作する手段を提供
    ArrayList	サイズ変更可能な配列の実装
    HashMap	連想配列を実装
    Locale	ロケール（地域）情報を管理
    Scanner	入力ストリームをプリミティブ型またはString型に変換するテキストスキャナを提供
    ResourceBundle	リソース（プロパティ）ファイルの参照手段を提供
    StringTokenizer	文字列をトークンに分解
java.util.regex
    → 正規表現操作
    Matcher	正規表現マッチングを制御する
    Pattern	コンパイル済みの正規表現パターンを保持する
java.util.zip
    → zip操作
    ZipEntry	Zipエントリを表現
    ZipOutputStream	Zip形式で書き込みを行うための出力ストリーム

引用：https://kanda-it-school-kensyu.com/java-basic-intro-contents/jbi_ch10/jbi_1005/

## 文字列操作のクラス
文字列操作には、以下のクラスがある。
1. java.lang.String
2. java.lang.StringBuffer
3. java.lang.StringBuilder

操作の仕組みが異なり、実行速度も異なる。

### String
- 文字列は可変でない。
  - つまり、値を更新するたびに新しい変数を作成している。
- メモリの節約となる。
  - 他のクラスに比べ変更への準備のためのメモリ確保は不要。ただし、文字列操作をする際はメモリを浪費する。

### StringBuffer
- 文字列は可変。配列のようになっている。
- マルチスレッドに対応している。スレッドセーフである。
- 速い。

### StringBuilder
- 文字列は可変。配列のようになっている。
- 単一のスレッドで動作する。
- 最も速い。

### Pythonでは
Stringがimmutableであるという原因から、同様に、Pythonではjoin()が使われる。

1. 配列に文字列を格納
2. join()で結合
という流れである。

