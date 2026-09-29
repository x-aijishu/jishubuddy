

# JishuBuddy

[![npm](https://img.shields.io/npm/v/jishubuddy?logo=npm)](https://www.npmjs.com/package/jishubuddy)
[![Node.js](https://img.shields.io/badge/Node.js-%3E%3D22-green?logo=node.js)](https://nodejs.org/)

**JishuBuddy，玩 AI 的技术伙伴。**  
**像使用 AI 助手一样简单，像专业工程工具一样深入。**

JishuBuddy 是一款面向 AI 硬件开发的 Agent。它能理解代码、运行命令、分析错误，也能通过 SSH 和串口连接真实设备，帮助开发者把模型和程序从代码、仿真一路带到真机。

你不需要先学习复杂的 Agent 配置和任务编排。直接告诉 JishuBuddy 想完成什么，它会结合项目、设备和运行环境继续推进。

[立即安装](#quick-start--快速开始) · [npm](https://www.npmjs.com/package/jishubuddy) · [Raspberry Pi Skills](https://github.com/x-aijishu/jishubuddy-skills) · [AIJISHU](https://aijishu.com/)

> 本仓库用于 JishuBuddy 的产品介绍、安装入口和使用指引，不提供产品源代码。

<p align="center">
  <img src="./assets/JishuBuddyBaner.png" alt="JishuBuddy" width="100%">
</p>

## What Can JishuBuddy Do? / 它能做什么

### 像日常 AI 助手一样使用

JishuBuddy 可以理解代码库、读取和修改文件、运行命令、搜索资料、分析错误，并协助完成开发、构建和测试。你只需要描述目标，不需要先学习怎么“操作一个 Agent”。

### 不只写代码，也连接真实设备

除了常见的编程任务，JishuBuddy 还能连接 Linux 开发板、读取设备状态和串口日志，协助分析依赖、资源、通信和运行环境问题，让代码和 AI 模型真正跑在设备上。

### 从仿真继续到真机

开发过程不必停在仿真结果。JishuBuddy 可以在同一个任务上下文中继续连接真机、读取日志、检查状态并比较结果，减少在多个工具和窗口之间反复切换。

### 记住项目和设备的上下文

同一个项目可能包含多块开发板、多个模型版本和长期积累的问题。JishuBuddy 可以结合项目、会话和设备信息继续工作，减少重复说明和重复排查。

## Try Asking / 可以直接这样说

```text
帮我检查这个项目为什么构建失败。

连接实验室里的开发板，查看系统、CPU 和内存状态。

SSH 一直连接超时，帮我判断问题出在哪个阶段。

读取串口启动日志，看看设备为什么没有正常启动。

检查磁盘、温度、降频和异常服务。

先分析仿真结果，再连接真机继续排查。
```

## Supported Scenarios / 支持场景

- AI 模型和开发环境调试
- Raspberry Pi 与 Linux 开发板
- SSH 连接和远程设备排障
- UART 串口输出和启动日志
- CPU、内存、磁盘、温度和服务检查
- 仿真与真机开发流程衔接
- 具身设备和机器人主控的后续扩展

## Key Capabilities / 核心能力

### Programming Agent / 编程 Agent

- 理解代码库、读取和修改文件
- 运行 Bash、分析错误并协助构建和测试
- 使用 MCP、Web Search 和 Deep Research 获取信息
- 支持全屏 TUI、多行输入、会话管理和历史搜索
- 支持 API Key、GitHub Copilot、Arm China 和 OpenAI 兼容模型服务

### Remote SSH Device

- 使用操作者电脑上的系统 OpenSSH
- 连接远程 Linux 设备并执行 Bash
- 保留 OpenSSH 返回的真实错误信息
- 区分域名解析、网络路径、连接超时、拒绝连接、Host Key、认证和远程 Bash 等问题阶段
- 遇到未知 Host Key 时，需要在本地 TUI 中人工核对

### Device Status

- 查看 SSH 设备的连接和采样状态
- 直接显示 CPU 和内存信息
- 支持 Raspberry Pi 5 Model B 和 Compute Module 5 的设备图
- 可通过远程 Bash 进一步检查磁盘、温度、降频、服务和进程

### Remote Serial Device

- 通过操作者电脑上的本机串口连接开发板
- 支持 `connect`、`status`、`write`、`read`、`exchange` 和 `close`
- 支持 UTF-8 和严格 Hex 数据
- 人工 Serial Console 可以显示和发送串口内容
- 已打开的 Console 会在临时断连或设备复位后保留记录并尝试重连

### Safety Review

- 危险的本机 Bash 和远程 SSH Bash 命令会进入审核
- 审核界面会展示操作目标、具体命令和相关风险
- 用户可以允许本次操作、在当前 Runtime 中保存相同授权，或拒绝执行

## Quick Start / 快速开始

### 运行环境

- Node.js 22+
- Linux x64、Linux ARM64 或 Apple Silicon macOS
- 当前不支持原生 Windows

### 安装并启动

```bash
npm install -g jishubuddy
jishubuddy
```

首次进入 JishuBuddy 后，登录并选择模型：

```text
/login
/model
```

更新到 npm 上的最新稳定版本：

```bash
jishubuddy update
```

## Raspberry Pi Skills

如果你希望 Agent 按照更明确的步骤处理 Raspberry Pi 任务，可以配合以下 Skills 使用：

| Skill | 适合什么时候使用 |
| --- | --- |
| [`raspberry-pi-first-setup`](https://github.com/x-aijishu/jishubuddy-skills/tree/main/raspberry-pi-first-setup) | 首次配置、无头安装、Wi-Fi、主机名和 SSH 准备 |
| [`raspberry-pi-ssh-doctor`](https://github.com/x-aijishu/jishubuddy-skills/tree/main/raspberry-pi-ssh-doctor) | SSH 超时、拒绝连接、认证、解析或 Host Key 问题 |
| [`raspberry-pi-serial-rescue`](https://github.com/x-aijishu/jishubuddy-skills/tree/main/raspberry-pi-serial-rescue) | SSH 不可用时，通过 UART 查看启动日志 |
| [`raspberry-pi-health-check`](https://github.com/x-aijishu/jishubuddy-skills/tree/main/raspberry-pi-health-check) | 卡顿、发热、重启、磁盘、降频和服务异常 |

## Boundaries and Privacy / 使用边界与隐私

JishuBuddy 会提供工具、证据和排查建议，但不会保证自动解决所有硬件问题，也不会绕过用户确认执行危险命令。

- 不会自动刷写固件或复位设备
- 不会在串口重连后自动重放之前的写入
- 未知 SSH Host Key 必须由用户人工核对
- 危险的本机和远程命令需要用户审核
- 安装成功不代表设备问题已经解决

TUI 和 AG-UI Server 默认发送低频 activation 和 heartbeat Telemetry。如需关闭，请在启动前设置：

```bash
export JISHUBUDDY_TELEMETRY_DISABLED=true
```

## About AIJISHU

JishuBuddy 由 [AIJISHU](https://aijishu.com/) 团队打造。我们关注 AI Agent、知识工具、评测系统，以及 AI 与真实设备结合的开发体验。

**AIJISHU builds practical AI tools for agents, knowledge, evaluation, and real-world development.**
