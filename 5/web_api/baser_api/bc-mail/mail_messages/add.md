# メールメッセージの新規追加

新しいメールメッセージを作成します。

## 実行に必要な権限

```
システム管理者以上
```

## リクエスト
```
POST /baser/api/admin/bc-mail/mail_messages.json
```

### クエリパラメーター

| パラメーター名   | 型   | 必須  | 内容          |
|-----------|-----|-----|-------------|
| mail_content_id        | 数値  | ●   | メールコンテンツのID |

### パスパラメーター

| パラメーター名   | 型   | 必須  | 内容          |
|-----------|-----|-----|-------------|
| メールフィールドに連動してカラム        |     |     |             |



## レスポンス例

### レスポンスボディ

```json
{
  "mailMessage": {
    "mail_content_id": "1",
    "name_1": "安藤",
    "name_2": "富士",
    "created": "2023-04-04T14:10:47+09:00",
    "modified": "2023-04-04T14:10:47+09:00",
    "id": 3
  },
  "message": "コンテンツタイトル への受信データ NO「3」を追加しました。",
  "errors": [
  ]
}

```