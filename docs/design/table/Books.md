# テーブル定義書

## テーブル名

- 論理名：書籍
- 物理名：books
- 説明：書籍データを登録するテーブル

## テーブル詳細


| No  | PK  | FK  | UK  | カラム名         | 項目名     | データ型        | 桁数  | NOT NULL | デフォルト値 | 列制約            | 備考                            |
| --- | --- | --- | --- | ------------ | ------- | ----------- | --- | -------- | ------ | -------------- | ----------------------------- |
| 1   | ○   |     |     | id           | 書籍ID    | BIGINT      | -   | ○        |        | AUTO INCREMENT |                               |
| 2   |     | ○   |     | user_id      | ユーザーID  | BIGINT      | -   | ○        |        |                |                               |
| 3   |     |     |     | title        | タイトル    | VARCHAR     | 255 | ○        |        |                |                               |
| 4   |     |     |     | author       | 著者      | VARCHAR     | 255 | ○        |        |                |                               |
| 5   |     |     |     | book_type    | 書籍種別    | VARCHAR     | 20  | ○        |        |                | `paper`（紙）/ `ebook`（電子書籍）    |
| 6   |     |     |     | price        | 価格      | BIGINT      | -   |          |        |                | ISBN取得時に価格が存在しない場合を想定しNULLを許容 |
| 7   |     | ○   |     | category_id  | カテゴリーID | BIGINT      | -   | ○        |        |                |                               |
| 8   |     | ○   |     | publisher_id | 出版社ID   | BIGINT      | -   |          |        |                | 未設定時はNULL                     |
| 9   |     |     |     | isbn         | ISBN番号  | VARCHAR     | 13  |          |        |                |                               |
| 10  |     |     |     | created_at   | 作成日時    | TIMESTAMP   | -   | ○        | now()  |                |                               |
| 11  |     |     |     | updated_at   | 更新日時    | TIMESTAMP   | -   | ○        | now()  |                |                               |


## インデックス


| No  | インデックス名            | カラム   | ユニーク | 備考  |
| --- | ------------------ | ----- | ---- | --- |
|     |                    |       |      |     |


## 外部キー制約


| No  | カラム名         | 参照テーブル名    | 参照カラム名 | ON DELETE | ON UPDATE | 備考  |
| --- | ------------ | ---------- | ------ | --------- | --------- | --- |
| 1   | user_id      | users      | id     | CASCADE   | CASCADE   |     |
| 2   | category_id  | categories | id     | RESTRICT  | CASCADE   |     |
| 3   | publisher_id | publishers | id     | RESTRICT  | CASCADE   |     |


## ポリシー

### PostgreSQL RLS の定義

このプロジェクトでは使用しない（Laravel Policy で対応）

### Laravel Policy の定義


| 操作  | 管理者 | 利用ユーザー  | 条件                                                                 |
| --- | --- | ------- | ------------------------------------------------------------------ |
| 閲覧  | ○   | ○（自分のみ） | user_id 一致                                                         |
| 登録  | ○   | ○（自分のみ） | category_id / publisher_id は自分のuser_idと一致するもののみ指定可(FormRequestで制御) |
| 編集  | ○   | ○（自分のみ） | category_id / publisher_id は自分のuser_idと一致するもののみ指定可(FormRequestで制御) |
| 削除  | ○   | ○（自分のみ） | user_id 一致                                                         |


