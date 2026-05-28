# テーブル定義書

## テーブル名

- 論理名：ユーザー
- 物理名：users
- 説明：利用ユーザーを登録するテーブル

## テーブル詳細

| No | PK | FK | UK | カラム名 | 項目名 | データ型 | 桁数 | NOT NULL | デフォルト値 | 列制約 | 備考 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|1|○|||id|ユーザーID|BIGINT|-|○||AUTO INCREMENT||
|2|||○|google_sub|GoogleユーザーID|TEXT|-|○|||Google OAuthで取得したsub情報|
|3||||username|ユーザー名|VARCHAR|255|○|||Google OAuthで取得したname情報|
|4||||email|ユーザーメールアドレス|VARCHAR|255|○|||Google OAuthで取得したemail情報|
|5||||picture|アバターURL|TEXT|-||||Google OAuthで取得したpicture情報|
|6||||last_login_at|最終ログイン日時|TIMESTAMP|-||||未ログイン時はNULL|
|7||||account_lock|アカウントロック|BOOLEAN|-|○|false|||
|8||||created_at|作成日時|TIMESTAMP|-|○|now()|||
|9||||updated_at|更新日時|TIMESTAMP|-|○|now()|||

## インデックス

| No | インデックス名 | カラム | ユニーク | 備考 |
|:---:|:---:|:---:|:---:|:---:|
|1|users_google_sub_unique|google_sub|○|ログイン時の検索キー|

## 外部キー制約

| No | カラム名 | 参照テーブル名 | 参照カラム名 | ON DELETE | ON UPDATE | 備考 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
||||||||

## ポリシー

### PostgreSQL RLS の定義

このプロジェクトでは使用しない（Laravel Policy で対応）

### Laravel Policy の定義

| 操作 | 管理者 | 利用ユーザー | 条件 |
|:---:|:---:|:---:|:---:|
|閲覧|○|○（自分のみ）|id 一致|
|登録|○|×|管理者のみ実行可能|
|編集|○|○（自分のみ）|id 一致|
|削除|○|×|管理者のみ実行可能|
