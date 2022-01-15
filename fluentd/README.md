## Filterに関するメモ

- filterでstdoutを設定することで以下のようなログが出力されます
  - 基本的にstdoutはdebug用として使われるので実運用では使いません

```conf
<filter docker.app>
  @type stdout
</filter>
```

```log
app_1      | Check It Out! Yo!
fluentd_1  | 2022-01-15 15:06:57.000000000 +0000 docker.app: {"container_id":"0e3d6c0e24e03e48a737605d5ac5bf87fc14751d77cce744079b7c25eeb2e01b","container_name":"/fluentd_app_1","source":"stdout","log":"Check It Out! Yo!"}
app_1      | Hey, Yo!
fluentd_1  | 2022-01-15 15:06:58.000000000 +0000 docker.app: {"log":"Hey, Yo!","container_id":"0e3d6c0e24e03e48a737605d5ac5bf87fc14751d77cce744079b7c25eeb2e01b","container_name":"/fluentd_app_1","source":"stdout"}
app_1      | Hey, Yo!
fluentd_1  | 2022-01-15 15:06:59.000000000 +0000 docker.app: {"source":"stdout","log":"Hey, Yo!","container_id":"0e3d6c0e24e03e48a737605d5ac5bf87fc14751d77cce744079b7c25eeb2e01b","container_name":"/fluentd_app_1"}
```

- stdoutで使用可能なKeyが確認できます
- 以下のようにfilterを設定することで扱うログを絞り込むことができます
  - 条件 -> logというKeyに対してHeyという文字が含まれること(patternはRubyの正規表現で記述する必要がある)

```conf
<filter docker.app>
  @type grep
  <regexp>
    key log
    pattern /Hey/
  </regexp>
</filter>
```

---

- https://docs.fluentd.org/filter/grep
- https://docs.fluentd.org/configuration/parse-section
