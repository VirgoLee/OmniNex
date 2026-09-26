<div align="center">

<img src="https://github.com/user-attachments/assets/a0020c27-6e10-4c96-bb38-a7f6c20aff8e" width="96" alt="OmniNex"/>


# 天演玄机 · OmniNex

**可视化网络安全靶场编排平台 —— 拖设备、连网线、双击开终端 / 桌面**

![Version](https://img.shields.io/badge/version-0.2.0-8b5cf6)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20WSL2%20%7C%20Ubuntu-3b82f6)

</div>

---

## 🌌 这是什么？

**OmniNex（天演玄机）** 是一个可视化网络安全靶场编排平台：

> 拖拽设备到画布 → 鼠标连线组网 → 一键部署启动 → 双击开终端 / 图形桌面 → 发起渗透攻击

图上连通的设备**真实互通**，图上断开的设备**真实隔离**——你只管攻击，环境交给平台。
用于**渗透测试演练、漏洞验证复现、攻防对抗教学**。

---

## 📸 界面一览

<p align="center"><b>🌌 星云暗色主题 · 拓扑编排画布</b><br/>
<img width="1080" height="534" alt="nebula" src="https://github.com/user-attachments/assets/5772d5ae-07fa-4763-b3d4-30e6371ffbc1"  alt="拓扑画布"/></p>


<p align="center"><b>🔍 连线抓包 · 实时协议解析</b><br/>
<img width="1080" height="534" alt="capture" src="https://github.com/user-attachments/assets/53d38c07-f235-49a1-bbb9-3323e569db79" alt="连线抓包"/></p>

<p align="center"><b>🖥️ 双击设备 · Kali 图形桌面</b><br/>
<img width="1080" height="534" alt="dock" src="https://github.com/user-attachments/assets/a6538d7c-f79d-437c-97c4-81a5373779a4"alt="图形桌面"/></p>


<p align="center"><b>🌐 链路代理 · 对接 Burp Suite</b><br/>
<img width="1080" height="534" alt="proxy" src="https://github.com/user-attachments/assets/8845f9d4-9b34-4016-a309-38cbd451c0ea" alt="链路代理"/></p>


<p align="center"><b>🎨 多套主题 · 一键切换</b><br/>
<img width="1080" height="617" alt="settings" src="https://github.com/user-attachments/assets/1b4295f8-4789-4e3a-951e-b8e688d51f59" alt="主题设置"/></p>


<p align="center"><b>📋 拓扑模板库 · 一键载入完整靶场</b><br/>
<img width="1080" height="617" alt="more-menu" src="https://github.com/user-attachments/assets/7ac02f43-c96d-482c-b185-df6a104f1735" alt="模板库"/></p>


---

## ✨ 它能做什么

- 🧲 **拖拽式编排**：路由器 / 交换机 / 防火墙 / Kali / DVWA 等 30+ 设备拖进来就能用；鼠标连线自动组网，支持快照回滚与设备克隆
- 🔌 **拓扑即网络**：每条连线映射为真实网络——图上连通真实互通，删线立即断网、复线立即恢复
- 🔍 **流量抓包与代理**：点任意连线即可抓包并下载 pcap 联动 Wireshark；链路上可透明插入代理对接 Burp Suite
- 🖥️ **双击开图形桌面**：双击 Kali 等桌面型设备，直接弹出可交互图形桌面与终端
- 🎨 **多套主题**：星云暗色 / 默认浅色 / 森林 / 海贼王……总有一款是你的菜

---

## 🚀 使用方式

### 方式一 · Windows + WSL2（推荐，本机一键部署）

1. **下载安装包** `OmniNex_0.2.0_x64-setup.exe`（Releases 页），双击安装
2. **启动 OmniNex**，程序自动开始环境体检：Windows 版本 → WSL2 → Ubuntu 发行版 → Docker/QEMU 逐项检测，缺什么给修复建议
3. **输入 Ubuntu 账户密码**（仅首次，密码存入 Windows 凭据管理器）
4. **在 Ubuntu (WSL2) 里执行一次**：

   ```bash
   bash deploy/wsl-setup.sh
   ```

   然后 Windows 端执行 `wsl --shutdown`，之后后端**开机自启**，顶栏徽标变为 `⚙ docker+qemu` 即真实模式
5. 体检全部通过 → **「一切准备就绪，开始你的天演之路吧！」** → 拖设备 → 连线 → 部署 → 攻击

> 💡 顶栏「··· 更多 → 载入模板 → 快速体验」可一键生成开箱靶场，无需自备任何镜像。

### 方式二 · Windows exe + 独立 Ubuntu 主机（编译好的后端）

不需要 WSL，把**编译好的 Linux 后端**部署到任意 Ubuntu 主机（物理机 / 虚拟机 / 云主机均可）：

1. **下载两样东西**（Releases 页）：Windows 前端 `OmniNex_0.2.0_x64-setup.exe` + Linux 后端 `omninex-backend-linux.tar.gz`（**无需安装 Python**）
2. **Ubuntu 主机**：解包后一条命令启动，自动完成全部环境搭建：

   ```bash
   tar -xzf omninex-backend-linux.tar.gz
   cd omninex-backend-1804
   sudo ./start-omninex.sh
   ```

   `start-omninex.sh` 会自动检测并安装 Docker/QEMU/KVM、构建基础镜像、启动后端，可重复执行；包内自带服务文件可**开机自启**
3. **Windows 端**：安装并启动 OmniNex，连接设置里填 Ubuntu 主机 IP（默认端口 `7150`），顶栏显示后端已连接即部署成功
4. 开始演练，与方式一完全一致

> 💡 两种形态体验零差异：WSL 场景后端在 `localhost:7150`，独立主机场景后端在 `<主机IP>:7150`。

---

## 📇 联系作者

<div align="center">

<img src="assets/wx-qr.jpg" width="220" alt="作者微信二维码"/>

**微信扫码添加作者**

微信号：`L3Yia_` · GitHub：[Vinglcez/OmniNex](https://github.com/Vinglcez/OmniNex)

我用夸克网盘分享了「OmniNex天演玄机
链接：https://pan.quark.cn/s/63ac466ec44a
提取码：d4d2

交流 / 授权 / 问题反馈 / 内测合作，欢迎添加

</div>

---

## ⚠️ 免责声明

本项目**仅供网络安全学习与研究使用**。请勿用于任何未经授权的测试或破坏行为，
使用者需对自己的行为负责。作者不承担任何因滥用本工具导致的法律责任。

<div align="center">

**天演玄机 · OmniNex** — *The nebula is your battlefield.* 🌌

</div>
