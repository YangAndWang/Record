---
title: React
date: 2018-11-29 22:05:27
tags:
---

# React

## React.Element

{
    "$$typeof": Symbol(reactType),
    "key":null,
    "ref":null,
    "type": constructor,
    "props":{},
    "_owner":null,
    "_self": null,
    "_store":{},
    "_source": {},
    "_store": {},
}

## ReactDOM.render

call: legacyRenderSubtreeIntoContainer
    判断是合法container

    !!(node && (node.nodeType === ELEMENT_NODE || node.nodeType === DOCUMENT_NODE || node.nodeType === DOCUMENT_FRAGMENT_NODE || node.nodeType === COMMENT_NODE && node.nodeValue === ' react-mount-point-unstable '))

call: legacyCreateRootFromDOMContainer // root = container._reactRootContainer = legacyCreateRootFromDOMContainer(container, forceHydrate);

new ReactRoot
call createContainer
call createFiberRoot
call createHostRootFiber
call createFiber
new FiberNode
goto legacyRenderSubtreeIntoContainer // 回到legacyRenderSubtreeIntoContainer继续执行
call unbatchedUpdates
root.render
new ReactWork
call updateContainer
call updateContainerAtExpirationTime
call getContextForSubtree
call scheduleRootUpdate
call createUpdate