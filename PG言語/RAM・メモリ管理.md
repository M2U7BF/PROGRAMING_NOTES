- [RAMについて](#ramについて)
  - [RAMの仕組み](#ramの仕組み)
- [プログラムとRAM](#プログラムとram)
  - [ソフトウェア実行時のRAM](#ソフトウェア実行時のram)
    - [Stack(スタック領域)](#stackスタック領域)
    - [Heap（ヒープ領域）](#heapヒープ領域)
  - [メモリ管理](#メモリ管理)


# RAMについて
## RAMの仕組み
https://www.youtube.com/watch?v=SSjeGjhwBo0

## メモリ管理
1. ファーストフィット
2. ベストフィット
3. 最悪のフィット感

### 1.ファーストフィット
メモリ管理において、空いている最初の領域にデータを割り当てる方式のことです。
具体的には、メモリ領域をリストのように管理し、空き領域のリストから最初に見つかった領域にデータを割り当てます。ファーストフィット方式は、シンプルで実装が簡単なため、メモリ管理において一般的に使用される方式の一つです。

- 実装が簡単であるため、効率的に実装できる
- メモリの断片化が起こりやすいため、空き領域の管理に工夫が必要
- データを格納する際、目的の領域よりも大きな領域を割り当ててしまうことがあるため、メモリ使用効率が悪くなる可能性がある
- メモリ使用効率が悪くなる場合があるものの、空き領域のリストに余計な情報を付加しなくても良いため、メモリの使用効率を高めることができる


### 2.ベストフィット
ベストフィット方式では割り当てを要求されたサイズよりも大きい空き領域の断片から、最も容量の少ないものを選択して割り当てる。

- 大きな空き領域が分割されずに温存されて残りやすい
- 領域を探索する処理が複雑で時間がかかる
- 割り当てごとに小さな空き領域の断片が残されるため、長時間経つと使いにくい細かい断片が多数できてしまう

### 3.ワーストフィット
割り当てを要求されたサイズよりも大きい空き領域の断片から、最も容量の多いものを選択して割り当てる。

- 割り当て後に残される空き領域の断片がなるべく大きくなるように割り当てるため、使いにくい細かな空き領域の断片が出にくい
- 割り当てと解放を繰り返すごとに空き領域の大きさの均一化が進むため、大きな領域の割り当てが難しくなっていく

## 断片化
### 内部断片化
固定長の領域を割り当てていくシステムで割り当てられた領域内に未使用の断片が生じること

### 外部断片化
可変長の領域を割り当てていくシステムで空き領域が細かく分割されすぎて連続した大きな領域の割り当てができなくなること

## ページング
仮想RAMを使う技術。
必要な部分（ページ）をメモリに残し、今すぐには必要でない部分（ページ）をディスク（仮想記憶用部分）に移す。
ディスク（仮想記憶用部分）にあるページが必要になったらメモリに移動、を行うことで見かけ上、メモリが実際の容量より多く見えます。

- 「メモリ⇔ディスクの一部」間のページの入れ替えが頻発すると、CPUの待ち時間が増え、処理速度が低下します。


# プログラムとRAM
## マルチプログラミング
メモリをパーティションで分割し、利用することでマルチプログラミングが可能になる。

## ソフトウェア実行時のRAM動作
OSがソフトウェアを実行する際には、必ず下記をRAMに読み込みます。

1. ソフトウェアのバイトコード
2. ソフトウェアで使用されるデータ値とデータ構造
3. 実行に必要なランタイムシステム

### Stack(スタック領域)
- プログラムが読み込まれた時、プログラム実行前、に静的に確保される領域。
- スタックはLIFO or FIFOで、データの検索が不要なため、データの格納と取り出しが高速
- ローカル変数、関数が読み出される。

### Heap（ヒープ領域）
- プログラムの実行時に動的に確保される領域。(https://proglife.net/heap-stack/)
- ヒープでは、データのアドレスを動的に割り当てるため、アクセスの際はポインタを使用してデータを検索する必要がある。
  - いわゆるポインタは、ヒープメモリの管理の話ってこと。
- 動的なため管理が難しく、メモリ管理の問題のほとんどはここから発生する。多くの言語で自動メモリ管理の仕組みが機能する。
-

## メモリ管理
1. GC
    1. マークアンドスイープGC
    2. 参照カウント GC
2. リソースの取得は初期化 (RAII)
3. 自動参照カウント(ARC)
4. 所有

