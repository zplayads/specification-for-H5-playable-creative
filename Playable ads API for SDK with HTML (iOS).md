# Content
1. Abstract
2. Introduction to ZPLAY Ads
3. The methods provided by SDK，and their functions
4. The meaning and necessity of methods provided by HTML/JS

## 1.Abstract
This document is for content producers who provide HTML5 playable creative for ZPLAY Ads. It describes the interactive methods between ZPLAY Ads SDK and HTML/JS. By simply calling or developing within developers’ own HTML5 playable creative’ code according to the rules in this file, a developer will be able to interact with ZPLAY Ads SDK, and deliver the creative.


## 2.Introduction to ZPLAY Ads Format 
There are two parts of ZPLAY’s Playable Ads. The first part is HTML5 of game page, which shall be developed by content producer of ZPLAY Ads;

<img src="imgs/playable_en.png" width="640" alt="playable part">

The second part is landing page of playable ads. This part will be provided by advertisers of ZPLAY Ads.
<img src="imgs/landingpage_en.png" width="640" alt="landingpage part">


## 3.The methods provided by SDK, and their functions
- #### window.webkit.messageHandlers.video.postMessage("video_did_start_playing");
This method should be called in order to inform SDK about a video is played when the HTML of game page detects that the video starts to play. For example:
```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("video_did_start_playing");
    ...
}
```
> This method is necessary

- #### window.webkit.messageHandlers.video.postMessage("video_did_end_playing");
This method should be called in order to inform SDK a video is completed, when the HTML of game page detects that the video is over. For example:
```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("video_did_end_playing");
    ...
}
```
> This method is necessary

- #### window.webkit.messageHandlers.video.postMessage("video_did_end_loading");
This method should be called in order to inform SDK that a video finishes with loading, when the HTML of game page detects that the video finishes with loading. For example:
```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("video_did_end_loading");
    ...
}
```
> This method is necessary

- #### window.webkit.messageHandlers.video.postMessage("user_did_tap_install");
This method should be called in order to inform SDK that the installment button is clicked when the installment button is clicked within the HTML of game page. For example:
```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("user_did_tap_install");
    ...
}
```
> This method is optional. Called when the HTML contains with installment button only. Similar with landing page’s installment method, but with different name. 


- #### window.webkit.messageHandlers.video.postMessage("close");
This method should be called when Game page HTML’s close button is clicked in order to inform SDK that the close button in game gage HTML is clicked. For example:
```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("close");
    ...
}
```
> This method is optional. Called when the HTML contains with close button only. Similar with landing page’s close method, but with different name. 

- #### window.webkit.messageHandlers.landingPage.postMessage("close");
When the HTML of landing page detects that users click “close” button, the event should be sent to SDK in order to close the activity action and take other actions accordingly.For example:
```
function yourFun(){
    ...
    window.webkit.messageHandlers.landingPage.postMessage("close");
    ...
}
```
> This method is necessary

- #### window.webkit.messageHandlers.landingPage.postMessage("click");
When HTML of landing page detects that users click “download app” button, the event should be sent to SDK. SDK will open App Store. For example:
```js
function yourFun(){
    ...
    window.webkit.messageHandlers.landingPage.postMessage("click");
    ...
}
```
> This method is necessary

## 4.The meaning and necessity of methods provided by HTML/JS
- #### startAd()
HTML of game page should be added with startAd() method, in which the logic of video play is implemented. For example:
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
SDK will call this method accordingly in order to play videos automatically. 
> This method is necessary

- #### setSDKVersionNumber(versionNumber)

HTML of game page should be added with setSDKVersionNumber(versionNumber) method, to receive version number, so that the HTML of game page can take the action of forward compatible.
> This method is optional

- #### Music player’s id in HTML of game page needs to be set as bgMusicPlayer, so that IOS SDK can apply.

`$('#bgMusicPlayer').get(0).pause();` to pause the music

`$('#bgMusicPlayer').get(0).play();` to resume the music
> This method is necessary


