# Active Screen Usage
The active screen is usually the screen that is currently on the device.

## Getting the Device Active Screen
1. Get a `Device` instance. How to get a `Device` instance is explained [here](get-device.md).
2. Use the `getActiveScreen()` method of the device instance.

Example code:
```java
Builder builder = Builder.getInstance();
DeviceSelectorBuilder selectorBuilder = new DeviceSelectorBuilder();
DeviceSelector deviceSelector = selectorBuilder.build();
Device device = builder.getDevice(deviceSelector);
Screen screen = device.getActiveScreen();
```
