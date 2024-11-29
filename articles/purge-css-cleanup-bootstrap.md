---
title: "Purge CssでBootstrapを一掃したよ"
emoji: "🧹"
type: "tech" 
topics: [purgecss]
published: false
publication_name: "communitio"
---

## Purge CSSとは？
**Purge CSS**は、使われていないCSSを検出して削除してくれる便利ツールです。

### 主な特徴
- **未使用CSSの削除**: プロジェクト内で使われていないCSSを自動で除去。
- **軽量化**: CSSファイルのサイズを大幅に削減。
- **パフォーマンス向上**: 無駄なスタイルが減るため、読み込みが速くなる。



## 背景
Vue.jsとTypeScriptを使ったプロジェクトで、以下のような状況に陥っていました。

- **Bootstrap**を導入してスタート。
- プロジェクトが進むにつれ、**自前CSS**でカスタマイズ。
- **Vuetify**を導入してコンポーネントも追加。

結果、CSSが混在し、以下のような問題が発生しました。

- **CSSファイルが肥大化**し、読み込みが遅い。
- **クラス名の競合**でスタイリングが崩れる。
- **どのCSSが適用されているか不明**で実装、デバッグがやりづらい。

そこで、この問題を解決するためにPurge CSSを導入し、Bootstrapを削除しました。


## 実践: Purge CSSでBootstrapを削除する

### プロジェクト環境
- **フレームワーク**: Vue.js + TypeScript
- **CSS**: Bootstrap、自前CSS、Vuetify CSSが混在

### 導入手順
#### 1. Purge CSSのインストール
まず、Purge CSSを開発依存としてインストールします。

```bash
npm i -g purgecss
```

### 2. PostCSSの設定
postcss.config.jsファイルを作成し、Purge CSSを設定します。

```js
const purgecss = require('@fullhuman/postcss-purgecss')({
  content: ['./src/**/*.html', './src/**/*.vue'],
  defaultExtractor: content => content.match(/[\w-/:]+(?<!:)/g) || [],
  safelist: ['btn-primary', 'text-center'] // 必要なクラスを指定
});

module.exports = {
  plugins: [
    require('autoprefixer'),
    ...(process.env.NODE_ENV === 'production' ? [purgecss] : [])
  ]
};
```

<!-- ### 3. Vue CLIでの設定
Vue CLIを使用している場合、PostCSS設定は自動的に適用されます。特に意識することなく動作するはずです。 -->

### 3. 実行
```bash
purgecss --css style.css --content index.html --output style.purged.css
```
オプションの --css は元のCSSファイル、--content は参照先のファイル、--output は書き出しファイルです。
ファイル名、ファイルパスは作業環境に合わせてください。

### 4. CSSファイルの確認
ビルド後のCSSファイルを確認して、未使用のBootstrapスタイルが削除されていることを確認します。

# まとめ
Purge CSSを使って、Vue.js/TypeScriptプロジェクトのBootstrapを一掃し、CSSを整理することに成功しました。

### この記事のポイント
- Purge CSSは使われていないCSSを削除して軽量化を実現。
- Vue.jsの動的クラス名問題もsafelistで解決可能。
- CSSの削減で、メンテナンス性とパフォーマンスが向上。

Purge CSSを導入することで、CSSの整理整頓が簡単にでき、結果的にプロジェクトの開発効率が大きく向上しました。
同じようにレガシーなcssで悩んでいる方は、ぜひ試してみてください！

コードをコピーする
