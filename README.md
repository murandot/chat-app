# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# テーブル設計

## users テーブル

| Colimn             | Type   | Option      |
| ------------------ | ------ | ------------|
| neme               | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: fals  |

### Association

- has_many :room, through: :room_users
- has_many :rooms, through: :room_users
- has_many :messages

## rooms テーブル

| Colimn  | Type   | Option      |
| ------- | ------ | ------------|
| neme    | string | null: false |

### Association

- has_many :room_users
- has_many :users, through: :room_users
- has_many :messages

## room_users テーブル

| Colimn | Type      | Option                         |
| ------ | --------- | -------------------------------|
| user   | reference | null: false, foreign_key: true |
| room   | reference | null: false, foreign_key: true |

### Association

- belong_to :room
- belong_to :user

## messages テーブル

| Colimn  | Type      | Option                        |
| ------- | --------- | ------------------------------|
| content | string    | null: false, foreign_key:true |
| user    | reference | null: false, foreign_key:true |
| room    | reference | null: false, foreign_key:true |

- belong_to :room
- belong_to :user