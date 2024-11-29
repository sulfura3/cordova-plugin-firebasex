# cordova-plugin-firebasex

Brings push notifications, analytics, event tracking, crash reporting and more from Google Firebase to your Cordova project.

Supported platforms: Android and iOS

# Differences of this fork over the repository it is based on
This fork adds a method that allows one to check if (and which) notification triggered the launch of the app in a more reliable way. As such, I will only document the changes I made. For a full documentation, please check the original repository

# Request the original notification that triggered the launch of the app
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

# Todo
* Currently, only the iOS code is implemented. Android implementation will be added shortly