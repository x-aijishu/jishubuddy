# JishuBuddy

JishuBuddy，玩 AI 的技术伙伴。

AI hardware development partner for model debugging, simulation, development boards, and real devices.

[npm](https://www.npmjs.com/package/jishubuddy) · [Documentation] · [Agent Skills](https://github.com/x-aijishu/jishubuddy-skill) · [Website] · [Feedback](https://github.com/x-aijishu/jishubuddy-skill/issues)

[需要链接：https://www.npmjs.com/package/jishubuddy]
[需要链接：JishuBuddy 文档]
[需要链接：https://github.com/x-aijishu/jishubuddy-skills]
[需要链接：AIJISHU 官网中的 JishuBuddy 产品页]
[需要链接：JishuBuddy Issues 或反馈入口]

## What is JishuBuddy?

JishuBuddy 是一个本地运行的智能 Agent 应用，拥有独立 CLI、Headless Runtime 和自定义 TUI。

它面向 AI 模型调试、开发板、仿真和真机开发，让 Agent 不只读取代码，也能通过 SSH 和串口读取真实设备返回的信息。

JishuBuddy 不会承诺一键修好硬件。它的核心是先获取真实证据，再帮助开发者判断问题、执行经过确认的操作，并明确说明仍然无法确认的部分。

## Demo

[需要图片：JishuBuddy 演示 GIF。内容建议为连接树莓派、查看状态面板、执行只读检查并返回结果。]

## Key Capabilities

### Remote SSH Device

- 使用操作者电脑上的系统 OpenSSH
- 连接远程 Linux 设备并执行 Bash
- 保留 OpenSSH 的真实错误信息
- 区分域名解析、网络路径、连接超时、拒绝连接、Host Key、认证和远程 Bash 等问题阶段
- 未知 Host Key 需要在本地 TUI 中人工核对

### Device Status

- 查看 SSH 设备的连接和采样状态
- 直接显示 CPU 和内存
- 支持 Raspberry Pi 5 Model B 和 Compute Module 5 的设备图
- 可通过远程 Bash 进一步检查磁盘、温度、降频、服务和进程

### Remote Serial Device

- 通过操作者电脑上的本机串口连接开发板
- 支持 connect、status、write、read、exchange 和 close
- 支持 UTF-8 和严格 Hex 数据
- 人工 Serial Console 可以显示和发送串口内容
- 已打开的 Console 在临时断连或设备复位后保留记录并尝试重连

### Safety Review

- 危险的本机 Bash 和远程 SSH Bash 命令会进入审核
- 审核界面展示目标、命令和风险
- 用户可以允许、保存当前 Runtime 的相同授权或拒绝

## Quick Start

### Requirements

- Node.js 22 或更高版本
- Linux x64、Linux ARM64 或 Apple Silicon macOS
- 当前不支持原生 Windows

### Install

npm install -g jishubuddy

### Start

jishubuddy

首次进入后通常需要：

/login

/model

[需要链接：完整安装、登录和模型配置说明]

## Raspberry Pi Skills

JishuBuddy Skills 当前提供四个 Raspberry Pi 任务入口：

- raspberry-pi-first-setup
- raspberry-pi-ssh-doctor
- raspberry-pi-serial-rescue
- raspberry-pi-health-check

每个 Skill 先识别问题和准备条件，再在用户明确授权后安装或复用 JishuBuddy，通过真实 SSH 或串口证据继续检测。

[查看 JishuBuddy Skills]

[需要链接：https://github.com/x-aijishu/jishubuddy-skills]

## Supported Scenarios

- AI 模型和开发环境调试
- Raspberry Pi 与 Linux 开发板
- SSH 连接和远程设备排障
- UART 串口输出和启动日志
- CPU、内存、磁盘、温度和服务检查
- 仿真与真机开发流程衔接
- 具身设备和机器人主控的后续扩展

最后一项属于产品方向，不应写成已经完整支持的能力。

## Product Boundaries

JishuBuddy 当前不会：

- 自动修复所有硬件问题
- 自动刷写固件
- 主动控制开发板复位、DTR、RTS 或 Boot Mode
- 自动配置所有 SSH 环境
- 绕过用户确认执行危险命令
- 在串口重连后自动重放之前的数据

安装成功不代表设备问题已经解决。诊断仍需采集真实设备证据，并区分：

- confirmed
- unconfirmed
- blocked

## Telemetry

JishuBuddy 的 TUI 和 AG-UI Server 默认发送低频 activation 和 heartbeat Telemetry。

可以在启动前关闭：

export JISHUBUDDY_TELEMETRY_DISABLED=true

## Platform Support

支持：

- Linux x64
- Linux ARM64
- Apple Silicon macOS

暂不支持：

- 原生 Windows

SSH 目标需要：

- Linux
- 已运行的 SSH Server
- 非交互 Bash
- 可以在 BatchMode=yes 下工作的认证方式

## Roadmap

- 扩展更多开发板和 Linux 设备
- 完善模型调试工作流
- 连接仿真和真机开发过程
- 增加更多真实设备状态与诊断入口
- 改进安装、文档和新用户引导

[需要团队确认：是否公开更具体的 Roadmap 和预计版本]

## Project Status

[需要团队确认后填写：Alpha / Beta / Stable]

[需要团队确认后填写以下其中一种说明：]

方案一，暂不开源：

JishuBuddy is currently distributed as a product package. The source code is not publicly available at this time.

方案二，部分开源：

JishuBuddy currently publishes selected components and integrations. See each repository for its license and source availability.

方案三，完整开源：

JishuBuddy is open source under the [需要填写：许可证名称] license.

## Feedback

如果你在安装、连接开发板或实际调试中遇到问题，欢迎提交反馈。

[提交 Issue] · [查看文档] · [联系我们]

[需要链接：JishuBuddy Issues]
[需要链接：JishuBuddy 文档]
[需要链接：公开邮箱或反馈表单]

## Disclaimer

JishuBuddy 是独立项目，与 Raspberry Pi Ltd. 无隶属关系，也未获得其官方背书。
