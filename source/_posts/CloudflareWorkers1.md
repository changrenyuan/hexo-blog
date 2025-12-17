---
title: cloudflare后端 API 

lang: zh
tags: 
    - web
date: 2025-12-17 09:40:52

---

# Hono + React Router + Vite + ShadCN UI on Cloudflare Workers

[](https://github.com/changrenyuan/react-router-hono-fullstack-template#hono--react-router--vite--shadcn-ui-on-cloudflare-workers)

[![部署到 Cloudflare](https://camo.githubusercontent.com/aa3de9a0130879a84691a2286f5302105d5f3554c5d0af4e3f2f24174eeeea25/68747470733a2f2f6465706c6f792e776f726b6572732e636c6f7564666c6172652e636f6d2f627574746f6e)](https://deploy.workers.cloudflare.com/?url=https://github.com/cloudflare/templates/tree/main/react-router-hono-fullstack-template) [![使用 Hono、React Router 和 ShadCN UI 在 Cloudflare Workers 上构建现代全栈应用程序](https://camo.githubusercontent.com/4138b893bc5fe5fb8f8852da15da862acf63ca353e79ae3fbcab7db632a9bc08/68747470733a2f2f696d61676564656c69766572792e6e65742f77534d594a76533358772d6e333339436244794449412f32346335613764642d653165332d343361392d623931322d6437386439613432393362632f7075626c6963)](https://camo.githubusercontent.com/4138b893bc5fe5fb8f8852da15da862acf63ca353e79ae3fbcab7db632a9bc08/68747470733a2f2f696d61676564656c69766572792e6e65742f77534d594a76533358772d6e333339436244794449412f32346335613764642d653165332d343361392d623931322d6437386439613432393362632f7075626c6963)

[这是一个由Cloudflare Workers](https://workers.cloudflare.com/)提供支持的现代全栈模板，使用[Hono](https://hono.dev/)实现后端 API，使用[React Router](https://reactrouter.com/)实现前端路由，并使用[shadcn/ui](https://ui.shadcn.com/)实现美观、易于访问的组件，这些组件使用[Tailwind CSS](https://tailwindcss.com/)进行样式设计。

[该应用使用Cloudflare Vite 插件](https://developers.cloudflare.com/workers/vite-plugin/)构建，以优化静态资源交付并实现无缝的本地开发。React 通过 Workers 配置为单页应用 (SPA) 模式。

这是一个完美的起点，可以以最少的配置构建交互式、样式化和边缘部署的单页应用程序 (SPA)。

## 特征

[](https://github.com/changrenyuan/react-router-hono-fullstack-template#features)

- ⚡ 基于 Cloudflare Workers 的全栈应用
- 🔁 Hono 用于后端 API 端点
- 🧭 React Router 用于客户端路由
- 🎨 ShadCN UI 与 Tailwind CSS 结合使用，实现组件和样式设计
- 🧱 基于文件的路由分离
- 🚀 适用于 Workers 的零配置 Vite 构建
- 🛠️ 使用 Wrangler 自动部署
- 🔎 内置可观测性，用于监控您的 Worker

## 技术栈

[](https://github.com/changrenyuan/react-router-hono-fullstack-template#tech-stack)

- **前端**：React + React Router + ShadCN UI
  
  - 基于 React Router 的 SPA 架构
  - 包含来自 ShadCN 的易于访问、可自定义主题的用户界面
  - 使用以实用性为先的 Tailwind CSS 进行样式设计
  - 使用 Vite 构建和优化

- **后端**：Hono on Cloudflare Workers
  
  - API路由通过Hono定义和处理`/api/*`
  - 支持类 REST 端点、CORS 和中间件

- **部署方式**：通过 Wrangler 部署 Cloudflare Workers
  
  - Vite插件会自动将前端和后端打包在一起。
  - 已在全球范围内部署于 Cloudflare 的边缘网络上

![](C:\Users\chang\AppData\Roaming\marktext\images\2025-12-17-09-41-53-image.png)

![](C:\Users\chang\AppData\Roaming\marktext\images\2025-12-17-09-41-53-image.png)
