# Redmine
Redmine is a flexible project management web application written using Ruby on Rails framework. 
More details can be found in the doc directory or on the official website http://www.redmine.org

# RedmineをDockerで管理したもの
Redmineプロジェクトを拝借し、dockerで管理したもの 
Redmine GitHub  
https://github.com/redmine/redmine

## ver
Ubuntu 18.04	
ruby :2.6.5	
rails:5.2.4.2	
mysql:5.7	
docker-compose:3

## 初期設定
環境に応じて、環境変数を設定する  
環境変数を設定すると、設定した環境すべてにおいて、docker-composeコマンドが適応される  
composeファイルが設定されるので注意。 
direnvの導入をおすすめする
```bash
# 開発環境
$ export COMPOSE_FILE=docker-compose.develop.yml
# 本番環境
$ export COMPOSE_FILE=docker-compose.prod.yml
```

## 初期設定 開発環境
```bash
$ docker-compose build
$ docker-compose up
# or
#$ docker-compose up -d

# 最初だけ-------------------------------
# db作成(appはコンテナ名)
$ docker-compose run app rake db:create
# テーブル設定
$ docker-compose run app rake db:migrate
# ---------------------------------------
```

### DB永続化
docker-compose.yml
```yaml
# DBを永続化する場合は
#- db-store:/var/lib/mysql
#volumes:
  #db-store:
# 上記のコメントを解除する
```

### 起動
```bash
$ docker-compose up -d
```

## 初期設定 本番環境
```bash
$ docker-compose build
# 最初だけ-------------------------------
# テーブル設定
$ docker-compose run -e RAILS_ENV=production app bundle exec rake db:migrate
# ---------------------------------------
# $ 起動
$ docker-compose up -d
```


