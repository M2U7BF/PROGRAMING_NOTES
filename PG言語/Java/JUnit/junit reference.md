
- [Test Fixture](#test-fixture)
- [概説](#概説)
  - [テスト作成単位](#テスト作成単位)
- [Junitのリファレンス](#junitのリファレンス)
- [Junitアノテーション](#junitアノテーション)
  - [セットアップ/終了](#セットアップ終了)
  - [テストケースの作成](#テストケースの作成)
  - [その他アノテーション](#その他アノテーション)
- [Junit AssertClass](#junit-assertclass)
- [JUnit Test Cases Class](#junit-test-cases-class)
- [JUnit TestResult Class](#junit-testresult-class)
- [JUnit Test Suite Class](#junit-test-suite-class)
- [テストの実行手順](#テストの実行手順)
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
## Junitアノテーション
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


## Junit AssertClass
void assertEquals(boolean expected, boolean actual)
  It checks whether two values are equals similar to equals method of Object class
void assertFalse(boolean condition)
  functionality is to check that a condition is false.
void assertNotNull(Object object)
  “assertNotNull” functionality is to check that an object is not null.
void assertNull(Object object)
  “assertNull” functionality is to check that an object is null.
void assertTrue(boolean condition)
  “assertTrue” functionality is to check that a condition is true.
void fail()
  If you want to throw any assertion error, you have fail() that always results in a fail verdict.
void assertSame([String message]
  “assertSame” functionality is to check that the two objects refer to the same object.
void assertNotSame([String message]
  “assertNotSame” functionality is to check that the two objects do not refer to the same object.


## JUnit Test Cases Class
int countTestCases()
  This method is used to count how many number of test cases executed by run(TestResult tr) method.
TestResult createResult()
  This method is used to create a TestResult object.
String getName()
  This method returns a string which is nothing but a TestCase.
TestResult run()
  This method is used to execute a test which returns a TestResult object
void run(TestResult result)
  This method is used to execute a test having a TestResult object which doesn’t returns anything.
void setName(String name)
  This method is used to set a name of a TestCase.
void setUp()
  This method is used to write resource association code. e.g. Create a database connection.
void tearDown()
  This method is used to write resource release code. e.g. Release database connection after performing transaction operation.


## JUnit TestResult Class
void addError(Test test, Throwable t)
  This method is used if you require add an error to the test.
void addFailure(Test test, AssertionFailedError t)
  This method is used if you require add a failure to the list of failures.
void endTest(Test test)
  This method is used to notify that a test is performed(completed)
int errorCount()
  This method is used to get the error detected during test execution.
Enumeration<TestFailure> errors()
  This method simply returns a collection (Enumeration here) of errors.
int failureCount()
  This method is used to get the count of errors detected during test execution.
void run(TestCase test)
  This method is used to execute a test case.
int runCount()
  This method simply counts the executed test.
void startTest(Test test)
  This method is used to notify that a test is started.
void stop()
  This method is used to test run to be stopped.


## JUnit Test Suite Class
void addTest(Test test)
  This method is used if you want to add a test to the suite.
void addTestSuite(Class<? extends TestCase> testClass)
  This method is used if you want to specify the class while adding a test to the suite.
int countTestCases()
  This method is used if you want to count the number of test cases.
String getName()
  This method is used to get the name of the test suite.
void run(TestResult result)
  This method is used to execute a test and collect test result in TestResult object.
void setName(String name)
  This method is used to set the name of TestSuite.
Test testAt(int index)
  This method is used if you want to return the test at given index.
int testCount()
  This method is used if you want to return a number of tests in the Suite.
static Test warning(String message)
  This method returns a test which will fail and log a warning message.


## テストの実行手順

1. テストケースを作成する
2. テストスイートクラスを作成する
3. TestRunnerクラスを作成する
4. 実行

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


## ログイン状態
#### @WithMockUser
ユーザーで擬似ログイン

#### @WithCustomMockUser (自作)
カスタムユーザーの利用
https://qiita.com/kazokmr/items/9fab9ad267d70e25da8d
https://docs.spring.io/spring-security/site/docs/4.2.x/reference/html/test-method.html#test-method-withsecuritycontext

## 各アノテーション

