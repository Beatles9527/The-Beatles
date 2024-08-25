## 1、问题描述

当我在尝试从Windows上克隆git文件时出现了如下错误：

```shell
$ git clone https://github.com/Beatles9527/The-Beatles.git
Cloning into 'The-Beatles'...
remote: Enumerating objects: 613, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 613 (delta 0), reused 0 (delta 0), pack-reused 610 (from 1)
Receiving objects: 100% (613/613), 101.02 MiB | 1.01 MiB/s, done.
Resolving deltas: 100% (125/125), done.
error: invalid path 'Java/并发编程/subfile/2-Fork:Join框架.md'
fatal: unable to checkout working tree
warning: Clone succeeded, but checkout failed.
You can inspect what was checked out with 'git status'
and retry with 'git restore --source=HEAD :/'

```

原因主要是由于我的仓库中的Windows无法解析":"字符导致，无法签出工作树，导致clone到本地之后无法checkout。

根据问题提示直接进入本地已经clone下来的仓库里执行

```shell
$ git restore --source=HEAD :/
error: invalid path 'Java/并发编程/subfile/2-Fork:Join框架.md'
```

建议修改该字符