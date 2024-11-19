---
title: 前8课围绕NUXT的个人知识总结
description: Nuxt3学习笔记，包括安装、目录结构、组件、路由和内容管理等基础知识
tags: 
  - Nuxt3
  - Vue
  - Web开发
  - 学习笔记
author: 学习者
date: 2024-01-19
cover: /images/nuxt-learning.png
---

## 前8课围绕NUXT的个人知识总结
### nuxt的安装和启动
##### 前置要求:
安装 node
安装 npm

##### 安装并创建nuxt项目
- 使用npx安装
```
npx nuxi@latest init <project-name>
```
#### 安装 nuxtUI
```
npm install -S @nuxt/ui
```
#### 启动项目
```
cd <project-name>
npm run dev
```
### nuxt目录结构
```
📁 your-project/
├─ 📁 .nuxt/          # 构建目录
├─ 📁 assets/         # 资源文件
├─ 📁 components/     # 组件目录
├─ 📁 composables/    # 组合式函数
├─ 📁 content/        # 内容目录
├─ 📁 layouts/        # 布局文件
├─ 📁 pages/          # 页面文件
├─ 📁 plugins/        # 插件目录
├─ 📁 public/         # 静态文件
├─ 🗒️ app.vue         # 应用入口
├─ 🗒️ nuxt.config.ts  # Nuxt配置文件
└─ 🗒️ package.json    # 项目配置文件
```
### 认识app.vue
app.vue是Nuxt3应用的入口文件，它定义了应用的布局和全局组件。
### 认识pages目录
Pages目录是Nuxt3中用于创建页面和路由的特殊目录。当你在pages目录中创建.vue文件时，Nuxt会自动为你生成对应的路由。
例如创建一个首页代码如下，使用 template 标签包裹内容
```
<!-- pages/index.vue -->
<template>
  <div>
    <h1>欢迎来到我的网站</h1>
    <p>这是首页内容</p>
  </div>
</template>
```
### 认识< NuxtPage >组件
<NuxtPage> 是 Nuxt3 的核心组件，用于渲染 pages/ 目录中的页面内容。
<NuxtPage> 组件用于显示位于 pages/ 目录中的页面。它应该在 app.vue 中使用。
```
📁 项目结构
├─ 📄 app.vue            # 使用 <NuxtPage/> 的主文件
└─ 📁 pages/             # 页面目录
   ├─ 📄 index.vue       # 首页 (/)
   ├─ 📄 about.vue       # 关于页 (/about)
   └─ 📁 blog/           # 博客目录
      ├─ 📄 index.vue    # 博客列表页 (/blog)
      └─ 📄 [id].vue     # 博客详情页 (/blog/123)
```
此时 app.vue 的代码如下
```
<!-- app.vue -->
<template>
  <div>
      <NuxtPage />
  </div>
</template>
```

### 认识 [...slug]
```
[...slug]是 Nuxt3 中的一种动态路由，它可以捕获多个路由段。
用法：

pages/
└─ [...slug].vue
```
这个vue文件将匹配任意深度的路径，但具体路由将优先于[...slug]，例如：/about.vue 会优先于 [...slug].vue
[...slug]像一个兜底或规则夹缝中的省力方案
##此时你应该可以完成hello world了!!

### 认识components目录
components/ 目录用于存放所有Vue组件，这些组件可以被导入到页面、布局或其他组件中
组件就像是"乐高积木"，是可以重复使用的代码块。它们就像一个个小部件，可以组合成一个完整的页面。例如博客文章页面可以分为头部、内容、底部、评论等组件。
组件的三个部分

```
<!-- components/TheFooter.vue -->
<template>
  <!-- 这里footer 组件 -->
  <div>我是 footer</div>
</template>
<script setup>
// 这里写JavaScript逻辑
</script>
<style scoped>
/* 这里写CSS样式 */
</style>
```

#### pages目录中的vue文件制作页面，components目录中的vue文件组成页面中的复用部分，包括可用于 app.vue
#### 使用时，直接在页面中引用组件名，组件名称要一致且区分大小写TheFooter.vue 对应 <TheFooter />

```
<!-- app.vue -->
<template>
  <div class="app">
    <!-- 使用Header组件 -->
    <TheHeader />

    <!-- 页面主体内容 -->
    <main class="main-content">
      <NuxtPage />
    </main>

    <!-- 使用Footer组件 -->
    <TheFooter />
  </div>
</template>
```
### 认识 #### < NuxtLink >
#### < NuxtLink > 是 Nuxt3 提供的内置组件，用于页面间导航，它是 Vue Router 的 <router-link> 的增强版本。
内部链接跳转
```
<template>
  <NuxtLink to="/about">
    关于页面
  </NuxtLink>
  <!-- <a href="/about">...</a> (+Vue Router & prefetching) -->
</template>
```
外部链接跳转
```
<template>
  <NuxtLink to="https://nuxtjs.org">
    Nuxt 网站
  </NuxtLink>
  <!-- <a href="https://nuxtjs.org" rel="noopener noreferrer">...</a> -->
</template>
```

