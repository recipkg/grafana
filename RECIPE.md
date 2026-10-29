# Grafana OSS 可观测性配方

```toml
format = "recipkg/1"

[package]
name = "grafana"
version = "0.1.0"
kind = "software"
description = "自托管的可观测性平台：查询多种数据源，探索指标/日志/追踪，构建仪表盘并发送告警。"
entry = "BUILD_PROMPT.md"

[dependencies.quality]
git = "https://github.com/recipkg/recipkg.git"
rev = "7f05425ae9843b7e8ce15cb80917977eedb36bdd"
subdir = "recipes/software-quality"

[dependencies.design]
git = "https://github.com/recipkg/design-directions.git"
rev = "6fdba350d1effa2d50dc0185095bb91ca7a699ee"
```

固定目标是 Grafana OSS v13.3.0，`grafana/grafana` 提交 `752e3462ff71a43a5c1fb62d00a482fa2dc0ee6a`，上游根许可证为 AGPL-3.0。版本、许可、依赖和来源证据见 `SOURCES.md` 与 `COVERAGE.md`。

配方目标涵盖 Grafana OSS 的自托管服务、Web 界面、查询与数据源插件、仪表盘、Explore、告警、用户/权限和文件化配置。Grafana 的配置数据库保存用户、数据源和仪表盘等元数据；被查询的数据源是另一类外部服务。Grafana Enterprise 与 Grafana Cloud 的商业功能不属于此配方。

`quality` 是数据权限、API、错误恢复和性能证据合同。`design` 指导高信息密度图表、时间范围、钻取、告警与空/错状态的产品设计，并递归包含设计基础。当前配方仍处于提取阶段，未逐项核对固定版本的插件、API、授权矩阵或真实 UI。
