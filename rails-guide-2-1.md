https://railsguides.jp/active_record_basics.html

# 1 Active Recordについて
- Active Record
  - MVCのMに相当する
  - ORMフレームワーク
  - 『Patterns of Enterprise Application Architecture』という書籍で記述されたパターンの一つ

# 2 Active RecordにおけるCoC(Convention over Configuration)
- モデル名やテーブル名には命名規則がある
  - それに従えば、自動で色々メソッドを生やしたりしてくれる

- 特定のカラム名は予約されている
  - STIで使うtype
  - ポリモーフィックで使う関連付け名_type等


# 3 Active Recordのモデルを作成する
- Active RecordモデルはApplicationRecordクラスを継承すれば良い

# 4 命名ルールを上書きする
- Active Recordは基本的にモデル名から自動でテーブル名を推測するが、もちろん明示的に指定することもできる
  - ActiveRecord::Base.table_name=

# 5 CRUD: データの読み書き
- Active RecordはCRUD操作に必要なメソッドを自動で生やしてくれる

# 6 バリデーション（検証）
- モデルがデータベースに書き込まれる前にモデルの状態を検証できる。
  - 属性が空じゃないか
  - 属性が一意か
  - 特定のフォーマットに沿っているか等

# 7 コールバック
- よくわからない
→ [Active Recordコールバックガイド[](https://railsguides.jp/active_record_callbacks.html)](https://railsguides.jp/active_record_callbacks.html)

# 8 マイグレーション
- RailsではDBスキーマをマイグレーションファイルで管理している
  - 下のコマンドを実行するとDBにスキーマが反映される
> bin/rails db:migrate


- RailsはDBへのコミット履歴を管理しているためロールバックもできる
  - ロールバックのコマンド
> bin/rails db:rollback

# 感想・メモ
- コールバック以外はだいたい知ってた
- destroy_byとかdestroy_allは知らなかった
- update_allも初めて知った
  - 結構知らんやん

- Active RecordはRails最大の利点らしいのでじっくり読む

# わかんないとこ
- コールバック
- bin/railsのbinってなんだ？