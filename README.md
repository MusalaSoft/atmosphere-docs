# ATMOSPHERE mobile testing framework
## Installation instructions
The instructions for installation could be found [here](installation.md).
## Quick start project
Find it [here](#atmosphere-tests).
## Overview
Atmosphere is a black-box testing framework for native Android applications. One of the advantages of our solution is that we do not need the code of the application being tested, it is sufficient to provide the installation file that is available on the markets of the certain mobile platform. Atmosphere is easy to integrate with other third party testing tools like TestNG and Selenium. The users (testers) can configure which tests are going to be executed on what kind of devices. They can also specify that some tests need to be run on multiple different in parameters devices simultaneously.
Here is a short list of mobile specific things that can be tested with our framework:
 * Resource exhaustion - mobile devices are still with more limited hardware parameters and thus they are a lot more easily subject to resource exhaustion, for example the device can run out of battery.
 * Complex interactions - in scrollable views, time and date pickers, notification bar. The fact that smart phones go with touch screen displays allow for a lot more complex interaction with them. Using such interaction technique is far more intuitive to human beings, but is very hard to simulate using software, thus making testing a lot harder.
 * Gestures - swiping, tapping, clear and input text.
 * Complex selectors - elements on screen can be selected both with XPath and CSS expressions.
 * Manipulation of hardware sensors such as position sensors (magnetic field) and motion sensors (device acceleration).
 * Setting device orientation.
 * Setting GPS coordinates.
 * Checking WiFi connection, camera availability and GPS coordinates.
 * Sending, receiving and answering calls.

We really believe we provide a product focused primarily on the specifics of mobile testing, allowing for automating all these weird scenarios that you can not test with any contemporary testing tool. We have already succeeded automating a lot greater percentage of the test scenarios for our own mobile applications than what we were able beforehand.

## Topology
The ATMOSPHERE mobile testing framework consists of 4 main topological parts:

### Agent
The agent is responsible for establishing and maintaining the connection with specific devices. It acts as a middleman between the server and the mobile devices. The project of the agent is implemented as Java Project and consists of the following projects:
 * atmosphere-agent
 * atmosphere-server-agent-lib
 * atmosphere-agent-device-lib
 * atmosphere-commons

### Server
This is the interface the clients speak to. It establishes connections to agents and uses their set of devices to serve client requests. It is the part of the project that defines the methods exposed to the end clients. The project of the server is implemented as Java Project and consists of the following projects:
* atmosphere-server
* atmosphere-server-agent-lib
* atmosphere-client-server-lib
* atmosphere-commons

The code is developed in such a way that the server does not necessarily live on the same machine the agent does.

### Client
The client is the library that exposes the Atmosphere framework to the application testers.
The tests that declare the atmosphere-client library as a dependency do not need to run on the same machine as the server.

### Target devices
The target device is the place where the actual execution of the code happens. The target devices can be either real mobile devices or software Android emulators. Keep in mind that some tests are executable only on emulators as some manipulations are not possible on actual devices.

The code that needs to be deployed on the device is separated in multiple applications:
 * **atmosphere-service** - this is the basic Android application that runs an Android service establishing socket connection between the agent and the target device.
 * **atmosphere-ime** - this is a small Android application that is a simple implementation of input keyboard for Android. It is needed in order to make sure we can execute the tests requiring text input.
 * **atmosphere-uiautomator-bridge** - this is a special project that is not deployed as a proper Android project. It is a Java library and it provides some missing Android classes on older Android API levels and an additional socket for communication between the agent and the target device. When it is deployed on the target device, the agent can recognize the service and connect to its socket.

## ATMOSPHERE Tests
The Atmosphere tests are extended JUnit tests. Because of this Atmosphere can also be integrated with  [TestNG][1], in a way JUnit is. The classes with test methods are annotated with Atmosphere annotation (`@Server`) , which defines the properties of the server connection. The Atmosphere test methods must be annotated with the JUnit `@Test` annotation. Executing Atmosphere tests is done like running JUnit tests.

### Creating a project
1. Create a new Maven project.
    * This can be done by right-clicking on the white space under the Package Explorer tab in Eclipse IDE and clicking `New` -> `Maven Project`. If the Maven Project option is not visible, select `Other...` and then find `Maven Project` under the Maven folder.
    * Click `Next` and choose a Workspace location. You may also select the `Create a simple project` option if you don't have a specific archetype in mind and just want to try out the Atmosphere framework. Click `Next`.
    * If you haven't selected the simple project option in the previous step, you can select the desired archetype here. Click `Next`.
    * Specify the properties of the Maven Project and click `Finish`.
1. Add the Atmosphere Client library to the `pom.xml` file.
    * Open the `pom.xml` file and add the following dependency inside the `dependencies` tag:
    ```xml
    <dependency>
        <groupId>com.musala.atmosphere</groupId>
        <artifactId>atmosphere-client</artifactId>
        <version>0.0.1</version>
    </dependency>
    ```
1. Update the version of the JUnit library.
    * Open the `pom.xml` file and update the `version` property of the JUnit library to version 4 (or whichever is the latest), for example `4.12`.
    ```xml
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.12</version>
    </dependency>
    ```

### Creating an ATMOSPHERE test class
1. Create a new class (for this example let's name it `AtmosphereTestCase`)
1. Add a `@Server` annotation to the `AtmosphereTestCase` class. (The annotation is located in the `atmosphere-client` library). The annotation is used for connection with the Atmosphere server. For example:

```
@Server(ip = "10.0.9.35", port = 1980, connectionRetryLimit = 10)
public class AtmosphereHelloWorldTest {...}
```
1. Populate all 3 fields of the `@Server` with appropriate values as follows:
 - **ip** - the ip of the server, represented as string
 - **port** - integer, representing the port in the server's address
 - **connectionRetryLimit** - integer, representing the numbers of retries which should be made in case the connection with the Server breaks.

### Creating an ATMOSPHERE test case
Atmosphere test cases are methods, annotated with the JUnit `@Test` annotation where the Atmosphere Client API is used.

#### Lifecycle of an ATMOSPHERE test
The following sequence of events represents the life cycle of an Atmosphere test:
 1. Connect to an Atmosphere server - the server divides all usable devices among all clients
 1. Allocate appropriate device(s) - the client reserves himself or herself one or more of the usable devices on the server, on which they will run their tests
 1. Run test(s) - the tests are executed on the allocated from the previous step devices
 1. Release devices - by releasing, the client tells the server that their reserved devices are no longer needed and can be provided to other clients.
  - **Important note:** Make sure that you release any allocated devices at the end of your tests! Otherwise when you run your test next time, it may fail due to `NoSuchAvailableDeviceFound` exception, because the server thinks the device is still being used and will wait several minutes before marking it as available for allocation. Everybody who uses the same server would also be unable to get the device until the server timeout is passed.

#### ATMOSPHERE test example
- Consider the following scenario:
  - Get running emulator from the server with some characteristics ( RAM, screen, etc... );
  - Validate its battery level is valid ( between 0 and 101 );
  - Set it to some user-defined value;
  - Get the battery level again and verify it's the same as the set.
- This is one way the work can be done, using one test method to do all the work:

``` java
import static org.junit.Assert.assertEquals;
import static org.junit.Assert.assertTrue;

import org.junit.Test;

import com.musala.atmosphere.client.Builder;
import com.musala.atmosphere.client.Device;
import com.musala.atmosphere.client.util.Server;
import com.musala.atmosphere.commons.PowerProperties;
import com.musala.atmosphere.commons.beans.BatteryLevel;
import com.musala.atmosphere.commons.cs.deviceselection.DeviceSelector;
import com.musala.atmosphere.commons.cs.deviceselection.DeviceSelectorBuilder;
import com.musala.atmosphere.commons.cs.deviceselection.DeviceType;

@Server(ip = "10.0.9.35", port = 1980, connectionRetryLimit = 10)
public class AtmosphereSampleTest {

  @Test
  public void testBattery() throws InterruptedException {

    // Setting characteristics of the device we want to get
    DeviceSelectorBuilder deviceSelectorBuilder = new DeviceSelectorBuilder();
    DeviceSelector deviceSelector = deviceSelectorBuilder.deviceType(DeviceType.DEVICE_ONLY)
                                                             .ramCapacity(512)
                                                             .screenHeight(720)
                                                             .screenWidth(340)
                                                             .build();
    // ...

    // Get the builder instance, which will allocate a device only for us
    Builder serverCommunicator = Builder.getInstance();
    // Get the device by required parameters
    Device testDevice = serverCommunicator.getDevice(deviceSelector);

    // we want to test setting/getting of battery level in our device
    PowerProperties devicePower = testDevice.getPowerProperties();
    final BatteryLevel actualBatteryLevel = devicePower.getBatteryLevel();
    assertTrue("Negative battery level !", actualBatteryLevel.getLevel() > 0);
    assertTrue("Battery level - over 100% !", actualBatteryLevel.getLevel() <= 100);

    PowerProperties userDevicePower = new PowerProperties();
    userDevicePower.setBatteryLevel(new BatteryLevel(87));
    testDevice.setPowerProperties(userDevicePower);

    // wait some time while the device updates itself
    Thread.sleep(100);

    // validation the operation was done successfully
    PowerProperties currentDevicePower = testDevice.getPowerProperties();
    final BatteryLevel currentDeviceBatteryLevel = currentDevicePower.getBatteryLevel();
    assertEquals("Device battery level differs from the set!", userDevicePower.getBatteryLevel().getLevel(),
        currentDeviceBatteryLevel.getLevel());

    // Make sure to release allocated devices!
    serverCommunicator.releaseAllDevices();
  }
}
```
- This is another example, where `@Before` and `@After` JUnit annotations are used. The test does exactly the same as the one above, just better organized:

``` java
package com.musala.atmosphere.client.test.helloworld;

import static org.junit.Assert.assertEquals;
import static org.junit.Assert.assertTrue;

import org.junit.After;
import org.junit.Before;
import org.junit.Test;

import com.musala.atmosphere.client.Builder;
import com.musala.atmosphere.client.Device;
import com.musala.atmosphere.client.util.Server;
import com.musala.atmosphere.commons.PowerProperties;
import com.musala.atmosphere.commons.beans.BatteryLevel;
import com.musala.atmosphere.commons.cs.deviceselection.DeviceSelector;
import com.musala.atmosphere.commons.cs.deviceselection.DeviceSelectorBuilder;
import com.musala.atmosphere.commons.cs.deviceselection.DeviceType;

@Server(ip = "10.0.9.35", port = 1980, connectionRetryLimit = 10)
public class AtmosphereSampleTest {

  private Device testDevice;

  @Before
  public void setUp() {
    // Setting characteristics of the device we want to get
    DeviceSelectorBuilder deviceSelectorBuilder = new DeviceSelectorBuilder();
    DeviceSelector deviceSelector = deviceSelectorBuilder.deviceType(DeviceType.DEVICE_ONLY)
                                                             .ramCapacity(512)
                                                             .screenHeight(720)
                                                             .screenWidth(340)
                                                             .build();
    // ...

    // Get the builder instance, which will allocate a device only for us
    Builder serverCommunicator = Builder.getInstance();

    // Get the device by required parameters
    Device testDevice = serverCommunicator.getDevice(deviceSelector);
  }

  @After
  public void tearDown() {

    // release taken device
    Builder serverCommunicator = Builder.getInstance();
    serverCommunicator.releaseDevice(testDevice);
  }

  @Test
  public void testBattery() throws InterruptedException {

    // we want to test setting/getting of battery level in our device
    PowerProperties devicePower = testDevice.getPowerProperties();
    final BatteryLevel actualBatteryLevel = devicePower.getBatteryLevel();
    assertTrue("Negative battery level !", actualBatteryLevel.getLevel() > 0);
    assertTrue("Battery level - over 100% !", actualBatteryLevel.getLevel() <= 100);

    PowerProperties userDevicePower = new PowerProperties();
    userDevicePower.setBatteryLevel(new BatteryLevel(0));

    // apply our properties to the device
    testDevice.setPowerProperties(userDevicePower);

    // wait some time while the device updates itself
    Thread.sleep(100);

    // validation the operation was done successfully
    PowerProperties currentDevicePower = testDevice.getPowerProperties();
    final BatteryLevel currentDeviceBatteryLevel = currentDevicePower.getBatteryLevel();
    assertEquals("Device battery level differs from the set!", userDevicePower.getBatteryLevel().getLevel(),
        currentDeviceBatteryLevel.getLevel());
  }
}
```

#### More examples
More usage scenarios are available [here][2]

### Running an ATMOSPHERE test case
Running Atmosphere Test cases is done in the same way as running any other JUnit test case. You should right click on the test class. Click on `Run As` -> `JUnit Test Case` or `Run As` -> `Run Configurations` and select the proper configurations for a JUnit test.

[1]: http://testng.org/
[2]: usage/README.md
