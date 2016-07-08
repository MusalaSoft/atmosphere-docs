## Gestures ##

Before executing a gesture on `UiElement`, testing device should be selected. For more information see
[How to get device](get-device.md).
Next step is to get the active screen from the selected device
```java
   Screen screen = device.getActiveScreen();
```
Now an `UiElement` can be picked. For the next example the clock on the desktop screen will be selected.
```java
UiElementSelector elementSelector = new UiElementSelector();
elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.view.View");
elementSelector.addSelectionAttribute(CssAttribute.PACKAGE_NAME, "com.android.deskclock");
UiElement uiElement = screen.getElement(elementSelector);
```
For more information about getting elements see [How to get element](get-element.md)

After that different gestures can be executed on the select `UiElement`.



 * **Long press**
```java
uiElement.longPress();
```
 It is also possible to give a certain timeout, which the element will be held, or to specify a point from the element to long press.
```java
uiElement.longPress(1000);
uiElement.longPress(new Point(66, 94), 1000);
```

* **Tap**
```java
uiElement.tap();
uiElement.tap(new Point(66, 94));
```

* **Double tap**
```java
uiElement.doubleTap();
```

 When using double tap, it is possible to specify a point in the `UiElement`.
```java
   uiElement.doubleTap(new Point(12, 15));
```

* **Swipe**

 `UiElement` can also be swapped, specifying the desired direction.
```java
   uiElement.swipe(SwipeDirection.RIGHT);
```

* **Pinch**
```java
uiElement.pinchIn();
uiElement.pinchOut();
```
 >***Note:*** *Emulator devices may not detect pinch gestures on UI elements with size smaller than 100x100dp*.

* **Clear, select, cut, copy, paste and input text**
 Text in the UI element can be manipulated. For example, let the element selected be a `TextView`.
 Only the attributes of the selector will be changed.
```java
 elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.view.TextView");
```

 The text in the selected UI element can be cleared
```java
   uiElement.clearText();
```
 and after that a new text can be set.
```java
    uiElement.inputText("Text to input");
```
 The user can also specify the timeout in milliseconds between the input of each letter. Using it makes the text input more human like
```java
   uiElement.inputText("Text to input", 100);
```
Other possible text operation is cut/copy paste. The steps usually are selecting the text then copy/cut and paste it to the wanted TextField.
```java
 uiElement.selectAllText();
 uiElement.copyText(); //uiElement.cutText();

 //Selecting secont TextFiels on Which will copied to the Text
 //Note: The new selector should select unique element otherwisi it will throw exception.
 elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.view.TextView");
 UiElement uiElementNewTextView = screen.getUiElement(elementSelector);

 uiElemntNewTextView.pasteText();
```

>***Note:*** *The user must aware himself that the field is empty before input new text  and the UI       element supports that kind of operations.*

* **Focus**
 Focuses the selected UI element.
```java
   uiElement.focus();
```
