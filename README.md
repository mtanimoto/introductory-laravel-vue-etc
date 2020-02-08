# Vue + Vue Router + Vuex + Laravelで写真共有アプリを作ろう

https://www.hypertextcandy.com/vue-laravel-tutorial-introduction

# 環境

- Windows10 Pro
- WSL
- docker
- docker-compose
- node
- npm

# 開発環境を整える

コマンドを打つ
```
docker volume create --name test_db
git clone https://github.com/mtanimoto/introductory-laravel-vue-etc.git vuesplash
docker-compose up -d
docker-compose exec vuesplash_web composer install
docker-compose exec vuesplash_web npm install
docker-compose exec vuesplash_web php artisan key:generate
docker-compose exec vuesplash_web php artisan migrate
```

`.env`を作成して、データベース接続情報を設定する
```
DB_CONNECTION=pgsql
DB_HOST=vuesplash_database
DB_PORT=5432
DB_DATABASE=postgres
DB_USERNAME=postgres
DB_PASSWORD=secret
```

`js`ファイルの更新を監視し、更新されたら自動ビルドするようにする
```
docker-compose exec vuesplash_web npm run watch
```

ローカルサーバを立ち上げる
```
docker-compose exec vuesplash_web php artisan serve --host 0.0.0.0 --port 8081
```

# 起動確認

`http://localhost:8081`にアクセスする