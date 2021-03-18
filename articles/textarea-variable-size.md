---
title: "改行で自動で大きさが変わるtextareaの作り方"
emoji: "💬"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [html,javascript,textarea]
published: false
---


textareaを改行に応じて自動で高さが変わるようにします

入力イベント(oninput)時に、textareaの`行の高さ × 行数(改行文字数)`でheightを変えることで実装しています
コードは数行で、HTML, CSS, JSのみで簡単に実装できます

![](https://storage.googleapis.com/zenn-user-upload/9crw3xliwtsup0zjusdu3e8mbyon)

## サンプル
http://runstant.com/cigar/projects/textareavariablesize

## コード解説

```html
<textarea id="textarea" placeholder="改行で高さが変わるtextarea" rows='1' oninput="resizeTextarea()"></textarea>
```
HTMLで`oninput="resizeTextarea()`と
入力イベント時にtextareaのサイズ変更をする関数を発火させています


```css
#textarea {
  resize: none;
  line-height: 1.5;
  width: 100%;
  padding: 10;
}
```
cssは自由に変えてもらってokです

textareaはデフォルトだと手動でサイズを変更できますが、今回は自動でサイズ変更されるため
`resize: none`で手動リサイズはしないようにしています

line-heightとpaddingは下記のjavascriptの関数内で計算に使っているため、
変更する場合は調整してください

```js
window.onload = function() {

  //- 改行に合わせてテキストエリアのサイズ変更
  this.resizeTextarea = () => {

    // textarea要素のpaddingのY軸(高さ)
    const PADDING_Y = 20;
    
    // textarea要素
    const $textarea = document.getElementById("textarea");
    
    // textareaそ要素のlineheight
    let lineHeight = getComputedStyle($textarea).lineHeight;
    // "19.6px" のようなピクセル値が返ってくるので、数字だけにする
    lineHeight = lineHeight.replace(/[^-\d\.]/g, '');

    // textarea要素に入力された値の行数
    const lines = ($textarea.value + '\n').match(/\n/g).length;

    // 高さを再計算
    $textarea.style.height = lineHeight * lines + PADDING_Y + 'px';
  };
};
```

ポイントはここで、textarea内の改行文字`\n`の数 = 行数として計算しています
```js
const lines = ($textarea.value + '\n').match(/\n/g).length;
```

取得した 行の高さ * 行数 でtextareaの高さを決めてあげれば完成です
```js
$textarea.style.height = lineHeight * lines + PADDING_Y + 'px';
```

#### 以上です
読んでいただきありがとうございました