ブラウザデバッグ
    Vue.jsのSFC Playground
        https://sfc.vuejs.org/

チュートリアルまとめ : https://hackmd.io/@yto60/SJ5qzYTFI

Options API
Vue.js
    コンポーネント指向に重きを置いたUIライブラリ

コンポーネント Component
    UIコンポーネント
        一般的なWeb開発におけるUI部品のこと
        UIコンポーネントをどれだけ効率的に書けるかが鍵となる
        再利用を容易にする

    カスタムタグ

    ローカルコンポーネント
    グローバルコンポーネント

    親子関係

    命名規則
        ケバブケースが推奨される
        ```
        same-hoge-component
        ```

    定義する
        カスタムタグ方式
            Vue.component()を使う。
            ```
            // options には data, methods など渡す
            Vue.component(tagName, options)
            ```
        サブコンストラクタ方式
            Vue.extend()を使う。
                Vue.extend()とは
                    グローバルなAPI
                    ベースのVueコンストラクタを継承した、サブクラスコンストラクタを作成できます。
            $mount関数
                定義したものを直接特定の要素にマウントする

プロパティ  ((オプション)オプションオブジェクト)
    dataプロパティ
        アプリケーションの様々なデータを管理・操作することができます（リアクティブな変数を定義することができます）。
        https://www.webdesignleaves.com/pr/plugins/vue-basic-01.html#:~:text=Options%20API%20%E3%81%A7%E3%81%AF%E3%80%81data%E3%80%81methods,%E3%82%AA%E3%83%97%E3%82%B7%E3%83%A7%E3%83%B3%E3%81%AA%E3%81%A9%E3%81%A8%E5%91%BC%E3%81%B3%E3%81%BE%E3%81%99%E3%80%82

        ここでreturnした値をtemplateで読み込める

    computedプロパティ
        Vueの能力を最大限に活かすのであれば、積極的に使うべき。

    propsプロパティ
        親コンポーネントから子コンポーネントに対してデータを渡す

        バリデーション
            型指定
                https://v2.ja.vuejs.org/v2/guide/components-props.html#%E3%83%97%E3%83%AD%E3%83%91%E3%83%86%E3%82%A3%E3%81%AE%E3%83%90%E3%83%AA%E3%83%87%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3
                https://prograshi.com/language/vue-js/validators-for-props/

            カスタムバリデータ
                https://qiita.com/potato4d/items/1b92df0cbf9b0b6cf8d6
                ```
                validator (val) {
                    return ['small', 'medium'].includes(val)
                }
                ```

        propsの初期値
            default関数で定義する必要がある。
            ```
            propE: {
                type: Object,

                default: function () {
                    return { message: 'hello' }
                }
            },
            ```
            https://jp.vuejs.org/v2/guide/components-props.html#%E3%83%97%E3%83%AD%E3%83%91%E3%83%86%E3%82%A3%E3%81%AE%E3%83%90%E3%83%AA%E3%83%87%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3

        propsとdataの連携
            特別な理由がない限り、dataへpropsを代入/コピーすべき場面はありません。代わりにcomputedを使うようにしましょう。
            https://ics.media/entry/200716/

        computed
            算出プロパティ
            あるデータから派生するデータをプロパティとして公開する仕組み

            computedで定義したプロパティは、データと同様にテンプレートで展開することが可能です。

ディレクティブ
    v-if v-show
        条件つきレンダリング

    v-for
        リストレンダリング
        繰り返し処理
        ```
        <div v-for="fruit in fruits" :key="fruit">
            {{ fruit }}
        </div>
        ```

        数字指定
        ```
        <span v-for="n in 5" :key="n">{{ n }} </span>
        ```

        v-bind属性
            ```
            v-bind:key="item.id"
            ```
            key変数。配列の中の何番目を表示しているのか把握する。

    v-bind
        バインディング

        文字結合
            v-bind:href="'#' + project.id"

    v-on
        イベント処理

    v-model
        フォーム入力

ライフサイクルフック

スロット
    https://qiita.com/myLifeAsaDog/items/206c04fdef3a874b86f6

formを利用する
    バリデーション
        v-modelの使用
        https://qiita.com/yasushi-jp/items/a887b11f2090c38e3e95

    v-model
        フォーム入力バインディング

        v-bindとv-onをまとめて書くための糖衣構文
            https://qiita.com/punkshiraishi/items/6f72389fa23b0820a72a
        双方向データバインディングを行う
        <input type="text" v-model="phoneNumber" name="phone_number" />
        と記載すると、phoneNumberという変数とテキストボックスに入力した値を同期してくれます。

DB実装
    //

状態管理
    データフローとは
        アプリケーションが持つデータの流れ。
        どこにデータを保持し、データを読み込む時や更新する時はどこからどのように行うのかという点を表
        すことが多いです。大規模な状態管理を行う際はデータフローの設計の良し悪しで実装の複雑さや難易
        度が大きく変わります。

        Flux
            Facebookが提唱しているデータフロー設計
            http://facebook.github.io/flux/docs/in-depth-overview

    イベントの感知
        v-on
            イベントの種類
            ```
            v-on: input="hoge"
            v-on: onclick ="hoge"
            v-on: mouseover ="huge"
            ```

イベント変数
    ```
    $event
    引用 : https://jp.vuejs.org/v2/guide/events.html#%E3%82%A4%E3%83%B3%E3%83%A9%E3%82%A4%E3%83%B3%E3%83[…]3%83%83%E3%83%89%E3%83%8F%E3%83%B3%E3%83%89%E3%83%A9
    ```

    class名取得
        ```
        event.target.className
        引用 : https://cpoint-lab.co.jp/article/201803/1958/
        ```

