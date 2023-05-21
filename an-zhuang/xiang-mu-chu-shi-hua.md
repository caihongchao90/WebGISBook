---
description: 使用Vite脚手架创建的vue项目
---

# 😅 项目初始化

* 首先新建文件夹，并使用vscode打开，打开后在终端使用下面的命令，创建项目。

```javascript
npm init vite@latest 
npm install
npm run dev
```

&#x20;       创建完成后，将自己不需要的组件或者脚本删除，并插入自己的组件脚本，即可开始自己的代码编写工作。

* 安装openlayers库

&#x20;       三种引入方法分别是

> 1、CDN引入
>
> ```markup
> <script src="https://cdn.jsdelivr.net/npm/ol@v7.3.0/dist/ol.js"></script>
> <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/ol@v7.3.0/ol.css">
> ```
>
> 2、插件方法引入
>
> ```javascript
> npm install ol
> ```
>
> 3、本地引入
>
> 找到openlayers的源码，解压后有一个dist文件，里边有js源码，并在源码文件里找到ol.css文件，将这两个文件引入项目即可，比如下边这样
>
> ```markup
> <link rel="stylesheet" href = "./src/lib/dist/ol.css">
> <script src="./src/lib/dist/ol.js"></script>
> ```
