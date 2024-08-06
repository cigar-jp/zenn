---
title: "【CSS】影を付けるのに何でもbox-shadowを使っていないか!?"
emoji: "👤"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [css]
published: true
publication_name: "communitio"
---

# はじめに
CSSで影を付ける際、まず`box-shadow`が思いつくかと思います
自分も特に考えず`box-shadow`を使っていたのですが,
便利なCSS関数`filter: drop-shadow()`について整理したいと思います

# box-shadowとdrop-shadowの描画の違い
まずそれぞれの描画の違いがこちらになります

### box-shadow
- svg画像のボックス要素全体に長方形の影を付ける
- 疑似要素に影が付かない
![](https://storage.googleapis.com/zenn-user-upload/zwn1rvwtq2tf4vg2dx2j6enta618)
![](https://storage.googleapis.com/zenn-user-upload/6r2177mwr8doqn7eakfrh6bjmzct)

### drop-shadow
- svg画像そのものの形に合った影を付ける
- 疑似要素にも影が付く
![](https://storage.googleapis.com/zenn-user-upload/pbub8hwqq19el7tifebxxcdycg51)
![](https://storage.googleapis.com/zenn-user-upload/3odbvtsst6ysuesethipe2kc2pey)

# サンプルコード
http://runstant.com/cigar/projects/css-tips-drop-shadow

# drop-shadowの使い方
```css
filter: drop-shadow(2px 4px 5px rgba(0, 0, 0, 0.5));
```
## 引数
`filter: drop-shadow( 水平位置, 垂直位置, ぼかし具合, 色 )`

### 水平位置（必須）
x軸の位置です. 指定した数値分右に移動します
マイナス値で左にも移動できます

### 垂直位置（必須）
y軸の位置です. 指定した数値分下に移動します
マイナス値で上にも移動できます

### ぼかし具合（任意）
blur値です. 値が大きくなるほど, 影は広く薄くなります
指定しない場合は規定値の0となり、ぼやけずくっきりとした影になります
マイナス指は指定できません

### 色（任意）
影の色です. 透明度も指定できます
指定されない場合の既定値は、ブラウザーによります

# drop-shadowの弱点
勉強していて, もう`box-shadow`要らないじゃん! と思ったのですが,
`drop-shadow`は`box-shadow`では指定できる
影の広がり距離とinset(内側の影)は指定できません
付けたいshadowによって使い分けしたほうがよいですね

# おわりに
上記で見たようなsvg画像の描画に合わせた影や,
疑似要素がある要素の影には`drop-shadow`が便利だと思います

ご覧いただき、ありがとうございました