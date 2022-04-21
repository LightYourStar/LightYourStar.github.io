---
title: 用hexo写一个博客
date: 2022-04-21 10:37:30
tags: hexo git github travisCi
---
### 在已经配置好git githua hexo travisCI的情况下 发布新的博客
创建新的md文件并编辑
```bash
cd D:/hexo
hexo new "yourBlogName"
vim source/_posts/yourBlogName.md
```
将创建的文件发布
```bash
hexo generate
```

写完后提交到本地仓库
```bash
git add source/_posts/yourBlogName.md
git commit source/_posts/yourBlogName.md
或者
git add .
git commit -a
wq并保存退出
```

推送到远程仓库
```bash
git push
```
