# テーブル設計

## users テーブル

| Column             | Type   | Options                  |
| ------------------ | ------ | ------------------------ |
| email              | string | null: false unique: true |
| encrypted_password | string | null: false              |
| nickname           | string | null: false              |
| last-name          | string | null: false              |
| first-name         | string | null: false              |
| last-name-k        | string | null: false              |
| first-name-k       | string | null: false              |
| date-of-birth      | string | null: false              |

### Association

-has_many :item
-has_many :send
-has_many :history
-has_many :comment

## items テーブル

| Column               | Type       | Options                       |
| -------------------- | ---------- | ----------------------------- |
| product-name         | string     | null: false                   |
| product-description  | text       | null: false                   |
| product-category_id  | integer    | null: false                   |
| product-condition_id | integer    | null: false                   |
| delivery-load_id     | integer    | null: false                   |
| prefectures_id       | integer    | null: false                   |
| delivery-days_id     | integer    | null: false                   |
| selling-price        | integer    | null: false                   |
| user                 | references | null: false foreign_key: true |

### Association

-belongs_to :user
-has_many :comment
-has_one :send
-has_one :history

## sends テーブル

| Column           | Type       | Options                       |
| ---------------- | ---------- | ----------------------------- |
| post-code_id     | integer    | null: false                   |
| prefectures_id   | integer    | null: false                   |
| municipalities   | string     | null: false                   |
| address          | string     | null: false                   |
| building-name    | string     |                               |
| telephone-number | string     | null: false                   |
| user             | references | null: false foreign_key: true |
| item             | references | null: false foreign_key: true |

### Association

-belongs_to :user
-has_one :item

## histories テーブル

| Column | Type       | Options                       |
| ------ | ---------- | ----------------------------- |
| item   | references | null: false foreign_key: true |
| user   | references | null: false foreign_key: true |

### Association

-belongs_to :user
-has_one :history

## comments テーブル

| Column  | Type       | Options                       |
| ------- | ---------- | ----------------------------- |
| content | text       | null:false                    |
| items   | references | null: false foreign_key: true |
| user    | references | null: false foreign_key: true |

### Association

-belongs_to :user
-belongs_to :item
