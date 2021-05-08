# 作ったもの

こんな感じで、指定したリポジトリに積んだコミットやSlack上の発言を収集して、日報を自動で生成できます。
[![Image from Gyazo](https://i.gyazo.com/473f48c6123473dc1c29fd919be0cc9f.gif)](https://gyazo.com/473f48c6123473dc1c29fd919be0cc9f)

<https://github.com/MasatoraAtarashi/nippo>

# インストール方法

### Homebrew

    brew install masatoraatarashi/nippo/nippo

### go get

Install

    go get github.com/MasatoraAtarashi/nippo-generator

Update

    go get -u github.com/MasatoraAtarashi/nippo-generator

# 使い方

#### 1. SlackのAPIトークンを取得

[こちらの手順](https://qiita.com/ykhirao/items/3b19ee6a1458cfb4ba21)を参考にSlackのAPIトークンを取得してください。

User Token Scopesで`search:read`を指定してください。
[![Image from Gyazo](https://i.gyazo.com/102a89d9cc86631437cb42a108bfee28.png)](https://gyazo.com/102a89d9cc86631437cb42a108bfee28)

#### 2. 初期化する

    nippo init

上記のコマンドで$HOME/.nippo.yamlという設定ファイルが生成されます。

#### 3. 設定ファイルを編集する

生成された設定ファイルを編集してください。

$HOME/.nippo.yaml

```yaml
template:
    #日報に含めたい見出しを自由に設定してください。
    - 今日やったこと
    - 明日の予定
    - 所感・連絡事項
    - git
    - slack
git:
    heading: "git"
    repositories: 
        #コミットを取得したいディレクトリの絶対パスを記入してください。
        - "Users/MasatoraAtarashi/workspace/hogehoge"
        - "Users/MasatoraAtarashi/workspace/hogehoge2"
slack:
    token: "" #Slack APIトークンを記入してください。
    username: "" #Slackのユーザ名を記入してください。
```

#### 4. 日報を生成する

    nippot generate

出力例

```md
# 2021-05-06
## 今日やったこと


## 明日の予定


## 所感・連絡事項


## git
### hogehoge(3 commits)
 - 7ae0175 Add count option
 - 7335722 Add slack to default config
 - 3bcd230 Add slackname option

### hogehoge2(1 commits)
 - 3bcd230 Update README

## slack
 - `よろしくお願いいたします！` (random)
 - `こんにちは` (テスト)
```

# オプション

templateを編集すれば日報に含める内容を自由に変更できます。

# 使った技術

golangとcobraというライブラリを使って作りました。
<https://github.com/spf13/cobra>
