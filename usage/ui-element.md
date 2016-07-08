## Elements

Before executing an action on `UiElement`, testing device should be selected. For more information see
[How to get device](get-device.md).
Next step is to get the active screen from the selected device

```java
Screen screen = device.getActiveScreen();
```

For more information about getting elements see [How to get element](get-element.md)

After that different actions can be executed on the selected `UiElement`.

### Gestures

You can execute simple gestures on the `UiElement`: tap, double tap, long press etc. Also there are Edit Text methods that allow you to clear or input Text in `UiElement` that is `EditText`. For more information see [Here](gestures.md).

### Revalidation

Interaction with Elements constantly changes the Active Screen of the Device. Re validation of an Element is done in order to check if the Element is still Intact and Present on the Active screen and can be interact with it. Usualy you have to update the Screen and get another instance of the Element which contains the new values of the css attributes. More information about when to updateScreen see [Here](active-screen.md).

Example code:

```java
boolean isElementValid = element.validate();
```


### Get Element Selector

You can get the Selector by which the element was Selected.

Example code:

```java
UiElementSelector elementSelector = element.getElementSelector();
```
### Get Children

`UiElements` usually have tree like structure. For example `UiElement` that is `ListView` can contain `TextView`, `ImageView` and so on. You can get them by `getChildren` methods.

Example code will return all Children of the element that are Images:

```java
UiElementSelector elementSelector = new UiElementSelector();
elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.view.ImageView");
List<UiElement> uiElementChildren = element.getChildrenBySelector(elementSelector);
```

For more information about getting children of `UiElement` look [Here](get-children.md).

### Get Text

This method returns as String the Text field of an `UiElement`.

Example code:

```java
String elementText = element.getText();
```

### Tap on Child Element

You can also tap on an Element that is in other Element. For example if you want to Click on some Element that is child on currently Selected Element instead of creating new Element instance you can just create a Selector for that element and use `tapOnChildElement(Selector)`.

Example code:

```java
UiElementSelector childElementSelector = new UiElementSelector();
childElementSelector.addSelectionAttribute(CssAttribute.CHECKED, true);
childElementSelector.addSelectionAttribute(CssAttribute.TEXT, "Receive notification");
element.tapOnChildElement(childElementSelector);
```

More information about Creating an Element Selector [Here](create-element-selector.md).
