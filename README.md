# テーブル設計

## users テーブル

| Column           | Type   | Options     |
| -----------------| ------ | ----------- |
| NickName         | string | null: false |
| email            | string | null: false |
| password         | string | null: false |
| family_name      | string | null: false |
| first_name       | string | null: false |
| family_name_kana | string | null: false |
| family_name_kama | string | null: false |
| birthday         | date   | null: false |
### Association

- has_many :customer
- has_many :item
- has_many :comment

## items テーブル

| Column           | Type   | Options     |
| -----------------| ------ | ----------- |
| image            |  | null: false |
| item__name       | string | null: false |
| memo             | text   | null: false |
| category_id         | string | null: false |
| item_status_id      | string | null: false |
発送料| ship_method_id      | string | null: false |
発送元地域| ship_city_id        | string | null: false |
発送までの日数| ship_date_id        | string | null: false |
価格| amount_sold      | integer| null: false |
| user_id          | references| null: false,foreign_key: true |
### Association
belongs_to :user
has_one :customer
has_many :comment


### customersテーブル
| Column           | Type   | Options     |
| -----------------| ------ | ----------- |
| user_id          | references|  null: false,foreign_key: true  |
| item_id          | references| null: false,foreign_key: true |

### Association
belogs_to :user
belogs_to :item
has_one :address

## commentsテーブル
| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| text    | string     | null: false |
| user_id | references | null: false, foreign_key: true |
| item_id | references | null: false, foreign_key: true |

### Association

belongs_to :item
 belongs_to :user

## addresses テーブル

| Column         | Type       | Options                        |
| -------------- | ---------- | ------------------------------ |
| post-code      | string     | null: false |
| ship_city      | string     | null: false |
| ship_address   | string     | null: false |          
| ship_to_address| string     | null: false |  
| building_name  | string     | 
| customer_id    | references | null: false, foreign_key: true |

### Association

belongs_to :customer