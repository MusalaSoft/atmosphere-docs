# Scrollable View

## Getting a Scrollable View Object
The `ScrollableView` class represents an element on the screen of the device for which we can perform scroll actions. In order to get a specific scrollable view, you need to use the `getScrollableView()` methods in the `Screen` class with a selector describing the needed scrollable view as parameter. For example:

```java
Screen screen = device.getActiveScreen();
ScrollableView scrollableView = screen.getScrollableView(scrollableViewSelector);
```

**Note:** There is a known issue with `ListView` nodes. Selecting a `ListView` node with the `scrollableViewSelector` will cause the ScrollableView to scroll the view but be unable to find the child element to tap on. To avoid this issue make the `scrollableViewSelector` select the first parent of the `ListView` which has a resource ID.

![ListViewIssue](images/ListViewIssue.jpg)

## Usage of Scrollable View
Note that there are no scroll functions in other classes. If you want to find an element in a scroll list or use other functionalities that require scrolling, you will need to create the `ScrollableView` object. Since it extends `UiElement`, you can use any `UiElement` functionalities provided their usage makes sense. That way, you can access specific elements in the chosen `ScrollableView` and interact with them. However, keep in mind that usage of any scroll functions does not update the visible content of the `ScrollableView` object. If you want to scroll and then interact with a specific element, you need to update the `ScrollableView` object. To do that, just get it from the screen again.
