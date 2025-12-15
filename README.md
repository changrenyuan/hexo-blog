# **第一步：重建 Hexo + 安装 Cactus**

假设你已经在新电脑执行了：

```
hexo init my-blog
cd my-blog
npm install

```

### **1️⃣ 安装 Cactus 主题**

```
cd themes
git clone https://github.com/probberechts/hexo-theme-cactus.git cactus
ll

```

然后在 `_config.yml` 中设置：

`theme: cactus`

保存后，你可以先预览：

`hexo s`

访问 http://localhost:4000 ，看看主题是否正常。

---

### **2️⃣ 初始化 Git 并推送 Hexo 源码**

```
cd my-blog
git init
git add .
git commit -m "init hexo source with cactus theme"
git branch -M main
git remote add origin https://github.com/你的用户名/hexo-source.git
git push -u origin main


```

### **3️⃣ 配置部署到 GitHub Pages**

在 `_config.yml`：

```
deploy:
  type: git
  repo: https://github.com/你的用户名/你的用户名.github.io
  branch: main

```

`npm install hexo-deployer-git --save`

部署：

```
hexo clean
hexo g
hexo d


```