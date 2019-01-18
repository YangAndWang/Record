---
title: ReactContext
date: 2018-12-06 14:05:54
tags:
---

# ReactContext

## 使用 React.createContext api

当 Provider 更新value时, 如果有更改, 会查找所有子元素, 找到对应的节点后 向上直到没有父节点 每个都标记 更新时间

## 使用 contextTypes, getChildContext 和 childContextTypes

只有当更新到 contextTypes 时才会去更新context, 如果中途 scu 了 会导致 context 传递 失败