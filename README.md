# README

## envファイルの編集
`.env.sample` をベースに`.env`に値を設定する

## Railsプロジェクト作成

``` sh
dc run web rails new . -f -d mysql -BT --no-deps
```

## DBの接続先を確認する

`config/database.yml` を修正する

``` yml
default: &default
  adapter: mysql2
  encoding: utf8
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: root
  password:  ${MYSQL_ROOT_PASSWORD}
  host: db # docker-compose.ymlに書いたdatabaseのサービス名
```

## dockerをbuild、起動

``` sh
docker-compose build
docker-compose up -d
```

## RailsのDB作成

``` sh
docker-compose run web rake db:create
```

## Rails実行確認

`localhost:3000'
