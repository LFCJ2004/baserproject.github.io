# 独自の Web API を開発する



## プレフィックス認証
独自の Web APIを開発するには、[プレフィックス認証](../creator/plugin/development/functions/prefix_auth) を利用すると JWT認証と RESTful なルーティングを簡単に実装する事ができます。  
標準では、`Api` というプレフィックスが定義済です。[RESTを有効化](./index#REST の有効化) するだけで特別な設定をせずともプレフィックス認証が利用可能です。

## コントローラーを作成する
`Api` というプレフィックス認証を利用している場合は、 Controller 内に、`Api` フォルダを作成し、その中にコントローラーを作成します。

その際、次のURLでアクセスすることができます。
```
https://localhost/baser/api/plugin-name/controller_name/action_name.json
```

なお、プレフィックス認証を利用している場合、`BaserCore\Controller\Api\BcApiController` を継承することをおすすめします。`BcApiController` を継承することで、簡単に JWT認証を実装できます。

## 特定のアクションを認証対象から外す
特定のアクションを認証なしでアクセスできるようにするためには、 `initialize` メソッドで許可するメソッドを定義します。

```php
public function initialize(): void
{
    parent::initialize();
    $this->Authentication->allowUnauthenticated(['allowed_action_name']);
}
```

## データベースの処理と Exception の対応
コントローラーにおいて、データーベースの処理における Exception は次のようにコントロールします。

- PersistenceFailedException
  - ステータスコード：400
  - メッセージ：入力エラーです。内容を修正してください。
- RecordNotFoundException
  - ステータスコード：404
  - データが見つかりません。
- Throwable（それ以外は基本的にThrowableでキャッチします）
  - ステータスコード：500
  - メッセージ： `'データベース処理中にエラーが発生しました。' . $e->getMessage()`

## 認証が必要なAPIが利用可能かどうかを判定 
`BcApiController` を継承している場合、コントローラー内のいて、次のメソッドでログイン状態、かつ、 `USE_CORE_ADMIN_API` が有効になっているかを確認する事ができます。
```php
if(!$this->isAdminApiEnabled()) {
    throw new ForbiddenException()
}
```