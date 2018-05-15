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
- #### window.PlayableAds.mediationStart()
游戏页html检测到视频开始播放时，调用该方法通知SDK视频开始播放。如：
```
function yourFun(){
    ...
    window.PlayableAds.mediationStart()
    ...
}
```
> 该方法为必须项

- #### window.PlayableAds.mediationEnd()
游戏页html检测到视频播放完毕时，调用该方法通知SDK视频播放完毕。如：
```
function yourFun(){
    ...
    window.PlayableAds.mediationEnd()
    ...
}
```
> 该方法为必须项

- #### window.PlayableAds.closeWebView()
落地页html检测到用户点击“关闭”按钮，发送该事件给SDK，以便SDK响应关闭activity以及其它操作。如：
```
function yourFun(){
    ...
    window.PlayableAds.closeWebView()
    ...
}
```
> 该方法为必须项

- #### window.PlayableAds.goInstallApp()
落地页html检测到用户点击“下载应用”按钮时，发送该事件给SDK，SDK会自动到google play或直接下载apk文件，安装并打开。如：
```
function yourFun(){
    ...
    window.PlayableAds.goInstallApp()
    ...
}
```
> 该方法为必须项

## 4.HTML/JS 需要提供的方法及其原因
- #### startAd()
SDK会在合适的时机去播放广告。游戏页html添加startAd()方法，方法中实现播放视频的逻辑，如：
```
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

- #### pauseVideoAudio()
在该方法中暂停音频和视频播放，比如：
```
function pauseVideoAudio(){
    var video = document.getElementById('your-video-id');
    var audio = document.getElementById('your-audio-id');
    
    video.pause();
    audio.pause();
}
```
SDK会在合适的时机调用该方法，优化视觉和听觉效果。
> 该方法为必须项

- #### resumeVideoAudio()
在该方法中resume音频和视频播放，比如：
```
function resumeVideoAudio(){
    var video = document.getElementById('your-video-id');
    var audio = document.getElementById('your-audio-id');
    
    video.play();
    audio.play();
}
```
SDK会在合适的时机调用该方法，优化视觉和听觉效果。
> 该方法为必须项

