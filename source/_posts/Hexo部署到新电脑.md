---
title: 'Hexo 部署到新电脑'
date: 2017-11-02 22:53:17
tags:
categories:
---
换了新的电脑，想把在 hexo 上的部署文件转移到新电脑上。因为提前在 github 为此做了一些工作，就是按照网上一些朋友的建议，在 github 上创建两个分支，一个分支 「master」 用于 hexo 部署，另一个分支「hexo」用于存储源文件。这样当需要在一台新电脑上使用 hexo 时，只需要把源文件 clone 到本地就行了。但事情总不是一帆风顺😅。今天遇到的问题是，把源文件拉到本地以后，每次执行 `hexo d` 部署， 都会把所有源文件都部署到 `master` 分支上。按照常理，应该是只有 public 文件夹里的内容才会放在 `master` 分支下的。

<!-- more -->

在网上找了很多解决方案，最终认为还是 cache 出了问题。但只是去 `hexo clean` 并不起效。

解决办法：

首先是检查，github.io 仓库下默认分支是哪个，这里要把默认分支改成存储源文件的那个分支。在我的仓库下就是把默认分支改成 「hexo」。

再者，就是 `hexo clean`，然后把目录下的 `.deploy_git` 删掉。然后再重新进行 `hexo generate` 和 `hexo deploy`。成功！
