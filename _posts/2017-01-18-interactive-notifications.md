---
layout: page
title: "Interactive Notifications"
subtitle: "Display Interactive Notification Messages"
category: features
date: 2017-01-18 12:00:00
order: 8
---
Add buttons called **interactive notifications** to push notifications in your Mobile app. The Marketing Cloud sends the category name for these interactive notifications in the message payload. This feature requires [enablement](http://help.exacttarget.com/en/documentation/mobilepush/administering_your_mobilepush_account/apps_and_optional_settings_in_your_mobilepush_account/#interactiveNotifications) in the Marketing Cloud application.

The code below would be added to the AppDelegate.m didFinishLaunchingWithOptions.  This is a sample only.  Please adjust for your specific circumstances.

This sample shows how to create a category named "Example".  When this category is sent with the payload from the Marketing Cloud, the notification will be displayed in the notification center with the buttons shown here.
  
For iOS 10 UNUserNotificationCenter implementations:

<script src="https://gist.github.com/sfmc-mobilepushsdk/f9bb3bb938034e053a35bf64c9fc7781.js"></script>

For iOS 9, use:

<script src="https://gist.github.com/sfmc-mobilepushsdk/a6acdcd08c06225f2394.js"></script>

In order to process the button taps, you need to add code to the AppDelegate. For example:

<script src="https://gist.github.com/sfmc-mobilepushsdk/26a92b4f7eb20d946c3e.js"></script>