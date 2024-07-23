---
title: "【ゼロパディング】`001`のように数値の桁を合わせる"
emoji: "0️⃣"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [zeropadding,javascript]
published: true
---

# ゼロパディング(zero padding)とは
書式の桁数に満たない数値の場合に,足りない桁数だけ`0`を追加して桁数を合わせることです

- (例) 日付入力欄
月日は2桁までの数値が存在するため, 1桁の場合は桁数を合わせて
2月を`02`と表現しています
![](https://storage.googleapis.com/zenn-user-upload/mb0cw6urgv1k5g5qbnwco8zmd26f)

### String.prototype.padStart()
`padStart()`メソッドは, 結果の文字列が指定した長さになるように,
現在の文字列を他の文字列で (必要に応じて繰り返して) 延長します
延長は現在の文字列の先頭から適用されます

```js
const num = 1;
const padNum = String(num).padStart(3, '0');

//- '001'
console.log(padNum);
```

### String.prototype.slice()
足りない桁数を先に文字列追加しておいて, 
希望の桁数分文字列の終わりから取得します

```js
const num = 1;
const padNum = ('000' + num).slice(-3);

//- '001'
console.log(padNum);
```

### サンプルコード
http://runstant.com/cigar/projects/zero-padding


### 以上です
意外と登場シーンが多いので, 初学者の方など参考にしてくだされば幸いです