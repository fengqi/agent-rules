<!-- 本文件维护 CSGO 相关仓库的项目级偏好。 -->

# CSGO 项目习惯

- 当项目依赖包含 `git.ourbluecity.com/csgo` 时，按 Blued 自研 csgo MVC 框架项目处理。
- 遵守 `controller/`、`service/`、`remote/`、`model/`、`dao/`、`conf/` 分层：`controller` 只做参数、权限、调用和响应，业务放 `service`，数据库操作放 `dao`，外部接口放 `remote`。
- 配置走 Apollo 或项目既有配置系统，不硬编码环境、域名、开关、阈值和敏感信息；新增 `csconfig.xxx("namespace.key")` 要检查 dev、pre、pro 配置声明。
- 复用 csgo 框架能力，不重复实现日志、错误处理、链路追踪、配置、Redis、MySQL、HTTP/RPC、Kafka 等基础能力。
- `server.Gtx` 禁止透传到 `service`、`dao`、`remote`；下层只接收 `context.Context`，非 `controller` 层不要依赖 `server` 包。
- 异步 goroutine 禁止直接使用 handler 传入的 `ctx` 或 `gtx`，必须派生独立上下文。
- Redis、MySQL、HTTP/RPC、Kafka 分别使用 `csredis`、`csmysql`、`cshttp`/`csremote`、`cskafka` 或项目封装，相关 namespace、实例名、服务名必须在 dev、pre、pro 配置中声明。
- 用户关系、用户设置、用户资料等公共基础服务优先使用 `csgo/infrarequest`；没有封装时先补 `infrarequest`，再让业务调用。
- 项目名前缀影响基础服务版本选择：`blued-` 使用 Blued 主站版本，`unsolo-` 使用 Unsolo 独立站版本。
- 涉及已有接口 client 时，优先把新增方法放在相近语义的方法后面。
- 接口路径、query string、返回 shape 按已有接口风格推断，不自作主张调整 contract 或预留无用扩展。
