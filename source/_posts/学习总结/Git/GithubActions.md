---
title: GitHub Actions 浅入
date: 2023-10-27
updated: 2023-10-27 11:33
tags: GitHub
catetory: 学习总结
---

#### 概念
GitHub Actions 是一种持续集成和持续交付 (CI/CD) 平台，可用于自动执行生成、测试和部署管道。 您可以创建工作流程来构建和测试存储库的每个拉取请求，或将合并的拉取请求部署到生产环境。
#### 实践
基于 `hexo` 博客框架实现的个人博客在 `Github Pages` 查看。
#### 问题
1. 本地执行 `npm run build` 命令之后的结果与 `workflow` 中的不一致
  在增加了主题（见 `themes/osean` ）后提交代码之后并没有被上传到仓库，原因是主题文件是从另一个代码库拉取的，由于关联了其他的git仓库（并被当前代码库记录了下来）导致无法被本地git进行上传。
  ##### 解决
  1. 在暂存区删除该文件夹，并重新添加跟踪、提交等

  {%codeblock %}
    git rm --cache themes/主题文件名
  {%endcodeblock %}
