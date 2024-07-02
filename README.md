## 内容（前端）

### 所用技术

1. 前端“三大件”及其作用：`HTML`、`CSS`、`JS`。

 ```Plain
  HTML (HyperText Markup Language)：是网页的基础，用于构建和设计网页的结构。它由一系列的标签（<xxx>）组成，这些标签定义了网页内容的类型和结构，如标题、段落、列表、链接、图片等。
  CSS (Cascading Style Sheets)：负责网页的表现和样式。它允许开发者控制网页的视觉元素，如颜色、字体、间距、布局等。
  JS（JavaScript）：是一种脚本语言（与Java、C等并列），用于增强网页的交互性。它可以处理用户事件（如点击、滚动）、操作DOM（文档对象模型）、发送异步请求（如 AJAX）、以及执行复杂的逻辑和数据处理。
 ```

2. `Vue`框架如何利用`.vue`文件组合“三大件”。

 ```Plain
  一个.vue文件的模板如下：
  <script>
  </script>
  
  <template>
  </template>
  
  <style>
  </style>
  
  在 .vue 文件中，<template> 标签用于定义组件的 HTML 结构。这是用户界面的骨架，可以包含 HTML 标签、Vue 指令（如 v-bind、v-if、v-for 等）以及插槽（slots）。
  <style> 标签用于定义组件的样式。在 <style> 标签内，你可以使用普通的 CSS 来为模板中的元素添加样式。
  <script> 标签包含了组件的 JavaScript 逻辑。在这里，你可以定义组件的数据（data）、计算属性（computed）、方法（methods）、生命周期钩子（如 created、mounted 等）以及任何其他需要的逻辑。
 ```

3. 本项目所采用的`Vue3`框架相对于`Vue2`的优点。

 ```Plain
  性能提升：Vue3使用了基于Proxy的响应式系统，相比Vue2提供了更好的性能和更多的语言特性支持。渲染性能得到了优化。通过Tree shaking和更高效的代码生成策略，减少了不必要的代码和模块。
  Composition API：Vue 3引入了组合式API，提供了setup、ref、reactive等函数，使得组件逻辑更加模块化，便于复用和测试。组合式API与TypeScript的集成更为紧密，有更好的TypeScript支持。
  全局API和应用实例的变化：Vue 3引入了应用实例的概念，改变了全局API的使用方式，比如使用createApp替代了Vue构造函数（main.ts文件中），促进了更好的代码模块化和封装。
  函数式组件：Vue3鼓励使用函数式组件，这种组件类型更轻量，且易于优化。
 ```

4. 本项目所采用的`TypeScript`相较于`JavaScript`的优点与要求。

 ```Plain
  TypeScript是JavaScript的超集，正如名字中的“Type”所表示的，它引入了静态类型系统，可以在编译时捕获潜在的错误，提高代码的可维护性和可读性。
  因此，在代码编写过程中必须声明好每一个变量的类型，并确保使用时类型匹配，即不把A类型的值赋值给B类型的变量。
 ```

5. `node.js`的作用。

 ```Plain
  Node.js是一个JavaScript运行环境，它允许开发者使用JavaScript编写服务器端代码（当然也能允许TypeScript）。它还提供了一个包管理器npm（Node Package Manager），这是全球最大的开源库生态系统，允许开发者安装和管理第三方库。
 ```

6. 本项目采用`Vite`构建工具。

 ```Plain
   Vite是一个现代化的前端构建工具，核心优势在于它在开发阶段使用原生ES模块和高效的服务器，而在构建阶段使用Rollup进行代码打包，这使得它在开发时非常快速，同时在生产环境中也能输出高度优化的静态资源。
   Node.js和Vite在web开发中可以相互配合使用。Node.js提供了服务器端的运行环境，而Vite专注于前端项目的构建和开发服务器。在实际项目中，开发者可能会使用Node.js来搭建服务器端逻辑，同时使用Vite来构建和管理前端资源。
 ```

7. 本项目采用`Element-plus`UI设计工具。

 ```Plain
   Element Plus是一个基于Vue3的组件库，提供了一套完整的UI组件，用于快速构建高质量的用户界面。网址在https://element-plus.org/zh-CN/component/overview.html。
 ```

8. 使用sessionStorage存储用户身份数据。

### 项目结构

以下是一些重要文件，其他辅助文件的作用已注释在文件最上方。

/src是项目的主要源代码目录，包含了所有的Vue组件、配置文件、静态资源等。

#### 2.1. /src/components

组件目录，存放可复用的Vue组件文件。

#### 2.2. /src/views

视图目录，存放页面级别的组件，对应应用的不同路由，会在其中包含页面的布局和导航逻辑。

#### 2.3. /src/router

路由目录，存放路由配置文件，定义了应用的路由规则和导航守卫。

#### 2.4. /src/api

API请求目录，包含处理与后端服务器通信的API请求逻辑。我们项目中采用了Axios客户端库。

```Plain
axios函数可以接收三个参数：url、data 和 config。
1. url (必需): 这是一个字符串，表示你想要请求的服务器地址。例如：'https://api.example.com/data'。
2. data (可选): 这是一个对象，包含了你想要发送到服务器的数据。这个参数通常用于 POST、PUT 或 PATCH 请求。例如：{ key1: 'value1', key2: 'value2' }。当使用 POST 方法时，这些数据会被添加到请求体中。
3. config (可选): 这是一个对象，包含了请求的配置选项。这个对象可以包含多个属性，用于定制请求的行为。以下是一些常用的配置选项：
（1）headers: 一个对象，包含了你想要设置的HTTP请求头部。
（2）params: 一个对象，包含了你想要添加到URL查询字符串中的参数。
（3）responseType: 一个字符串，指定服务器响应的数据类型。可以是 'arraybuffer', 'blob', 'document', 'json', 'text' 或 'stream'。

对于前面介绍的三种传递参数的方法：
1. @PathVariable注解
视为url参数中的变量，使用axios.post(url/${xxx}, data, config)，其中data、config都可以省略     
2. @RequestParam注解
视为config参数中的params，使用axios.post(url, data, {params: xxx}) ，其中data不可省略，如果是空就用null填补，不然会把config当成data
3. @RequestBody注解
视为data参数，使用axios.post(url, data, config)，其中config可以省略 
```

#### 2.5. /src/assets

静态资源目录，存放图片、CSS样式表、字体文件等静态资源。

#### 2.6. /src/utils

工具函数目录，包含项目中使用的各种辅助函数和工具类，如日期处理、字符串操作、请求封装（request.ts）等。

#### 2.7. /src/**App.vue**

根组件，所有界面都是从这个界面发展来的，包含了应用的全局布局和导航。通过<router-view />来表示：展示当前router路由对应的界面。

#### 2.8. /src/**main.ts**

入口文件，用于创建Vue实例，引入全局样式、插件、路由、状态管理等。

#### 2.9. index.html

入口HTML文件，Vue实例将挂载到这个元素上。

#### 2.10. package.json

依赖和脚本配置文件，列出了项目的所有依赖项，并提供了用于开发和构建项目的脚本。

#### 2.11. vue.config.ts

Vue CLI配置文件，用于配置Vue CLI，包括开发服务器、构建选项等。

#### 2.12. .gitignore

 Git忽略文件，指定git操作时应忽略的文件和目录。

#### 2.13. /public

公共资源目录，存放不会被Webpack处理的公共静态资源。
