## Using Device Settings Manager ##

Before getting or inserting some android system settings, testing device should be selected. More information about getting the preferred device is available [here](get-device.md).

Device instance, created after this step, already offers some functionalities related with manipulation of the Android settings, such as getting screen orientation, setting airplane mode or screen off timeout.
But for the most curious users Atmosphere provides Device Settings Manager for getting or inserting all kinds of Android device settings. Instance of the settings manager for the current device can be created as follows:
```java
DeviceSettingsManager deviceSettings = device.getDeviceSettingsManager();
```

Simple examples will be given to explain the usage of the provided manager. There is an enumeration - !AndroidSystemSettings, representing miscellaneous system preferences.

The following example will change the brightness of the screen:
```java
int defaultBrightness = deviceSettings.getInt(AndroidSystemSettings.SCREEN_BRIGHTNESS);
System.out.println("Default brightness: " + defaultBrightness);
deviceSettings.putInt(AndroidSystemSettings.SCREEN_BRIGHTNESS, 54);
int changedBrightness = deviceSettings.getInt(AndroidSystemSettings.SCREEN_BRIGHTNESS);
System.out.println("Brightness after change: " + changedBrightness);
```

Next example shows how to increment alarm volume with 2:
```java
int defaultAlarmVolume = deviceSettings.getInt(AndroidSystemSettings.VOLUME_ALARM);
System.out.println("Default alarm volume: " + defaultAlarmVolume);
deviceSettings.putInt(AndroidSystemSettings.VOLUME_ALARM, defaultAlarmVolume + 2);
int changedAlarmVolume = deviceSettings.getInt(AndroidSystemSettings.VOLUME_ALARM);
System.out.println("Alarm volume after change: " + changedAlarmVolume);
```

>***Note:***  
>For some of the settings provided in the !AndroidSystemSettings users may need admin privileges.

## Useful links ##
[Android Settings](https://developer.android.com/reference/android/provider/Settings.System.html)
