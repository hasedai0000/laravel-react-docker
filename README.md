# Laravel React Docker プロジェクト

## Docker のディレクトリ構成

```
project-root/
├── docker/           # Docker 関連ファイル
│   ├── nginx/        # Nginx の設定
│   ├── php/          # PHP の設定
│   └── mysql/        # MySQL の設定
├── backend/          # Laravel プロジェクト
├── frontend/         # React プロジェクト
├── docker-compose.yml # Docker Compose 設定
└── .env              # 環境変数
```

## Laravel プロジェクトの作成

### Docker イメージのビルド

```bash
docker-compose build
```

### Laravel プロジェクトを作成

```bash
# --rm　オプションをつけることで不要なコンテナを残さないようにしています。
docker-compose run --rm app composer create-project laravel/laravel "10.*"
```

### Laravel の環境設定

backend/.env ファイルの データベース接続情報を以下のように編集する。

```bash
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laravel_db
DB_USERNAME=laravel
DB_PASSWORD=secret
```

## React プロジェクトの作成

```bash
# --rm　オプションをつけることで不要なコンテナを残さないようにしています。
docker-compose run --rm node sh -c "npx create-react-app . --template typescript"
```

### React の設定

frontend/package.json に以下の行を追加する

```bash
"proxy": "http://web"
```

## CORS の設定

// TODO: Laravel10 での動作確認をしてからここを記載する
