<!-- 本文件维护 CSGO 相关仓库的项目级偏好。 -->

# CSGO 项目习惯

- 当项目依赖包含 `git.ourbluecity.com/csgo` 时，按 Blued 自研 csgo MVC 框架项目处理。
- 目录结构遵守 `controller/`、`service/`、`remote/`、`model/`、`dao/`、`conf/` 分层，职责不要混放。
- `controller` 只做参数校验、权限检查、调用组织和响应返回；业务逻辑放 `service`，数据库操作放 `dao`。
- 外部服务、跨团队接口调用统一放 `remote/` 目录，并按外部模块拆子目录封装。
- 所有配置项走 Apollo 或项目既有配置系统，不硬编码环境、域名、开关、阈值和敏感配置。
- 新增或修改 `csconfig.xxx("namespace.key")` 时，必须检查 dev、pre、pro 三个环境配置是否都显式声明对应 namespace 和 key。
- 数据库密码、AK、SK、token 等敏感信息不得写在代码或明文配置文件里。
- 优先复用 csgo 框架提供的中间件、日志、错误处理、链路追踪、配置、Redis、MySQL、HTTP/RPC、Kafka 能力，不重复造轮子。
- `server.Gtx` 是请求上下文对象，禁止透传到 `service`、`dao`、`remote` 等下层逻辑。
- 下层业务逻辑只接收 `context.Context`，不要在非 `controller` 层导入或依赖 `server` 包。
- 异步 goroutine 禁止直接使用 handler 传入的 `ctx` 或 `gtx`；必须用 `server.ContextForkCtx(ctx)`、`server.ContextForkGtx(gtx)` 或 `context.WithXXX` 派生独立上下文。
- Redis 操作使用 `csredis.Conn(redisNamespace, redisInstanceName)` 或项目基于它的封装，不直接初始化原生 Redis client。
- MySQL 操作使用 `csmysql.Conn(mysqlNamespace, mysqlInstanceName)` 或项目基于它的封装，不直接初始化 DB 连接。
- 外部 HTTP/RPC 请求使用 `cshttp`、`csremote` 或项目基于它们的封装，不直接使用裸 `http.Client` 和硬编码服务地址。
- Kafka 生产消息使用 `cskafka.Producer(kafkaInstanceName)` 或项目基于它的封装，不直接初始化 Kafka producer。
- Redis、MySQL、HTTP/RPC、Kafka 调用里用到的 namespace、实例名、服务名，必须在 dev、pre、pro 三个环境配置中声明。
- 用户关系、用户设置、用户资料等公共基础服务调用，优先使用 `csgo/infrarequest` 公共封装。
- `csgo/infrarequest` 没有现成封装时，先在 `infrarequest` 补公共封装，再让业务代码调用封装后的方法。
- 项目名前缀影响基础服务版本选择：`blued-` 项目使用 Blued 主站版本，`unsolo-` 项目使用 Unsolo 独立站版本。
- 不使用 csgo 框架已标记废弃的 API。
- Dockerfile、K8s 等部署配置要符合项目已有 Go 版本、基础镜像、资源限制和健康检查规则。
- 被注释掉的测试逻辑要恢复或删除，不保留无效测试代码。
- 接口结构体字段变更要评估下游兼容性，重点看 `omitempty`、字段名、字段类型、新增必填字段和旧客户端适配。
- 涉及已有接口 client 时，优先把新增方法放在相近语义的方法后面。
- 接口路径、query string、返回 shape 按已有接口风格推断，不自作主张调整 contract。
- 新增字段或参数时，先确认调用方真实需要，不预留暂时不用的扩展。
- 改完优先跑受影响 package 的定向测试或构建。
