# 📋 TODO List 待办事项应用

<div align="center">
  <p class="text-lg font-medium">本项目由阿里云ESA提供加速、计算和保护</p>
  <img src="esa.png" alt="阿里云ESA" style="max-width: 200px; margin: 16px 0;">
  <p class="text-lg font-medium text-blue-600">✨ 本项目全程使用AI完成 ✨</p>
</div>

<div align="center">
  <img src="https://img.shields.io/badge/Vue-3.x-brightgreen.svg" alt="Vue 3">
  <img src="https://img.shields.io/badge/Vite-5.x-blue.svg" alt="Vite">
  <img src="https://img.shields.io/badge/Tailwind%20CSS-3.x-purple.svg" alt="Tailwind CSS">
  <img src="https://img.shields.io/badge/License-MIT-green.svg" alt="MIT License">
</div>

<div align="center">
  <h3>一个现代化、响应式的TODO List应用</h3>
  <p>支持明亮/黑暗模式切换，数据本地存储，简洁美观的用户界面</p>
</div>

## ✨ 核心功能

<div align="center">
  <table style="width: 100%; border-collapse: collapse;">
    <tr>
      <td style="padding: 12px; text-align: center;">
        <div style="font-size: 2rem; margin-bottom: 8px;">📝</div>
        <div style="font-weight: bold;">任务管理</div>
        <div style="color: #666;">添加、删除、标记完成/未完成任务</div>
      </td>
      <td style="padding: 12px; text-align: center;">
        <div style="font-size: 2rem; margin-bottom: 8px;">🔍</div>
        <div style="font-weight: bold;">智能筛选</div>
        <div style="color: #666;">支持全部、已完成、未完成任务筛选</div>
      </td>
      <td style="padding: 12px; text-align: center;">
        <div style="font-size: 2rem; margin-bottom: 8px;">🌓</div>
        <div style="font-weight: bold;">主题切换</div>
        <div style="color: #666;">支持明亮/黑暗模式，自动保存主题偏好</div>
      </td>
    </tr>
    <tr>
      <td style="padding: 12px; text-align: center;">
        <div style="font-size: 2rem; margin-bottom: 8px;">💾</div>
        <div style="font-weight: bold;">数据持久化</div>
        <div style="color: #666;">localStorage存储，刷新页面不丢失</div>
      </td>
      <td style="padding: 12px; text-align: center;">
        <div style="font-size: 2rem; margin-bottom: 8px;">📱</div>
        <div style="font-weight: bold;">响应式设计</div>
        <div style="color: #666;">适配移动端和桌面端</div>
      </td>
      <td style="padding: 12px; text-align: center;">
        <div style="font-size: 2rem; margin-bottom: 8px;">🎨</div>
        <div style="font-weight: bold;">现代UI设计</div>
        <div style="color: #666;">简洁扁平设计，流畅动画效果</div>
      </td>
    </tr>
  </table>
</div>

## 🛠️ 技术栈

<div align="center">
  <div style="display: flex; flex-wrap: wrap; justify-content: center; gap: 16px;">
    <div style="background: #fff; padding: 20px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); width: 180px; text-align: center;">
      <div style="font-size: 3rem; margin-bottom: 8px;">⚡</div>
      <div style="font-weight: bold; margin-bottom: 4px;">Vue 3</div>
      <div style="color: #666; font-size: 0.9rem;">渐进式JavaScript框架</div>
    </div>
    <div style="background: #fff; padding: 20px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); width: 180px; text-align: center;">
      <div style="font-size: 3rem; margin-bottom: 8px;">🛠️</div>
      <div style="font-weight: bold; margin-bottom: 4px;">Vite</div>
      <div style="color: #666; font-size: 0.9rem;">下一代前端构建工具</div>
    </div>
    <div style="background: #fff; padding: 20px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); width: 180px; text-align: center;">
      <div style="font-size: 3rem; margin-bottom: 8px;">🎨</div>
      <div style="font-weight: bold; margin-bottom: 4px;">Tailwind CSS</div>
      <div style="color: #666; font-size: 0.9rem;">实用优先的CSS框架</div>
    </div>
    <div style="background: #fff; padding: 20px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); width: 180px; text-align: center;">
      <div style="font-size: 3rem; margin-bottom: 8px;">💾</div>
      <div style="font-weight: bold; margin-bottom: 4px;">localStorage</div>
      <div style="color: #666; font-size: 0.9rem;">浏览器本地存储方案</div>
    </div>
  </div>
