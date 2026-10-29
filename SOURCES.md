# Grafana 来源与许可记录

## 固定上游

- 项目：[grafana/grafana](https://github.com/grafana/grafana)
- 发布版：[Grafana v13.3.0](https://github.com/grafana/grafana/releases/tag/v13.3.0)，GitHub Release 日期 2026-10-27。
- 标签：[`v13.3.0`](https://github.com/grafana/grafana/tree/v13.3.0)
- 固定提交：[`752e3462ff71a43a5c1fb62d00a482fa2dc0ee6a`](https://github.com/grafana/grafana/tree/752e3462ff71a43a5c1fb62d00a482fa2dc0ee6a)。标签是 annotated tag；解引用后的 commit 为上述 SHA。
- 固定提交根许可证：[LICENSE](https://github.com/grafana/grafana/blob/752e3462ff71a43a5c1fb62d00a482fa2dc0ee6a/LICENSE)，AGPL-3.0。Grafana Enterprise/Cloud 商业功能、单独插件与第三方数据源需逐项核对授权，不能仅凭仓库根许可证覆盖。
- GitHub API 于 2026-10-29 查询到 77,583 stars、仓库大小 2,101,189 KB；这是日期快照及 API 元数据，不等于展开目录大小或软件质量。

## 固定提交源码入口

- [README 功能与产品描述](https://github.com/grafana/grafana/blob/752e3462ff71a43a5c1fb62d00a482fa2dc0ee6a/README.md)
- [Dashboard 服务与访问控制](https://github.com/grafana/grafana/blob/752e3462ff71a43a5c1fb62d00a482fa2dc0ee6a/pkg/services/dashboards/service/dashboard_service.go)
- [Data source 服务](https://github.com/grafana/grafana/blob/752e3462ff71a43a5c1fb62d00a482fa2dc0ee6a/pkg/services/datasources/service/datasource.go)
- [Alerting 服务入口](https://github.com/grafana/grafana/blob/752e3462ff71a43a5c1fb62d00a482fa2dc0ee6a/pkg/services/ngalert/ngalert.go)
- [Provisioning 生命周期](https://github.com/grafana/grafana/blob/752e3462ff71a43a5c1fb62d00a482fa2dc0ee6a/pkg/services/provisioning/provisioning.go)

只定点核对上述源码入口，未审阅整个仓库及其所有测试。

## 官方文档

以下 Grafana 官方资料于 2026-10-29 查阅。多数链接指向滚动的 `latest` 文档；用于发现产品概念，具体 v13.3.0 合同行为须再查固定版本资料：

- [Grafana OSS、Enterprise 与 Cloud](https://grafana.com/docs/grafana/latest/)
- [Grafana OSS 简介与用户任务](https://grafana.com/docs/grafana/latest/introduction/)
- [数据源与插件](https://grafana.com/docs/grafana/latest/datasources/)
- [Grafana 配置数据库和部署规模](https://grafana.com/docs/grafana/latest/setup-grafana/installation/)
- [Grafana 认证方式](https://grafana.com/docs/grafana/latest/setup-grafana/configure-access/configure-authentication/)
- [Dashboards 变量](https://grafana.com/docs/grafana/latest/visualizations/dashboards/variables/)
- [文件化 Provisioning](https://grafana.com/docs/grafana/latest/administration/provisioning/)
- [Enterprise 专属功能](https://grafana.com/docs/grafana/latest/introduction/grafana-enterprise/)

## Recipkg 依赖

| 别名 | 固定来源 | 用途与边界 |
| --- | --- | --- |
| `quality` | [Recipkg `recipes/software-quality`](https://github.com/recipkg/recipkg/tree/7f05425ae9843b7e8ce15cb80917977eedb36bdd/recipes/software-quality)，提交 `7f05425ae9843b7e8ce15cb80917977eedb36bdd` | 数据权限、配置状态、插件/API 错误、恢复与性能证据合同；不是运行时服务。 |
| `design` | [recipkg/design-directions](https://github.com/recipkg/design-directions/tree/6fdba350d1effa2d50dc0185095bb91ca7a699ee)，提交 `6fdba350d1effa2d50dc0185095bb91ca7a699ee` | 选择有依据的高信息密度数据界面方向；递归包含 `design-foundations` 提交 `8c5bf1f1e40719789cf51bc0dfd8f5aeecae0538`。不是 Grafana 运行时库或 UI 验收。 |

未将数据源、可选 SQL 配置数据库或商业插件写成无条件依赖。每个具体部署的外部版本都要单独固定与验收。
