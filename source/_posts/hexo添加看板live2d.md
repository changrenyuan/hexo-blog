---
title: hexo添加看板live2d
date: 2025-12-12 16:51:03
tags: 
    - skills
    - UI
categories: 
    - UI

---

搜到的基本上是安装插件

hexo-oh-my-live2d

太麻烦了。

只要自己加一段代码在scripts.ejs文件最末尾就好了。

```
<!-- ====== 看板娘 JS START ====== -->
<script src="https://unpkg.com/live2d-widget@3.1.4/lib/L2Dwidget.min.js"></script>
<script>
  L2Dwidget.init({
    model: {
      jsonPath: "https://unpkg.com/live2d-widget-model-z16@1.0.5/assets/z16.model.json",
      scale: 1
    },
    display: {
      position: "right",
      width: 150,
      height: 300,
      hOffset: 0,
      vOffset: -20
    },
    mobile: {
      show: false
    },
    react: {
      opacityDefault: 0.7,
      opacityOnHover: 0.95
    }
  });
</script>
<!-- ====== 看板娘 JS END ====== -->
```

[Live2d Cubism 2](https://imuncle.github.io/live2d/)  来选择直接喜欢的模型
