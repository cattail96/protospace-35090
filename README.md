# テーブル設計

## usersテーブル

| Column      | Type   | Options     |
| ----------- | ------ | ----------- |
| email       | string | null: false |
| password    | string | null: false |
| name        | string | null: false |
| profile     | text   | null: false |
| occupation  | text   | null: false |
| position    | text   | null: false |

### Association

- has_many :prototypes
- has_many :comments

## prototypesテーブル

| Column      | Type            | Options                       |
| ----------- | -------------- | ------------------------------ |
| title       | string         | null: false, foreign_key: true |
| catch_copy  | text           | null: false, foreign_key: true |
| concept     | text           | null: false, foreign_key: true |
| image       | ActiveStorage  | null: false, foreign_key: true |
| user        | reference      | null: false, foreign_key: true |

### Association

- belongs_to :users
- has_many :comments

## commentsテーブル

| Column     | Type       | Options                        |
| ---------- | ---------- | ------------------------------ |
| text       | text       | null: false, foreign_key: true |
| user       | reference  | null: false, foreign_key: true |
| prototype  | reference  | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :prototypes