---
title: "Herokuとgithubを連携して自動デプロイする方法"
emoji: "🐥"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [heroku]
published: true
publication_name: "communitio"
---

## Herokuをgithubを連携するメリット
- GitHubのpull request毎に自動で環境が作られる
- GitHub上にHeroku環境のリンクが表示される
![](https://storage.googleapis.com/zenn-user-upload/e0k0x0tcw3rvml4joj7j8zqtdssf)

上記2点のおかげで簡単にGitHub上pull requestの環境を確認できます
チーム開発などでレビュー効率化に繋がります

## 基本セットアップ

### 1. Herokuのダッシュボードにアクセスします
https://dashboard.heroku.com

### 2. 画面右上のNewからcreate new pipelineを選びます
![](https://storage.googleapis.com/zenn-user-upload/urv60hgtud0matv0768yzmpbiso7)

### 3. Pipeline nameを入力します
- 任意でok, Heroku上で表示されるサービス名になります
### 4. 連携するgithubを検索して選択します
![](https://storage.googleapis.com/zenn-user-upload/1turvopz0ixqg8qcjwv27bf0rb7x)

### 5. 環境変数の変更 
- デプロイする環境を設定します
デフォルトはproductionになっているので開発環境で使う場合はdevelopmentとしておきます
![](https://storage.googleapis.com/zenn-user-upload/5pni3smqp2pmohn4kf2d4ua1cf3c)
![](https://storage.googleapis.com/zenn-user-upload/syk6gh709ptw1a9cq9c4q6gmzdzl)

### 6. STAGINGにappを追加
- ※バグ回避のための設定です
この設定をしておくことで、Github上のpull requestが全て消えるとHerokuのpipelineごと削除されてしまうことを防止できます
![](https://storage.googleapis.com/zenn-user-upload/t85oqzvjhekno72n0b28mgxt24iu)

### 7. GitHubにpull requestを出して自動環境が作られることを確認
![](https://storage.googleapis.com/zenn-user-upload/e0k0x0tcw3rvml4joj7j8zqtdssf)


### 以上です
数STEPで簡単にセットアップできました
間違っている箇所や不足ありましたら気軽にご指摘いただけると嬉しいです

ご覧いただきありがとうございました 