---
title: devise導入における基本コマンド
tags:
  - Ruby
  - Rails
private: false
updated_at: '2024-04-09T00:22:17+09:00'
id: f30ca8cf1579301ac4dd
organization_url_name: null
slide: false
ignorePublish: false
---
# devise 導入 基本手順
## deviseとは?
deviseとはユーザー認証機能導入を手助けするgemです。
## ユーザー管理機能の実装
### deviseのinstall
#### gemファイルへの追記  
**Gemfile**
```
# 中略
gem 'devise'
```
#### bundleによる反映
**コマンド**
```
bundle install
```
### deviseの設定ファイルの作成
```
rails g devise:install
```
### userモデルの作成
モデルやマイグレーションファイルの自動生成、ルーティングへの追記を行う[^1]  

[^1]:**user**はあくまでモデル名の一例。masterでもなんでも良い。
```
rails g devise user
```
### usersテーブルの作成
マイグレーションの実行
```
rails db:migrate
```
再起動して反映
```
rails s
```

### viewの作成
```
rails g devise:views users
```

### controllerの作成[^2]
[^2]:私はまだ使ったことはない。googleアカウントでのログイン機能実装で使う予定。

```
rails g devise:controller
```

