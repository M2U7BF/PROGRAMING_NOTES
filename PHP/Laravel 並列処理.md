- [並列処理](#並列処理)
  - [並列処理を行う方法](#並列処理を行う方法)
  - [Laravel Horizonセットアップ](#laravel-horizonセットアップ)
  - [Queセットアップ](#queセットアップ)


# 並列処理
## 並列処理を行う方法
1. Laravel Horizon
2. LaravelのQueを利用
3. プロセスフォークを使用する

上記の1~2が推奨される。

## Laravel Horizonセットアップ
   a. LaravelプロジェクトにLaravel Horizonをインストールします。

   ```bash
   composer require laravel/horizon
   ```

   b. Horizonの設定ファイルを公開し、必要な設定を行います。

   ```bash
   php artisan vendor:publish --tag=horizon-config
   ```

   c. ワーカープロセスを起動します。

   ```bash
   php artisan horizon
   ```

   これにより、Laravel HorizonがRedisキューを監視し、タスクを並列で実行します。
## Que
### Queセットアップ

   a. キュージョブを作成します。

   ```bash
   php artisan make:job MyJob
   ```

   b. ジョブの中に実行したいコードを記述します。

   c. ジョブをディスパッチします。

   ```php
   MyJob::dispatch();
   ```

   d. Queueワーカーを起動します。

   ```bash
   php artisan queue:work
   ```

   これにより、Queueに追加されたジョブが非同期で実行されます。


### Queの実行
下記を実行しておく。非同期処理を逐次実行する。
```
php artisan queue:work
```

