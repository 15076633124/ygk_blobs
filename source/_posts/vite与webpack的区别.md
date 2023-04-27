---
title: vite和webpack的区别
date: 
# comments: true         true false默认不写
tags: vite和webpack的区别
description: vite和webpack的区别
categories: 前端
---
<img src="/images/vite与webpack.jpg"   />
<!--more-->

## vite

一种新型前端构建工具，能够显著提升前端开发体验。它由两部分组成：

- 开发服务器：它是基于 [原生 ES 模块](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules) 提供了  [丰富的内建功能](https://cn.vitejs.dev/guide/features.html)，例如  [模块热更新（HMR）](https://cn.vitejs.dev/guide/features.html#hot-module-replacement) 
- 一套构建指令，它基于 [Rollup](https://rollupjs.org/) 打包代码，并且是预配置的，可输出于生产环境的高度优化过的静态资源

Vite 提供开箱即用的配置，同时它的  [插件 API](https://cn.vitejs.dev/guide/api-plugin.html)  和 [JavaScript API](https://cn.vitejs.dev/guide/api-javascript.html) 带来了高度的可扩展性，并有完整的类型支持。

![vite](/images/vite.png)

## webpack

本质上，**webpack** 是一个用于现代 JavaScript 应用程序的 *静态模块打包工具*。当 webpack 处理应用程序时，它会在内部从一个或多个入口点构建一个 [依赖图(dependency graph)](https://webpack.docschina.org/concepts/dependency-graph/)，然后将你项目中所需的每一个模块组合成一个或多个 *bundles*，它们均为静态资源，用于展示你的内容。

![webpack](/images/webpack.png)

## vite 和 webpack的区别

- vite 是一个快速构建工具，适用于小型项目和快速原型开发。它使用 ES模块作为开发模式，可以快速启动开发服务器，支持热更新和快速构建
- webpack 是一个功能强大的构建工具，适用于大型项目和复杂的构建需求。它可以处理各种类型的文件，支持代码分割、懒加载、优化和压缩等功能，可以满足更多的构建需求
- 区别：Vite 和 Webpack都是 JavaScript 应用程序的构建工具，它们的共同目标都是将应用程序源代码转换为可部署的 JavaScript、HTML、CSS。
  - 构建方式
    - Vite 是一种 “零配置” 构建工具，使用 Rollup 进行快速的开发环境构建，同时支持基于插件的定制。在开发模式下 Vite 使用 ES modules 来直接引入模块，而不是打包所有代码，因此启动时间非常快。生产模式下，Vite 会对所有模块进行打包和压缩
    - webpack 则需要一个配置文件来定义如何构建应用程序

