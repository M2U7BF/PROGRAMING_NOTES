
- [概説](#概説)
  - [テスト作成単位](#テスト作成単位)
- [Junitのリファレンス](#junitのリファレンス)
  - [ログイン状態](#ログイン状態)
      - [@WithMockUser](#withmockuser)
      - [@WithCustomMockUser (自作)](#withcustommockuser-自作)
  - [各アノテーション](#各アノテーション)


## 概説
### テスト作成単位
クラス毎に作成するのが一般的（ネット調べ）。クラス毎にテストクラスを作成し、各メソッドや機能を単独でテストする。

## Junitのリファレンス
### ログイン状態
##### @WithMockUser
ユーザーで擬似ログイン

##### @WithCustomMockUser (自作)
カスタムユーザーの利用
https://qiita.com/kazokmr/items/9fab9ad267d70e25da8d
https://docs.spring.io/spring-security/site/docs/4.2.x/reference/html/test-method.html#test-method-withsecuritycontext

### 各アノテーション

