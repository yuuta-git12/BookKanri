# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## プロジェクト概要

個人が所有する書籍（紙の本・電子書籍）をオンラインで一元管理するWebアプリケーション。ISBNを入力すると外部APIから書籍情報を自動取得して登録できる。個人開発・ポートフォリオ目的のプロジェクト。

## 現在のフェーズ

設計フェーズ。ソースコードはまだ存在せず、`docs/design/` に要件定義書・フロー図が格納されている。

## 決定済み技術スタック

| レイヤー | 技術 |
|---|---|
| フロントエンド | React（Inertia.js 経由で Laravel と連携） |
| バックエンド | Laravel + Inertia.js |
| データベース | PostgreSQL |
| 認証 | 利用ユーザー: Google OAuth / 管理者: メールアドレス＋パスワード + 2要素認証（google2fa） |
| スタイル | Tailwind CSS |
| 外部API | openBD（日本書籍）/ Google Books API（補完） |
| ホスティング | Railway（Laravel + PostgreSQL 一体構成） |

Inertia.js を使用するためフロントとバックは分離しない一体構成。Vercel 等への別途フロントデプロイは不要。

## ディレクトリ構成

```
BookKanri/
├── docs/
│   ├── design/          # 設計書（要件定義書・フロー図など）
│   │   └── image/       # drawio・SVG形式のフロー図
│   ├── manual/          # 実装マニュアル（実装後に追加予定）
│   └── Reference/       # 参考にした技術記事のリンク集
├── diary/               # 日報（.gitignore 対象・コミット不可）
└── src/                 # ソースコード（実装フェーズ以降）
```

## ドキュメント管理ルール

- 設計書は `docs/design/` に Markdown で管理する
- フロー図は draw.io（`.drawio`）で作成し SVG でエクスポートして同ディレクトリに保存する
- `diary/` は `.gitignore` に含まれており Git 管理対象外。ファイル名は `YYYYMMDD.md` 形式
- 参考記事は `docs/Reference/参考にした技術記事.md` に追記する

## ロールと権限

- **管理者**：全ユーザーのアカウント管理 + 全ユーザーの書籍データの閲覧・編集・削除
- **利用ユーザー**：自分の書籍データのみ登録・閲覧・編集・削除可能（他ユーザーのデータにはアクセス不可）
