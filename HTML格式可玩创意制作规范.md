# HTML格式可玩创意制作规范

- [HTML格式可玩创意制作规范](#html%E6%A0%BC%E5%BC%8F%E5%8F%AF%E7%8E%A9%E5%88%9B%E6%84%8F%E5%88%B6%E4%BD%9C%E8%A7%84%E8%8C%83)
    - [1. 概要](#1-%E6%A6%82%E8%A6%81)
    - [2. 对接前须知](#2-%E5%AF%B9%E6%8E%A5%E5%89%8D%E9%A1%BB%E7%9F%A5)
    - [3. 需要在HTML中使用的方法及其作用](#3-%E9%9C%80%E8%A6%81%E5%9C%A8html%E4%B8%AD%E4%BD%BF%E7%94%A8%E7%9A%84%E6%96%B9%E6%B3%95%E5%8F%8A%E5%85%B6%E4%BD%9C%E7%94%A8)
        - [3.1 创意加载](#31-%E5%88%9B%E6%84%8F%E5%8A%A0%E8%BD%BD)
        - [3.2 广告调起](#32-%E5%B9%BF%E5%91%8A%E8%B0%83%E8%B5%B7)
        - [3.3 广告的展示](#33-%E5%B9%BF%E5%91%8A%E7%9A%84%E5%B1%95%E7%A4%BA)
            - [3.3.1 当设备是iOS时](#331-%E5%BD%93%E8%AE%BE%E5%A4%87%E6%98%AFios%E6%97%B6)
            - [3.3.2 当设备是Android时](#332-%E5%BD%93%E8%AE%BE%E5%A4%87%E6%98%AFandroid%E6%97%B6)
        - [3.4 广告被点击](#34-%E5%B9%BF%E5%91%8A%E8%A2%AB%E7%82%B9%E5%87%BB)
            - [3.4.1 当设备是iOS时](#341-%E5%BD%93%E8%AE%BE%E5%A4%87%E6%98%AFios%E6%97%B6)
            - [3.4.2 当设备是Android时](#342-%E5%BD%93%E8%AE%BE%E5%A4%87%E6%98%AFandroid%E6%97%B6)
        - [3.5 获取操作系统版本](#35-%E8%8E%B7%E5%8F%96%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F%E7%89%88%E6%9C%AC)
            - [3.5.1 当设备是iOS时](#351-%E5%BD%93%E8%AE%BE%E5%A4%87%E6%98%AFios%E6%97%B6)
            - [3.5.2 当设备是Android时](#352-%E5%BD%93%E8%AE%BE%E5%A4%87%E6%98%AFandroid%E6%97%B6)
        - [3.6 暂停和播放广告](#36-%E6%9A%82%E5%81%9C%E5%92%8C%E6%92%AD%E6%94%BE%E5%B9%BF%E5%91%8A)
        - [3.7 控制广告的声音展示](#37-%E6%8E%A7%E5%88%B6%E5%B9%BF%E5%91%8A%E7%9A%84%E5%A3%B0%E9%9F%B3%E5%B1%95%E7%A4%BA)
        - [3.8 传递创意方向](#38-%E4%BC%A0%E9%80%92%E5%88%9B%E6%84%8F%E6%96%B9%E5%90%91)

## 1. 概要

该文档提供给使用HTML5 形式的可玩广告创意的广告主在 ZPLAY 可玩广告平台投放广告时使用。广告主需要在自己开发的 HTML5 可玩创意的代码中按照规定的方法进行调用或者开发，以符合 ZPLAY 可玩广告的投放规范。

## 2. 对接前须知

- 我们建议可玩广告包含可玩及落地页两部分，实践证明，这种做法在保证良好用户体验的同时，确保广告具有最好的投放效果。

- 我们会自动的在可玩创意上增加关闭按钮，因此您不需要在HTML5 的创意中添加关闭按钮；为了确保关闭按钮在不同方向屏幕上显示正确，我们需要您将创意的方向传递给我们，详见“getOrientation()”方法；

- 你需要在HTML5 创意中制作下载按钮，并且在用户点击下载按钮的时候，调用下载方法，请注意：在iOS中，该方法是“user_did_tap_install”；在Android中，该方法是“goInstallApp”。

## 3. 需要在HTML中使用的方法及其作用

### 3.1 创意加载

> 仅设备是iOS时需要使用

- **window.webkit.messageHandlers.video.postMessage("video_did_end_loading")**
  当HTML 检测到创意加载完成时, 调用该方法通知 SDK 创意加载完成. 如：

```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("video_did_end_loading");
    ...
}
```

> 该方法为必须项

- **window.webkit.messageHandlers.video.postMessage("video_did_fail_loading")**
  当HTML 检测到创意加载失败时, 调用该方法通知 SDK 创意加载失败. 如：

```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("video_did_fail_loading");
    ...
}
```

> 该方法为必须项

### 3.2 广告调起

> iOS设备 和Android 设备使用同样的方法

- **startAd()**
  SDK 会在适当的时机调用该方法，达到广告打开的目的。在该方法被调用之前，可玩广告应该处于暂停状态，不得播放及发出声音。如:

```js
function startAd() {
    .....
}
```

> 该方法为必须项

### 3.3 广告的展示

#### 3.3.1 当设备是iOS时

- **window.webkit.messageHandlers.video.postMessage("video_did_start_playing")**
  当HTML 检测到创意开始播放时，调用该方法通知 SDK 广告开始。如：

```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("video_did_start_playing");
    ...
}
```

> 该方法为必须项

- **window.webkit.messageHandlers.video.postMessage("animated_end_card")**
  当HTML 检测到可玩部分广告结束播放时，要展示落地页时，调用该方法通知 SDK 可玩部分结束。如果您的HTML 广告没有落地页，在可玩部分结束后广告即结束，也需要调用此方法。如：

```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("animated_end_card");
    ...
}
```

> 该方法为必须项

#### 3.3.2 当设备是Android时

- **window.PlayableAds.mediationStart()**
  当HTML 检测到创意开始播放时，调用该方法通知 SDK 广告开始。如：

```js
function yourFun(){
    ...
    window.PlayableAds.mediationStart()
    ...
}
```

> 该方法为必须项

- **window.PlayableAds.animatedEndCard()**
  当HTML 检测到可玩部分广告结束播放时，要展示落地页时，调用该方法通知 SDK 可玩部分结束。如果您的HTML 广告没有落地页，在可玩部分结束后广告即结束，也需要调用此方法。如：

```js
function yourFun(){
    ...
    window.PlayableAds.animatedEndCard()
    ...
}
```

> 该方法为必须项

### 3.4 广告被点击

#### 3.4.1 当设备是iOS时

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

#### 3.4.2 当设备是Android时

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

### 3.5 获取操作系统版本

> 为了方便HTML 创意能够对设备进行更好的兼容，HTML 创意可使用以下方法接收SDK传递的操作系统版本号。

#### 3.5.1 当设备是iOS时

- **setIosVersion("versionNumber")**

> 该方法非必须项。

#### 3.5.2 当设备是Android时

- **setAndroidVersion(versionNumber)**

> 该方法非必须项。

### 3.6 暂停和播放广告

> iOS设备 和Android 设备使用同样的方法

- **pauseVideoAudio()**

> 暂停广告，包括HTML 创意中的音视频。
> 该方法为必须项。

- **resumeVideoAudio()**

> 恢复广告，包括HTML 创意中的音视频。
> 该方法为必须项。

### 3.7 控制广告的声音展示

> 仅设备是iOS时需要使用

- **muteSound(false/true)**

> 是否静音所有音视频.
> 如果你使用的 WebView 为 WKWebView，则必需实现该方法，在此方法中静音所有音频。

### 3.8 传递创意方向

> iOS设备 和Android 设备使用同样的方法

- **getOrientation()**

> HTML 创意添加获取getOrientation()方法，支持向SDK 返回HTML 的方向。
> 返回值为json格式： {"orientation" : "PORTRAIT"} 或者 {"orientation" : "LANDSCAPE"}。
> 该方法为必须项。
