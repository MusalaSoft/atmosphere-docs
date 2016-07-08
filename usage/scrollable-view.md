# Scrollable View
## Getting a Scrollable View Object

The `ScrollableView` class represents an element on the screen of the device for which we can perform scroll actions. In order to get a specific scrollable view, you need to use the `getScrollableView()` functions in the `Screen` class with a selector describing the needed scrollable view as parameter. For example:

```java
Screen deviceActiveScreen = device.getActiveScreen();
ScrollableView scrollableView = deviceActiveScreen.getScrollableView(scrollableViewSelector);
```

## Usage of Scrollable View

Note that there are no scroll functions in other classes. If you want to find an element in a scroll list or use other functionalities that require scrolling, you will need to create the `ScrollableView` object. Since it extends `UiElement`, you can use any `UiElement` functionalities provided their usage makes sense. That way, you can access specific elements in the chosen `ScrollableView` and interact with them. However, keep in mind that usage of any scroll functions does not update the visible content of the `ScrollableView` object. If you want to scroll and then interact with a specific element, you need to update the `ScrollableView` object. To do that, just get it from the screen again.
