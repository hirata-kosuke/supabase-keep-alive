# Supabase Keep Alive

Supabase無料プランのプロジェクト一時停止（pause）を防止するGitHub Actionsワークフロー。

## 仕組み

- **3日ごと**にSupabaseプロジェクトへ3種類のリクエストを送信
  - REST API ping（`/rest/v1/`）
  - DBクエリ実行（`/rest/v1/rpc/now`）
  - Auth ヘルスチェック（`/auth/v1/health`）
- 7日間の無活動による自動停止を確実に防止

## 対象プロジェクト

| プロジェクト | リポジトリ |
|---|---|
| rokomo-check-app | [hirata-kosuke/rokomo-check-app](https://github.com/hirata-kosuke/rokomo-check-app) |
| stroke-risk-check | [hirata-kosuke/stroke-risk-check](https://github.com/hirata-kosuke/stroke-risk-check) |

## 手動実行

Actions タブ → "Supabase Keep Alive" → "Run workflow" で即時実行可能。

CLI: `gh workflow run keep-alive.yml --repo hirata-kosuke/supabase-keep-alive`

## プロジェクト追加方法

1. GitHub Secrets に `{NAME}_SUPABASE_URL` と `{NAME}_SUPABASE_ANON_KEY` を追加
2. `.github/workflows/keep-alive.yml` にpingステップを追加
3. README.md の対象プロジェクト一覧を更新
