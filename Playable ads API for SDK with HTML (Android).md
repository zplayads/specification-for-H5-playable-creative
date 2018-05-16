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


## 3.The methods provided by SDK，and their functions
- #### window.PlayableAds.mediationStart()
This method should be called in order to inform SDK about the ad is played when the HTML of game page detects that the game starts to play. For example:
```
function yourFun(){
    ...
    window.PlayableAds.mediationStart()
    ...
}
```
> This method is necessary

- #### window.PlayableAds.mediationEnd()
This method should be called in order to inform SDK a ads is completed, when the HTML of game page detects that the game finishes. For example:
```
function yourFun(){
    ...
    window.PlayableAds.mediationEnd()
    ...
}
```
> This method is necessary

- #### window.PlayableAds.MediapageClose()
When the HTML of landing page detects that users click “close” button, this event should be sent to SDK in order to close the activity action and take other actions accordingly.
```
function yourFun(){
    ...
    window.PlayableAds.MediapageClose()
    ...
}
```
> This method is necessary

- #### window.PlayableAds.goInstallApp()
When HTML of landing page detects that users click “download app” button, the event should be sent to SDK. SDK will launch Google Play or start to download, install the APK file. For example: 
```
function yourFun(){
    ...
    window.PlayableAds.goInstallApp()
    ...
}
```
> This method is necessary

## 4.The meaning and necessity of methods provided by HTML/JS
- #### startAd()
SDK will call this method accordingly in order to start ads:
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
> This method is necessary

- #### pauseVideoAudio()
Pause the audio and video which are in game, for example:
```
function pauseVideoAudio(){
    var video = document.getElementById('your-video-id');
    var audio = document.getElementById('your-audio-id');
    
    video.pause();
    audio.pause();
}
```
SDK will call this method accordingly to optimize the visual and auditory effect.
> This method is necessary

- #### resumeVideoAudio()
Resume audio and video which are in game, for example:
```
function resumeVideoAudio(){
    var video = document.getElementById('your-video-id');
    var audio = document.getElementById('your-audio-id');
    
    video.play();
    audio.play();
}
```
SDK will call this method accordingly to optimize the visual and auditory effect.
> This method is necessary

