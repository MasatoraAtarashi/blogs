# 背景
Dockerを利用して作成したRailsアプリ(v5.2.4)を本番環境にデプロイする際、アセットをプリコンパイルしようとしたところ、以下のエラーがでて実行できなかった。

```sh
$docker-compose run web bundle exec rake assets:precompile RAILS_ENV=production
```
```sh
Starting excite-map_db_1 ... done
Yarn executable was not detected in the system.
Download Yarn at https://yarnpkg.com/en/docs/instal
```

# 解消方法
Dockerfileに以下を追加

```Dockerfile
RUN curl https://deb.nodesource.com/setup_12.x | bash
RUN curl https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

RUN apt-get update && apt-get install -y nodejs yarn postgresql-client
```

# 参考
https://github.com/yarnpkg/yarn/issues/7329
