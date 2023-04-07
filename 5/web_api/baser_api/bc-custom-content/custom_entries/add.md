# カスタムエントリーの新規追加

新しいカスタムエントリーを追加します。

## 実行に必要な権限

```
システム管理者以上
```

## リクエスト
```
POST /baser/api/admin/bc-custom-content/custom_entries/add/{customTableId}.json
```

### パスパラメーター

| パラメーター名   | 型   | 必須  | 内容         |
|-----------|-----|-----|------------|
| customTableId            | 数値 |●  | カスタムテーブルID |

### リクエストボディ

| パラメーター名   | 型   | 必須  | 内容                |
|-----------|-----|-----|-------------------|
| custom_table_id   | 数値 |  ●    | カスタムテーブルID              |
| parent_id   | 数値 |  ●    | 親ID              |
| name   | 文字列 |   ●  | カスタムテーブル名              |
| title   | 数値 |   ●  | タイトル              |
| level   | 数値 |     | 階層              |
| lft   | 数値 |     | 右位置              |
| rght   | 数値 |     | 左位置              |
| creator_id   | 数値 |     | 作成者ID              |
| status   | 真偽値 |     | 公開状態              |


## レスポンス例

### レスポンスボディ

```json
{
  "message": "フィールド「石油」を追加しました。",
  "entry": {
    "title": "石油",
    "name": "石油",
    "custom_table_id": 5,
    "created": "2023-04-06T13:00:12+09:00",
    "modified": "2023-04-06T13:00:12+09:00",
    "lft": 1,
    "rght": 2,
    "level": 0,
    "id": 3
  },
  "errors": null
}

```