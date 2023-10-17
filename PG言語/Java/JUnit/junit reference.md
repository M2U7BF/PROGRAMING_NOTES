
- [Test Fixture](#test-fixture)
- [概説](#概説)
  - [テスト作成単位](#テスト作成単位)
- [Junitのリファレンス](#junitのリファレンス)
  - [セットアップ/終了](#セットアップ終了)
  - [テストの実行](#テストの実行)
  - [ログイン状態](#ログイン状態)
      - [@WithMockUser](#withmockuser)
      - [@WithCustomMockUser (自作)](#withcustommockuser-自作)
  - [各アノテーション](#各アノテーション)


## Test Fixture
to set up system state and input data needed for test execution.

## 概説
### テスト作成単位
クラス毎に作成するのが一般的（ネット調べ）。クラス毎にテストクラスを作成し、各メソッドや機能を単独でテストする。

## Junitのリファレンス
### セットアップ/終了
@BeforeClass
  テストの前に1回だけ実行するメソッド
@AfterClass
  テストの後に1回だけ実行するメソッド

@Before
  各テストケースの前に実行するメソッド
@After
  各テストケースの後に実行するメソッド

### テストケースの作成
@Test
  テストメソッドとして認識させる

  @Test(timeout=500)
    タイムアウトを設定。実行時間がある範囲内であるかテストする。

### その他アノテーション
@Ignores
  テストのスキップを設定する
@Test(expected=IllegalArgumentException.class)
  メソッドが特定のエラーを扱うか、テストする。


## テストの実行手順

1. テストケースを作成する
2. TestRunnerクラスを作成する

下記のようにして、テストの実行順番を指定する。
```
// （略）関数名の宣言
// テストクラスを指定し実行
Result result = JUnitCore.runClasses(CreateAndSetName.class);

for (Failure failure : result.getFailures()) {
  System.out.println(failure.toString());
}
System.out.println(result.wasSuccessful());
```


### ログイン状態
##### @WithMockUser
ユーザーで擬似ログイン

##### @WithCustomMockUser (自作)
カスタムユーザーの利用
https://qiita.com/kazokmr/items/9fab9ad267d70e25da8d
https://docs.spring.io/spring-security/site/docs/4.2.x/reference/html/test-method.html#test-method-withsecuritycontext

### 各アノテーション

