# question and answer example app

# テーブル設計

* user
  * name:string: 
  * email:string
  * password_digest:string
  * remember_digest:string
  * created_at:datetime
  * updated_at:datetime
  * admin:boolean
  * 
* question
  * title:string
  * content:text
  * solved:boolean
  * user_id:integer
  * created_at:datetime
  * updated_at:datetime
* answer
  * content:text
  * user_id:integer
  * question_id:integer
  * created_at:datetime
  * updated_at:datetime  
  
## メモ  
User  
    has_many :questions, :answers
    has_one_attached :image
     (ActiveStorageを使用)
Question  
    belongs :users  
    hasmany :answers  
Answer  
    belongs :users   