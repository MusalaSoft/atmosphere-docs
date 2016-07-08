# Notification Bar Usage

1. The `NotificationBar` class is used to interact with the notification bar.
2. In order to get the notification bar from a device, you should use the constructor of the `NotificationBar` which requires a device as parameter:
```java
NotificationBar notificationBar = new NotificationBar(device);
```
3. Now that you have a `NotificationBar` object, you can use the functions provided in the class.
4. The functions `open()` or `clearAllNotifications()` do nothing if the notification bar is already opened or the notifications are all cleared respectively, so you do not have to worry about that.
5. In order to get a single notification, you should use one of the get notification functions provided. You don't have to use the functions with parameters that describe the full size notification, they can be used with parameters that describe a part of the notification and the returned result will be the full size notification as an `UiElement`:

```java
UiElement notification = notificationBar.getNotificationByText("Sample");
```
6. To use functions on the returned notification, simply use functions from `UiElement`. Some of the functions that can be used on a `UiElement` notification are `tapOnChildElement()` (which can be used to tap on a specific button in the notification), `tap()`, `pinchIn()` or `pinchOut()`, where the last two functions can be used to make the notification bigger or smaller.

### Notes
> 1. The notification bar class functions use functionality from `UiAutomator` requiring API 18 or above, so the notification bar class should be used only on a device with API 18 or higher.
