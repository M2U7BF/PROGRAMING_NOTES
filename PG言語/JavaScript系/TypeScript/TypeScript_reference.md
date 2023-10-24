- [ドキュメント](#ドキュメント)
- [変数](#変数)
  - [宣言](#宣言)
    - [オブジェクト型](#オブジェクト型)
  - [変数宣言文](#変数宣言文)
- [標準のデータ型とその操作](#標準のデータ型とその操作)
  - [型についての前提知識](#型についての前提知識)
  - [プリミティブ型一覧](#プリミティブ型一覧)
    - [プリミティブ型の特徴](#プリミティブ型の特徴)
  - [組み込みオブジェクト型一覧](#組み込みオブジェクト型一覧)
  - [Number (数値系)](#number-数値系)
    - [操作メソッド](#操作メソッド)
  - [String (文字列)](#string-文字列)
  - [操作メソッド](#操作メソッド-1)
  - [Boolean (真偽値)](#boolean-真偽値)
  - [Arrays (配列)](#arrays-配列)
    - [宣言](#宣言-1)
    - [操作](#操作)
    - [操作メソッド](#操作メソッド-2)
  - [タプル](#タプル)
  - [Enum](#enum)
  - [Union](#union)
  - [Any](#any)
  - [Void](#void)
  - [Never](#never)
- [型アサーション](#型アサーション)
  - [書き方](#書き方)
  - [キャストとの違い](#キャストとの違い)
- [switch文](#switch文)
- [for](#for)
- [関数](#関数)
  - [定義](#定義)
    - [Anonymous Function](#anonymous-function)
    - [引数](#引数)
    - [オプションの引数](#オプションの引数)
    - [デフォルトの引数](#デフォルトの引数)
  - [特別な形](#特別な形)
    - [アロー関数](#アロー関数)
    - [関数のオーバーロード](#関数のオーバーロード)
    - [残余引数](#残余引数)
- [インターフェース](#インターフェース)
  - [定義](#定義-1)
- [クラス](#クラス)
  - [クラス操作](#クラス操作)
    - [クラスオブジェクト作成](#クラスオブジェクト作成)
    - [継承](#継承)
    - [インターフェースの実装](#インターフェースの実装)
- [アクセス修飾子](#アクセス修飾子)
  - [readonlyキーワード](#readonlyキーワード)
- [モジュール](#モジュール)
  - [操作](#操作-1)
    - [export](#export)
    - [import](#import)
      - [Renaming Export Module](#renaming-export-module)
- [名前空間](#名前空間)
- [Generics](#generics)
  - [Generic Interfaces](#generic-interfaces)
  - [Generic Class](#generic-class)


----------


## ドキュメント
英語
[TypeScript Documentation](https://devdocs.io/typescript/)

日本語
[サバイバルTypeScript](https://typescriptbook.jp/)

## 変数
### 宣言
```
var age: number = 32; // number variable
var name: string = "John";// string variable
var isUpdated: boolean = true;// Boolean variable
```
- var 変数名: 型名 という形で宣言する。


#### オブジェクト型
```
var employee : {
    id: number;
    name: string;
};

employee = {
  id: 100,
  name : "John"
}
```

### 変数宣言文
var
    関数スコープまたはグローバルスコープの変数を宣言し、任意でそれをある値に初期化します。
let
    ブロックスコープのローカル変数を宣言します。任意で値を代入して初期化できます。
    また、case sensitiveで、同名の変数を再宣言できません。
const
    - 定数を宣言します。
    - ブロックスコープを持ちます。
    - constで宣言する定数は、宣言時に必ず初期化される必要があります。
    - 定数の値は、再代入、再宣言できません。
    - しかし、定数がオブジェクトまたは配列であった場合、そのプロパティやアイテムは更新したり削除したりすることができます。


## 標準のデータ型とその操作
### 型についての前提知識
公式によると、プリミティブ型を積極的に使うそう。
https://www.typescriptlang.org/docs/handbook/declaration-files/do-s-and-don-ts.html#general-types

以下理由。
通常の操作においてはプリミティブな型を使う方が効率的で適切である。
1. **メモリ効率**: プリミティブな型（例: 数値、文字列、真偽値）は、単一の値を格納するための簡潔なデータ型です。一方、ボックス化オブジェクト型（Number、String、Boolean など）は、追加のオブジェクトラッパーを持ち、これらのオブジェクトはメモリをより多く消費します。そのため、大量のデータを扱う場合や、メモリ使用量が重要な場合には、プリミティブな型を使用する方が効率的です。
2. **演算速度**: プリミティブな型は通常、演算速度が高速です。ボックス化オブジェクト型は、オブジェクトの操作に関連する追加の処理が必要で、演算が遅くなる可能性があります。特に数値計算の場合、Number オブジェクトを使用するよりも、プリミティブな数値を使用した方が高速です。
3. **コードの可読性**: プリミティブな型を使用することで、コードがシンプルで読みやすくなります。コードの読み手は、変数がどの型を持っているかを明示的に理解でき、コードの動作が予測しやすくなります。ボックス化オブジェクト型を使うことで、コードが冗長になり、理解しにくくなる可能性があります。


### プリミティブ型一覧
- undefined
- boolean
- number
- bigint
- string
- symbol

https://developer.mozilla.org/ja/docs/Glossary/Primitive

#### プリミティブ型の特徴
イミュータブルである。
つまり、値自体を変更できず、参照値のみ変更できる。

https://zenn.dev/hogeisfuga/articles/db8a14a19f91ce


### 組み込みオブジェクト型一覧
プリミティブ型のラッパクラスと思われる。
https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects

### Number (数値系)
number型(数値型): 0や0.1のような数値。

#### 操作メソッド
toFixed()
    数を固定小数点表記を用いて整形します。
toPrecision()
    Number オブジェクトを指定された精度で表した文字列を返します。
toString()
valueOf()
    指定されたオブジェクトのプリミティブな値を返します。


### String (文字列)
string型(文字列型): "Hello World"のような文字列。

テンプレートリテラル（テンプレート文字列）
    - バッククオートを用いて、文字列を作成する。

### 操作メソッド
charAt()
concat()
indexOf()
replace()
split()


### Boolean (真偽値)
boolean型(論理型): trueまたはfalseの真偽値。

TypeScriptの場合、注意が必要である。
Booleanとbooleanは違う。Booleanはオブジェクト型でbooleanはプリミティブ型。
判定に、積極的にbooleanを用いるようにするべき。
https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Boolean


### Arrays (配列)
#### 宣言
```
let fruits: string[] = ['Apple', 'Orange', 'Banana'];
let fruits: Array<string> = ['Apple', 'Orange', 'Banana'];
```

複数の型を含む配列
コードの可読性などから、非推奨である。
```
let values: (string | number)[] = ['Apple', 2, 'Orange', 3, 4, 'Banana'];
let values: Array<string | number> = ['Apple', 2, 'Orange', 3, 4, 'Banana'];
```

#### 操作
取得
```
let fruits: string[] = ['Apple', 'Orange', 'Banana'];
fruits[0]; // returns Apple
```

#### 操作メソッド
pop()
push()
sort()
concat()
indexOf()
copyWithin()
    配列の一部を、配列にコピーする
fill()
    任意の位置のすべての要素を変更する。
shift()
    配列から最初の要素を取り除き、その要素を返します。
splice()
    その場で既存の要素を取り除いたり、置き換えたり、新しい要素を追加したりすることで、配列の内容を変更します。
unshift()
    配列の最初に 1 つ以上の要素を追加し、新しい配列の長さを返します。
includes()
    配列に含むかの判定。
join()
    全要素を順に連結した文字列を作成する。
lastIndexOf()
slice()
toString()
toLocaleString()
    配列の要素を表す文字列を返します。配列の要素は、それぞれの toLocaleString メソッドを使い、ロケール固有の文字列に変換されます（例えばカンマ "," など）。


### タプル
タプルは配列をより厳格に定義できる。
配列の各要素の数と型を定義できる。

```
var employee: [number, string] = [1, "Steve"];
var person: [number, string, boolean] = [1, "Steve", true];

var user: [number, string, boolean, number, string];// declare tuple variable
user = [1, "Steve", true, 20, "Admin"];// initialize tuple variable
```

タプルの配列
```
var employee: [number, string][];
employee = [[1, "Steve"], [2, "Bill"], [3, "Jeff"]];
```

### Enum
列挙型。

```
enum PrintMedia {
  Newspaper,
  Newsletter,
  Magazine,
  Book
}
```

Computed Enums
```
enum PrintMedia {
    Newspaper = 1,
    Newsletter = getPrintMediaCode('newsletter'),
    Magazine = Newsletter * 3,
    Book = 10
}
```

列挙型に計算メンバと定数メンバが含まれる場合、未初期化の列挙型メンバが最初に来るか、数値定数を持つ他の初期化メンバの後に来なければなりません。


String Enum
```
enum PrintMedia {
    Newspaper = "NEWSPAPER",
    Newsletter = "NEWSLETTER",
    Magazine = "MAGAZINE",
    Book = "BOOK"
}
// Access String Enum
PrintMedia.Newspaper; //returns NEWSPAPER
PrintMedia['Magazine'];//returns MAGAZINE
```

Heterogeneous Enum
```
enum Status {
    Active = 'ACTIVE',
    Deactivate = 1,
    Pending
}
```


### Union
TypeScriptでは、変数や関数に複数の型を設定でき、Union型と呼ぶ。

```
(type1 | type2 | type3 | .. | typeN)
```


### Any
どんな型でも許容する型。

```
let something: any = "Hello World!";
let arr: any[] = ["John", 212, true];
```


### Void
何のデータも返さないことを意味する。
```
function sayHi(): void {
    console.log('Hi!')
}
```

void型には、undefinedかnullのみ代入可能。
```
let nothing: void = undefined;
```


### Never
値を持たない型。
never型には、nullもundefinedも代入できない。


## 型アサーション
型推論を上書きする機能。
TypeScriptの型推論は非常に知的ですが、場合によってはコンパイラーよりもプログラマーがより正確な型を知っている場合があります。
やむを得ない場合のみ使用します。

### 書き方
as構文を使用した書き方
```
const value: string | number = "this is a string";
const strLength: number = (value as string).length;
```

アングルブラケット構文を使用した書き方
```
const value: string | number = "this is a string";
const strLength: number = (<string>value).length;
```

### キャストとの違い
キャスト: 実行時にある値の型を別の型に変換することです。
型アサーション: コンパイル時にコンパイラーに型を伝える。値の型変換はしない。


## switch文
```
switch(expression) {
   case constant-expression1: {
      //statements;
      break;
   }
   case constant_expression2: {
      //statements;
      break;
   }
   default: {
      //statements;
      break;
   }
}
```


## for
```
for (let i = 0; i < 3; i++) {
  console.log ("Block statement execution no." + i);
}
```


## 関数
### 定義
#### Anonymous Function
```
let greeting = function() {
    console.log("Hello TypeScript!");
};

greeting(); //Output: Hello TypeScript!
```

型指定した場合
```
let Sum = function(x: number, y: number) : number
{
    return x + y;
}

Sum(2,3); // returns 5
```

#### 引数
下記のように、型を指定する。
関数呼び出しの際は、引数の型と個数を合わせる必要がある。
```
function Greet(greeting: string, name: string ) : string {
    return greeting + ' ' + name + '!';
}
```

#### オプションの引数
引数名に?をつけることとで、オプションの引数を設定できる。
```
function Greet(greeting: string, name?: string ) : string {
    return greeting + ' ' + name + '!';
}
```

#### デフォルトの引数
引数に=をつけることで、デフォルト値を設定できる。
```
function Greet(name: string, greeting: string = "Hello") : string {
    return greeting + ' ' + name + '!';
}
```


### 特別な形
#### アロー関数
アロー関数式は、従来の関数式の簡潔な代替構文ですが、意味的な違いや意図的な使用上の制限もあります。
- アロー関数自身には this、arguments、super へのバインドがないので、メソッドとして使用することはできません。
- アロー関数はコンストラクターとして使用することはできません。 new をつけて呼び出すと TypeError が発生します。 new.target キーワードにアクセスすることもできません。
- アロー関数は本体内で yield を使用することができず、ジェネレーター関数として作成することもできません。

https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Functions/Arrow_functions


#### 関数のオーバーロード
引数と戻り値型が異なれば、同名の関数を定義できる。


#### 残余引数
個数未定の引数を定義できる。

例）
```
function Greet(greeting: string, ...names: string[]) {
    return greeting + " " + names.join(", ") + "!";
}

Greet("Hello", "Steve", "Bill"); // returns "Hello Steve, Bill!"

Greet("Hello");// returns "Hello !"
```
https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Functions/rest_parameters


## インターフェース
インターフェースはクラスが実装すべきフィールドやメソッドを定義した型です。
Javaとは異なり、フィールドについても定義できます。

### 定義
```
interface Person{
    name:string;
    age:number;
}

class Taro implements Person{
    name:string;
    age:number;
}
```


## クラス
Javaと同じ。
```
class Employee {
    //フィールドの定義
    public empCode: number;
    public empName: string;

    //コンストラクターの定義
    constructor(code: number, name: string) {
            this.empName = name;
            this.empCode = code;
    }

    //メソッドの定義
    getSalary() : number {
        return 10000;
    }
}
```


### クラス操作
#### クラスオブジェクト作成
Javaと同じ。
```
let emp = new Employee();
```

#### 継承
Javaと同じ。
```
class Employee extends Person {
    ...
}
```

#### インターフェースの実装
Javaと同じ。
```
class Employee implements IPerson, IEmployee {
    ...
}
```

## アクセス修飾子
### readonlyキーワード
オブジェクト型のプロパティを読み取り専用にする。


## モジュール
JavaScriptでは、デフォルトで全ファイルの変数が全ファイルから参照できるようになっている。
モジュールという考えでまとめることで下記メリットを享受する。
1. 保守性の向上
2. 変数の衝突を防止
3. コードの再利用を容易にする


### 操作
#### export
```
export let age : number = 20;
export class Employee {
    empCode: number;
    empName: string;
    constructor(name: string, code: number) {
        this.empName = name;
        this.empCode = code;
    }
    displayEmployee() {
        console.log ("Employee Code: " + this.empCode + ", Employee Name: " + this.empName );
    }
}
let companyName:string = "XYZ";
```


#### import
```
Import { export name } from "file path without extension"
```

##### Renaming Export Module
asキーワードで、名前の変更ができる
```
import { Employee as Associate } from "./Employee"
let obj = new Associate("James Bond" , 3);
obj.displayEmployee();//Output: Employee Code: 3, Employee Name: James Bond
```


## 名前空間
名前空間よりも柔軟なモジュールを好んで使用する、という例もあるようだ。
```
namespace <name>
{

}
```


## Generics
基本Javaと同じ。

例）
```
function getArray<T>(items : T[] ) : T[] {
    return new Array<T>().concat(items);
}
```

複数の場合、Tに加え、Uキーワードを用いる。
```
function displayType<T, U>(id:T, name:U): void {
  console.log(typeof(id) + ", " + typeof(name));
}

displayType<number, string>(1, "Steve"); // number, string
```

### Generic Interfaces
```
interface KeyPair<T, U> {
    key: T;
    value: U;
}
```

### Generic Class
```
class KeyValuePair<T,U>
{
    private key: T;
    private val: U;

    setKeyValue(key: T, val: U): void {
        this.key = key;
        this.val = val;
    }

    display():void {
        console.log(`Key = ${this.key}, val = ${this.val}`);
    }
}
```