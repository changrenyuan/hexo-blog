# **步骤 1：本地新建 Hexo 项目**

在你的新电脑执行：

```
hexo init my-blog 
cd my-blog 
npm install
```

现在你就有一个干净的 Hexo 博客。

---

# **步骤 2：创建 GitHub 仓库（保存 Hexo 源码）**

去 GitHub 新建一个仓库：

👉 名称示例：

```
hexo-source 
hexo-blog 
hexo-main
```

❗ 注意：不要勾选 README（保持仓库为空）

---

# **步骤 3：在本地初始化 Git & 推送源码**

在 my-blog 项目目录：

```
git init 
git add . 
git commit -m "init hexo source" 
git branch -M main git remote add origin https://github.com/你的用户名/hexo-source.git 
git push -u origin main
```

这样你的 Hexo 源码就永远安全地放在 GitHub 了。

---

# **步骤 4：设置部署到 username.github.io**

现在编辑项目根目录下的 `_config.yml`  
找到 `deploy:` 部分，改成：

```
deploy:
  type: git
  repo: https://github.com/你的用户名/你的用户名.github.io
  branch: main

```

---

# **步骤 5：安装部署插件**

```
`npm install hexo-deployer-git --save`
```

---

# **步骤 6：首次部署（生成 public 并推送到 pages 仓库）**

```
hexo clean
hexo g
hexo d

```

你将看到：

- public 内容推送到了 pages 仓库（username.github.io）

- 你的线上博客可以访问了 🎉

---

# 

以后写博客：

```
hexo new post "文章标题"
hexo g
hexo d

```

同步源码：

```
git add .
git commit -m "update"
git push

```

换电脑时：

```
git clone https://github.com/你的用户名/hexo-source.git
npm install

```

继续写。