## Filterに関するメモ
### stdout

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

### grep

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

### record_transformer

- 現在のコードだとこんな感じでログが出力される
  - {}の中に日時とタグを`time`と`tag`として含めることも可能
  - 左に出てる{}に囲われていない日時とタグを`time`と`tag`として扱ってもOK(これが本来の使われ方)

```log
fluentd_1  | 2022-01-24 15:45:26.963648840 +0000 app.tail: {"record":"Hey, Yo!","tag":"app.tail","time":"2022-01-24 15:45:26 +0000"}
fluentd_1  | 2022-01-24 15:45:26.963673799 +0000 app.tail: {"record":"Hey, Yo!","tag":"app.tail","time":"2022-01-24 15:45:26 +0000"}
fluentd_1  | 2022-01-24 15:45:26.963685924 +0000 app.tail: {"record":"Hey, Yo!","tag":"app.tail","time":"2022-01-24 15:45:26 +0000"}
```

#### renew_time_key

- 例えばアプリのログで`timestamp`を出力している場合に
  - `renew_time_key ${record.dig("timestamp")}`のように指定したらアプリのログをfluentdの`time`に設定できる

## match.forward

- 別のFluentdサーバにログを横流ししたりできる
  - `@type record_transformer`を指定している場合、設定値によってはforwardでエラーが発生する

---

- https://docs.fluentd.org/filter/grep
- https://docs.fluentd.org/configuration/parse-section
