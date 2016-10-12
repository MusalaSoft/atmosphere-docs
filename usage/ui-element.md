## UI Elements

Before executing an action on a `UiElement`, a testing device should be selected. For more information see [How to get a device](get-device.md).
Next step is to get the active screen from the selected device:

```java
Screen screen = device.getActiveScreen();
```

More information about how to get an element can be found [here](get-element.md).

After all that is set, you can execute several actions on the selected `UiElement`.

### Gestures

You can execute simple gestures on the `UiElement`: tap, double tap, long press etc. Also there are Edit Text methods that allow you to clear or input Text in a `UiElement` that is of type `EditText`. You can find more information about gestures [here](gestures.md).

### Revalidation

Interaction with Elements constantly changes the Active Screen of the Device. Revalidation of an Element is done in order to check if the Element is still intact and present on the Active screen and can be interacted with it.

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

`UiElements` usually have tree like structure. For example a `UiElement` that is of type `ListView` can contain `TextView`, `ImageView` and so on. You can get them using the `getChildren` method.

This example code will return all Children of the element that are of type `ImageView`:

```java
UiElementSelector elementSelector = new UiElementSelector();
elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.view.ImageView");
List<UiElement> uiElementChildren = element.getChildrenBySelector(elementSelector);
```

For more information about getting children of a `UiElement` see [here](get-children.md).

### Get Text

This method returns a String with the contents of the Text field of a `UiElement`.

Example code:

```java
String elementText = element.getText();
```

### Tap on Child Element

You can also tap on an Element that is in other Element. For example, if you want to tap on an Element that is a child of the currently selected Element, instead of creating a new Element instance you can just create a Selector for that element and use `tapOnChildElement(selector)`.

Example code:

```java
UiElementSelector childElementSelector = new UiElementSelector();
childElementSelector.addSelectionAttribute(CssAttribute.CHECKED, true);
childElementSelector.addSelectionAttribute(CssAttribute.TEXT, "Receive notification");
element.tapOnChildElement(childElementSelector);
```

More information about creating an Element Selector can be found [here](create-element-selector.md).
