---
title: 使用 hexo 与 github pages 构建个人博客的总结
date: 2019-03-15 17:31:38
tags:
---

### 前置知识

需要 yarn, git

### 安装 hexo

首先要安装 hexo, 我个人不喜欢装在全局, 所以这里将其装在了本地 hexo 目录下

可以根据需要自己决定

另外, 我使用了 yarn 代替 npm (其实不用说吧?)

```sh
mkdir hexo
cd hexo/
yarn add hexo
```

### 初始化项目

初始化项目, blog 是项目名, 根据需要自己更改

```sh
yarn hexo init blog
```

### 安装依赖

移动到项目目录下, 初始化 git, 安装依赖

```sh
cd blog
git init
yarn install
```

为了使用 github pages, 首先要有 github 上的仓库. 这里就不多说了.

#### 添加 git deployer

安装 git deployer

```sh
yarn add hexo-deployer-git
```

### 修改 _comfig.yml 文件

#### #URL 部分

URL 部分要修改一下 url 和 root, 需要和实际的根目录匹配, 不然找不到正确的静态资源地址

```yml
# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: https://gyongyon.github.io/blog/
root: /blog
permalink: :year/:month/:day/:title/
permalink_defaults:
```

#### deploy 属性

type 为 git

repo 就是仓库地址

branch 推荐 gh-pages

```yml
deploy:
  type: git
  repo: https://github.com/GyonGyon/blog.git
  branch: gh-pages
```

### 部署

生成静态资源

```sh
yarn hexo generator
```

部署到 github

```sh
yarn hexo deploy
```

这样就有了初始化的博客

### node 脚本

为了更方便, 可以修改 package.json

```json
"scripts": {
    "new": "hexo new",
    "server": "hexo server",
    "build": "hexo generate",
    "predeploy": "yarn build",
    "deploy": "hexo deploy"
  }
```

| 控制台命令      | 作用                          |
| --------------- | ----------------------------- |
| yarn new "post" | 新建文档, post 是自定的文件名 |
| yarn server     | 起本地测试                    |
| yarn build      | 生成静态资源                  |
| yarn deploy     | 部署到 github                 |

### 写文章

```sh
yarn new "post"
```

会生成 post.md 文件, 在 `./source/_post/` 目录下.

然后修改其内容即可. 这里推荐下 [typora](https://typora.io/), 是简洁好用美观还免费的 markdown 编辑器.

其他的就看 [hexo 文档吧](https://hexo.io/zh-cn/docs/)

