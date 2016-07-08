# Get device

## Getting a device without specifying parameters

To simply get a connected device without setting some specific device parameters and execute test scenarios on it, first a Builder instance should be created. After that a device can be get from the builder, passing an empty device selector with no specific parameters to it.
```java
Builder builder = Builder.getInstance();
DeviceSelectorBuilder selectorBuilder = new DeviceSelectorBuilder();
DeviceSelector deviceSelector = selectorBuilder.build();
Device device = builder.getDevice(deviceSelector);
```

## Getting a device with specific parameters

In some situations, the client may want to get a certain device, for example with a specific version of the operating system, API level or specify whether the device is emulator or a real device is preferred.

 * There are four different options for device type supported, which can be set to the device selector, when getting a device from the builder: `EMULATOR_ONLY`, `DEVICE_ONLY`, `DEVICE_PREFERRED`, `EMULATOR_PREFERRED`. For example using `EMULATOR_PREFERRED`, will get an emulator, but if no emulator is found a real device will be chosen.
```java
Builder builder = Builder.getInstance();
DeviceSelectorBuilder selectorBuilder = new DeviceSelectorBuilder().deviceType(DeviceType.EMULATOR_PREFERRED);
DeviceSelector deviceSelector = selectorBuilder.build();
Device device = builder.getDevice(deviceSelector);
```
 * A device can also be selected by setting its operating system version. For example:
```java
 Builder builder = Builder.getInstance();
 DeviceSelectorBuilder selectorBuilder = new DeviceSelectorBuilder().deviceOs(DeviceOs.KITKAT_4_4);
 DeviceSelector deviceSelector = selectorBuilder.build();
 Device device = builder.getDevice(deviceSelector);
```
 * A device can be taken by its API level. The only thing, that must be changed in the previous examples to match the preferred device, is to set different criterion that is used by the device selector builder. Next few examples will introduce the option for specifying the minimum, maximum and target API level as a device selection criterion. If a target API is given, device with API level equals to the requested one will be searched.
```java
selectorBuilder.targetApi(18);
```
 When both range and target API levels are set, first the builder will try to find a device matching the target. If such device is not available, it will search for a suitable device in the given range of API levels.
```java
selectorBuilder.minApi(12).maxApi(21).targetApi(18);
```

 * Another matching criterion, when getting a device from the created builder instance is the model of the preferred device. For example:
```
selectorBuilder.deviceModel("GT-I9100");
```

 * It is also possible to set if the selected device has a camera:
```java
selectorBuilder.isCameraAvailable(true);
```

* Another example of getting a specific device from the builder is to set the screen DPI of the preferred device:
```java
selectorBuilder.screenDpi(48);
```

* An useful device selection criterion is also setting the wanted screen resolution:
```java
selectorBuilder.screenHeight(720);
selectorBuilder.screenWidth(480);
```

* Setting RAM of the device, which will be chosen, is also available:
```java
selectorBuilder.ramCapacity(512);
```

* And finally the device can also be picked by a serial number:
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
