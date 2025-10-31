## 上下文

libssp 是一个用于视频流传输的客户端库,基于 libuv 事件循环。项目中已经提供了 Windows x64 平台的预编译库文件(Release 和 Debug 版本)。需要创建一个简单的 C++ 工程来演示如何集成和使用这个库。

约束条件:
- 使用 C++17 标准
- 使用 CMake 作为构建系统
- Windows 平台开发

相关方:
- 开发人员需要快速上手使用 libssp 库

## 目标 / 非目标

**目标:**
- 提供可工作的 CMake 配置以正确链接 libssp
- 创建简单示例展示 libssp 基本用法
- 支持 Debug 和 Release 构建配置

**非目标:**
- 跨平台支持(当前仅 Windows)
- 完整的功能演示(仅基本连接和回调)
- 生产环境使用的完整应用

## 决策

### 决策 1: 使用现代 CMake 风格

**选择:** 使用 target_include_directories 和 target_link_libraries 等现代 CMake 命令

**原因:**
- 更清晰的依赖关系管理
- 更好的可维护性
- CMake 最佳实践

**备选方案:**
- 使用传统的 include_directories/link_directories:缺点是全局污染,不推荐

### 决策 2: 使用配置生成器表达式区分 Debug/Release

**选择:** 使用 $<CONFIG:Debug> 等生成器表达式来选择不同的库文件

**原因:**
- 单一 CMakeLists.txt 支持多配置
- Visual Studio 等多配置生成器的标准做法
- 避免手动切换构建配置

**备选方案:**
- 为 Debug/Release 创建不同的 CMake 配置文件:维护成本高

### 决策 3: 示例程序最小化

**选择:** 创建最小可运行示例,仅展示:
- Loop 创建和初始化
- SspClient 创建和基本配置
- 基本回调注册

**原因:**
- 降低学习曲线
- 聚焦核心 API 使用
- 作为其他功能的起点

**备选方案:**
- 完整功能演示:对于入门来说过于复杂

### 决策 4: 静态链接导入库,动态加载 DLL

**选择:** 链接 .lib 导入库,运行时加载 .dll

**原因:**
- Windows 动态库的标准做法
- 符合 libssp 的分发方式
- 允许 DLL 更新而不重新编译

## 风险 / 权衡

### 风险 1: DLL 路径问题
- **描述:** 运行时找不到 libssp.dll
- **缓解:** 在 README 中明确说明需要将 DLL 复制到可执行文件目录或添加到 PATH

### 风险 2: C++ 运行时库不匹配
- **描述:** libssp 使用的 CRT 版本与示例程序不匹配可能导致崩溃
- **缓解:** 在 CMake 中明确使用 /MD (Release) 和 /MDd (Debug),与 libssp 保持一致

### 风险 3: libuv 版本兼容性
- **描述:** libssp 内部使用的 libuv 版本可能与系统其他库冲突
- **缓解:** 仅使用 libssp 提供的 libuv 头文件,不额外依赖

## 迁移计划

**初始实施:**
1. 创建 CMakeLists.txt
2. 创建 src/main.cpp 示例
3. 创建 README.md 文档
4. 测试 Debug 和Release 构建

**回滚:**
- 这是新项目,无需回滚计划

## 开放问题

- 是否需要支持其他平台(Linux/macOS)?当前 ssp 目录仅包含 Windows 库
- 是否需要更复杂的示例展示视频/音频数据接收?

