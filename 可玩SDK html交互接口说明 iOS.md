# 目录
1. 概要
2. 可玩广告形式说明
3. SDK提供的方法及其作用
4. HTML/JS需要提供的方法及其原因

## 1.概要
该文档提供给为ZPLAY可玩广告平台提供 HTML5 可玩广告的制作者或制作公司使用，文档描述了ZPLAY可玩广告 SDK 与 HTML/JS 之间的交互方法。开发者只需要在自己开发的 HTML5 可玩广告的代码中按照规定的方法进行调用或者开发，就可以和ZPLAY可玩广告的 SDK 交互，完成可玩广告的投放。

## 2.可玩广告形式说明
ZPLAY的可玩广告分为两个部分，第一部分为可玩的 HTML5 部分，这一部分是可玩广告的制作者或制作公司进行开发；
<img src="imgs/playable.png" width="640" alt="可玩的 游戏 部分">

第二部分为可玩广告的落地页部分，这一部分是可玩广告的广告主提供。
<img src="imgs/landingpage.png" width="640" alt="可玩的 落地页 部分">


## 3.SDK提供的方法及其作用
- #### window.webkit.messageHandlers.video.postMessage("video_did_start_playing");
游戏页HTML检测到视频开始播放时，调用该方法通知SDK视频开始播放。如：
```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("video_did_start_playing");
    ...
}
```
> 该方法为必须项

- #### window.webkit.messageHandlers.video.postMessage("video_did_end_playing");
游戏页HTML检测到视频播放完毕时，调用该方法通知SDK视频播放完毕。如：
```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("video_did_end_playing");
    ...
}
```
> 该方法为必须项

- #### window.webkit.messageHandlers.video.postMessage("video_did_end_loading");
游戏页 HTML 检测到视频加载完成时, 调用该方法通知 SDK 视频加载完成. 如:
```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("video_did_end_loading");
    ...
}
```
> 该方法为必须项

- #### window.webkit.messageHandlers.video.postMessage("user_did_tap_install");
游戏页 HTML 中的安装按钮被点击时, 调用该方法通知 SDK 安装按钮被点击. 如:
```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("user_did_tap_install");
    ...
}
```
> 该方法非必须项，仅在 HTML 中包含安装按钮的时候使用，与 landingPage 的安装方法功能相同，但名称不同


- #### window.webkit.messageHandlers.video.postMessage("close");
游戏页 HTML 中的关闭按钮被点击时, 调用该方法通知 SDK 游戏页 HTML 关闭按钮被点击. 如:
```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("close");
    ...
}
```
> 该方法为非必须项，仅在 HTML 中包含关闭按钮的时候使用，与 landingPage 的关闭方法功能相同，但名称不同

- #### window.webkit.messageHandlers.landingPage.postMessage("close");
落地页HTML检测到用户点击“关闭”按钮，发送该事件给SDK，以便SDK响应关闭activity以及其它操作。如：
```
function yourFun(){
    ...
    window.webkit.messageHandlers.landingPage.postMessage("close");
    ...
}
```
> 该方法为必须项

- #### window.webkit.messageHandlers.landingPage.postMessage("click");
落地页HTML检测到用户点击“下载应用”按钮时，发送该事件给SDK，SDK会打开 App Store。如：
```js
function yourFun(){
    ...
    window.webkit.messageHandlers.landingPage.postMessage("click");
    ...
}
```
> 该方法为必须项

## 4.HTML/JS需要提供的方法及其原因
- #### startAd()
游戏页HTML添加startAd()方法，方法中实现播放视频的逻辑，如:
```js
function startAd(){
    var video = document.getElementById('your-video-id');
    video.currentTime = 0;
    video.play();

    var audio = document.getElementById('your-audio-id');
    audio.currentTime = 0;
    audio.play();
}
```
SDK会在适当的时机调用该方法，达到自动播放的目的。
> 该方法为必须项

- #### setSDKVersionNumber(versionNumber)

游戏页 HTML 添加 setSDKVersionNumber(versionNumber) 方法, 接收版本号, 以便游戏页 HTML 做向前兼容的操作。
> 该方法非必须项。

- #### pauseVideoAudio()
暂停游戏，包括游戏中的音视频
> 该方法非必须项。

- #### resumeVideoAudio()
恢复游戏，包括游戏中的音视频
> 该方法为必须项。

- #### muteSound(false/true)
是否静音所有音视频，如果你使用的WebView为WKWebView，则必需实现该方法，在此方法中静音所有音频。原因WKWebView对iPhone的静音键不敏感，SDK监听到静音键状态改变时会主动调用该方法。


