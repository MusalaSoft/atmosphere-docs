# Notification Bar Usage

1. The `NotificationBar` class is used to interact with the notification bar.
2. In order to get the notification bar for a device, you should use the constructor of the `NotificationBar` class which requires a device as parameter:

 ```java
 NotificationBar notificationBar = new NotificationBar(device);
 ```

3. Now that you have a `NotificationBar` instance, you can use the methods provided in the class.
4. The methods `open()` or `clearAllNotifications()` do nothing if the notification bar is already opened or the notifications are all cleared respectively, so you do not have to worry about that.
5. In order to get a single notification, you should use one of the get notification methods provided. You don't have to use these methods with parameters that describe the full size notification, they can be used with parameters that describe a part of the notification and the returned result will be the full size notification as an `UiElement`:

 ```java
 UiElement notification = notificationBar.getNotificationByText("Sample");
 ```

6. The notification instance supports some of the regular `UiElement` methods. For example the `tap()` or `tapOnChildElement()` methods can be used to tap on a specific button in the notification and `pinchIn()` or `pinchOut()` can be used to make the notification bigger or smaller.

> ***Note:*** *The notification bar methods use functionality from `UiAutomator` requiring API 18 or above, so the notification bar class should be used only on a device with API 18 or higher.*
