## 为什么

需要创建一个简单的 C++ 工程来使用 libssp 库的功能。libssp 是一个流媒体协议客户端库,当前项目中已有 Windows x64 版本的预编译库文件,需要一个构建系统来正确链接和使用这个库。

## 变更内容

- 创建 CMake 构建系统配置
- 设置 C++17 标准
- 配置 libssp 库的头文件和库文件路径
- 创建示例程序演示 libssp 库的基本使用
- 配置 Windows 平台下的 DLL 链接

## 影响

- 受影响的规格: `build-system`(新建), `sample-application`(新建)
- 受影响的代码: 新建 CMakeLists.txt, 新建示例源代码文件

