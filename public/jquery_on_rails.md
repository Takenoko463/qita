---
title: Ruby On RailsにおけるjQuery初期設定
tags:
  - Ruby
  - Rails
private: false
updated_at: '2024-04-15T13:02:20+09:00'
id: 1d3d79fc94dd97d2d370
organization_url_name: null
slide: false
ignorePublish: false
---
# Ruby On RailsにおけるjQuery初期設定
## 背景説明
現在のrailsに即した日本語版jQuery導入方法説明を見つけられなかったので、ここに記します。ムダな記述が多い気がするので訂正があればコメントをください。[^1]

[^1]:[参考文献](https://stackoverflow.com/questions/70921378/how-to-install-jquery-and-bootstrap-in-rails-7-app-using-esbuild-without-webpac)

## 初期設定
### アプリを作成します。
```sh
rails new useJquery
```
### 作成したフォルダーへ移動
```sh
cd useJquery
```
### コントローラーとビューを作成
```sh
rails g controller tests index
```
### ルーティング設定
```ruby
Rails.application.routes.draw do
  get 'tests/index'
  root to: "tests#index"
end
```
### app/views/tests/index.html.erbへの書き込み
```html
<h1>Tests#index</h1>
<p id="hoge">赤色になるよ</p>
```
## jQuery導入
ここからが**本題**
### Gemfileへの追加
```gemfile
##中略
gem "jquery-rails"
gem "bootstrap"
gem "sassc-rails"
```
### ダウンロード
```sh
bundle install
```

### app/assets/stylesheets/application.cssの拡張子をscssへ変更
```sh
mv app/assets/stylesheets/application.css app/assets/stylesheets/application.scss
```
### app/assets/stylesheets/application.scssへ以下を追加
```scss
*= @import "bootstrap";
```

### config/initializers/assets.rbへ以下を追加
```ruby
Rails.application.config.assets.precompile += %w( jquery.min.js jquery_ujs.js bootstrap.min.js popper.js )
```
### config/importmap.rbへ以下を追加
```ruby
pin "jquery", to: "jquery.min.js", preload: true
pin "jquery_ujs", to: "jquery_ujs.js", preload: true
pin "popper", to: "popper.js", preload: true
pin "bootstrap", to: "bootstrap.min.js", preload: true
```

### app/javascript/application.jsへ追加[^2]
```javascript
//必ず、これらを先頭に記す
import "jquery"
import "jquery_ujs"
import "popper"
import "bootstrap"
//以下他のファイル
```
[^2]:importされる順番が大事です。必ず、controllersなどより上に記してください

## javascript実行
### javascriptファイル作成
```sh
touch app/javascript/change_color.js
```
### config/importmap.rbへ追加
```ruby
pin "change_color", to: "change_color.js"
```
### app/javascript/application.jsへ追加
```javascript
import "change_color"
```

### app/javascript/change_color.jsにスクリプトを記載[^3]
```javascript 
$("#hoge").css("color","red");
```
[^3]:[参考文献](https://qiita.com/ngron/items/95846bd630a723e00038)

### このように赤色になっているなら成功です。
[![Image from Gyazo](https://i.gyazo.com/2289012162a3741a52aa28b5d1a93e59.png)](https://gyazo.com/2289012162a3741a52aa28b5d1a93e59)
