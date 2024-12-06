# cordova-plugin-firebasex

Brings push notifications, analytics, event tracking, crash reporting and more from Google Firebase to your Cordova project.

Supported platforms: Android and iOS

## About This Fork

This fork introduces a new method for reliably identifying whether a notification triggered the app launch, and if so, retrieving the associated notification. This feature addresses issues observed in iOS where notifications may not reliably trigger the `onMessageReceived` callback, particularly during a cold start.

For comprehensive documentation of the base plugin, please refer to the [original repository](https://github.com/dpa99c/cordova-plugin-firebasex).

## New Feature: Retrieve the Notification That Triggered App Launch
This fork provides a method to retrieve the original notification that caused the app to launch. Use the following code to access this feature:
```javascript
document.addEventListener('deviceready', function() {
    FirebasePlugin.getLaunchNotification(notification => {
        if (notification) {
            // do something based on notification
        }
    }, error => {
        console.error("Error retrieving launch notification:", error);
    });
})
```

## Notes
### Launch Notification Behavior
* **Clearing Behavior**: Once the launch notification is requested using getLaunchNotification, it is cleared from memory. This prevents the app from repeatedly behaving as though it was launched by a notification.
* **Implementation Consideration**: While a more robust approach might involve clearing the launch notification upon detecting a webview refresh, the current implementation aligns with our use case. Be mindful of this behavior when integrating the plugin into your project.
Requesting the launch notification currently clears it from memory. This is done so that, if the launch notification handling happens immediately when the web view is loaded, the app does no longer behave like it was launched from a notification.
