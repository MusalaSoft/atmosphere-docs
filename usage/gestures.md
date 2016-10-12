## Gestures ##

Before executing a gesture on a `UiElement`, a testing device should be selected. For more information see [How to get a device](get-device.md). The next step is to get the active screen from the selected device:
```java
   Screen screen = device.getActiveScreen();
```
Now a `UiElement` can be selected. In the next example the clock on the desktop screen will be selected.
```java
UiElementSelector elementSelector = new UiElementSelector();
elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.view.View");
elementSelector.addSelectionAttribute(CssAttribute.PACKAGE_NAME, "com.android.deskclock");
UiElement uiElement = screen.getElement(elementSelector);
```
For more information about getting elements see [How to get an element](get-element.md).

Different gestures can be executed on the selected `UiElement`:

 * **Long press**
```java
uiElement.longPress();
```
 It is also possible to specify the time (in milliseconds) for which the element will be held, or a point of the element to long press.
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
uiElement.doubleTap(new Point(12, 15));
```

* **Swipe**

 A `UiElement` can be swiped in the specified direction:
```java
   uiElement.swipe(SwipeDirection.RIGHT);
```

* **Pinch**
```java
uiElement.pinchIn();
uiElement.pinchOut();
```
 >***Note:*** *Emulator devices may not detect pinch gestures on UI elements with size smaller than 100x100dp.*

* **Clear, select, cut, copy, paste and input text**  
 The text of the UI element can be manipulated.

 For example, the text of the selected UI element could be cleared:
```java
   uiElement.clearText();
```
 and then a new text could be set:
```java
    uiElement.inputText("Text to input");
```
 Additionally, the timeout (in milliseconds) between the input of each letter could be set, making the text input more human like:
```java
   uiElement.inputText("Text to input", 100);
```
Other possible text operation are cut, copy and paste. The steps usually are selecting the text and then copying/cutting it and pasting it in the desired TextField.
```java
 uiElement.selectAllText();
 uiElement.copyText(); //uiElement.cutText();

 //Selecting second TextFiels on Which will copied to the Text
 //Note: The new selector should select unique element otherwisi it will throw exception.
 elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.view.TextView");
 UiElement uiElementNewTextView = screen.getUiElement(elementSelector);

 uiElemntNewTextView.pasteText();
```

>***Note:*** *You must assure the field is empty before inputting a new text and the UI element supports that kind of operation.*

* **Focus**
 Focuses the selected UI element.
```java
   uiElement.focus();
```
