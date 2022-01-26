トラブルシューティング中

```log
2022-01-26T14:04:53.930202Z  INFO vector::app: Log level is enabled. level="vector=info,codec=info,vrl=info,file_source=info,tower_limit=trace,rdkafka=info,buffers=info"
2022-01-26T14:04:53.930342Z  INFO vector::app: Loading configs. paths=["/etc/vector/vector.toml"]
2022-01-26T14:04:53.932958Z  INFO vector::sources::docker_logs: Capturing logs from now on. now=2022-01-26T14:04:53.932800920+00:00
2022-01-26T14:04:53.933546Z  INFO vector::sources::docker_logs: Listening to docker log events.
2022-01-26T14:04:53.934045Z  INFO vector::topology::running: Running healthchecks.
2022-01-26T14:04:53.934288Z  INFO vector::topology::running: Starting source. key=app_source
2022-01-26T14:04:53.934393Z  INFO vector::topology::running: Starting sink. key=app_sink
2022-01-26T14:04:53.934509Z  INFO vector: Vector has started. debug="false" version="0.20.0" arch="aarch64" build_id="84b6663 2022-01-22"
2022-01-26T14:04:53.934566Z  INFO vector::app: API is disabled, enable by setting `api.enabled` to `true` and use commands like `vector top`.
2022-01-26T14:04:53.935671Z  INFO vector::topology::builder: Healthcheck: Passed.
2022-01-26T14:04:53.937595Z ERROR source{component_kind="source" component_id=app_source component_type=docker_logs component_name=app_source}: vector::sources::docker_logs: Listing currently running containers failed. error=error trying to connect: No such file or directory (os error 2)
2022-01-26T14:04:53.937814Z  INFO vector::shutdown: All sources have finished.
2022-01-26T14:04:53.937821Z  INFO vector: Vector has stopped.
2022-01-26T14:05:32.862675Z  INFO vector::app: Log level is enabled. level="vector=info,codec=info,vrl=info,file_source=info,tower_limit=trace,rdkafka=info,buffers=info"
2022-01-26T14:05:32.862763Z  INFO vector::app: Loading configs. paths=["/etc/vector/vector.toml"]
2022-01-26T14:05:32.863310Z  INFO vector::sources::docker_logs: Capturing logs from now on. now=2022-01-26T14:05:32.863261507+00:00
2022-01-26T14:05:32.863371Z  INFO vector::sources::docker_logs: Listening to docker log events.
2022-01-26T14:05:32.863521Z  INFO vector::topology::running: Running healthchecks.
2022-01-26T14:05:32.863557Z  INFO vector::topology::running: Starting source. key=app_source
2022-01-26T14:05:32.863573Z  INFO vector::topology::running: Starting sink. key=app_sink
2022-01-26T14:05:32.863593Z  INFO vector: Vector has started. debug="false" version="0.20.0" arch="aarch64" build_id="84b6663 2022-01-22"
2022-01-26T14:05:32.863600Z  INFO vector::app: API is disabled, enable by setting `api.enabled` to `true` and use commands like `vector top`.
2022-01-26T14:05:32.863612Z  INFO vector::topology::builder: Healthcheck: Passed.
2022-01-26T14:05:32.863737Z ERROR source{component_kind="source" component_id=app_source component_type=docker_logs component_name=app_source}: vector::sources::docker_logs: Listing currently running containers failed. error=error trying to connect: No such file or directory (os error 2)
2022-01-26T14:05:32.863830Z  INFO vector::shutdown: All sources have finished.
2022-01-26T14:05:32.863855Z  INFO vector: Vector has stopped.
```
