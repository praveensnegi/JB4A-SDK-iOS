---
layout: page
title: "Custom Keys"
subtitle: "Handling Custom Keys Sent with Message Payload"
category: features
date: 2017-01-18 12:00:00
order: 10
---

Use custom keys to send extra data along with a push notification. You can use custom keys to add tracking or additional functionality to your app. For example, you can define a custom key that allows a third-party application to provide custom tracking information regarding customer usage on your mobile app. This data can include an ID value used by the app to retrieve additional data or other function. You must [enable](http://help.exacttarget.com/en/documentation/mobilepush/administering_your_mobilepush_account/apps_and_optional_settings_in_your_mobilepush_account/#customkeys) this feature in the Marketing Cloud application.

<br/>
 <img class="img-responsive" src="{{ site.baseurl }}/assets/CustomKeys.png" /><br/>
<br/>

To process custom keys contained within the payload of a remote notification, use the following code as an example:

<script src="https://gist.github.com/sfmc-mobilepushsdk/6a2e837b628bdada0d7a45fc4d6a0235.js"></script>