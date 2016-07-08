## How to get element from Screen ##

The main method for interacting with a Device is using Elements. Element can execute actions like clicks, scrolls, input text, double taps, long press and so on. There are also some specific Elements like `ScrollableView`, `DatePicker` and `TimePicker` that have additional functionality. The main method for creating Elements is by `ElementSelector` which contains the attributes that Element should have. Note that if there are two or more Element with the same attributes an error occur. We get Elements from the screen that's why it's important to always keep our screen instance up to date. More information about Active Screen and how to Create Screen instance [Here](active-screen.md).

### Get Element by `ElementSelector`

1. Create `Screen` instance.
2. Create `ElementSelector` and add `CssAttributes`.
   * Creating and adding `CssAttributes` explained [Here](create-element-selector.md).
3. Get Element by screen's `getElement(selector)` method using the created `ElementSelector`.

Example code:

```java
Screen screen = device.getActiveScreen();
UiElementSelector elementSelector = new UiElementSelector();
elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.widget.TextView");
elementSelector.addSelectionAttribute(CssAttribute.TEXT, "Browser");
UiElement browserElement = screen.getElement(elementSelector);
```

### Get Element by `CssQuery`

1. Create `Screen` instance.
2. Construct `CssQuery` that contains an Element attributes.
  * More information about Constructing `CssQuery` [Here](create-xpath-and-cssquery.md).
3. Get Element by screen's `getElementByCSS(query)` method using the created `CssQuery`.

Example code:

```java
Screen screen = device.getActiveScreen();
final String CSS_QUERY = "[bounds=[37,27][99,46]][class=android.widget.TextView]";
UiElement textViewElement = screen.getElementByCSS(CSS_QUERY);
```

### Get Element by xPathQuery ###

1. Create `Screen` instance.
2. Construct `xPathQuery` that contains an Element attributes.
  * More information about Constructing `XpathQuery` [Here](create-xpath-and-cssquery.md).
3. Get Element by screen's `getElementByXPath(xPathquery)` method using the created `xPathQuery`.

Example code:

```java
Screen screen = device.getActiveScreen();
final String XPATH_QUERY = "//node[@class='android.widget.ImageView']";
UiElement textViewElement = screen.getElementByXPath(XPATH_QUERY);
```

### Get Element When Present ###

This method is needed because sometimes when we want to start an Application or execute some action, like clicking a button, the Device might need some time for loading the next screen. As you know you can't get or interact with Element that is not present on the active screen so in some cases you need to wait for the `Element` to show.
 * Getting an Element When Present
  1. Create `Screen` instance.
  2. Create `ElementSelector` and add `CssAttributes`.
    * Creating and adding `CssAttributes` explained [Here](create-element-selector.md).
  3. Get Element by screen's `getElementWhenPresent(selector, Timeout)` method using the created `ElementSelector`.
    * Timeout is the time you are willing to wait for the Element to show on the screen. If there is no present Element on the screen after timeout error occurs.
    * Timeout is set in milliseconds so if you want to wait at least 1 second give timeout 1000.  
    * Note that `getElementWhenPresent()` contains default timeout so it's not necessary to give timeout parameter.

Example Code:

```java
Screen screen = device.getActiveScreen();
UiElementSelector elementSelector = new UiElementSelector();
elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.widget.TextView");
elementSelector.addSelectionAttribute(CssAttribute.TEXT, "Browser");
UiElement browserElement = screen.getElementWhenPresent(elementSelector, 3000);
```

### Get all Elements by Selector ###

There is an option for getting many Elements with common Attributes. For Example get all Elements that have class name `android.widget.EditText`. They can also be selected by CssQuery, XPath and `ElementSelector`. These methods return `List<UiElement>`.

### Get Children of Element

You can also get the Children of an Element by given selector. For example get all `TextView` Elements in `FrameLayout` Element. More information about how to get Children [Here](get-children.md).

### Attributes with which you can Select an Element ###

You can select an Element with the attributes in `NoteDetails`. Every Element has these attributes and can be selected by one or more of them. Also they contained fields like `Enabled`, `Checked`, `Focused` and others. With them we can check if the interactions are successful or not.  For more information you can check [How to dump Xml](xml-dump.md).

![Xml Dump](images/DumpXmlAttributes.jpg)
