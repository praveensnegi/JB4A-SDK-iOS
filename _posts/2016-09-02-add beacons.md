---
layout: page
title: "Beacons"
subtitle: "Add Beacons"
category: location
date: 2016-09-02 08:43:35
order: 3
---

1. Add geolocation. Follow the steps for [Add Geolocation]({{ site.baseurl}}/location/geolocation.html) before continuing.
1. Set `andProximityServices` and `andLocationServices` to YES in the `configureSDK()` call.


#### <a name="plist"></a>Info.plist Update

There is one Info.plist entry to add, depending on the way your app works:  

* Range for Beacons in the background: This permission will ensure that your app can range for beacons when your app is in the background or suspended.

Implement the following key if you want to enable this function:

* "App registers for location updates" is required if you have Proximity Services turned on in configureSDK and want to range for beacons in the background.

<br/><img class="img-responsive" src="{{ site.baseurl }}/assets/background_modes_plist_entry.png" /><br/>

> MobilePush prevents the app from displaying a beacon message with an empty alert. If you include AMPscript in your message that returns no content or an empty string, the mobile app will not display that message.

> To understand how beacons behave in different situations, see the MobilePush beacons help documentation.