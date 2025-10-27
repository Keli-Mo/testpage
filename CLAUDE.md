# CLAUDE.md

此文件为 Claude Code (claude.ai/code) 提供在此代码仓库中工作的指导。

## 项目概述

Global 是一个现代化的 HTML5 单页作品集模板，专为创意专业人士和代理机构设计。它具有平滑滚动导航、移动端响应式设计和触摸手势支持。

## 开发工作流程

本项目使用 **CodeKit** 进行构建处理。开发工作流程包括：

1. **Sass 编译**：编辑 `assets/css/` 中的 `.sass` 文件 - CodeKit 自动将 `main.sass` 编译为 `main.css`
2. **JavaScript 处理**：编辑 `functions.js` - CodeKit 处理压缩生成 `functions-min.js`
3. **资源优化**：图片应在添加到 `assets/img/` 之前进行优化

## 架构与结构

### 核心导航系统
模板使用基于部分的导航系统，由以下文件控制：
- `assets/js/functions.js`：主要导航逻辑，包含滚动处理和部分转换
- `assets/css/modules/`：各个部分的独立样式（intro、work、about、contact、hire）

### 关键组件
- **单页部分**：首页、作品、关于、联系、聘请我们
- **双重导航**：侧边导航（`side-nav`）和外部导航（`outer-nav`）
- **触摸手势**：通过 Hammer.js 集成实现移动端滑动导航
- **自定义滚动处理**：鼠标滚轮和键盘导航，带防抖功能

### CSS 架构（Sass）
```
assets/css/
├── main.sass              # 导入所有组件
├── base/                  # 基础样式（字体、变量、标准化）
├── layouts/               # 网格系统
└── modules/               # 组件特定样式
```

### JavaScript 依赖
- jQuery 2.2.4（DOM 操作）
- Hammer.js 2.0.8（触摸手势）
- 自定义 functions.js（导航和交互）

## 常见开发任务

### 添加新部分
1. 在 `index.html` 中创建新部分 HTML
2. 在 `assets/css/modules/` 中添加对应的 Sass 模块
3. 在 `assets/css/main.sass` 中导入新模块
4. 在 `assets/js/functions.js` 中更新导航

### 修改导航
导航逻辑集中在 `functions.js` 中：
- `updateHelper()`：处理部分转换
- `updateNavs()`：更新活动导航状态
- `updateContent()`：管理部分可见性和动画

### 样式更改
所有样式应通过 Sass 文件完成：
- 变量在 `assets/css/base/vars.sass` 中
- 组件样式在 `assets/css/modules/` 中
- 基础样式在 `assets/css/base/` 中

## 性能考虑

- 资源已预压缩 - 避免直接编辑压缩文件
- `assets/img/` 中的图片已针对网络进行优化
- CSS 和 JS 在生产环境中合并为单个文件
- 使用 CodeKit 进行所有编译任务以保持优化