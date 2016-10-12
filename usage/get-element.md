## How to get element from Screen

The main method for interacting with a Device is using Elements. The Elements can execute actions like clicks, scrolls, input text, double taps, long press and so on. There are also some specific Elements like `ScrollableView`, `DatePicker` and `TimePicker` that have additional functionality. The main method for creating Elements is by using an `ElementSelector` which contains the attributes that the desired Element should have. Note that if there are two or more Elements with the same attributes an error occurs. We can get an instance of an Element from the Active Screen. More information about the Active Screen and how to create a Screen instance can be found [here](active-screen.md).

### Get an Element by an `ElementSelector`

1. Create a `Screen` instance.
2. Create an `ElementSelector` and add `CssAttributes`.
   * Creating and adding `CssAttributes` is explained [here](create-element-selector.md).
3. Use the `screen.getElement(selector)` method and pass the created `ElementSelector` as an argument.

Example code:

```java
Screen screen = device.getActiveScreen();
UiElementSelector elementSelector = new UiElementSelector();
elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.widget.TextView");
elementSelector.addSelectionAttribute(CssAttribute.TEXT, "Browser");
UiElement browserElement = screen.getElement(elementSelector);
```

### Get an Element by a `CssQuery`

1. Create a `Screen` instance.
2. Construct a `CssQuery` that contains Element attributes.
  * More information about constructing a `CssQuery` can be found [here](create-xpath-and-cssquery.md).
3. Use the `screen.getElementByCSS(query)` method and pass the created `CssQuery` as an argument.

Example code:

```java
Screen screen = device.getActiveScreen();
final String CSS_QUERY = "[bounds=[37,27][99,46]][class=android.widget.TextView]";
UiElement textViewElement = screen.getElementByCSS(CSS_QUERY);
```

### Get an Element by xPathQuery

1. Create a `Screen` instance.
2. Construct an `xPathQuery` that contains Element attributes.
  * More information about constructing an `XpathQuery` can be found [here](create-xpath-and-cssquery.md).
3. Use the `screen.getElementByXPath(xPathquery)` method and pass the created `xPathQuery` as an argument.

Example code:

```java
Screen screen = device.getActiveScreen();
final String XPATH_QUERY = "//node[@class='android.widget.ImageView']";
UiElement textViewElement = screen.getElementByXPath(XPATH_QUERY);
```

### Get an Element When Present

This method is useful when we want to start an Application or execute some action which might take some time to load the next screen. As you know you can't get or interact with an Element that is not present on the active screen, so in some cases you need to wait for the `Element` to show.

1. Create a `Screen` instance.
2. Create an `ElementSelector` and add `CssAttributes`.
  * Creating and adding `CssAttributes` is explained [here](create-element-selector.md).
3. Use the `screen.getElementWhenPresent(selector, timeout)` method using the created `ElementSelector` and a given timeout.
  * Timeout is the time you are willing to wait for the Element to show on the screen. If there is no such Element on the screen after that time, an error will occur.
  * Timeout is set in milliseconds, so if you want to wait for a second, give a timeout of 1000.
  * Note that the `getElementWhenPresent()` method contains a default timeout, so it's not necessary to always pass a timeout parameter.

Example Code:

```java
Screen screen = device.getActiveScreen();
UiElementSelector elementSelector = new UiElementSelector();
elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.widget.TextView");
elementSelector.addSelectionAttribute(CssAttribute.TEXT, "Browser");
UiElement browserElement = screen.getElementWhenPresent(elementSelector, 3000);
```

### Get all Elements by a Selector

There is an option for getting many Elements with common Attributes. For example, we could get all Elements that have the class name `android.widget.EditText`. They can also be selected by CssQuery, XPath and `ElementSelector`. These methods return `List<UiElement>`.

### Get the Children of an Element

You can get the Children of an Element by a given selector. For example, we could get all `TextView` Elements inside a `FrameLayout` Element. More information about how to get Children Elements can be found [here](get-children.md).

### Attributes with which you can Select an Element ###

You can select an Element with the attributes in **NoteDetails** in the Dump XML. Every Element has these attributes and can be selected by one or more of them. Also they contain fields like `Enabled`, `Checked`, `Focused` and others. With them we can check if the interactions are successful or not. For more information you can check [How to dump XML](xml-dump.md).

![XML Dump](images/DumpXmlAttributes.jpg)
