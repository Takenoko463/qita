---
title: Ruby On Railsの基本操作
tags:
  - 'Ruby'
private: true
updated_at: '2024年4月2日'
id: null
organization_url_name: null
slide: false
ignorePublish: false
---
# Ruby On Railsの基本操作

## 背景説明
プログラミングスクールで学んだ**Ruby on Rails**の基本操作方法をまとめる。
メモとして使う予定。
## アプリ作成。
webアプリケーションを作成しするコマンド。アプリを作成したいフォルダーで実行。[^1]
[^1]アプリの名前は**appName**にしています。
### 細かい指定をしないなら
```
rails new appName
```

### バージョンやデータベース管理システム名を指定する場合  
- バージョン:7.0.0
- データベース管理システム:mysql[^2]
[^2]mysqlをダウンロードしていることが前提です。
```
rails _7.0.0_ new appName -d mysql
```
