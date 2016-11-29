# Parallel testing
The ATMOSPHERE framework suports a parallel testing using TestNG. Of course you can use a parallelism in the standard way provided by TestNG or every other test framework with ability to run tests in parallel.

You can run a single unit test on multiple devices following these easy steps:
* Add TestNG to the build path of the test project
* The test class should inherits `ParallelDataProvider` and implements `setUp()` method. Don't forget a `@BeforeClass` annotation.

* In the `setUp()` method you can create multiple device selector and add the selectors with `this.addSelector` method:
```java
@Override
    @BeforeClass
    public void setUp() {
        this.testBuilder = Builder.getInstance();
        DeviceSelectorBuilder selectorBuilder = new DeviceSelectorBuilder();
        DeviceSelector firstSelector = selectorBuilder.deviceType(DeviceType.DEVICE_PREFERRED).targetApi(22).build();
        DeviceSelector secondSelector = selectorBuilder.deviceType(DeviceType.DEVICE_PREFERRED).targetApi(23).build();
        this.addSelector(firstSelector);
        this.addSelector(secondSelector);
    }
```

* Add an anotation to the method that you want to execute in parallel. This is a standard TestNG annotation:
```java
@Test(dataProvider = "getData")
public void testInParallel(DeviceSelector deviceSelector) throws Exception {
    // the test logic
}
```
> Note: ``"getData"`` is a static method provided from `ParallelDataProvider` class.
