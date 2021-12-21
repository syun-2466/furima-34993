# テーブル設計

## users テーブル

| Column             | Type   | Options                  |
| ------------------ | ------ | ------------------------ |
| email              | string | null: false unique: true |
| encrypted_password | string | null: false              |
| nickname           | string | null: false              |
| last_name          | string | null: false              |
| first_name         | string | null: false              |
| last_name_k        | string | null: false              |
| first_name_k       | string | null: false              |
| date_of_birth      | date   | null: false              |

### Association

-has_many :items
-has_many :histories

## items テーブル

| Column               | Type       | Options                       |
| -------------------- | ---------- | ----------------------------- |
| product_name         | string     | null: false                   |
| product_description  | text       | null: false                   |
| product_category_id  | integer    | null: false                   |
| product_condition_id | integer    | null: false                   |
| delivery_load_id     | integer    | null: false                   |
| prefectures_id       | integer    | null: false                   |
| delivery_days_id     | integer    | null: false                   |
| selling_price        | integer    | null: false                   |
| user                 | references | null: false foreign_key: true |

### Association

-belongs_to :user
-has_one :history

## sends テーブル

| Column           | Type       | Options                       |
| ---------------- | ---------- | ----------------------------- |
| post_code        | string     | null: false                   |
| prefectures_id   | integer    | null: false                   |
| municipalities   | string     | null: false                   |
| address          | string     | null: false                   |
| building_name    | string     |                               |
| telephone_number | string     | null: false                   |
| history          | references | null: false foreign_key: true |

### Association

-belongs_to :history

## histories テーブル

| Column | Type       | Options                       |
| ------ | ---------- | ----------------------------- |
| item   | references | null: false foreign_key: true |
| user   | references | null: false foreign_key: true |

### Association

-belongs_to :user
-belongs_to :item
-has_one :send
