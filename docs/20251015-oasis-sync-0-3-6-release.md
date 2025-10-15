---
title: 【リリースノート】Oasis Sync v0.3.6 - Qiita連携の安全性向上とドキュメント更新
post_status: publish
post_excerpt: Oasis Sync v0.3.6をリリースしました。本バージョンではQiitaへの新規記事投稿時にIDを自動採番するよう修正し、意図しない記事の上書きを防止。v0.3.4のリリースノート記事も追加しています。
featured_image: https://raw.githubusercontent.com/Sunwood-ai-labs/oasis-sync/main/generated-images/release-v0.3.6-20251015_131339/imagen-4-ultra_2025-10-15T13-14-42-068Z_A_mesmerizing_and_vivid_digital_painting_featuring_1.png
taxonomy:
  category:
  - release-note
  - github-actions
  - automation
  post_tag:
  - OasisSync
  - Qiita
  - GitHubActions
  - Automation
  - ReleaseNote
custom_fields:
  lead: Oasis Sync v0.3.6では、Qiita連携の安全性を向上させました。新規投稿時のID自動採番により、既存記事を誤って上書きするリスクを解消。あわせてドキュメントの更新も行っています。
---

## はじめに
Oasis Sync v0.3.6をリリースしました。このバージョンでは、Qiitaへの記事投稿ワークフローを改善し、より安全に新規投稿が行えるように修正しました。また、過去のリリースに関するドキュメントの追加も行っています。

## 主な変更点
本リリースにおける主な変更点は以下の通りです。

- **Qiita連携の安全性向上**: 新規記事をQiitaに投稿する際、記事IDを自動採番するようワークフローを修正し、既存記事を誤って上書きするリスクを解消しました。
- **ドキュメント追加**: v0.3.4のリリースノート記事を各連携プラットフォーム（Oasis, Qiita, WordPress, Zenn）向けに追加しました。

## 技術的な詳細
### バグ修正
#### Qiita投稿時のID自動採番への対応
これまで、Oasis SyncからQiitaへ新しい記事を投稿する際、フロントマターに `id` が設定されていると、そのIDを持つ既存の記事を意図せず上書きしてしまう可能性がありました。

今回の修正（`5ae8cba`）では、新規投稿と判断された場合にフロントマターの `id` を強制的に `null` に設定する処理をワークフローに追加しました。

```yaml
# 修正前 (上書きの可能性があった)
qiita:
  id: "some-preset-id-..."
```

```yaml
# 修正後 (新規投稿時)
qiita:
  id: null
```

これにより、Qiita APIが記事IDを自動で採番するため、既存記事との競合を防ぎ、安全に新規投稿を行えるようになります。

### ドキュメント
リポジトリの情報を最新に保つため、v0.3.4のリリースノート記事を各プラットフォーム向けに追加しました（`6baa6a3`）。これにより、プロジェクトの変更履歴が追いやすくなります。

## まとめ
Oasis Sync v0.3.6では、特にQiita連携の安定性向上に焦点を当てた改善を行いました。

| 変更カテゴリ | 内容 |
| :--- | :--- |
| **バグ修正** | Qiitaへの新規投稿時に`id`を`null`に設定し、IDの自動採番を有効化 |
| **ドキュメント** | v0.3.4のリリースノート記事を各プラットフォーム向けに追加 |

この改善により、コンテンツ管理者はより安心して記事投稿の自動化ワークフローを利用できます。

---
### 📚 参考リンク
- **GitHubリポジトリ**: [Sunwood-ai-labs/oasis-sync](https://github.com/Sunwood-ai-labs/oasis-sync)
- **リリースページ**: [v0.3.6 Release](https://github.com/Sunwood-ai-labs/oasis-sync/releases/tag/v0.3.6)
- **変更差分**: [Compare v0.3.4...v0.3.6](https://github.com/Sunwood-ai-labs/oasis-sync/compare/v0.3.4...v0.3.6)
