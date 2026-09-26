<div align="center">

<img src="website/assets/logo.png" width="96" alt="OmniNex Logo"/>

# 天演玄机 · OmniNex

**浏览器里的拖拽式网络安全靶场 —— 拖设备、连网线、双击开终端/桌面**

[![Version](https://img.shields.io/badge/version-0.2.0-8b5cf6)](https://github.com/Vinglcez/OmniNex/releases)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20WSL2%20%7C%20Linux-3b82f6)]()
[![Frontend](https://img.shields.io/badge/React%20%2B%20TS%20%2B%20React%20Flow-22d3ee)]()
[![Backend](https://img.shields.io/badge/FastAPI%20%2B%20QEMU%20%2B%20Docker-34d399)]()
[![Use](https://img.shields.io/badge/use-security%20learning%20%26%20research-fbbf24)]()

[官网](https://github.com/Vinglcez/OmniNex) · [下载桌面版](website/downloads/OmniNex_0.2.0_x64-setup.exe) · [文档索引](docs/README.md) · [联系作者](#-联系作者)

</div>

---

## 🌌 这是什么？

**OmniNex（天演玄机）** 是一个可视化网络安全靶场编排平台：

> 拖拽设备到画布 → 鼠标连线组网 → 一键部署启动 → 双击开终端 / 图形桌面 → 发起渗透攻击

底层把**每条连线映射为真实的 Docker bridge / QEMU tap 网络**——「拓扑即网络」：
图上连通的设备真实互通，图上断开的设备真实隔离。用于**渗透测试演练、漏洞验证复现、攻防对抗教学**。

| | |
|:---:|:---:|
| **🌌 星云暗色主题 · 拓扑编排画布** | **🔍 连线工具 · 流量抓包（Wireshark 联动）** |
| <img src="website/assets/screen-nebula.png" width="470"/> | <img src="website/assets/screen-capture.png" width="470"/> |
| **🖥️ 双击设备 · Kali 图形桌面浮动窗** | **🌐 连线工具 · 流量代理（Burp 联动）** |
| <img src="website/assets/screen-dock.png" width="470"/> | <img src="website/assets/screen-proxy.png" width="470"/> |
| **🎨 8 套平台主题 · 一键切换** | **📋 拓扑模板库 · 6 套预置靶场** |
| <img src="docs/screenshots/theme-nebula-settings.png" width="470"/> | <img src="docs/screenshots/nebula-more-menu.png" width="470"/> |

<details>
<summary><b>📷 更多界面截图（点击展开）</b></summary>

| | |
|:---:|:---:|
| **☀️ 明亮主题 · 六节点实战拓扑（DMZ 企业架构）** | **🔍 抓包面板 · 实时协议解析** |
| <img src="website/assets/screen-topology.png" width="470"/> | <img src="docs/screenshots/link-tools-02-capture-panel.png" width="470"/> |

</details>

---

## ✨ 核心特性

### 🧲 拖拽式编排
- **设备面板**：路由器 / 交换机 / 防火墙 / 服务器 / Kali / DVWA / Vulhub 靶机等 30+ 内置设备，拖进来就能用
- **鼠标连线**：自动建节点、自动分配端口；右键设备 = 控制台 / 启动 / 停止 / 克隆 / 删除
- **快照系统**：一键创建快照 / 随时回滚 / 重命名 / 删除，支持克隆设备
- **模板库**：基础靶场 / DMZ 企业架构 / 办公内网 / 综合攻防 / One 精简，一键载入完整拓扑

### 🔌 拓扑即网络（真实虚拟化）
- 容器类设备走 **Docker**，虚拟机类设备走 **QEMU/KVM**，驱动可插拔、不可用自动回退模拟
- **每条连线 = 一个独立网桥**：交换机是二层广播域，直连是点对点链路，删线立即断网、复线立即恢复
- 网络类设备自动开启 IP 转发，路由器 / 防火墙跨网段转发行为与真实一致
- 顶栏运行时徽标实时显示 `模拟模式` / `docker+qemu`，可查看容器/虚拟机可用性详情

### 🛠️ 连线工具（渗透工作台）
- **流量抓包**：点任意连线即可开始抓包，实时解析 ARP/ICMP/TCP/HTTP，一键下载 `.pcap` 并联动本机 Wireshark
- **流量代理**：在链路上透明插入 TCP/HTTPS 代理（对接 Burp Suite），攻击机流量自动过代理
- **端口镜像**：复制目标端口流量到指定 host，便于旁路监听

### ⚔️ 攻击面板
- 选定攻击机与目标 → **端口扫描 / 漏洞利用 / 口令爆破 / 一键渗透**
- 攻击结果由「拓扑连通性 + 运行状态 + 目标类型」真实决定：**未连线 = 目标网络不可达**
- 攻击日志逐行回放（级别着色），渗透成功给出 FLAG

### 🖥️ Windows 桌面版（Tauri 2）
- 面向「不会配环境」的用户：双击 `OmniNex.exe` → **7 步环境体检**（Windows / WSL2 / Ubuntu / Docker / QEMU / KVM）→ 一切通过才放行
- Ubuntu 账户密码存入 **Windows 凭据管理器**，只经 stdin 传递，不落命令行
- 支持**上传自定义镜像**（`qcow2 / img / raw / docker tar`），拖出来就是一台专属服务器
- 与浏览器版**共用同一份前端与后端**，一个平台两种形态

---

## 🚀 用户使用方式

### 方式一 · Windows 桌面版（推荐给普通用户）

1. **下载安装包** [`OmniNex_0.2.0_x64-setup.exe`](website/downloads/OmniNex_0.2.0_x64-setup.exe)，双击安装
2. **启动 OmniNex**，程序自动开始环境体检：Windows 版本 → WSL2 → Ubuntu 发行版 → Docker/QEMU 逐项检测
   - 缺什么会给出**修复建议**，致命项不通过不能前进
3. **输入 Ubuntu 账户密码**（仅首次，密码存入 Windows 凭据管理器）
4. 体检全部通过 → **「一切准备就绪，开始你的天演之路吧！」** → 进入靶场画布
5. 开始演练：**拖设备 → 连线 → 点「部署/启动」→ 双击设备开终端 / 桌面 → 打开攻击面板发起渗透**

> 💡 顶栏「··· 更多 → 载入模板 → 快速体验」可一键生成开箱靶场（Alpine 虚拟机 + DVWA + 路由交换），
> 无需自备任何镜像即可跑通「连线 → 互通 → 攻击 → 拿 FLAG」全链路。

### 方式二 · 源码运行（本机模拟，无需 Docker）

```bash
# 1. 后端（Python FastAPI）
cd backend
python -m venv .venv && .venv/Scripts/pip install -r requirements.txt
python run.py                    # http://127.0.0.1:7150

# 2. 前端（React + Vite）
cd ../frontend
npm install
npm run dev                      # http://localhost:5173
```

浏览器打开 `http://localhost:5173`，拖两个设备 → 连线 → 启动 → 双击开终端 → `ping` 对端应互通。

### 方式三 · WSL2 真实虚拟化（容器 + 虚拟机真跑）

```bash
# 在 Ubuntu (WSL2) 中执行一次
bash deploy/wsl-setup.sh         # 装 Docker/QEMU + 配网络 + 注册 systemd 服务
```

Windows 端执行 `wsl --shutdown` 使组权限生效，之后开机自启；
浏览器打开 `http://localhost:7150`，顶栏徽标变为 `⚙ docker+qemu` 即真实模式。

```bash
sudo systemctl status omninex    # 后端状态
docker ps                        # 看真实跑起来的容器
bash deploy/run-tests.sh         # 跑全部 5 套验收脚本
```

<details>
<summary><b>📦 验收脚本（源码方式可选）</b></summary>

```bash
cd backend
python tests/test_closed_loop.py     # 闭环：拖拽 / 连线 / 互通
python tests/test_snapshot_clone.py  # 克隆 + 快照
python tests/test_templates.py       # 模板 + 快照管理
python tests/test_attack.py          # 攻击面板
python tests/test_phase2.py          # 真实虚拟化
python tests/test_custom_images.py   # 自定义镜像
```

</details>

---

## 📚 文档

| 文档 | 内容 |
|---|---|
| [docs/README.md](docs/README.md) | **文档总索引** ← 找文档先来这里 |
| [docs/00-项目概览.md](docs/00-项目概览.md) | 项目全貌 |
| [docs/01-入门/](docs/01-入门/) | 新手指南 / 平台介绍 / 快速上手 / 环境部署 |
| [docs/02-部署/](docs/02-部署/) | WSL 一键部署 / 前后端分离 / 打包发行 / 新机 checklist |
| [docs/03-架构与方案/](docs/03-架构与方案/) | Vulhub 集成 / 镜像仓库 / 需求文档 |
| [docs/04-授权/](docs/04-授权/) | 授权方案与使用手册 |
| [docs/05-排障/](docs/05-排障/排障手册.md) | 排障手册 |
| [desktop/README.md](desktop/README.md) | Windows 桌面版说明 |

---

## 🛠️ 技术栈

| 层 | 技术 |
|---|---|
| 前端 | React 18 + TypeScript + React Flow + xterm.js |
| 后端 | Python FastAPI + WebSocket |
| 虚拟化 | QEMU/KVM + Docker（驱动可插拔，无依赖时回退模拟） |
| 网络 | Linux Bridge（连线 → 网桥映射，增量重连） |
| 桌面 | Tauri 2（Rust：环境体检 / 凭据管理 / 镜像导入） |
| 授权 | Ed25519 离线签名验票 |

---

## 📇 联系作者

<div align="center">

<img src="wx.jpg" width="220" alt="作者微信二维码"/>

**微信扫码添加作者**

微信号：`L3Yia_` · GitHub：[Vinglcez/OmniNex](https://github.com/Vinglcez/OmniNex)

交流 / 授权 / 问题反馈 / 内测合作，欢迎添加

</div>

---

## ⚠️ 免责声明

本项目**仅供网络安全学习与研究使用**。请勿用于任何未经授权的测试或破坏行为，
使用者需对自己的行为负责。作者不承担任何因滥用本工具导致的法律责任。

<div align="center">

**天演玄机 · OmniNex** — *The nebula is your battlefield.* 🌌

</div>
