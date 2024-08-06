---
title: "フォームデザインパターン - フロントエンドエンジニアが知っておくべきこと -ストーリーポイントとは何なのか"
emoji: "🤵🏻‍♂️"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [ui, design patterns, form, cmnt]
published: false
publication_name: "communitio"
---


Form Design Patternsを読んでみました
[Form Design Patterns ―シンプルでインクルーシブなフォーム制作実践ガイド](https://www.amazon.co.jp/dp/4862464513)

<aside>
💡 ひとりのユーザーとして、私は「あなたのサービス」にログインしたい。そうすることで、「物事を行うこと」ができるから。

— そんな人いるわけがない！

</aside>

> 訳注：この一文はアジャイル開発のプロジェクトで用いられるuser storyという手法にもとづいた記述である。
> 

つまり、ユーザーはあなたのサービスを通じて何らかのベネフィットを得たいのであって、

登録/ログインフォームは、あなたのサービスを安全に使ってもらうための必要な手続きです。

入口の段階でのユーザーの負担をできるだけ小さくすることに気を遣いましょう。

## ユニバーサルデザイン

---

- 本書では重要視して触れられているが、個人的にはプロダクトとして対応すべきフェーズは結構後だと考えています

## ユーザーエクスペリエンス（UX）の向上

---

### **簡潔なフォーム**

必要最小限の入力項目で済むように設計し、ユーザーが迅速に入力できるようにします。

- email,passwordのみで、ユーザー情報はあとにできないか？
- ユーザーはあなたのサイトを単に使いたいだけで、最初に負担を大きくしない方がよい

### **視覚的なヒント**

プレースホルダーやラベルを使って、ユーザーにどのような情報を入力すべきかを明確に示します。

- プレースホルダー
    - ミニマルデザインでスペースを節約できる
    - パスワードルールなどをプレイスホルダーに記載すると、パスワード入力中は見えないのでエラー原因となり得る
        - 便利だが使うシーンは注意
        - 上記の例はサブラベル（パスワードというラベルの下）としてルールを記載するという選択肢も考慮すべき
        - inputとヒントを結びつけるaria-describedby属性がある
        
        ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/c6685822-ac42-41ed-ac0c-483485112e2b/24ec9335-f514-424f-945e-fcf75101c699/Untitled.png)
        
- フロートラベル
    - UIライブラリでたまによく見る（MUI とか）
    - 本書では否定的
        - おしゃれだけど、スペース節約にならないし、入力済みのフィールドと勘違いするリスクがある
        
        [レコーディング 2024-08-01 153631.mp4](https://prod-files-secure.s3.us-west-2.amazonaws.com/c6685822-ac42-41ed-ac0c-483485112e2b/e2fce59e-89dc-4b48-9f7a-18a9242cb0e8/%E3%83%AC%E3%82%B3%E3%83%BC%E3%83%87%E3%82%A3%E3%83%B3%E3%82%B0_2024-08-01_153631.mp4)
        
- フォームUIはフォームらしくあれ
    - ユーザーが使い慣れたフォームとして近くできるべき
    - おしゃれさより、ユーザーの知覚に寄り添って他サイトを含んだ統一性を保つ
    - 例）空のボックスは枠で四方を囲まれたテキストボックス

## アクセシビリティの考慮

---

### **ラベルの明確化**

各入力フィールドに対して適切なラベルを設定します。

システムとしてメールアドレスをユーザー名として扱っている場合

- ×「ユーザー名・ユーザーID」
- ○「メールアドレス」

### **エラーメッセージの提供**

入力エラーが発生した場合は、具体的で理解しやすいエラーメッセージを表示します。

- 平易な言葉で、シンプルに伝わる文言であること
- 能動態の方がユーザーの行動が理解しやすい
    - ×「お名前は入力される必要があります」
    - ○「お名前を入力してください」

### **プログレッシブエンハンスメント**

> プログレッシブエンハンスメントはWebデザインの戦略で、全ての人がWebページの基本的なコンテンツと機能にアクセスできるようにしつつ、追加のブラウザ機能やより高速なインターネットアクセスを持つユーザーには、代わりに強化されたバージョンを提供するものです。
> 
- JavaScript だけでなくモダンCSSなども対象
- Next.js App Router を例に挙げると、Server Actions を有効活用することで、JavaScript が無効な状態でもフォームの動作を実現できます。
- JavaScript が無効な状態というのはレアケース（ユーザーの0.5%程度）なので、JavaScript 以外のプログレッシブエンハンスメント全体についても、費用対効果の検討をしましょう