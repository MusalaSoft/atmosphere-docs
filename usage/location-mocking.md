# Mocking the device location
The device's location can be easily mocked using the `Device.mockLocation` method by providing a `GeoLocation` as a parameter. *Information about how to get a Device instance can be found [here](get-device.md).*

1. You will only need latitude and longtitude values to create a `GeoLocation` object. The `provider` parameter is not required and defaults to `gps`:
 ```java
 GeoLocation mockLocation = new GeoLocation(latitude, longitude, provider);
 ```
 A list of all currently supported providers (by API level) is available in the `LocationManager` [documentation](https://developer.android.com/reference/android/location/LocationManager.html#constants). You can either use the provider's string value as a `GeoLocation` parameter or import the `LocationManager` class and use its constants like this: `LocationManager.GPS_PROVIDER`.

1. You can set additional properties of the `GeoLocation` object by using its `set` methods, for example:
 ```java
 mockLocation.setAltitude(altitude);
 ```
1. Once you have a `GeoLocation` instance ready, just call the `mockLocation` method and use the location as a parameter:
 ```java
 device.mockLocation(mockLocation);
 ```
 The device's location should now be being mocked.

1. To disable the location mocking for a specific provider use `disableMockLocation`:
 ```java
 device.disableMockLocation(provider);
 ```
