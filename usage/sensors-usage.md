## Sensors ##

Most Android-powered devices have built-in sensors that measure motion, orientation, and various environmental conditions. These sensors are capable of providing raw data with high precision and accuracy, and are useful if you want to monitor three-dimensional device movement or positioning, or you want to monitor changes in the ambient environment near a device. You can get or set `Acceleration, Magnetic field and Device Orientation`. Note that all `set` methods can be used for `Emulator only`.

In order to use these methods you have to select testing device. For more information see [How to get device](get-device.md).

### Acceleration ###

You can set or get current `Device Acceleration`. `Device Acceleration` has it's own class and contains 3 variables X, Y and Z representing coordinate system.

 * Device Acceleration class
  * Class containing information about the device acceleration.
  * It contains different Device perspective.
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

### Device Orientation ###

You can set or get current Device Orientation. Device Orientation has it's own class and contains 3 variables `AZIMUTH`, `PITCH` and `ROLL` representing space. The Device Orientation set method is `Deprecated` by Android and it's not wise to use it.

 * Device Orientation class
  * Container class for the device orientation in space.
  * Contains Get methods for Landscape, Portrait, upsideDownLanscape and upsideDownPortrait.
  * Contains Set methods for North, South, East, West.

Example code:

```java
DeviceOrientation deviceOrientation = testDevice.getDeviceOrientation();
```

### Magnetic Field ###

You can sets new magnetic field for device. `DeviceMagneticField` class contains `MagneticField's logic`.  

Example Code:

```java
DeviceMagneticField magneticField = testDevice.setMagneticField();
```
