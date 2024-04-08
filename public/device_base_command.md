---
title: device_base_command
tags:
  - 'ruby'
  - 'rails'
private: true
updated_at: ''
id: null
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
### userテーブルの作成
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
rails g devise:views
```

### controllerの作成[^2]
[^2]:私はまだ使ったことはない。googleアカウントでのログイン機能実装で使う予定。

```
rails g devise:controller
```

