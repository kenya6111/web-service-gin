## 起動手順

#### 1. 環境変数を設定する

以下の環境変数を .env ファイルに設定し、プロジェクトのルートディレクトリに配置してください

```bash
# アプリ用（Go）
DB_USER
DB_PASSWORD
DB_HOST
DB_PORT
DB_NAME

# MYSQL用
MYSQL_ROOT_PASSWORD
MYSQL_ALLOW_EMPTY_PASSWORD
MYSQL_RANDOM_ROOT_PASSWORD
MYSQL_USER
MYSQL_PASSWORD
MYSQL_DATABASE
```

<br/>
ex

```bash
# アプリ用（Go）
DB_USER=mysql
DB_PASSWORD=mypassword
DB_HOST=db
DB_PORT=3306
DB_NAME=testdb


# MYSQL用
MYSQL_ROOT_PASSWORD=password
MYSQL_ALLOW_EMPTY_PASSWORD=false
MYSQL_RANDOM_ROOT_PASSWORD=false
MYSQL_USER=mysql
MYSQL_PASSWORD=mypassword
MYSQL_DATABASE=testdb
```

## 開発環境の場合

#### 2. イメージをビルド（開発用）

```bash
docker compose -f docker-compose-dev.yml build
```

#### 3. コンテナを起動（開発用）

```bash
docker compose -f docker-compose-dev.yml up -d
```

- `Air` による **ソースのライブリロード** が有効になります
- http://localhost:8080 にアクセスして動作を確認

---

## 本番環境の場合

#### 2. イメージをビルド

```bash
docker compose build
```

#### 3. コンテナを起動

```bash
docker compose up -d
```

- http://localhost:8080 にアクセスして動作を確認

---
