---
title: "tailwindで子要素にクラスを指定したいときの書き方"
emoji: "👈"
type: "tech" 
topics: [tailwind css]
published: true
publication_name: "communitio"
---

## はじめに
この記事では、Tailwind CSSを使用して子要素や子孫要素にクラスを適用する方法について説明します。
この記事で使用している`className`は、Next.jsとTypeScriptの組み合わせを想定していますが、他の環境でも同様のアプローチが可能です。
ご自身のプロジェクトで異なるフレームワークやライブラリを使用している場合は、適宜classや他の属性名に変更してください。


## 子要素につけたいとき

```tsx
  className="[&.your-class]:p-2"
```

## 子孫要素につけたいとき

```tsx
  className="[&>li]:italic"
```

## `:nth-child`のようなCSS疑似クラスセレクタも使える

```tsx
  className="[&:nth-child(3)]:underline"
```

### 他にも以下のようなCSS疑似クラスセレクタが使えます

- `hover:` - ホバー時のスタイル（例：`hover:bg-blue-500`）
- `focus:` - フォーカス時のスタイル（例：`focus:outline-none`）
- `sm:`, `md:`, `lg:`, `xl:` - レスポンシブデザイン用（例：`sm:text-lg`）
- `dark:` - ダークモード用（例：`dark:bg-gray-800`）
- `group-hover:` - 親要素のホバー時に適用（例：`group-hover:text-white`）
- `first:`, `last:` - 最初/最後の要素にスタイルを適用（例：`first:mt-0`）
- `even:`, `odd:` - 偶数/奇数番目の要素にスタイルを適用（例：`odd:bg-gray-100`）



## Next.jsでの使用例
Next.jsとTypeScriptを使用した簡単なReactコンポーネントの例です。
こんな感じで指定できます。
この例では、親要素内の特定の子要素にTailwind CSSのクラスを適用しています。

```tsx
  import React from 'react';

  const StyledList: React.FC = () => {
    return (
      <ul className="[&>li]:italic [&:nth-child(2)]:underline space-y-2">
        <li>アイテム1</li>
        <li>アイテム2</li>
        <li>アイテム3</li>
      </ul>
    );
  };

  export default StyledList;
```

## 補足情報
- [Tailwind CSS公式ドキュメント](https://tailwindcss.com/docs)
  Tailwind CSSの詳細な使い方やカスタマイズ方法については、公式ドキュメントを参照してください。
