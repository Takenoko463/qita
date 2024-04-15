---
title: Ruby On Railsにおける基本コマンド
tags:
  - Ruby
private: false
updated_at: '2024-04-15T12:48:40+09:00'
id: 6e1e6be83357b29adf3e
organization_url_name: null
slide: false
ignorePublish: false
---
# Ruby On Railsにおける基本コマンド

## 背景説明
プログラミングスクールで学んだ**Ruby on Rails**の基本操作方法をまとめる。
メモとして使う予定。
## アプリ作成。
webアプリケーションを作成するコマンド。アプリを作成したいフォルダーで実行。[^1]

[^1]:アプリの名前は**appName**にしています。
### 基本
```
rails new appName
```
### よく使うオプション
バージョン7.0.0、データベースにmysqlを指定
```
rails _7.0.0_ new appName -d mysql
```
## コントローラー作成

コントローラーを作成するコマンド。[^2]

[^2]:コントローラーの名前は**mails**にしています。名前を必ず**複数形**にすること
```
rails g controller mails
```

## モデル作成
モデル作成するコマンド。[^3]

[^3]:モデルの名前は**mail**にしています。
```
rails g model mail
```
## マイグレーション反映
マイグレーションを実行し、データベースに反映
```
rails db:migrate
```
