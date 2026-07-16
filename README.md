# CodeLearn Studio

<div align="center">

🐍 一款基于 Tauri v2 + React + TypeScript 构建的跨平台桌面应用，用于交互式学习 Python 编程。

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.x-green.svg)](https://www.python.org/)
[![Tauri](https://img.shields.io/badge/Tauri-v2-23ffcb.svg)](https://tauri.app/)
[![React](https://img.shields.io/badge/React-v18-61dafb.svg)](https://react.dev/)

</div>

## ✨ 功能特性

- **双模式系统**：
  - 📖 **学习模式** — 60 节精心设计的 Python 教程，涵盖从零基础到精通的 10 大知识模块
  - 🏆 **闯关模式** — 30 个循序渐进的挑战练习，巩固所学知识
- **内置 Python 代码运行器**：在桌面应用中直接运行 Python 代码，无需离开应用
- **实时测试验证**：每节课和挑战都配有自动化测试用例，即时反馈
- **VS Code 风格界面**：深色主题，熟悉的编辑器体验
- **进度持久化**：自动保存学习进度到本地存储
- **提示系统**：卡壳时随时获取提示
- **跨平台支持**：Windows、macOS、Linux

## 📚 教程模块

| 模块 | 内容 |
|------|------|
| 基础入门 | print、运算符、变量、数据类型、输入与类型转换、布尔值、综合练习(BMI计算器) |
| 流程控制 | if/else/elif、逻辑运算、for/while 循环、break/continue、嵌套循环、综合练习(九九乘法表) |
| 数据结构 | 列表、元组、字典、集合、嵌套数据结构、综合练习(学生成绩管理) |
| 字符串与文本处理 | 字符串方法、切片与 f-string、文本统计、综合练习(回文判断) |
| 函数 | 定义与返回值、默认参数、可变参数、作用域、lambda、递归、综合练习(函数工具箱) |
| 面向对象编程 | 类与对象、方法与属性、类变量与静态方法、继承、多态、封装、综合练习(图形面积计算器) |
| 文件与异常 | 文件读写、多行数据处理、try/except、finally/else、自定义异常、综合练习(安全数据解析器) |
| 进阶特性 | 列表推导式、字典/集合推导式、生成器与 yield、装饰器、map/filter、enumerate/zip、综合练习(数据处理管道) |
| 模块与标准库 | import、datetime/random、JSON、collections、正则表达式、pathlib、综合练习(日志分析器) |
| 综合实战项目 | 记账本、成绩分析、词频分析、单元测试、待办事项应用(Capstone) |

## 🏗️ 技术栈

| 层次 | 技术 |
|------|------|
| 桌面框架 | Tauri v2 (Rust 后端) |
| 前端框架 | React 18 + TypeScript |
| 构建工具 | Vite 6 |
| 代码编辑器 | Monaco Editor |
| 样式 | 纯 CSS + CSS 自定义属性 |
| 后端执行 | Rust 调用系统 Python |

## 📁 项目结构

```
codelearn-studio/
├── src/                              # React 前端
│   ├── main.tsx                      # 入口文件
│   ├── App.tsx                       # 根组件：模式切换、状态管理
│   ├── App.css                       # 布局样式
│   ├── index.css                     # CSS 自定义属性（VS Code 深色主题）
│   ├── components/                   # React 组件
│   │   ├── Sidebar.tsx/.css          # 侧边栏（双模式导航）
│   │   ├── TutorialPanel.tsx/.css    # 教程面板
│   │   ├── EditorPanel.tsx/.css      # Monaco 编辑器 + 运行 + 测试
│   │   ├── ChallengePanel.tsx/.css   # 闯关模式 UI
│   │   ├── TerminalPanel.tsx/.css    # 终端面板（装饰用）
│   │   └── StatusBar.tsx/.css        # 状态栏
│   ├── hooks/
│   │   └── useCodeRunner.ts          # Python 代码执行 + 测试验证
│   ├── lib/
│   │   └── tauri.ts                  # Tauri invoke 封装
│   └── data/
│       ├── lessons.ts                # 60 节教程数据
│       └── challenges.ts             # 30 个挑战练习
├── src-tauri/                        # Rust/Tauri 后端
│   ├── src/
│   │   ├── main.rs                   # Tauri 入口 + Python 执行命令
│   │   └── lib.rs                    # 存根文件
│   ├── Cargo.toml                    # Rust 依赖
│   ├── tauri.conf.json               # Tauri 配置
│   └── icons/
│       └── icon.ico                  # 应用图标
├── package.json
├── tsconfig.json
├── vite.config.ts
├── index.html
└── CLAUDE.md
```

## 🚀 快速开始

### 前置要求

- **Node.js** 18+ 和 **npm**
- **Rust** 工具链（cargo、rustc）
- **Python** 3.x（用于代码执行）
- **Tauri CLI**：`npm install -g @tauri-apps/cli` 或使用 npx

### 安装与运行

```bash
# 进入项目目录
cd codelearn-studio

# 安装依赖
npm install

# 仅前端开发（Vite 开发服务器，端口 1420）
npm run dev

# 完整桌面应用开发（Vite 子进程 + Tauri 窗口）
npm run tauri dev

# 生产构建
npm run build

# 构建桌面应用安装包
npm run tauri build
```
或者通过安装包直接安装
### 重要说明

- `npm run dev` 仅在浏览器中运行前端开发服务器
- **代码执行功能（运行按钮）仅在 Tauri 桌面窗口中可用**，浏览器预览中无法执行 Python 代码
- Tauri 开发模式下，前端更改会通过 Vite 热更新自动刷新
- 生产构建产物输出到 `dist/` 目录
- 安装包输出到 `src-tauri/target/release/bundle/`

## 💾 数据存储

学习进度保存在浏览器 `localStorage` 中：

- `codelearn-state` — 学习模式进度：`{ completedLevels: number[] }`
- `challenge-progress` — 闯关模式进度：`{ completedChallenges: number[] }`

## 📄 许可证

MIT License
