## 最初の使用方法
- .tsの拡張子のファイルに記述する。

コンパイルする
```
tsc <filename>.ts
```


クラス定義

インターフェイス定義
    interface User {
        name: string;
        age: number;
    }

    interface UserDictionary {
        [id: string]: User;
    }