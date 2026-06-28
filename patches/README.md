# Patches

- `server-host-port.patch`: 让 `Games.<game>.Hosts` 同时支持 `host` 和 `host:port`，默认仍保持旧行为 `host -> 443`。
- `server-host-port.patch`: lets `Games.<game>.Hosts` accept both `host` and `host:port` while keeping the old `host -> 443` behavior.
- `goreleaser-docker.patch`: 通过构建时 patch 同时调整 GoReleaser 生成链路和 `tools/server-docker/server/Dockerfile`，让 `server` 镜像改为基于预构建二进制与运行时资源打包，并发布到 `ghcr.io/tofuliang/agelanserver`。
- `goreleaser-docker.patch`: patches both the GoReleaser generator and `tools/server-docker/server/Dockerfile` at build time so the `server` image is assembled from prebuilt release binaries plus runtime resources, then published to `ghcr.io/tofuliang/agelanserver` with `{{ .Version }}` and `latest` tags.
- 无效配置应在服务启动时直接报错，不会静默回退。
- This patch is intended to be applied during CI/build time, not by permanently editing tracked upstream source files.
- 如果上游源码变化导致补丁失效，请在临时副本中重新生成补丁，再替换这里的文件。
