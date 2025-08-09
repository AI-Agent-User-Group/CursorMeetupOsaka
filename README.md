# CursorMeetupOsaka

## 概要

5月から世界各地で Cursor Meetup が開催されています。日本でも世界に負けず、Cursor ユーザが集まってお祭りをしましょう！今回は、企業単位で Cursor を導入したユーザ事例のLTとユーザによるLT、Cursorチームからの日本ユーザへの動画メッセージ紹介後、ユーザ同士の交流会を予定しています。

## 日程・場所
- *日程*: 2025/08/23（土）14:00 - 19:00
- *会場*: エムオーテックス株式会社
- *住所*: 〒532-0011 大阪府大阪市淀川区西中島５丁目１２−１２ エムオーテックス新大阪ビル
- *オンライン配信*: Youtube Live(配信環境確定したら募集開始します)

## 参加方法
[Connpassページ](https://aiau.connpass.com/event/363025/) から参加登録してください。

## 主催者情報

主催：[AIエージェントユーザー会（AIAU）](https://discord.gg/GatQE7wGvK)


## issueについて。

### Issues Translate Action の使い方

- **目的**: 英語以外の Issue／コメント本文を自動検出し、英訳を Bot が返信します
- **トリガー**: Issue の新規作成、Issue への新規コメント作成
- **参考**: [dromara/issues-translate-action](https://github.com/dromara/issues-translate-action)

#### 最小設定
`.github/workflows/issue-translator.yml` を作成（または既存を更新）します。

```yaml
name: issue-translator
on:
  issue_comment:
    types: [created]
  issues:
    types: [opened]

jobs:
  translate:
    runs-on: ubuntu-latest
    steps:
      - uses: usthe/issues-translate-action@v2.7
        with:
          IS_MODIFY_TITLE: false
          CUSTOM_BOT_NOTE: Bot detected non-English content and translated it automatically.
```

#### 独自 Bot を使う場合（任意）
1. Bot 用 GitHub アカウントで PAT を発行し、リポジトリ Secrets に `BOT_GITHUB_TOKEN` を追加
2. YAML を以下のように変更

```yaml
      - uses: usthe/issues-translate-action@v2.7
        with:
          BOT_GITHUB_TOKEN: ${{ secrets.BOT_GITHUB_TOKEN }}
          IS_MODIFY_TITLE: false
          CUSTOM_BOT_NOTE: Bot detected non-English content and translated it automatically.
```

#### 注意点
- タイトルも英訳したい場合は `IS_MODIFY_TITLE: true` にし、Bot に書き込み権限（コラボレーター招待）が必要
- 動作確認は日本語で Issue を作成し、Bot からの英訳返信を確認
- 詳細は公式 README を参照: [dromara/issues-translate-action](https://github.com/dromara/issues-translate-action)
