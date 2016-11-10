## ATMOSPHERE Features for emulators and real devices overview

### Overview
| Feature                    | On emulator   | On real device  | Comments      |
| -------------------------- |:-------------:|:---------------:|:--------------|
| getFreeRam()               | ?             | ?               |               |
| getScreenshot()            | ?             | ?               |               |
| installApk()               | ?             | ?               |               |
| startActivity()            | ?             | ?               |               |
| setAutoRotation()          | ?             | ?               |               |
| setScreenOrientation()     | ?             | ?               |               |
| getUiXml()                 | ?             | ?               |               |
| inputText()                | ?             | ?               |               |
| setNetworkLatency()        | ?             | ?               |               |
| setNetworkSpeed()          | ?             | ?               |               |
| ~~setDeviceOrientation()~~ | ?             | ?               |               |
| setAcceleration()          | ?             | ?               |               |
| getPowerState()            | ?             | ?               |               |
| getBatteryState()          | ?             | ?               |               |
| getBatteryLevel()          | ?             | ?               |               |
| setAirplaneMode()          | ?             | ?               |               |
| getDeviceOrientation()     | ??            | ??              |               |
| getConnectionType()        | ?             | ?               |               |
| setBatteryLevel()          | ?             | ?               |On real device, sets the battery level only for limited time|
| setBatteryState()          | ?             | ?               |On real device, sets the battery state only for limited time|
| setPowerState()            | ?             | ?               |On real device, sets the power state only for limited time  |
| getMobileDataState()       | ?             | ?               |               |
| setMobileDataState()       | ?             | ?               |               |
| getNetworkSpeed()          | ?              | ?               |               |
| getNetworkLatency()        | ?              | ?               |               |
| setWiFi()                  | ?             | ?               |               |
| setLocked()                | ?             | ??              |               |
| isAwake()                  | ?             | ?               |               |
| receiveSms()               | ?             | ?               |               |
| mockLocation()             | ?             | ?               |               |

#### Legend:
|sign   | description      |
|---|----------------------|
|?  | fully working|
|?? | unrealiable |
|?  | unknown |
|? | missing |
|blank|  not possible |

### Features that work on both real devices and emulators
* getFreeRam();
* getScreenshot();
* installApk();
* setAutoRotation()
* setScreenOrientation();
* getUiXml();
* record macro;
* inputText();
* setAirplaneMode();

### Emulator ONLY features
* setNetworkLatency();
* setNetworkSpeed();
* ~~setDeviceOrientation()~~ - deprecated
* setAcceleration();
* setMobileDataState();
* getMobileDataState();
* receiveSms();

### Things that we can't do on real devices but would like to
* All emulator ONLY features
