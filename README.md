## 🌍 TravelMapGallery (极简旅行地图相册)

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Leaflet](https://img.shields.io/badge/Leaflet-1.9.4-green.svg)](https://leafletjs.com/)

这不仅仅是一个在地图上打点的相册，它是一个**追求极致性能与视觉交互**的硬件加速级旅行回忆录。

本项目旨在解决传统 Web 地图（如 Leaflet）在长距离飞行平移时出现的轨迹撕裂、闪烁以及性能卡顿问题，通过底层 Canvas 渲染与纯原生 CSS 掩码动画，实现了真正的“德芙般丝滑”。

## ✨ 核心硬核特性

* 🚀 **终极防撕裂流水动画**：彻底抛弃传统的 JS 逐帧算坐标和 SVG 渲染。采用 `pathLength` 魔法与纯 CSS 硬件加速，即使地图进行跨大洋的剧烈缩放，轨迹连线也绝对不会发生“甩尾”、“反向抽动”或“闪现”。
* 🖼️ **桌面级八向无极缩放 PIP 悬浮窗**：彻底重构的画中画（Picture-in-Picture）回放窗口。支持顶部磁性拖拽，以及四个角、四条边的八向无极拉伸，图片自动按比例完美适应，交互媲美原生桌面应用。
* 🚁 **智能防晕车运镜系统**：根据照片间的物理距离自动切换镜头语言。同城短途（8km内）采用平滑的 `panTo` 贴地滑行，跨城长途采用 `flyTo` 升空航拍，视角转换自然克制。
* 📍 **纯本地 EXIF 智能解析**：在浏览器前端直接解析照片的经纬度和拍摄时间（基于 `exifr`），保护隐私，一键批量导入。
* 🎨 **Apple Maps 银灰蓝质感**：定制的地图滤镜与高斯模糊（Backdrop-filter）玻璃态 UI，剔除原生高德瓦片的土气，呈现干净克制的高级视觉。

## 🛠️ 技术栈

* **核心引擎**: HTML5 + Vanilla JavaScript + CSS3
* **地图基建**: [Leaflet](https://leafletjs.com/) (强制挂载 Canvas Renderer) + [MarkerCluster](https://github.com/Leaflet/Leaflet.markercluster)
* **EXIF 解析**: [exifr](https://github.com/MikeKovarik/exifr)
* **样式框架**: [Tailwind CSS](https://tailwindcss.com/) (CDN)
* **数据存储**: IndexedDB (本地默认) / Firebase (可选云端同步)

## 🚀 快速开始

本项目为纯前端单文件应用，零配置，开箱即用。

1. 克隆或下载本项目：
   ```bash
   git clone [https://github.com/你的用户名/TravelMapGallery.git](https://github.com/你的用户名/TravelMapGallery.git)
   
