クラス定義

インターフェイス定義
    interface User {
        name: string;
        age: number;
    }

    interface UserDictionary {
        [id: string]: User;
    }