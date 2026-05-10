# テーブル定義書

## テーブル名

- 論理名：管理者
- 物理名：admins
- 説明：管理者ユーザーを登録するテーブル

## テーブル詳細

| No | PK | FK | UK | カラム名 | 項目名 | データ型 | 桁数 | NOT NULL | デフォルト値 | 列制約 | 備考 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|1|○|||id|管理者ID|BIGINT|-|○||AUTO INCREMENT||
|2|||○|email|管理者メールアドレス|VARCHAR|255|○||||
|3||||username|管理者ユーザー名|VARCHAR|255|○||||
|4||||password|管理者パスワード|VARCHAR|255|○|||ハッシュ化済み|
|5||||google2fa_secret|2FA秘密鍵|VARCHAR|255||||未設定時はNULL|
|6||○||permission_id|管理区分ID|INTEGER|-|○||||
|7||||created_at|作成日時|TIMESTAMP|-|○|now()|||
|8||||updated_at|更新日時|TIMESTAMP|-|○|now()|||

## インデックス

| No | インデックス名 | カラム | ユニーク | 備考 |
|:---:|:---:|:---:|:---:|:---:|
|1|admins_email_unique|email|○||

## 外部キー制約

| No | カラム名 | 参照テーブル名 | 参照カラム名 | ON DELETE | ON UPDATE | 備考 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|1|permission_id|permissions|id|RESTRICT|CASCADE||

## ポリシー

### PostgreSQL RLS の定義

このプロジェクトでは使用しない（Laravel Policy で対応）

### Laravel Policy の定義

| 操作 | 管理者 | 利用ユーザー | 条件 |
|:---:|:---:|:---:|:---:|
|閲覧|○（自分のみ）|×|管理者のみアクセス可能|
|編集|○（自分のみ）|×|管理者のみアクセス可能|
|削除|×|×|システム運用で直接DB操作を想定|



