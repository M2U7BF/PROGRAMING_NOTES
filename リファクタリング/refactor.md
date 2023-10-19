## if文
### if文のネスト
リファクタリング前
```java
public boolean isLeapYear(int year){
    if (year % 4 == 0){
        if(!((year % 100 == 0) && (year % 400 != 0))) {
            return true;
        }
    }

    return false;
}
```

リファクタリング後
```java
public boolean isLeapYear(int year) {
    return (year % 4 == 0) && ((year % 100 != 0) || (year % 400 == 0));
}
```
- booleanを直接返すようにした。
- ド・モルガンの法則で、notのnotといった複雑さをなくした。
- if文のネストをなくした。
