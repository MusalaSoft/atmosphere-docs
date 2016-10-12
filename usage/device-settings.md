## Using Device Settings Manager

Before getting or setting device system settings, a testing device should be selected. More information about getting the preferred device is available [here](get-device.md).

The `Device` instance offers some functionalities related to manipulation of system settings, such as getting the screen orientation, setting airplane mode or screen off timeout but for the most curious users Atmosphere provides Device Settings Manager for getting and setting all kinds of device settings. Instance of the settings manager for the current device can be created as follows:
```java
DeviceSettingsManager deviceSettings = device.getDeviceSettingsManager();
```

The following examples will explain the usage of the provided manager. The `AndroidSystemSettings` enumeration represents miscellaneous system preferences.

To change the brightness of the screen:
```java
int defaultBrightness = deviceSettings.getInt(AndroidSystemSettings.SCREEN_BRIGHTNESS);
System.out.println("Default brightness: " + defaultBrightness);
deviceSettings.putInt(AndroidSystemSettings.SCREEN_BRIGHTNESS, 54);
int changedBrightness = deviceSettings.getInt(AndroidSystemSettings.SCREEN_BRIGHTNESS);
System.out.println("Brightness after change: " + changedBrightness);
```

To increment alarm volume with 2:
```java
int defaultAlarmVolume = deviceSettings.getInt(AndroidSystemSettings.VOLUME_ALARM);
System.out.println("Default alarm volume: " + defaultAlarmVolume);
deviceSettings.putInt(AndroidSystemSettings.VOLUME_ALARM, defaultAlarmVolume + 2);
int changedAlarmVolume = deviceSettings.getInt(AndroidSystemSettings.VOLUME_ALARM);
System.out.println("Alarm volume after change: " + changedAlarmVolume);
```

>***Note:*** *Some settings provided with the `AndroidSystemSettings` may need admin privileges.*

## Useful links ##
[Android Settings](https://developer.android.com/reference/android/provider/Settings.System.html)
