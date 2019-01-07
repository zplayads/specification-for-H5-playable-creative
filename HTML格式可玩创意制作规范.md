# HTML格式可玩创意制作规范

- [HTML格式可玩创意制作规范](#html%E6%A0%BC%E5%BC%8F%E5%8F%AF%E7%8E%A9%E5%88%9B%E6%84%8F%E5%88%B6%E4%BD%9C%E8%A7%84%E8%8C%83)
    - [1. 概要](#1-%E6%A6%82%E8%A6%81)
    - [2. 对接前须知](#2-%E5%AF%B9%E6%8E%A5%E5%89%8D%E9%A1%BB%E7%9F%A5)
    - [3. 需要在HTML中使用的方法及其作用](#3-%E9%9C%80%E8%A6%81%E5%9C%A8html%E4%B8%AD%E4%BD%BF%E7%94%A8%E7%9A%84%E6%96%B9%E6%B3%95%E5%8F%8A%E5%85%B6%E4%BD%9C%E7%94%A8)
        - [3.1 当设备是iOS时](#31-%E5%BD%93%E8%AE%BE%E5%A4%87%E6%98%AFios%E6%97%B6)
        - [3.2 当设备是Android时](#32-%E5%BD%93%E8%AE%BE%E5%A4%87%E6%98%AFandroid%E6%97%B6)
    - [4. 使用测试工具测试您的广告](#4-%E4%BD%BF%E7%94%A8%E6%B5%8B%E8%AF%95%E5%B7%A5%E5%85%B7%E6%B5%8B%E8%AF%95%E6%82%A8%E7%9A%84%E5%B9%BF%E5%91%8A)
        - [4.1 iOS设备上的测试应用](#41-ios%E8%AE%BE%E5%A4%87%E4%B8%8A%E7%9A%84%E6%B5%8B%E8%AF%95%E5%BA%94%E7%94%A8)
        - [4.2 Android设备上的测试工具](#42-android%E8%AE%BE%E5%A4%87%E4%B8%8A%E7%9A%84%E6%B5%8B%E8%AF%95%E5%B7%A5%E5%85%B7)

## 1. 概要

该文档提供给使用HTML5 形式的可玩广告创意的广告主在 ZPLAY 可玩广告平台投放广告时使用。广告主需要在自己开发的 HTML5 可玩创意的代码中按照规定的方法进行调用或者开发，以符合 ZPLAY 可玩广告的投放规范。

## 2. 对接前须知

- 我们建议可玩广告包含可玩及落地页两部分，实践证明，这种做法在保证良好用户体验的同时，确保广告具有最好的投放效果。落地页指的是一个包含了游戏的名称、icon、描述以及星级的页面。

- 我们会自动的在可玩创意上增加关闭按钮，因此您不需要在HTML5 的创意中添加关闭按钮。

- 你需要在HTML5 创意中制作下载按钮，并且在用户点击下载按钮的时候，调用下载方法，请注意：在iOS中，该方法是“user_did_tap_install”；在Android中，该方法是“goInstallApp”。

## 3. 需要在HTML中使用的方法及其作用

> 您仅需要在广告的下载按钮被点击时，调用点击下载方法，以便打开应用市场进行下载

### 3.1 当设备是iOS时

- **window.webkit.messageHandlers.video.postMessage("user_did_tap_install")**
  当HTML 中的安装按钮被点击时，调用该方法通知 SDK 安装按钮被点击。 如:

```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("user_did_tap_install");
    ...
}
```

> 该方法为必须项

### 3.2 当设备是Android时

- **window.PlayableAds.goInstallApp()**
  当HTML 中的安装按钮被点击时，调用该方法通知 SDK 安装按钮被点击。如：

```js
function yourFun(){
    ...
    window.PlayableAds.goInstallApp()
    ...
}
```

> 该方法为必须项

## 4. 使用测试工具测试您的广告

> 为了确保您的创意在投放时没有问题，请进行多种机型的测试

### 4.1 iOS设备上的测试应用

### 4.2 Android设备上的测试工具