非同期処理
    async
        非同期処理が発生する関数にasyncをつける

    await
        その関数内で、処理を待たなければならない部分にawaitをつける
    https://rara-world.com/es2017-async-await/

vue-router
    SPAのためのページルーティング機能を提供する
    https://qiita.com/morrr/items/873ea25a806167c8d426

    コードで画面遷移を制御する
        ```
        // 単純な遷移
        this.$router.push('/user/123')

        // 名前による指定
        // /user/:id のrouteがあった場合に /user/123 に遷移する
        this.$router.push({ name: 'user', { id: '123' }})

        // パラメータを渡す  /foo?bar=baz
        this.$router.push({ path: 'foo', query: { bar: 'baz' }})
        ```

htmlの文字列を置換する
    v-text
        ```
        <p v-text="error-message"></p>
        ```

    {{}}
        ```
        <p>{{ error-message }}</p>
        ```

共通関数の定義
    jsファイルで定義
        定義
            ```
            export const dateHelper = {
                formatedDate(date: string | Date) {
                    const d = new Date(date);
                    return d.toLocaleDateString();
                },
            };
            https://azukiazusa.dev/blog/vue-js-mixin/#%E5%86%8D%E5%88%A9%E7%94%A8%E5%8F%AF%E8%83%BD%E3%81%AA%E6%A9%9F%E8%83%BD%E3%81%AF%E7%B4%94%E7%B2%8B%E3%81%AAjavascript%E3%81%A7%E8%A1%8C%E3%81%86
            ```

        呼びだし
            ```
            import { dateHelper } from "@/helpers/dateHelper";
            ```

    ミックスイン
        ミックスインはやめよう
        https://azukiazusa.dev/blog/vue-js-mixin/#%E5%86%8D%E5%88%A9%E7%94%A8%E5%8F%AF%E8%83%BD%E3%81%AA%E6%A9%9F%E8%83%BD%E3%81%AF%E7%B4%94%E7%B2%8B%E3%81%AAjavascript%E3%81%A7%E8%A1%8C%E3%81%86

オブジェクトのエクスポートとインポート
    エクスポート
        ```
        export const hoge = 0;
        ```

        ```
        export default const hoge = 0;
        ```

    インポート
        ```
        import { hoge } from "./../hoge.js";
        ```

クラス定義
    https://reffect.co.jp/vue/vue3-composition

型定義
    ```
    <script lang="ts" setup>
    import ChildComponent from '@/components/ChildComponent.vue'

    const childProps: InstanceType<typeof ChildComponent>['$props'] = {}
    </script>
    ```

変数公開
    https://tech.innovator.jp.net/entry/2017/10/31/140000s

クラス名を動的にする
    ```
    <a :href="'tel:'+'090XXXXZZZZ '">でんわ</a>
    https://programmer-note.hatenablog.com/entry/2021/09/24/194914
    ```

コンポーネント間通信
    子から親
        emitを使う
        https://qiita.com/masatomix/items/ab4f0488083554f5fceb

デバッグ
    ブラウザの開発者ツールを使用する。Vue.jsの開発者ツール拡張機能をインストールすることで、コンポーネントの階層構造、データ、コンピューテッドプロパティ、ウォッチャー、そしてデバッグログなどを表示できます。

    Vue.jsのデバッグモードを有効にする。Vue.jsはデバッグモードを有効にすることで、エラーの情報をより詳しく表示します。

    console.logを使用する。JavaScriptで一般的に使用されるデバッグ方法で、特定の箇所にログを出力し、変数やオブジェクトの値を確認できます。

    Vue.jsのデバッグツールを使用する。Vue.jsには、Vue.js devtoolsと呼ばれるデバッグツールがあります。これを使用すると、コンポーネントの状態やイベントのトリガー、そしてストアの状態を確認できます。

    Vue.jsのストアの状態を確認する。Vue.jsのストアは、アプリケーションの状態を管理するための中央データストアです。ストアの状態を確認することで、アプリケーションの状態を理解できます。

    Vue.jsのウォッチャーを使用する。ウォッチャーは、データの変更を監視するためのVue.jsの機能で、変数の値の変化を検知することができます。

    Vue.jsのコンピューテッドプロパティを使用する。コンピューテッドプロパティは、データの計算値を表現するためのVue.jsの機能で、依存関係の変更に応じて自動的に更新されます。

    ブレークポイントを使用する。JavaScriptのデバッグツールには、ブレークポイントと呼ばれる機能があります。ブレークポイントを設定すると、指定した箇所で実行を停止し、変数の値やスタックトレースを確認できます。

    テストツールを使用する。Vue.jsのテストフレームワークやライブラリを使用することで、コンポーネントやアプリケーションの動作を自動化してテストできます。

レスポンシブ対応
    v-flex
    12点グリッド

.vueファイル
    .vueファイルをブラウザで表示するには、Vue.jsのビルドプロセスを使ってコンパイルし、JavaScript、HTML、CSSに変換する必要があります。
    これは、Vue CLIやWebpackなどのビルドツールを使用することで行うことができます。

● 関数を共通化させる
    https://programmer-note.hatenablog.com/entry/2021/09/26/175427



Q
async function という記述はなんだろ??
    非同期処理行っているっぽい!!!!

Q
{{}} ← これは何という
A
Mustache(ムスタッシュ、口ひげ)

Q
vmとは
A
ViewModelの略。慣例として、vm (ViewModel の略) を Vue インスタンスの変数名としてよく使います。
引用 : https://jp.vuejs.org/v2/guide/instance.html
