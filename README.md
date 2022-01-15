# fluentd-sample

- アプリケーションログを受け取ってホストに出力
- ホストに出力したログからFilterで抜き出して別のログに出力
  - ホスト出力にしてるけどmatch.typeで出力方法は指定可能

## 実行方法

```shell
# build
docker-compose build
# up(fluentdコンテナ起動が遅いので何回かコケる -> リトライし続けたら動くようになる)
docker-compose up
```
