---
title: 使用Hexo搭建个人博客
date: 2021-04-20 10:54:39
tags:
type: hexo
---
前提：在不想自己买云服务器搭建个人博客的情况下，可以使用Hexo配合GitHub Pages搭建个人博客。

## Hexo
[Hexo](https://hexo.io/zh-cn/) 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

### 安装前提
- [Node.js](https://nodejs.org/en/)((Node.js 版本需不低于 10.13，建议使用 Node.js 12.0 及以上版本))
- [git](https://git-scm.com/)

### 安装Hexo
全局安装
``` bash
npm install -g hexo-cli
```
局部安装
``` bash
npm install hexo
```

## 部署

### 创建Hexo项目
在空文件夹中执行下列命令，folder可填可不填（填了则会新建目录，不填则执行命令的文件夹必须为空，否则报错。）
``` bash
hexo init <folder>
cd <folder>
npm install
```

### 创建repository
GitHub中创建repository，如果你希望你的站点能通过 `<你的 GitHub 用户名>.github.io`域名访问，你的 repository 应该直接命名为 `<你的 GitHub 用户名>.github.io`。

### 推送repository
将Hexo项目中的<folder> 中的文件复制或剪贴到repository中。需要检查git忽略配置文件`.gitignore`文件中是否包含`public`。没有需要加上

### 注册并配置Travis CI 
1. 使用GitHub账号注册Travis CI
2. 注册后，配置权限，只访问刚创建的repository，而不是所有的repository
3. 将GitHub新建的[Personal Access Token](https://github.com/settings/tokens)，只勾选`repo`权限
4. 在Travis CI的repository设置页面，设置环境变量Name：GH_TOKEN，value：Github刚生成的Token确保 DISPLAY VALUE IN BUILD LOG 保持 不被勾选 避免你的 Token 泄漏。点击 Add 保存。
5. 在你的 Hexo 站点文件夹中新建一个 .travis.yml 文件并推送到GitHub：
``` bash
sudo: false
language: node_js
node_js:
  - 10 # use nodejs v10 LTS
cache: npm
branches:
  only:
    - master # build master branch only
script:
  - hexo generate # generate static files
deploy:
  provider: pages
  skip-cleanup: true
  github-token: $GH_TOKEN
  keep-history: true
  on:
    branch: master
  local-dir: public
```