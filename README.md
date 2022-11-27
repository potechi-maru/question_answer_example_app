# question and answer example app

# テーブル設計

* user
  * name:string: 
  * email:string
  * password_digest:string
  * remember_digest:string
  * image_name:string
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
User has_many :question, :answer  
Question belongs :user  
        　hasmany :answer  
Answer belongs :user  