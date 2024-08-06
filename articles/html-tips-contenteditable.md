---
title: "HTML5のcontenteditable属性"
emoji: "📝"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [HTML5, contenteditable]
published: true
publication_name: "communitio"
---

## contenteditable属性とは
HTML5の仕様で,要素内の編集可否を指定する属性です
すべてのHTML要素において使用することができます

編集は画面上のみ反映され,ソースが編集されたり保存されることはありません

## 使いどころ
開発者ではない方に,要素の確認をしてもらう場合などに便利かもしれません
- この見出しテキスト、2行になったらどんな折り返し表示になるか
- この要素だけ削除してスクショが取りたい

など

## サンプルコード
http://runstant.com/cigar/projects/html-tips-contenteditable

```html
<h2> 編集可能なリスト </h2>
<ol contenteditable="true" >
  <li> 布団から出る </li>
  <li> 歯を磨く </li>
  <li> 会社に行く </li>
</ol>

<h2> 編集不可能なリスト </h2>
<ol>
  <li> 布団から出ない </li>
  <li> 歯を磨かない </li>
  <li> 会社に行かない </li>
</ol>
```

### 以上です
ご覧いただきありがとうございました