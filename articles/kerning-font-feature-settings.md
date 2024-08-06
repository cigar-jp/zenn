---
title: "カーニングしてテキストを文字詰めする"
emoji: "📝"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [font, css]
published: true
publication_name: "communitio"
---

# カーニングとは
文字詰めのことです
自動カーニングをcss1行で指定できる便利な`font-feature-settings`プロパティについて説明します

# 日本語フォントこそ文字詰めが活きる
日本語フォントは、全ての文字が正方形の仮想bodyに文字が収まるようにデザインされています
原稿用紙に1文字ずつ書くイメージです
句読点や小文字など、小さな文字であっても1文字として等間隔で描写されるため、場合によっては間延びして読みにくい印象にあります
![](https://storage.googleapis.com/zenn-user-upload/nrsqcssblbxivuf7wjbp5yfkwasj)


# font-feature-settingsについて
## 字詰め
`font-feature-settings: "palt";` で指定できます

（`palt`の字詰め以外にもタイポグラフィの様々なオプションが指定できます）


## サンプル
![](https://storage.googleapis.com/zenn-user-upload/lsdi7glrhr37ey1kmbyjnrjsxxxt)
http://runstant.com/cigar/projects/619d9947

## 対応環境
ほぼ全てブラウザで対応
https://caniuse.com/font-feature



以上です
css1行で簡単にできました
楽しいタイポグラフィライフをお送りください