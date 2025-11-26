# 高校心理咨询系统

## 📖 项目简介
本项目是一个基于 **C/S (Client/Server)** 架构的高校心理咨询管理系统。项目严格遵循前后端分离原则，旨在为高校学生、心理医生及管理员提供高效、隐私、便捷的心理咨询预约与管理服务。

## 🏗 系统架构
系统分为两部分，通过 **TCP/JSON** 协议进行通信，物理上完全解耦：

*   **服务端 (PsyServer):** 负责数据库连接 (PostGreSQL)、业务逻辑处理 (鉴权、预约冲突检测、报表统计) 以及高并发 TCP 连接管理。
*   **客户端 (PsyClient):** 基于 **Qt Quick (QML)** 开发的跨平台用户界面，提供学生、心理医生、管理员三种角色的操作视图。

## 🏗 技术栈
- **语言标准**: C++17
- **构建工具**: CMake 3.16+
- **UI 框架**: Qt 6 (QML / Qt Quick)
- **网络通信**: TCP Socket (Qt Network), JSON 协议
- **数据库**: PostGreSQL 12+
- **平台支持**: Linux

## 📂 项目结构
本仓库作为聚合仓库，管理客户端和服务端的版本。
```text
College-psychological-counseling-system/
├── PsyClient/      # [子模块] 客户端源码
├── PsyServer/      # [子模块] 服务端源码
└── README.md
```

## 🚀 快速开始
### 1. 克隆项目
```bash
git clone --recursive https://github.com/lanse69/College-psychological-counseling-system.git
```
如果您已经使用普通方式克隆了代码，请手动初始化子模块：
```bash
git submodule update --init --recursive
``
### 2. 数据库环境准备
请确保服务端安装了 PostGreSQL .详看服务端readme文件
### 3. 编译与运行
请分别进入 PsyServer 和 PsyClient 目录,进行编译。

启动顺序: 请先启动服务端 (PsyServer)，再启动客户端 (PsyClient)。

## 🤝 交互协议
客户端与服务端通过 TCP + JSON 进行通信，不共享任何代码。

客户端: 负责 UI 展示、输入校验、JSON 序列化/反序列化。

服务端: 负责 Socket 监听、业务逻辑校验、数据库读写、消息推送。
