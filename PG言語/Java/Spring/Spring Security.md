## 認証
### 基本的な流れ
https://qiita.com/d-yosh/items/7e905bfc20a1bfe5243a

### 主なクラス
◆ 実装クラス
1. UserDetails
2. AuthenticationProvider
3. AbstractUserDetailsAuthenticationProvider

◆ その他関連クラス
1. UsernamePasswordAuthenticationFilter
2. AuthenticationManager
3. AuthenticationProvider
4. UserDetailsService


## テストにおいて
#### CustomMockUser
https://qiita.com/kazokmr/items/9fab9ad267d70e25da8d
https://docs.spring.io/spring-security/site/docs/4.2.x/reference/html/test-method.html#test-method-withsecuritycontext

    主な使用クラス
        1. WithSecurityContextFactory
        2. 

Role
    Role.USER.name : 規定のRoleクラスから参照

    hasRoleのROLE_自動付与
    参考 : https://qiita.com/yokobonbon/items/7d729bd8085f3fb898bb

