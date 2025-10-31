## ADDED Requirements

### Requirement: SSP 客户端示例

应用程序 SHALL 提供一个简单的示例,演示如何使用 libssp 库连接到 SSP 服务器。

#### Scenario: 事件循环初始化
- **WHEN** 应用程序启动
- **THEN** 创建 imf::Loop 对象并初始化

#### Scenario: SSP 客户端创建
- **WHEN** 初始化完成
- **THEN** 创建 imf::SspClient 对象,指定 IP 地址、端口和流类型

#### Scenario: 回调函数注册
- **WHEN** 客户端对象创建后
- **THEN** 注册必要的回调函数(连接、断开、数据接收等)

### Requirement: 错误处理

应用程序 SHALL 正确处理错误情况。

#### Scenario: 初始化失败
- **WHEN** Loop 或 SspClient 初始化失败
- **THEN** 输出错误信息并返回非零退出码

#### Scenario: 连接失败
- **WHEN** 无法连接到服务器
- **THEN** 通过异常回调函数报告错误

### Requirement: 资源清理

应用程序 SHALL 正确管理和清理资源。

#### Scenario: 正常退出
- **WHEN** 应用程序退出
- **THEN** 停止 SspClient,退出事件循环,释放所有资源

#### Scenario: 信号中断
- **WHEN** 收到 Ctrl+C 或其他中断信号
- **THEN** 优雅地停止客户端并退出

