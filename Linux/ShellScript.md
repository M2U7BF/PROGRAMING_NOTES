- [関数](#関数)
- [配列](#配列)
  - [取り出し](#取り出し)
  - [forループ](#forループ)

### 関数
定義

### 配列
#### man
man -a bash、でArraysで検索

#### 取り出し
third_element=${array[2]}

#### forループ
for num in ${array[@]};do
done

### for文
#### man
man -a bash、でforで検索

## テクニック
### 分割保存
１）
```
elems=($(echo "$i" | tr ':' ' '))
```
「elems=()が基本形」
「$(echo "$i" | tr ':' ' ')」でまとめて変数にしている
「echo "$i"」が入力
「tr ':' ' '」で置き換え

２）
ちょっと意味が違うが似てる
awk -F' ' '{print $0}'
