# https://hub.docker.com/r/fluent/fluentd/
FROM fluent/fluentd:v1.7.0-debian-1.0

# fluentd設定ファイル配置
COPY fluent.conf /fluentd/etc/

# ポート開放
EXPOSE 24224
