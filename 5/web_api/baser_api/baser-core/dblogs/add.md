# コンテンツフォルダの追加

ログ情報を追加します。

## 実行に必要な権限
    
```
システム管理者（システム管理者の追加はユーパーユーザーのみ）
```

## リクエスト
```
POST /baser/api/baser-core/dblogs.json
```

### リクエストボディ

| パラメーター名             | 型   | 必須  | 内容                |
|---------------------|-----|-----|-------------------|
| message | 文字列	  | ●   | ログ内容              |
| user_id         | 数値 | ●   | 更新者              |

## レスポンス例

### レスポンスボディ

```json
{
  "message": "ログを追加しました。",
  "dblog": {
    "message": "ユーザー「佐藤」を追加しました。",
    "controller": "Dblogs",
    "action": "add",
    "user_id": 1,
    "created": "2023-03-27T17:04:22+09:00",
    "modified": "2023-03-27T17:04:22+09:00",
    "id": 4
  },
  "errors": null
}

```