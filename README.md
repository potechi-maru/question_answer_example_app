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

# エンドポイント・コントローラ設計

| やりたいこと | HTTPメソッド | エンドポイント | コントローラ#アクション |
| --- | --- | --- | --- |
| ユーザー登録画面を表示する | GET | /users/new | users#new |
| ユーザー登録をする | POST | /users | users#create |
| ログイン画面を表示する | GET | /login | users#login |
| ログインする | POST | /login | sessions#new |
| ログアウトする | DELETE | /logout | sessions#destroy |
| 質問一覧を表示する（全て） | GET | /questions | questions#index |
| 質問一覧を表示する（未解決） | GET | /questions/unsolved | questions#unsolved |
| 質問一覧を表示する（解決済み） | GET | /questions/solved | questions#solved |
| 質問投稿ページを表示する | GET | /questions/new | questions#new |
| 質問投稿をする | POST | /questions | questions#create |
| 質問詳細を表示する | GET | /questions/:id | questions#show |
| 質問編集ページを表示する | GET | /questions/edit | questions#edit |
| 質問を削除する | DELETE | /questions/:id | questions#destroy |
| 回答する | POST | /questions/:id/answers | answers#new |
| ユーザー一覧を表示する | GET | /users | users#index |
| 管理画面用のログインページを表示する | GET | /admin/login | admin/sessions#new |
| 管理画面用のログインをする | POST | /admin/login | admin/sessions#create |
| （管理画面）質問一覧ページを表示する | GET | /admin/questions |admin/questions#index |
| （管理画面）質問を削除する | DELETE | /admin/questions/:id | admin/questions#destroy |
| （管理画面）ユーザー一覧ページを表示する | GET | /admin/users | admin/users#index |
| （管理画面）ユーザーを削除する | DELETE | /admin/users/:id | admin/users#destroy |
