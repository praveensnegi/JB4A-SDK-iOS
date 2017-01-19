---
layout: page
title: "ATS Considerations"
subtitle: "ATS Considerations"
category: resources
date: 2017-01-18 12:00:00
order: 1
---

If you use MarketingCloudSDK and build your app for iOS 9 or higher, App Transport Security (ATS) is supported.


With ATS, you must use HTTPS instead of HTTP. For details, see [Apple’s documentation](https://developer.apple.com/library/content/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html#//apple_ref/doc/uid/TP40009251-SW35)


> To find any HTTP connections to your app, run a proxy debugger, such as Charles proxy.


While Apple allows you to bypass ATS using NSAppTransportSecurity, [Apple announced](https://developer.apple.com/news/?id=12212016b) that ATS will be required for all apps in the future. If you enable NSAppTransportSecurity in your .plist to bypass ATS, your app may not be published in the Apple Store.


If you are using an older version without ATS enabled, we strongly encourage you to upgrade to the newest MarketingCloudSDK version and build your app for iOS 9 or higher.