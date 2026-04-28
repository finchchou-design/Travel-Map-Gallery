# 🌍 Travel-Map-Gallery — 极简旅行地图相册

> **🚀 在线预览地址：[https://finchchou-design.github.io/Travel-Map-Gallery/](https://finchchou-design.github.io/Travel-Map-Gallery/)**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Leaflet](https://img.shields.io/badge/Leaflet-1.9.4-green.svg)](https://leafletjs.com/)

> 这不仅仅是一个在地图上打点的相册，它是一个追求极致性能与视觉交互的**硬件加速级旅行回忆录**。

本项目旨在解决传统 Web 地图（如 Leaflet）在长距离飞行平移时出现的**轨迹撕裂、闪烁以及性能卡顿**问题，通过底层 Canvas 渲染与纯原生 CSS 掩码动画，实现了真正的「德芙般丝滑」。

---

## ✨ 核心硬核特性

| 特性 | 说明 |
|------|------|
| 🚀 **终极防撕裂流水动画** | 彻底抛弃传统 JS 逐帧算坐标和 SVG 渲染。采用 `pathLength` 魔法与纯 CSS 硬件加速，即使地图进行跨大洋的剧烈缩放，轨迹连线也绝对不会发生「甩尾」、「反向抽动」或「闪现」。 |
| 🖼️ **桌面级八向无极缩放 PIP 悬浮窗** | 彻底重构的画中画（Picture-in-Picture）回放窗口。支持顶部磁性拖拽，以及四个角、四条边的八向无极拉伸，图片自动按比例完美适应，交互媲美原生桌面应用。 |
| 🚁 **智能防晕车运镜系统** | 根据照片间的物理距离自动切换镜头语言。同城短途（8km 内）采用平滑的 `panTo` 贴地滑行，跨城长途采用 `flyTo` 升空航拍，视角转换自然克制。 |
| 📍 **纯本地 EXIF 智能解析** | 在浏览器前端直接解析照片的经纬度和拍摄时间（基于 `exifr`），保护隐私，一键批量导入。 |
| 🎨 **Apple Maps 银灰蓝质感** | 定制的地图滤镜与高斯模糊（`backdrop-filter`）玻璃态 UI，剔除原生高德瓦片的土气，呈现干净克制的高级视觉。 |

---

## 🛠️ 技术栈

- **核心引擎**：HTML5 + Vanilla JavaScript + CSS3
- **地图基建**：Leaflet（强制挂载 Canvas Renderer）+ MarkerCluster
- **EXIF 解析**：exifr
- **样式框架**：Tailwind CSS（CDN）
- **数据存储**：IndexedDB（本地默认）/ Firebase（可选云端同步）

---

## 🚀 快速开始

本项目为**纯前端单文件应用**，零配置，开箱即用。

**1. 克隆或下载本项目：**

```bash
git clone https://github.com/你的用户名/TravelMapGallery.git
```

**2.** 双击打开 `Travel-Map-Gallery.html`。

**3.** 点击左侧面板的「添加回忆照片」，全选你的旅行照片（确保照片带有 GPS 位置信息）。

**4.** 点击播放按钮 🎬，享受你的专属旅途回放！

---

## ☁️ 云端同步：多端数据无缝连接

本项目默认采用 IndexedDB 本地存储，以保证极致的加载速度和绝对的隐私安全。如果你希望在手机上拍的照片，回家后在电脑地图上立刻看到，可以一键激活内置的 **Google Firebase 云端同步引擎**。

### 第一步：创建你的云端空间

1. 访问 [Firebase 控制台](https://console.firebase.google.com)
2. 点击「添加项目」，起一个你喜欢的名字
3. 按照引导完成创建（建议关闭 Google Analytics 以加快速度）

### 第二步：开启「数据大脑」(Firestore)

1. 在左侧菜单找到「构建」→「Firestore Database」
2. 点击「创建数据库」
3. 选择一个离你较近的服务器位置（如 `asia-east1`）
4. **关键**：选择「以测试模式启动」，最后点击确定

### 第三步：开启「免密登录」(Authentication)

1. 在左侧菜单找到「构建」→「Authentication」
2. 点击「开始使用」
3. 在「登录方法」标签页，选择「匿名 (Anonymous)」并开启开关，点击保存

> 匿名登录让不同设备能自动识别身份并隔离数据，无需输入账号密码。

### 第四步：获取代码钥匙并配置

1. 点击项目概览旁的齿轮图标 → 项目设置
2. 在「您的应用」里点击 Web 图标（`</>`），注册应用
3. 获取你的专属 Firebase Web 配置代码
4. 用文本编辑器打开 `Travel-Map-Gallery.html`，找到 `firebaseConfig` 变量区，取消注释并替换为你的专属密钥：

```javascript
const firebaseConfig = {
  apiKey: "你的_API_KEY",
  authDomain: "你的项目ID.firebaseapp.com",
  projectId: "你的项目ID",
  // ...
};
```

### ⚠️ 安全警告（非常重要）

> **永远不要公开你的真实密钥！**
> 填入真实密钥后的 HTML 文件是你个人的「私有云端版」。请**绝对不要**将包含真实 `apiKey` 的文件 Push 回公开的 GitHub 仓库，以免他人滥用耗尽你的免费云服务额度！
>
> **正确的开源方式**：在 GitHub 上分享或提交代码时，务必保持代码库中的 `firebaseConfig` 变量为 `null` 或占位符状态。

---

## 🤝 贡献与反馈

如果你在部署或使用过程中遇到任何 Bug，或者有更酷的功能建议，欢迎提交 [Issue](../../issues) 或发起 [Pull Request](../../pulls)。

---

## 📄 开源协议

本项目基于 [MIT License](./LICENSE) 开源，你可以自由地使用、修改和分发。
