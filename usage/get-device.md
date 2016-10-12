# Get a device

## Getting a device without specifying parameters

To simply get a connected device without specifying device parameters, and execute test scenarios on it, a `Builder` and an empty `DeviceSelector` should be created first. A `Device` instance can then be gotten from from the `Builder` by passing the empty device selector.
```java
Builder builder = Builder.getInstance();
DeviceSelectorBuilder selectorBuilder = new DeviceSelectorBuilder();
DeviceSelector deviceSelector = selectorBuilder.build();
Device device = builder.getDevice(deviceSelector);
```

## Getting a device with specific parameters

In some situations, the client may want to get a certain device, for example with a specific version of the operating system, API level or specify whether the device is an emulator or a real device is preferred.

 * There are four supported options for a device type that could be set in the device selector: `EMULATOR_ONLY`, `DEVICE_ONLY`, `DEVICE_PREFERRED`, `EMULATOR_PREFERRED`. For example using `EMULATOR_PREFERRED`, will get an emulator, but if no emulator is found a real device will be chosen.
```java
Builder builder = Builder.getInstance();
DeviceSelectorBuilder selectorBuilder = new DeviceSelectorBuilder().deviceType(DeviceType.EMULATOR_PREFERRED);
DeviceSelector deviceSelector = selectorBuilder.build();
Device device = builder.getDevice(deviceSelector);
```
 * A device can also be selected by setting its operating system version in the selector. For example:
```java
 Builder builder = Builder.getInstance();
 DeviceSelectorBuilder selectorBuilder = new DeviceSelectorBuilder().deviceOs(DeviceOs.KITKAT_4_4);
 DeviceSelector deviceSelector = selectorBuilder.build();
 Device device = builder.getDevice(deviceSelector);
```
 * A device can be selected by its API level. If a target API is given, the Builder will look for a device with the exact API level.
```java
selectorBuilder.targetApi(18);
```
 However, if both range and target API levels are set, the Builder will try to find a device matching the target API, but if such device is not available, it will search for a suitable device in the given range of API levels.
```java
selectorBuilder.minApi(12).maxApi(21).targetApi(18);
```

 * Another selector criterion can be the device model. For example:
```
selectorBuilder.deviceModel("GT-I9100");
```

 * It is also possible to specify if the selected device should have a camera:
```java
selectorBuilder.isCameraAvailable(true);
```

* Or the specific screen DPI:
```java
selectorBuilder.screenDpi(450);
```

* Or the exact screen resolution:
```java
selectorBuilder.screenHeight(1920);
selectorBuilder.screenWidth(1080);
```

* Or the RAM of the device:
```java
selectorBuilder.ramCapacity(2048);
```

* And finally the device can also be selected by a serial number:
```java
selectorBuilder.serialNumber("0176c8b7c6200c00");
```

## Recommendation
One important thing to remember is that it is recommended to release devices in the end of the test, in a finally clause. In this way when something goes wrong there is no need to wait for the default timeout to expire and all devices will be released on time.
```java
builder.releaseAllDevices();
```
It is also possible to release a certain device:
```java
builder.releaseDevice(device);
```