### 认识layouts目录
Layouts 目录用于存放页面布局组件，可以包含页面的公共部分，如页眉、页脚、侧边栏等。
添加 <NuxtLayout>，可以启用布局
在布局文件中，页面的内容将显示在 <slot /> 组件中
```
layouts/
├─ default.vue     # 默认布局
├─ auth.vue        # 登录注册页面布局
└─ blog.vue        # 博客页面布局
```
default布局示例

```
<!-- layouts/default.vue -->
<template>
  <div class="bg-sky-100 py-2">
    <p class="px-6 py-4 text-2xl text-gray-700">这是default布局，全部页面都会使用到</p>
    <slot />
  </div>
</template>

```
default 布局使用<slot />将页面内容加载
Components中的组件可以加入布局中，如下
```
// layouts/default.vue
<template>
  <div>
    <TheHeader />
    <slot />
    <TheFooter />
  </div>
</template>
```
在 app.vue 中使用<NuxtLayout>来使用layouts/default.vue 布局
```
// app.vue
<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>
```
这时候如果制作一张首页pages/index.vue，效果如下
```
// pages/index.vue
<template>
  <div>
    <h3>Home Page</h3>
  </div>
</template>
```
![这是图片](/public/首页布局.png)

layouts/ 目录用于存放布局组件。在上述示例中，我们有一个名为 default.vue 的布局组件。
pages/ 目录用于存放页面组件。例如，我们有一个名为 index.vue 的页面组件。
app.vue 是根组件，它将布局应用于页面组件。

#### 附加知识：单独指定布局的附加知识，例如 main 布局
```
layouts
|—— default.vue
|—— main.vue
```
```
// layouts/main.vue
<template>
  <div>
    <h2>Main Layout</h2>
    <slot />
  </div>
</template>
```
例如在 index.vue 中使用
```
// pages/index.vue
<template>
  <div>...</div>
</template>

<script setup>
definePageMeta({
  layout: 'main'
});
</script>
```
### 认识content 目录
使用 content/ 目录为你的应用创建一个基于文件的内容管理系统（CMS），创建一个文件产生一条内容。
Nuxt Content会读取你项目中的content/目录，并解析.md、.yml、.csv和.json文件，为你的应用创建基于文件的内容管理系统。
安装@nuxt/content模块，并通过以下命令将其添加到nuxt.config.ts中
```
npx nuxi module add content
```
然后，在 content 目录中创建 md 格式的文件，就相当于发布了一篇文章 例如：content/index.md
路由示例：
```
content/
├─ index.md           # / (首页)
├─ about.md           # /about
├─ blog/
│  ├─ index.md        # /blog首页
│  ├─ post-1.md       # /blog/post-1 博客文章页
│  └─ post-2.md       # /blog/post-2
└─ products/
   ├─ index.md        # /products首页
   └─ item-1.md       # /products/item-1 产品详情页
```
### 认识content中的content-list
ContentList 是 Nuxt Content 提供的组件，用于列出和显示内容目录中的文件列表。
示例代码如下
```
<template>
  <main>
    <!-- ContentList 组件 -->
    <!-- path="/articles" 指定要获取的内容路径，将读取 content/articles 目录下的内容 -->
    <!-- v-slot="{ list }" 使用解构获取内容列表数据 -->
    <ContentList path="/articles" v-slot="{ list }">
      <!--  循环渲染文章列表 -->
      <!-- v-for="article in list" 遍历list数组中的每篇文章 -->
      <!-- :key="article._path" 使用文章路径作为唯一标识符 -->
      <div v-for="article in list" :key="article._path">
        <!--  显示文章标题 -->
        <h2>{{ article.title }}</h2>
        <!--  显示文章描述 -->
        <p>{{ article.description }}</p>
      </div>
    </ContentList>
  </main>
</template>
```
```
PATH路径的逻辑:
    / - 读取 content 根目录
    /blog - 读取 content/blog 目录下的文件
    /docs/guide - 读取 content/docs/guide 目录
```

## "理解为乐高或者 Minecraft 的话，components 是零件，layout 是图纸，选取一张图纸，他会自动帮你找零件组合，而 pages 里面是你创建的每个世界"
## app.vue是根，分发各个 pages 内容，pages 加载 layouts 图纸，图纸找各个components 零件组合