</div>

## 📦 安装步骤

### 🚀 快速开始

```bash
# 1. 克隆仓库
git clone <repository-url>
cd ESA-TODO

# 2. 安装依赖
npm install

# 3. 启动开发服务器
npm run dev

# 4. 构建生产版本
npm run build
```

<div align="center">
  <div style="background: #f0f4ff; padding: 16px; border-radius: 8px; width: 100%; max-width: 600px; text-align: left;">
    <h4>📝 开发服务器信息</h4>
    <ul style="margin: 0; padding-left: 20px;">
      <li><strong>地址：</strong> http://localhost:5173</li>
      <li><strong>热更新：</strong> 支持自动刷新</li>
      <li><strong>构建产物：</strong> 生成在 `dist` 目录</li>
    </ul>
  </div>
</div>

## 🚀 使用说明

### 📝 添加任务

<div style="background: #f0f4ff; padding: 20px; border-radius: 10px; margin: 16px 0;">
  <div style="display: flex; align-items: center; gap: 12px; margin-bottom: 8px;">
    <div style="font-size: 1.5rem;">1️⃣</div>
    <div style="font-weight: bold;">在输入框中输入任务内容</div>
  </div>
  <div style="display: flex; align-items: center; gap: 12px;">
    <div style="font-size: 1.5rem;">2️⃣</div>
    <div style="font-weight: bold;">点击「添加」按钮或按回车键</div>
  </div>
</div>

### ✅ 管理任务

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 16px; margin: 16px 0;">
  <div style="background: #e8f5e9; padding: 20px; border-radius: 10px;">
    <div style="font-size: 2rem; margin-bottom: 12px;">✅</div>
    <div style="font-weight: bold; margin-bottom: 8px;">标记完成/未完成</div>
    <div style="color: #666;">点击任务前的复选框，轻松切换任务状态</div>
  </div>
  <div style="background: #ffebee; padding: 20px; border-radius: 10px;">
    <div style="font-size: 2rem; margin-bottom: 12px;">🗑️</div>
    <div style="font-weight: bold; margin-bottom: 8px;">删除任务</div>
    <div style="color: #666;">点击任务右侧的删除按钮，快速删除任务</div>
  </div>
</div>

### 🔍 筛选任务

<div style="background: #fff3e0; padding: 20px; border-radius: 10px; margin: 16px 0;">
  <div style="font-weight: bold; margin-bottom: 12px;">支持三种筛选模式：</div>
  <div style="display: flex; gap: 12px; flex-wrap: wrap;">
    <div style="background: #fff; padding: 10px 20px; border-radius: 20px; box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);">
      <strong>全部</strong> - 显示所有任务
    </div>
    <div style="background: #fff; padding: 10px 20px; border-radius: 20px; box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);">
      <strong>未完成</strong> - 只显示未完成的任务
    </div>
    <div style="background: #fff; padding: 10px 20px; border-radius: 20px; box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);">
      <strong>已完成</strong> - 只显示已完成的任务
    </div>
  </div>
</div>

### 🌓 切换主题

<div style="background: #f3e5f5; padding: 20px; border-radius: 10px; margin: 16px 0;">
  <div style="display: flex; align-items: center; gap: 12px; margin-bottom: 12px;">
    <div style="font-size: 2rem;">🌓</div>
    <div style="font-weight: bold;">主题切换</div>
  </div>
  <div style="color: #666;">
    点击右上角的主题切换按钮，在明亮模式和黑暗模式之间切换。
    主题偏好会自动保存到本地存储，下次访问时自动恢复。
  </div>
</div>

### 🧹 清除已完成任务

<div style="background: #e3f2fd; padding: 20px; border-radius: 10px; margin: 16px 0;">
  <div style="display: flex; align-items: center; gap: 12px; margin-bottom: 12px;">
    <div style="font-size: 2rem;">🧹</div>
    <div style="font-weight: bold;">清除已完成任务</div>
  </div>
  <div style="color: #666;">
    点击「清除已完成」按钮，一键删除所有已完成的任务，保持界面整洁。
  </div>
</div>

## 📁 项目结构

