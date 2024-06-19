---
title: 使用流程
---

## 新建笔记
官方推荐使用以下的生成方式，但不符合coding习惯

```
hexo new xxx.md
```

可以在`_posts`目录下新建目录，手动添加`Front Matter`。

在对应的笔记目录下生成Markdown文件后，指定categories或者tag，然后开始写作。

## Github托管
1. 启动Github Action
2. 增加一个workflow文件，要和本地使用的node版本一致

git push一直超时，原理在于git命令没有走代理，操作步骤：
1. 检查有无代理，有则走第2步先删除
```
git config --global http.proxy
git config --global https.proxy
```
2. 删除代理
```
git config --global --unset http.proxy
git config --global --unset https.proxy
```
3. 重设代理
注意端口号和本地的代理要一致
```
git config --global https.proxy 127.0.0.1:7890
git config --global http.proxy 127.0.0.1:7890
```

## 参考内容

1. [Hexo官方网站](https://hexo.io/zh-cn/docs/)
2. [Butterfly主题官方网站](https://butterfly.js.org/)

