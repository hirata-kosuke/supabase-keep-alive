# Supabase Keep Alive

Supabase無料プランのプロジェクト一時停止を防止するGitHub Actionsワークフロー。

## 仕組み

- 5日ごとにSupabase REST APIへ軽量リクエストを送信
- 7日間の無活動による自動停止を防止

## 対象プロジェクト

| プロジェクト | リポジトリ |
|---|---|
| rokomo-check-app | [hirata-kosuke/rokomo-check-app](https://github.com/hirata-kosuke/rokomo-check-app) |
| stroke-risk-check | [hirata-kosuke/stroke-risk-check](https://github.com/hirata-kosuke/stroke-risk-check) |

## 手動実行

Actions タブ → "Supabase Keep Alive" → "Run workflow" で即時実行可能。

## プロジェクト追加方法

1. GitHub Secrets に `{NAME}_SUPABASE_URL` と `{NAME}_SUPABASE_ANON_KEY` を追加
2. `.github/workflows/keep-alive.yml` にpingステップを追加
