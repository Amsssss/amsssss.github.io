---
title: git_learn
date: 2021-06-04 14:02:17
tags:
---

# Git学习

## 三大区域
* 本地仓库
* 暂存区
* 工作区

## 本地仓库

### 初始化本地仓库
```bash
git init
```
### 本地仓库状态
```bash
git status
```
### 版本切换
```bash
设置头指针到对应版本
git reset --[soft | hard | default] HEAD


git checkout HEAD
```

## 暂存区与工作区
### 提交工作区文件到暂存区
```bash
## 添加单个或多个文件到暂存区
git add <file>...
```

### 将暂存区的文件取消添加
```bash
## 从暂存区将修改的部分取消添加 文件继续被追踪
git restore --staged <file>...

## 从暂存区将文件取消添加 文件不再被追踪
git rm --cached <file>...
```

## 暂存区与本地库
### 查询本地库的提交信息
```bash
## 查看基础信息
git reflog

## 查看详细信息
git log
```

### 提交暂存区到本地库
```bash
## 使用文本信息注释该次提交
git commit -m ''
```

## 分支
### git branch
```bash
## 创建 name分支
git branch name

## 删除 name分支
git branch -d name
```
### 切换分支
```bash
## 切换到 name分支
git checkout name
```
### 合并分支
```bash
## 合并name分支到当前分支
git merge name
```

## 场景
### 删除的文件在历史版本中如何恢复
```bash
git reset HEAD <file>
git checkout <file>
```

### reset 几种模式
* --soft: 移动head到指定位置， 不修改工作区和暂存区内容，与历史版本不一致的内容将添加到暂存区
* --hard: 移动head到指定位置， 丢弃工作区，暂存区内容，完全切换到历史版本
* --mixed: 移动head到指定位置， 不修改工作区，丢弃暂存区内容
