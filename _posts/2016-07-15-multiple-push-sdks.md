---
layout: page
title: "Multiple Push SDKs"
subtitle: "Troubleshooting Multiple Push SDKs"
category: trouble
date: 2016-07-15 12:00:00
order: 2
---
While multiple push SDKs can be integrated into a single app, this may cause issues, and we cannot guarantee results. This section provides some considerations you should keep in mind as you develop your app.  Note that this is not an exhaustive list.

#### 1. Registration

Only ONE call to register for push notifications can be made; otherwise, multiple notification banners, alerts, and/or sounds may be triggered in a single push. If you are using the JB4A  registerForRemoteNotifications method, do not use a direct call to [[UIApplication sharedApplication] registerForRemoteNotifications] in your application.

#### 2. Notification Settings

An app can call registerUserNotificationSettings multiple times, but only the last call is used. The settings are overwritten each time it is called.

#### 3. Badging

There is no way to guarantee the value of a badge.

#### 4. Notification Handling

Notification handling in the AppDelegate with multiple SDKs depends on the SDKs used. The notifications may be visually stacked, discarded, or otherwise confused.

#### 5. Custom Payload Keys

Use custom keys or other payload-specific data to ensure that the correct SDK handler is called in an app that supports multiple notification handlers.

#### 6. Method Swizzling

Warning: If a push SDK uses method swizzling (a means of replacing iOS framework code at runtime), the MobilePush SDK will not work.

In order to tell if an SDK uses swizzling, look for SDKs that do not use:

`- (void)application:(UIApplication *)application`
`didReceiveRemoteNotification:(NSDictionary *)userInfo`
`fetchCompletionHandler:(void (^)(UIBackgroundFetchResult result))handler`

Some SDKs offer a secondary implementation, which uses standard app delegate methods. If so, you must use the secondary implementation.

#### 7. Geolocation

If you implement multiple SDKs that use location-enabled services, use only one SDK's location enablement. Using more than one will lead to unknown and unsupportable consequences.

For example, it is likely that each provider will be affected by the methods used by the other providers to interact with iOS CoreLocation services and enablement of location services. Within an app, there is a limited number of geofences that can be monitored at any one time. (This number depends on iOS version, device type, etc.) With multiple implementations competing for a limited resource, users' experience may suffer.

In addition, permissions needed to use location-enabled SDKs may overlap or conflict.

#### 8. Feedback

All providers may not be able to detect if a device has been unregistered.

The binary APNS (Apple Push Notification Service) uses a feedback mechanism to let the provider know if a device has been unregistered from APNS. This feedback mechanism clears the list of unregistered devices after it is read by the provider and only returns failures that happened since the provider last connected. So, the first provider to read from the feedback mechanism would clear the list, preventing the other providers from determining if a device has unregistered. If the other providers can’t tell that a device has been unregistered, they will still attempt to send to the device.

The HTTP/2 APNS communication mechanism has a more direct feedback system, which pushes to the device and immediately notifies the provider if the device is unregistered. Once a device is marked as unregistered in APNS and this is communicated to a push provider, the information may not be communicated to secondary push providers accessing the feedback mechanism. Therefore, secondary push providers may not know that a device is unregistered and may get errors back from APNS that don’t make sense.