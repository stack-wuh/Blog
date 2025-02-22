## 什么是pnpm

Next已经升级到了14版本，具有一些全新的功能特性，现在有一个全新的计划，将所有的博客相关的仓库全部聚拢到一个仓库内部管理。

而这个功能可以利用pnpm来帮助我实现。

![image-20240414162924726](https://src.wuh.site/2024-04/2024-04-14-082928.png)

一、安装pnpm

在mac上直接使用npm安装

```bash
brew install pnpm
```



设置华为的镜像源

```bash
npm config set registry https://mirrors.huaweicloud.com/repository/npm/
```



包的管理

```bash
// 新增

pnpm install react
pnpm add react // 默认-S dependencies
pnpm add react -D // devDependencies
pnpm add -g react // 全局

// 移除
pnpm remove react
pnpm remove react -g
```



给子包安装包

```bash
pnpm add react --filter package-name -D
```





二、工程化配置

同npm一样，pnpm init，会自动生成一个package.json文件，跟npm一样。

先确定一下整个工程的结构，全部的子项目都在packages目录下，然后在pnpm-workspaces.yaml里面维护一下。



![image-20241208173114701](https://src.wuh.site/2024-11/2024-12-08-093146.png)

在packages目录下的每一个子项目都需要执行一次pnpm init，生成一个package.json文件。

在将子项目添加到根目录的说明文件下的时候，需要配置一下.npmrc文件，让pnpm优先使用本地包，否则npm会报出404错误。



这里贴一个nextjs的monorepo实现[nextjs-sharing-code-monorepo](https://github.com/cpvdeveloper/nextjs-sharing-code-monorepo/tree/main/packages)
