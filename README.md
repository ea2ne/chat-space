# DB設計

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false|
|user_name|string|null: false|
|mail|string|null: false|
|password|string|null: false|
|pass-check|string|null: false|

### Association
- has_many :group-name, through: users_group 
- has_many :message
- has_many :image

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false|
|message|string|null: false, foreign_key: true|
|users_id|integer|null: false, foreign_key: true|
|create-date|date|  |

### Association
- belongs_to :user

## groupテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false|
|group_name|string|null: false|

### Association
- has_many :message, through: users_group 

## imagesテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false|
|image|image|null: false|
|users_id|integer|null: false, foreign_key: true|

### Association 
- belongs_to :user

## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user