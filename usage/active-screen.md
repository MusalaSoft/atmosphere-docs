# Active Screen Usage
Active screen is usually the screen that is currently on the device. It's very important to keep your screen instance up to date, because it contains the latest changes and currently present Elements.

## Get Device Active Screen
1. Get device. How to get a Device explained [Here](get-device.md).
2. use Device method getActiveScreen.

Example code:
```java
Builder builder = Builder.getInstance();
DeviceSelectorBuilder selectorBuilder = new DeviceSelectorBuilder();
DeviceSelector deviceSelector = selectorBuilder.build();
Device device = builder.getDevice(deviceSelector);
Screen screen = device.getActiveScreen();
```

## When to Update Screen
We get Elements from the **Active Screen** of the **Device** so when we want to get specific Element it should be present on the **Active screen** and our screen instance should be up to date. Which means that every time there is some change on the **Active Screen** in order to get Elements that were not there before we have to call **screen.updateScreen()** method to update our screen instance. Also when one Element is not on the active screen anymore it becomes unusable because you can only interact with Elements that are present on the **Active Screen**. You need to **updateScreen** in following cases.
>* Started new Application or Activity and we want to interact with it.
* Element changed his status. If you want to check his new status you need to update Screen and get another instance of this Element because the information it contains is from the old Screen.
* Usually after every big change you need to update the Screen or changed Element's status and want to continue to interact with it.
