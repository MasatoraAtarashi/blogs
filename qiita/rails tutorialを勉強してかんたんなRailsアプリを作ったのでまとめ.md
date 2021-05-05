# はじめに
タイトルの通り

# 作ったもの
[ten-books](https://ten-books.herokuapp.com/)(自分の人生に強い影響を与えた10冊の本をピックアップして登録・公開することのできるアプリケーションです。様々な人の人生を変えた書籍を閲覧し学ぶことができます。)
github: (https://github.com/MasatoraAtarashi/ten-books)
<img width="1271" alt="スクリーンショット 2019-08-11 4.07.57.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/455240/181e6452-9b99-7fef-1cee-f927f262cbe2.png">

## 機能
データベース(mysql)
CSSフレームワーク(materialize)
デプロイ(heroku)
テスト(Rspec,minitest)
ユーザー有効化とパスワードリセット(ActionMailer)
ページネーション(kaminari)
ユーザー登録機能
認証機能
SNSによるログイン機能(omniauth-facebook)
書籍検索機能(google books api)
書籍登録機能
書籍にコメントをつける機能
ユーザープロフィール画像変更機能(CarrierWave, AWS s3)
本棚をお気に入りに登録する機能(Ajax)
本棚にコメントをつける機能
登録されている書籍のランキング機能
本棚のいいね数によるランキング機能
ユーザー検索機能(Searchcop)
API
## 作成期間
2週間

# 勉強したこと
progateの[ruby]()、[ruby on rails]()を２周
sql,git
(ドットインストールのruby)
[rails tutorial]()２周
Everyday rails

# 反省点
-  テーブル設計をちゃんとする。ER図を書く。事前に
-  認証はdeviseを使う
-  bootstrapでやる
-  AWSとかに？
- form_withす
-  いろんな技術の理解が乏しい
-  ゴミコードがおそらく多い。
-  はじめからdockerで環境つくってcircleciもつかってデプロイ
-  cdnで配信

# 終わりに
これをポートフォリオとしてインターン等探してみようと思います。
