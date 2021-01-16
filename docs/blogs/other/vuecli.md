---
title: git多个账户在win10上的使用
date: 2021-01-16
categories:
 - other
tags:
 - vue/cli
 - vue
---



# 一、项目初始化



## 使用 Vue CLI 创建项目



> 注意：不要使用 Git Bash 执行项目创建操作，使用  cmd 或者 powershell 之类的工具。



> 如果你还没有安装 VueCLI，或者版本低于 4，请执行下面的命令安装或是升级：
>
> ```
> npm install --global @vue/cli
> ```



在命令行中输入以下命令创建 Vue 项目：



```
vue create toutiao-publish-admin
```



```
Vue CLI v4.2.3
? Please pick a preset:
  default (babel, eslint)
> Manually select features
```



> default：默认勾选 babel、eslint，回车之后直接进入装包
>
> manually：自定义勾选特性配置，选择完毕之后，才会进入装包
>
> 选择第 2 种：手动选择特性，支持更多自定义选项



```
? Please pick a preset: Manually select features
? Check the features needed for your project:
 (*) Babel
 ( ) TypeScript
 ( ) Progressive Web App (PWA) Support
 (*) Router
 ( ) Vuex
 (*) CSS Pre-processors
>(*) Linter / Formatter
 ( ) Unit Testing
 ( ) E2E Testing
```



> 分别选择：
> Babel：es6 转 es5
> Router：路由
> CSS Pre-processors：CSS 预处理器，后面会提示你选择 less、sass、stylus 等
> Linter / Formatter：代码格式校验，ESLint 代码格式校验



```
? Use history mode for router? (Requires proper server setup for index fallback in production) (Y/n) n
```



> 是否使用 history 路由模式，这里输入 `n` 不使用



```
? Pick a CSS pre-processor (PostCSS, Autoprefixer and CSS Modules are supported by default):
  Sass/SCSS (with dart-sass)
  Sass/SCSS (with node-sass)
> Less
  Stylus
```



> 选择 CSS 预处理器，这里选择我们熟悉的 Less



```
? Pick a linter / formatter config:
  ESLint with error prevention only
  ESLint + Airbnb config
> ESLint + Standard config
  ESLint + Prettier
```



> 选择校验工具，这里选择 ESLint + [Standard config](https://standardjs.com/)



```
? Pick additional lint features:
 (*) Lint on save
>(*) Lint and fix on commit
```



> 选择在什么时机下触发代码格式校验：
>
> - Lint on save：每当保存文件的时候
>
> - Lint and fix on commit：每当执行 `git commit` 提交的时候
>
> 这里建议两个都选上，更严谨。



```
? Where do you prefer placing config for Babel, ESLint, etc.? (Use arrow keys)
> In dedicated config files
  In package.json
```



> Babel、ESLint 等工具会有一些额外的配置文件，这里的意思是问你将这些工具相关的配置文件写到哪里：
>
> - In dedicated config files：分别保存到单独的配置文件
>
> - In package.json：保存到 package.json 文件中
>
> 这里建议选择第 1 个，保存到单独的配置文件，这样方便我们做自定义配置。



```
? Save this as a preset for future projects? (y/N) N
```



> 这里里是问你是否需要将刚才选择的一系列配置保存起来，然后它可以帮你记住上面的一系列选择，以便下次直接重用。



> 这里根据自己需要输入 y 或者 n，我这里输入 n 不需要。



```
✨  Creating project in C:\Users\LPZ\Desktop\topline-m-fe89\topline-m-89.
�  Initializing git repository...
⚙  Installing CLI plugins. This might take a while...

[          ........] - extract:object-keys: sill extract json5@2.1.1
```



> 向导配置结束，开始装包。
> 安装包的时间可能较长，请耐心等待......



```
⚓  Running completion hooks...

�  Generating README.md...

�  Successfully created project topline-m-89.
�  Get started with the following commands:

 $ cd topline-m
 $ npm run serve
```



安装结束，命令提示你项目创建成功，按照命令行的提示在终端中分别输入：



```
# 进入你的项目目录
cd toutiao-webapp

# 启动开发服务
npm run serve
```



```
 DONE  Compiled successfully in 7527ms


  App running at:
  - Local:   http://localhost:8080/
  - Network: http://192.168.10.216:8080/

  Note that the development build is not optimized.
  To create a production build, run npm run build.
```



> 启动成功，命令行中输出项目的 http 访问地址。
> 打开浏览器，输入其中任何一个地址进行访问。

::: right
来自 [bilibili](https://www.yuque.com/lipengzhou/toutiao-publish-vue/dkhzid)
:::