---
title: 构建个人域名 + GitHub Pages + cloudflare后端 API 的完整攻略

lang: zh
tags: 
    - web
date: 2025-12-16 10:34:52

---

本文记录我在搭建个人网站和 API 服务过程中遇到的问题、解决方案以及最终实现的流程，适合个人开发者参考和复用。

---

## 背景与需求

我有以下需求：

1. **博客前端**：使用 GitHub Pages 托管静态博客。  
2. **后端 API**：提供一些接口（例如 `/api/message`），需要一个轻量后端。  
3. **自定义域名**：`yikii.cn`，包括 `blog.yikii.cn` 和 `api.yikii.cn`。  
4. **邮箱**：使用飞书邮箱。  
5. **HTTPS 和 CDN**：保证访问安全和加速。  

---

## 遇到的问题

1. GitHub Pages 只能托管静态内容，无法提供后端 API。  

2. Worker 路由问题：
   
   - 前端请求 `https://api.yikii.cn/api/message/` 报 404。  
   - 报错 `blocked by CORS policy`。   

3. DNS / 域名解析问题：
   
   为了解决cors错误，只能尝试把dns解析从原运营商转移到cloudflare。

4. 路径和 HTTP 方法不对齐：
   
   - Worker 路由严格匹配 `/api/message`，多余的 `/` 或 POST 方法未注册会导致 404。  

---

## 解决方案与流程

### 域名注册与 DNS

- 域名仍在原注册商（火山引擎）注册。  

- 将 **NS 指向 Cloudflare**，统一管理解析。  

- 在 Cloudflare DNS 配置：
  
  ```text
  blog.yikii.cn → changrenyuan.github.io  # CNAME，开启 CDN/HTTPS
  api.yikii.cn  → blog-backend.changrenyuan.workers.dev  # CNAME
  www.yikii.cn  → blog.yikii.cn  # CNAME
  MX / TXT 解析配置飞书邮箱
  ```
