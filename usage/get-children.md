## How to Get the Children of an Element ##

### Get Children of Element ###

There are option for getting Elements that are inside an Element. For example getting an Element that contains text "settings" from Element that contains `FrameLayout`. The children can also be selected by CssQuery, xPath or Element Selector. More information about getting an Element [Here](get-element.md).

### Get children by Xpath Query ###

   1. Get Element from the Active Screen.
   2. Create xPathQuery.
     * How to create xPathQuery explained [Here](create-xpath-and-cssquery.md)
   3. Use the method `element.getChildren(xPathQuery)` to get the children.

Example Code:

```java
Screen screen = device.getActiveScreen();
UiElementSelector elementSelector = new UiElementSelector();
elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.widget.FrameLayout");
UiElement element = screen.getCollectionBySelector(elementSelector);
final String XPATH_QUERY = "//node[@class='android.widget.TextView' and @text='settings']";
List<UiElement> children = element.getChildren(XPATH_QUERY);
```

### Get children by `CssQuery` ###

   1. Get Element from the Active Screen.
   2. Create CSS Query.
     * How to create `CssQuery` explained [Here](create-xpath-and-cssquery.md)
   3. Use the method `element.getChildrenByCssQuery(CssQuery)` to get the children.

Example Code:

```java
Screen screen = device.getActiveScreen();
UiElementSelector elementSelector = new UiElementSelector();
elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.widget.FrameLayout");
UiElement element = screen.getCollectionBySelector(elementSelector);
final String CSS_QUERY = "[class=android.widget.TextView][text=settings]";
List<UiElement> children = element.getChildren(CSS_QUERY);
```

### Get children by Element Selector

   1. Get Element from the Active Screen.
   2. Create Element Selector.
     * How to Create Element Selector explained [Here]().
   3. Use the method `element.getChildrenBySelector(ElementSelector)` to get the children.

Example Code

```java
Screen screen = device.getActiveScreen();
UiElementSelector elementSelector = new UiElementSelector();
elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.widget.FrameLayout");
UiElementSelector elementChildrenSelector = new UiElementSelector();
elementChildrenSelector.addSelectionAttribute(CssAttribute.CHECKED, true);
elementChildrenSelector.addSelectionAttribute(CssAttribute.TEXT, "Receive notification");
List<UiElement> children = element.getChildrenBySelector(elementChildrenSelector);
```

### Attributes with which you can Select an Element

You can select an Element with the attributes in `NoteDetails` in the Dump Xml. Every Element has these attributes and can be selected by one or more of them. Also they contained fields like `Enabled`, `Checked`, `Focused` and others. With them we can check if the interactions are successful or not.  For more information you can check [How to dump Xml](xml-dump.md).