```
ESA-TODO/
├── src/                    # 源代码目录
│   ├── components/          # 组件目录
│   ├── assets/             # 静态资源（图片、图标等）
│   ├── App.vue             # 主应用组件
│   ├── main.js             # 应用入口文件
│   └── style.css           # 全局样式文件
├── index.html              # HTML模板文件
├── vite.config.js          # Vite构建配置
├── tailwind.config.js      # Tailwind CSS配置
├── postcss.config.js       # PostCSS配置
└── package.json            # 项目依赖和脚本配置
```

<div align="center">
  <div style="background: #f0f4ff; padding: 16px; border-radius: 8px; width: 100%; max-width: 600px; text-align: left;">
    <h4>📌 核心文件说明</h4>
    <ul style="margin: 0; padding-left: 20px;">
      <li><strong>App.vue</strong> - 主应用组件，包含所有功能实现</li>
      <li><strong>main.js</strong> - 应用入口，初始化Vue应用</li>
      <li><strong>tailwind.config.js</strong> - Tailwind CSS配置，包括暗色模式支持</li>
      <li><strong>style.css</strong> - 全局样式，包含Tailwind CSS基础指令</li>
    </ul>
  </div>
</div>

## 🎨 设计特点

### 🎯 色彩方案

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 16px; margin: 16px 0;">
  <div style="background: linear-gradient(135deg, #e0f2fe 0%, #f0f9ff 100%); padding: 20px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);">
    <div style="font-size: 2rem; margin-bottom: 12px;">☀️</div>
    <div style="font-weight: bold; margin-bottom: 8px;">明亮模式</div>
    <div style="color: #666;">蓝白色调，简洁清爽，适合日间使用</div>
  </div>
  <div style="background: linear-gradient(135deg, #1f2937 0%, #374151 100%); padding: 20px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); color: #fff;">
    <div style="font-size: 2rem; margin-bottom: 12px;">🌙</div>
    <div style="font-weight: bold; margin-bottom: 8px;">黑暗模式</div>
    <div style="opacity: 0.8;">黑色+紫色调，现代科技感，适合夜间使用</div>
  </div>
</div>

### 📐 布局设计

<div style="background: #f0f4ff; padding: 20px; border-radius: 10px; margin: 16px 0;">
  <div style="display: flex; align-items: center; gap: 12px; margin-bottom: 12px;">
    <div style="font-size: 2rem;">📋</div>
    <div>
      <div style="font-weight: bold;">卡片式布局</div>
      <div style="color: #666; font-size: 0.9rem;">清晰的视觉层次，良好的信息架构</div>
    </div>
    <div style="display: flex; align-items: center; gap: 12px;">
      <div style="font-size: 2rem;">✨</div>
      <div>
        <div style="font-weight: bold;">流畅动画</div>
        <div style="color: #666; font-size: 0.9rem;">平滑的过渡效果，即时的状态反馈</div>
      </div>
    </div>
    <div style="display: flex; align-items: center; gap: 12px;">
      <div style="font-size: 2rem;">📱</div>
      <div>
        <div style="font-weight: bold;">响应式设计</div>
        <div style="color: #666; font-size: 0.9rem;">适配不同屏幕尺寸，支持移动端和桌面端</div>
      </div>
    </div>
  </div>
</div>

## 🔧 开发说明

### 🌓 主题配置

主题切换功能通过Tailwind CSS的dark模式实现，配置在 `tailwind.config.js` 中：

```javascript
// tailwind.config.js
export default {
  // ...
  darkMode: 'class', // 使用类名切换暗色模式
  // ...
}
```

### 💾 数据存储

任务数据使用localStorage存储，关键函数：

| 函数名 | 功能描述 |
|-------|---------|
| `loadTodos()` | 从localStorage读取任务数据 |
| `saveTodos(todos)` | 将任务数据保存到localStorage |
| `watchEffect()` | 监听数据变化，自动保存到localStorage |

### 🧩 组件设计

使用Vue 3 Composition API开发，组件化设计，代码结构清晰，易于维护：

- 采用Composition API进行状态管理
- 组件化设计，功能模块清晰
- 响应式数据绑定，实时更新
- 简洁的代码风格，良好的可读性

## 📄 许可证

MIT License

## 🤝 贡献

欢迎提交Issue和Pull Request！

## 📞 联系方式

如有问题或建议，欢迎通过以下方式联系：
- 项目地址：<repository-url>
- 提交Issue：<repository-url>/issues

---

**享受高效的任务管理体验！** 🎉