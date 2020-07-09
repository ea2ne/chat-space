# DB設計

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false|
|name|string|null: false|
|mail|string|null: false|
|password|string|null: false|
|pass_check|string|null: false|

### Association
- has_many :groups, through:  :users_groups 
- has_many :messages
- has_many :users_groups 

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false|
|text|string|  |
|image|image|  |
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false|
|name|string|null: false|

### Association
- has_many :messages, through:  :users_groups 
- has_many :users_groups
- 

## users_groupsテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user