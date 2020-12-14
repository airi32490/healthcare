# テーブル設計

## users テーブル

| Column          | Type    | Options                   |
| --------------- | ------- | ------------------------- |
| name            | string  | null: false               |
| email           | string  | null: false, unique: true |
| password_digest | string  | null: false               |
| checker_id      | integer | null: false               |

### Association

- has_many :conditions
- has_one :check

## healths テーブル

| Column           | Type       | Options                        |
| ---------------- | ---------- | ------------------------------ |
| body_temperature | float      | null: false                    |
| condition_id     | integer    | null: false                    |
| alcohol_level    | float      | null: false                    |
| user             | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_one :check

## checks テーブル

| Coulmn | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| health | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :health