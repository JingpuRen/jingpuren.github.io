---
id: modify-method
title: 添加文章
sidebar_label: 怎么添加文章？
description: 添加文章的方法
# 设定文章的显示顺序
sidebar_position: 1
# 指定标签
tags:
  - docusaurus
---

# 添加文章
> 由于本网站的主要性质是学习笔记和博客，因此对于添加文章来说，我个人的想法是多在导航栏中创建菜单项（导航栏指的是最顶部的部分，
其中的`Java`、`Golang`等就是导航栏中的菜单项）。

### 1. 修改根目录下的sidebars.ts文件
下面是某一时刻的sidebars.ts文件中的主要代码：
```typescript
const sidebars: SidebarsConfig = {
    goSidebar: [{type: 'autogenerated', dirName: 'golang'}],
    javaSidebar: [{type: 'autogenerated', dirName: 'java'}],
};
```
比如，我想在导航栏中加入`部署`菜单项，代码修改如下：
```typescript
const sidebars: SidebarsConfig = {
    goSidebar: [{type: 'autogenerated', dirName: 'golang'}],
    javaSidebar: [{type: 'autogenerated', dirName: 'java'}],
    // 新添加的一行代码
    deploySidebar: [{type: 'autogenerated', dirName: 'deploy'}],
};
```
- `deploySidebar` : 侧边栏的名称，自定义即可。
- `type: 'autogenerated'` : 指定侧边栏的生成方式是自动生成，Docusaurus会根据指定的目录——`dirName`属性，自动扫描该目录下的Markdown文件，并生成对应的侧边栏导航项。
- `dirName: 'deploy'` : 指定侧边栏对应的文档目录路径，Docusaurus会从`docs/deploy`目录中读取所有Markdown文件。

### 2. 创建对应的目录和Markdown文件
在修改完sidebars.ts文件后，由于我们已经指定了`dirName`，因此我们要在`docs`目录下新建`deploy`目录，并在`deploy`目录下新建一个Markdown文件，
文件名自定义，创建后我们要指定该文件的元数据。在文件的头部添加如下的代码：
```markdown
---
id: modify-method
title: 部署相关
sidebar_label: 怎么添加文章？
description: the method to modify the website
---
```
- `id` : 文档的唯一标识符，影响着文档的Url路径，比如我们这里id是modify-method，那么我们在浏览这篇文章时，Url显示的是`/docs/deploy/modify-method`。
- `title` : 文档的标题，直接展示在页面顶部和浏览器标签中。
- `sidebar_label` : 侧边栏中显示的名称，譬如这篇文章在侧边栏中的显示名称为**怎么添加文章？**。
- `description` : 文档的简要说明或摘要，可以显示在搜索引擎中，帮助用户了解文档内容。

:::warning
在创建目录后，一定也要创建出一个**Markdown**文件。
:::

:::tip
如果不会Markdown相关语法，可以参考这篇**Markdown语法速查表指南** : :link:[Markdown语法速查表](https://markdown.com.cn/cheat-sheet.html)
:::

### 3. 修改根目录下的docusaurus.config.ts文件
修改前，在`docusaurus.config.ts`文件的`themeConfig`部分中，`item`部分代码如下所示：
```typescript
items: [
        {
          type: 'docSidebar',
          sidebarId: 'javaSidebar',
          position: 'left',
          label: 'Java',
        },
        {
          type: 'docSidebar',
          sidebarId: 'goSidebar',
          position: 'left',
          label: 'Golang',
        },
    // ...
```
添加新创建的`deploySidebar`，修改后的代码如下所示：
```typescript
items: [
        {
          type: 'docSidebar',
          sidebarId: 'javaSidebar',
          position: 'left',
          label: 'Java',
        },
        {
          type: 'docSidebar',
          sidebarId: 'goSidebar',
          position: 'left',
          label: 'Golang',
        },
        // 新添加的部分
        {
          type: 'docSidebar',
          sidebarId: 'deploySidebar',
          position: 'left',
          label: '部署',
        },
    // ...
```
- `type: 'docSidebar'` : 指定该菜单项的类型为**文档侧边栏**
- `sidebarId: 'deploySidebar'` : 指定该菜单项关联的侧边栏标识符
- `position: 'left'` : 控制菜单项在导航栏中的位置，这里是设置显示在导航栏的左侧区域
- `label: '部署'` : 设置导航栏中显示的菜单名称，这里是设置菜单的显示名称为**部署**