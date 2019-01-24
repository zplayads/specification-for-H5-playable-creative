# Specification for HTML Format Playable Ads

- [Specification for HTML Format Playable Ads](#specification-for-html-format-playable-ads)
  - [1. Abstract](#1-abstract)
  - [2. Before development](#2-before-development)
  - [3. Specifications](#3-specifications)
  - [4. test your HTML5 creative though using testing tool](#4-test-your-html5-creative-though-using-testing-tool)
    - [4.1 testing tool for iOS device](#41-testing-tool-for-ios-device)
    - [4.2 testing tool for Android device](#42-testing-tool-for-android-device)

## 1. Abstract

This documentation is for the advertiser who displays HTML5 format playable creative on ZPLAY Ads platform. Applying to these specification will help the HTML5 format playable creative showing smoothly on ZPLAY ads platform.

## 2. Before development

- According best practice, we strongly recommend that there are both playable part and animated landing page in each playable creative. Animated landing page is a page that includes name, icon, description and rating of apps.

- We will take charge of the close button and close function for each playable creative, so you must not add close button in your HTML file.

- The install button needs be made by you. when users tap the install button, HTML must call method `window.openStoreUrl()`, iOS and Android can use the same method, please refer to the third part to get more details.
- Playable creative should be single HTML file, all resources must be included locally within the creative. JavaScript, CSS, image, audio can included in this file, must be encoded as string by base 64.
- Playable creative should not use external resource.
- Playable creative can use responsive design to fit different device.
- Playable creative should not include re-target.
- Playable creative should not use external links.

## 3. Specifications

> Playable creative should call install function to open the store when user click install button, you can use either of the following two method

3.1 Call this method in your JS code
```JS
window.openStoreUrl()
```

3.2 Execute the following JS, using standard anchor tags
```js
...
<a onclick="openStoreUrl()">download</a>
...
```

## 4. test your HTML5 creative though using testing tool

> For making sure of the compatible with most of device, please try to test on every popular devices.

### 4.1 testing tool for iOS device

### 4.2 testing tool for Android device
