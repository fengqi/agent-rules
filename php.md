<!-- 本文件维护 PHP 项目中的编码、接口和框架使用偏好。 -->

# PHP 代码习惯

- 遵守项目现有框架约定，不混用不同风格的 service、controller、repository 写法。
- `controller` 只做参数、权限、调用和响应组织，业务逻辑不要堆在 `controller`。
- 接口参数、返回字段、数组结构保持 contract 稳定，不随意改名或改 shape。
- 对可能为空的输入、数组 key、外部响应字段和类型转换做显式处理，避免依赖 PHP 隐式行为。
- SQL、缓存 key、队列 topic、配置项命名要和项目既有模式一致。
