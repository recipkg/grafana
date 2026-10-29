# Grafana OSS · Recipkg 配方维护

- 固定目标是 Grafana OSS v13.3.0，提交 `752e3462ff71a43a5c1fb62d00a482fa2dc0ee6a`。
- 阅读 `RECIPE.md`、`BUILD_PROMPT.md`、`ACCEPTANCE.md`、`COVERAGE.md` 和 `SOURCES.md` 后再添加行为主张。
- 区分 Grafana 配置数据库、外部查询数据源、会话缓存与插件；不得把一种组件当成另一种。
- 明确 OSS、Enterprise 和 Cloud 的许可与功能边界；不把商业插件和专有服务混入 OSS 重建声明。
- 固定版本代码观察、滚动在线文档、上游实测、独立重建、浏览器和插件验收分别记录。
- 配方归档只提交 UTF-8 Markdown；不得加入 Grafana 实现代码、第三方插件、数据库文件、凭据或安装钩子。
- 设计和质量依赖是重建合同，不是 Grafana 运行时服务；可选外部数据库和数据源不得无条件声明为必需。
