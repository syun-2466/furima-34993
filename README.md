# テーブル設計

## users テーブル

| Column             | Type     | Options                  |
| ------------------ | -------- | ------------------------ |
| email              | string   | null: false unique: true |
| encrypted_password | string   | null: false              |
| nickname           | string   | null: false              |
| last-name          | string   | null: false              |
| first-name         | string   | null: false              |
| last-name-k        | string   | null: false              |
| first-name-k       | string   | null: false              |
| date-of-birth      | datetime | null: false              |

### Association

-has_many :items
-has_many :purchases
-has_many :comments

## items テーブル

| Column              | Type       | Options                       |
| ------------------- | ---------- | ----------------------------- |
| image               | text       | null: false                   |
| product-name        | string     | null: false                   |
| product-description | text       | null: false                   |
| product-category    | string     | null: false                   |
| product-condition   | string     | null: false                   |
| delivery-load       | string     | null: false                   |
| delivery-area       | string     | null: false                   |
| delivery-days       | string     | null: false                   |
| selling-price       | integer    | null: false                   |
| user                | references | null: false foreign_key: true |

### Association

-belongs_to :users
-has_many :comments
-has_one :purchases

## purchases テーブル

| Column           | Type       | Options                       |
| ---------------- | ---------- | ----------------------------- |
| post-code        | integer    | null: false                   |
| prefectures      | string     | null: false                   |
| municipalities   | string     | null: false                   |
| address          | string     | null: false                   |
| building-name    | string     |                               |
| telephone-number | integer    | null: false                   |
| user             | references | null: false foreign_key: true |
| item             | references | null: false foreign_key: true |

### Association

-belongs_to :users
-has_one :items

## comments テーブル

| Column  | Type       | Options                       |
| ------- | ---------- | ----------------------------- |
| content | text       | null:false                    |
| items   | references | null: false foreign_key: true |
| user    | references | null: false foreign_key: true |

### Association

-belongs_to :user
-belongs_to :items
