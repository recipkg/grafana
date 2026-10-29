# 来源覆盖与验证状态

**状态：提取中。** 固定目标为 Grafana OSS v13.3.0。只检查了上游 README、少量后端服务代码入口与官方在线文档；没有克隆 2 GB 级源码仓库、启动 Grafana、运行测试或独立重建。

## 固定来源

- 上游：[grafana/grafana](https://github.com/grafana/grafana)
- 发布版：[v13.3.0](https://github.com/grafana/grafana/releases/tag/v13.3.0)，2026-10-27 发布
- 固定提交：[`752e3462ff71a43a5c1fb62d00a482fa2dc0ee6a`](https://github.com/grafana/grafana/tree/752e3462ff71a43a5c1fb62d00a482fa2dc0ee6a)。`v13.3.0` 标签解析到此提交。
- 根许可证：[固定提交 LICENSE](https://github.com/grafana/grafana/blob/752e3462ff71a43a5c1fb62d00a482fa2dc0ee6a/LICENSE)，GitHub API 识别为 AGPL-3.0。发行物和插件的许可仍需分别检查。
- GitHub API 于 2026-10-29 查询：77,583 stars、仓库大小 2,101,189 KB。仅为日期快照；仓库大，故本次采用 GitHub API、固定源码网页和官方文档定点检查，没有完整克隆。

## 已观察

- 固定提交 README 描述 Grafana 的查询、可视化和告警能力，包含面板插件、变量、Explore、通知和混合数据源等功能。这是上游说明，不是运行结果。
- 固定提交 `pkg/services/dashboards/service/dashboard_service.go` 包含仪表盘访问控制、服务与清理路径。
- 固定提交 `pkg/services/datasources/service/datasource.go` 与 `store.go` 包含数据源服务、读取和存储入口；没有审阅所有查询代理与插件实现。
- 固定提交 `pkg/services/ngalert/ngalert.go` 与关联目录包含告警服务；`pkg/services/provisioning/provisioning.go` 包含启动 provisioning 与面板加载重试入口。没有完整还原状态机、路由、重试和 OSS feature gate。
- 官方文档说明 Grafana OSS 可查询、探索、可视化和告警多种外部数据；面板可通过变量复用查询，数据源插件负责连接存储后端。
- 官方安装配置文档说明 Grafana 自身的配置数据库与被查询数据源不同：默认配置库为内嵌 SQLite，文档列出 MySQL 与 PostgreSQL 为外部选项。生产容量、数据库版本支持和迁移应按固定 v13.3.0 再核对。
- 官方文档区分 Grafana OSS、Enterprise 与 Cloud。Enterprise 的商业功能/数据源、额外认证和支持不能直接归入 OSS。

## Recipkg 依赖审阅

- `quality`：Recipkg 提交 `7f05425ae9843b7e8ce15cb80917977eedb36bdd` 的 `recipes/software-quality`，用于权限、状态一致性、插件/API 错误、恢复和性能证据。
- `design`：[`recipkg/design-directions`](https://github.com/recipkg/design-directions/tree/6fdba350d1effa2d50dc0185095bb91ca7a699ee)，提交 `6fdba350d1effa2d50dc0185095bb91ca7a699ee`，递归包含 `design-foundations` 提交 `8c5bf1f1e40719789cf51bc0dfd8f5aeecae0538`，用于仪表盘、Explore、告警和资源配置的实际界面任务；不代表 UI 已验收。
- 未将 PostgreSQL 配方声明为强制运行依赖：Grafana 默认使用内嵌 SQLite，PostgreSQL 是可选配置数据库；标准库 PostgreSQL 配方也仍在提取，尚无 Grafana v13.3 接口验收。Prometheus、Loki 等同样是部署可选择的数据源，不是 Grafana 的唯一直接依赖。

## 未覆盖与未知

- 没有逐页/逐查询验证 Dashboard、Explore、面板、Transformations、变量、分享、实时数据和浏览器交互；没有视觉或无障碍实测。
- 没有枚举固定版 OSS 内置数据源、面板插件、插件签名与兼容矩阵；没有运行插件隔离或恶意插件检查。
- 没有导出完整 REST/WebSocket/Live/API 契约、错误码、分页、授权矩阵或会话生命周期。
- 没有实测用户/组织/团队/服务账号与各类权限，也未完成 OSS 与商业功能开关审计。
- 没有实测告警评估、状态转换、分组/静默/抑制、通知路由、重试、持久化和故障恢复。
- 没有运行 SQLite、PostgreSQL、MySQL 的迁移/故障/HA 场景；Grafana 数据源性能和配置数据库容量都没有实测。
- 没有验证所有部署形态、插件、云服务、升级和恢复。验收文件是计划，不是通过记录。

Recipkg 检查只能验证配方归档，不证明 Grafana OSS、任何数据源、插件或商业授权行为已重建。
