# Latest Laravel From Scratch News

課題1の模範解答です。動作方法の書き方がわからない人は参考にしてください。

# Features

Laravelを用いたニュースサイトです．
 
# Environment

<div style="display: flex;">
<img src="https://img.shields.io/badge/-PHP%208.0.23-black.svg?logo=php&style=plastic">
<img src="https://img.shields.io/badge/-Laravel%208.33.1-black.svg?logo=laravel&style=plastic">
<img src="https://img.shields.io/badge/-Docker%2020.10.17-black.svg?logo=docker&style=plastic">
<img src="https://img.shields.io/badge/-Mysql%20%208.0.30-black.svg?logo=mysql&style=plastic">
<img src="https://img.shields.io/badge/-Apache%202.4.54-black.svg?logo=apache&style=plastic">
</div>
  

# Installation

任意シェルにて以下を実行
 
```bash

# clone
git clone https://github.com/lion-rion/Laravel-From-Scratch-Blog-Project.git

# change dir
cd Laravel-From-Scratch-Blog-Project

# docker-compose and start
docker-compose up -d --build
```

## DB接続

.env.exampleをコピーして.envファイルを作成する

DBの設定を以下の通りに変更する
```
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laravel_scratch
DB_USERNAME=root
DB_PASSWORD=secret
```
## laravelのセッティング

任意のシェルにて以下を実行

```
# login apache bash
docker-compose exec apache /bin/bash

# package install
composer install

# key setting
php artisan key:generate

# storage setting
chmod -R 666 storage
php artisan storage:link

# DB migration with factory
php artisan migrate
```

## ファクトリーを用いたサンプルの生産

apacheのbashにて以下を実行

```bash
php artisan migrate:fresh --seed
```

# Ports

|  元Port  |  割当Port  |
| ---- | ---- |
|  tcp:80  |  8081  |
|  mysql:3606  |  4606  |

# Usage

ブラウザにて「 http://localhost:8081 」 を開く

# Note

## about superuser

以下の通り，admin(superuser)の権限は「JeffreyWay」という名前のユーザーに割り当てられる． adminアカウントの作成を行う際は「JeffreyWay」というユーザーネームにしてください．

```php

//AppServiceProvider.php

Gate::define('admin', function (User $user) {
    return $user->username === 'JeffreyWay';
});
```
