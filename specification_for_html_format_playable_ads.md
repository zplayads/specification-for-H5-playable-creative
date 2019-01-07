# Specification for HTML Format Playable Ads

- [Specification for HTML Format Playable Ads](#specification-for-html-format-playable-ads)
    - [1. Abstract](#1-abstract)
    - [2. Before development](#2-before-development)
    - [3. Specifications](#3-specifications)
        - [3.1 on iOS device](#31-on-ios-device)
        - [3.2 on Android device](#32-on-android-device)
    - [4. test your HTML5 creative though using testing tool](#4-test-your-html5-creative-though-using-testing-tool)
        - [4.1 testing tool for iOS device](#41-testing-tool-for-ios-device)
        - [4.2 testing tool for Android device](#42-testing-tool-for-android-device)

## 1. Abstract

This documentation is for the advertiser who displays HTML5 format playable creative on ZPLAY Ads platform. Applying to these specification will help the HTML5 format playable creative showing smoothly on ZPLAY ads platform.

## 2. Before development

- According best practice, we strongly recommend that there are both playable part and animated landing page in each playable creative. Animated landing page is a page that includes name, icon, description and rating of apps.

- We will take charge of the close button and close function for each playable creative, so you must not add close button in your HTML file.

- The install button needs be made by you. when users tap the install button, you need pass us a method that "user_did_tap_install" with iOS device and "goInstallApp" with Android device.

## 3. Specifications

> the only method that is needed to use in your HTML5 creatives is the method that open the store within traffic apps when user taps the click button.

### 3.1 on iOS device

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

### 3.2 on Android device

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

## 4. test your HTML5 creative though using testing tool

> For making sure of the compatible with most of device, please try to test on every popular devices.

### 4.1 testing tool for iOS device

### 4.2 testing tool for Android device
