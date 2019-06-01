---
layout: post
title: Github Pages
---

# 安装

## Windows

1. 下载并安装 [Ruby+Devkit](https://rubyinstaller.org/downloads/)
2. 运行cmd

        gem install jekyll bundler

3. 查看jekyll -v

# 搭建

不要用jekyll官方引擎，要用github pages自己的引擎，两者markdown解析器有差异。  

        bundle exec jekyll serve

# 访问

        127.0.0.1:4000
