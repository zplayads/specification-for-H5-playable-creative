# Specification for HTML Format Playable Ads

- [Specification for HTML Format Playable Ads](#specification-for-html-format-playable-ads)
    - [1. Abstract](#1-abstract)
    - [2. Before development](#2-before-development)
    - [3. Specifications](#3-specifications)
        - [3.1 Creative Loading](#31-creative-loading)
        - [3.2 Creative Invoking](#32-creative-invoking)
        - [3.3 Playable ads Showing](#33-playable-ads-showing)
            - [3.3.1 on iOS device](#331-on-ios-device)
            - [3.3.2 on Android device](#332-on-android-device)
        - [3.4 Playable ads Clicking](#34-playable-ads-clicking)
            - [3.4.1 on iOS device](#341-on-ios-device)
            - [3.4.2 on Android device](#342-on-android-device)
        - [3.5 OS Version Obtaining](#35-os-version-obtaining)
            - [3.5.1 on iOS device](#351-on-ios-device)
            - [3.5.2 on Android device](#352-on-android-device)
        - [3.6 Playable ads Pausing and Resuming](#36-playable-ads-pausing-and-resuming)
        - [3.7 Sound Muting](#37-sound-muting)
        - [3.8 Orientation of HTML Sending](#38-orientation-of-html-sending)

## 1. Abstract

This documentation is for the advertiser who displays HTML5 format playable creative on ZPLAY Ads platform. Applying to these specification will help the HTML5 format playable creative showing smoothly on ZPLAY ads platform.

## 2. Before development

- According best practice, we strongly recommend that there are both playable part and animated landing page in each playable creative.

- We will take charge of the close button and close function for each playable creative, so you must not add close button in your HTML file. For making sure of good user experience, we need show the close button correctly, so we want you pass the orientation that HTML support to us through "“getOrientation()" method.

- The install button needs be made by you. when users tap the install button, you need pass us a method that "user_did_tap_install" with iOS device and "goInstallApp" with Android device.

## 3. Specifications

### 3.1 Creative Loading

> The methods below are just for iOS device. No method is for Android.

- **window.webkit.messageHandlers.video.postMessage("video_did_end_loading")**
> When HTML detects all assets have downloaded, call this method to inform SDK. For example:

```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("video_did_end_loading");
    ...
}
```

> This method is necessary

- **window.webkit.messageHandlers.video.postMessage("video_did_fail_loading")**
  When HTML detects all assets have failed to download, call this method to inform SDK. For example:

```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("video_did_fail_loading");
    ...
}
```

> This method is necessary

### 3.2 Creative Invoking

> The methods are same on iOS device and Android device.

- **startAd()**
  SDK will invoke this method in right time in order to invoke creative displaying.  after all assets of creative have downloaded, the HTML creative should be pause itself to play before this method is invoked. For example:

```js
function startAd() {
    .....
}
```

> This method is necessary

### 3.3 Playable ads Showing

#### 3.3.1 on iOS device

- **window.webkit.messageHandlers.video.postMessage("video_did_start_playing")**
  When HTML starts to show, call this method to inform SDK. For example:

```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("video_did_start_playing");
    ...
}
```

> This method is necessary

- **window.webkit.messageHandlers.video.postMessage("animated_end_card")**
  When the playable part of HTML finishes to show, call this method to inform SDK. This method need to be called even if there is no any kind of landing page. For example:

```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("animated_end_card");
    ...
}
```

> This method is necessary

#### 3.3.2 on Android device

- **window.PlayableAds.mediationStart()**
  When HTML starts to show, call this method to inform SDK. For example:

```js
function yourFun(){
    ...
    window.PlayableAds.mediationStart()
    ...
}
```

> This method is necessary

- **window.PlayableAds.animatedEndCard()**
  When the playable part of HTML finishes to show, call this method to inform SDK. This method need to be called even if there is no any kind of landing page. For example:

```js
function yourFun(){
    ...
    window.PlayableAds.animatedEndCard()
    ...
}
```

> This method is necessary

### 3.4 Playable ads Clicking

#### 3.4.1 on iOS device

- **window.webkit.messageHandlers.video.postMessage("user_did_tap_install")**
  When install button is be clicked, call this method to inform SDK. For example:

```js
function yourFun(){
    ...
    window.webkit.messageHandlers.video.postMessage("user_did_tap_install");
    ...
}
```

> This method is necessary

#### 3.4.2 on Android device

- **window.PlayableAds.goInstallApp()**
  When install button is be clicked, call this method to inform SDK. For example:

```js
function yourFun(){
    ...
    window.PlayableAds.goInstallApp()
    ...
}
```

> This method is necessary

### 3.5 OS Version Obtaining

> For good compatible with different device, HTML is able to obtain the OS version through this method.

#### 3.5.1 on iOS device

- **setIosVersion("versionNumber")**

> This method is optional

#### 3.5.2 on Android device

- **setAndroidVersion("versionNumber")**

> This method is optional

### 3.6 Playable ads Pausing and Resuming

> The methods are same on iOS device and Android device.

- **pauseVideoAudio()**

> Pause the HTML creative including video and audio
> This method is necessary

- **resumeVideoAudio()**

> Resume the HTML creative including video and audio
> This method is necessary

### 3.7 Sound Muting

> The methods below are just for iOS device. No method is for Android.

- **muteSound(false/true)**

> This method is necessary if you use WKWebView

### 3.8 Orientation of HTML Sending

> The methods are same on iOS device and Android device.

- **getOrientation()**

> Please add getOrientation() method in HTML for Sending the orientation of HTML when SDK needs
> The value returned should be json format: {"orientation" : "PORTRAIT"} or {"orientation" : "LANDSCAPE"}
> This method is necessary
