---
layout: post
title:  "Tailwindcss与Parcel 本地环境配置"
date:   2020-08-15 11:00:00 +0800
categories: web
preview: 介绍使用Parcel搭建本地开发Tailwindcss的环境
author: monsterooo
---

Parcel是Web应用的打包工具，使用它我们可以快速的创建一个本地开发环境。然后我们利用Parcel来构建Tailwindcss

## 1. 初始化项目

```shell
mkdir happy-tailwindcss && cd happy-tailwindcss
npm init -y
```

## 2. 安装Parcel与Tailwindcss

```shell
npm i --save-dev parcel-bundler
npm i --save tailwindcss # 安装tailwindcss包依赖
npx tailwindcss init --full # 初始化完整的配置文件
```

## 3. 创建项目文件

```shell
touch index.html style.pcss .sassrc postcss.config.js
```

## 4. 文件代码

index.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="/style.pcss" />
    <title>Happy-tailwindcss</title>
  </head>
  <body>
    <div class="p-3">
      Hello, World
    </div>
  </body>
</html>
```

style.pcss

```scss
@tailwind base;
@tailwind components;
@tailwind utilities;
```


.sassrc

```json
{
  "includePaths": ["node_modules"],
}
```

postcss.config.js

```javascript
module.exports = {
  plugins: ["tailwindcss"]
};
```

然后我们修改`package.json`的`scripts`为

```json
"scripts": {
  "start": "parcel s -p 3000 index.html"
}
```

最后我们运行命令，在浏览器打开`http://localhost:3000`即可

```shell
npm start
```