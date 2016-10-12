## Sensors
Most Android-powered devices have built-in sensors that measure motion, orientation, and various environmental conditions. These sensors are capable of providing raw data with high precision and accuracy, and are useful if you want to monitor three-dimensional device movement or positioning, or you want to monitor changes in the ambient environment near a device. You can get or set *Acceleration*, *Magnetic field* and *Device Orientation*. **Note that all `set` methods are only supported on Emulators.**

To use these methods you have to select a testing device. For more information see [How to get a device](get-device.md).

### Acceleration
You can set or get the current `Device Acceleration`. `Device Acceleration` has it's own class and contains 3 variables X, Y and Z representing the coordinate system.

The `Device Acceleration` class contains information about the device acceleration and several Device perspectives:
* Landscape
* Portrait
* Lie Down
* Reverse Landscape
* Reverse Lie Down
* Reverse Portrait

Example code: Set Device Acceleration.

```java
final float accelerationX = 3.087f;
final float accelerationY = -1.130f;
final float accelerationZ = 5.904f;
DeviceAcceleration deviceAcceleration = new DeviceAcceleration(accelerationX, accelerationY, accelerationZ);
testDevice.setAcceleration(deviceAcceleration);
```

Example code: Get Device Acceleration.

```java
DeviceAcceleration deviceAcceleration = testDevice.getAcceleration();
```

### Device Orientation

You can set or get the current `Device Orientation`. `Device Orientation` has it's own class and contains 3 variables `AZIMUTH`, `PITCH` and `ROLL` representing space. **Note that the Device Orientation `set` method is now `Deprecated` in Android.**

The `Device Orientation` class is a container for the device orientation in space.
* Contains `get` methods for Landscape, Portrait, upsideDownLanscape and upsideDownPortrait.
* Contains `set` methods for North, South, East, West.

Example code:

```java
DeviceOrientation deviceOrientation = testDevice.getDeviceOrientation();
```

### Magnetic Field

You can set the magnetic field for a device. The `DeviceMagneticField` class contains the `MagneticField` logic.

Example Code:

```java
final float xAxis = 3.087f;
final float yAxis = -1.130f;
final float zAxis = 5.904f;
DeviceMagneticField magneticField = new DeviceMagneticField(xAxis, yAxis, zAxis);
boolean isMagneticFieldSet = testDevice.setMagneticField(magneticField);
```
