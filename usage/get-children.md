## How to Get the Children of an Element

### Get Children of an Element

It is possible to get the Elements that are inside a specific Element. The children can be selected by CssQuery, xPath or Element Selector. More information about getting an Element can be found [here](get-element.md).

As an example we will use an Element that contains the text "settings" and is inside an Element of type `FrameLayout`.

### Get children by Xpath Query

   1. Get the Element from the Active Screen.
   2. Create an xPathQuery.
     * How to create an xPathQuery is explained [here](create-xpath-and-cssquery.md).
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

   1. Get the Element from the Active Screen.
   2. Create a CSS Query.
     * How to create a `CssQuery` is explained [here](create-xpath-and-cssquery.md).
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

   1. Get the Element from the Active Screen.
   2. Create an Element Selector.
     * How to create an Element Selector is explained [here](create-element-selector.md).
   3. Use the method `element.getChildrenBySelector(ElementSelector)` to get the children.

Example Code:

```java
Screen screen = device.getActiveScreen();
UiElementSelector elementSelector = new UiElementSelector();
elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.widget.FrameLayout");
UiElementSelector elementChildrenSelector = new UiElementSelector();
elementChildrenSelector.addSelectionAttribute(CssAttribute.CHECKED, true);
elementChildrenSelector.addSelectionAttribute(CssAttribute.TEXT, "Receive notification");
List<UiElement> children = element.getChildrenBySelector(elementChildrenSelector);
```

### Attributes with which you can select an Element

You can select an Element with the attributes in **NoteDetails** in the Dump XML. Every Element has these attributes and can be selected by one or more of them. Also they contain fields like `Enabled`, `Checked`, `Focused` and others. With them we can check if the interactions are successful or not. For more information you can check [How to dump XML](xml-dump.md).

![XML Dump](images/DumpXmlAttributes.jpg)
