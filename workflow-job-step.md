# workflow,job,step の使い分けの基準を考える

author
:   Kazuhiro NISHIYAMA

content-source
:   GitHub Actions Meetup Osaka #1

date
:   2019/11/26

allotted-time
:   10m

theme
:   lightning-simple

# 自己紹介

- 西山 和広
- Ruby のコミッター
- twitter, github など: @znz
- 株式会社Ruby開発 www.ruby-dev.jp

# workflow,job,step

- workflow
  - 1 YAML ファイル
- job
  - ランナー (コンテナなどの仮想環境)
- step
  - プログラム

# workflow の分割

- トリガーが違うなら分割必須
- pull request だけ
- tag push だけ (リリースアクション)
- issue に反応など

# workflow の分割?

- CI 環境の違い
- ubuntu と macos と windows で CI
- 次の job で分割でも構わない

# job の分割

- 実行環境 (`runs-on`) が違うときは必須
- `matrix` で一部の違いはまとめられる
- `needs` で依存関係
- `if` で ci skip

# step の分割

- 分割必須
  - `uses:` を使う
  - `shell:` が違う
- よくあるその他の分割理由
  - ログを分ける

# まとめ

- workflow: トリガー
- job: 実行環境
- step: `uses` やシェル
