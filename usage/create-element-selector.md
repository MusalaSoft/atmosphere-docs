# How to Create an Element Selector

A `UiElementSelector` usually contains `CssAttributes` by which we will **select a UiElement from the active screen**.

## Create UiElementSelector and add selector Attributes

1. Create a `UiElementSelector`.
1. **Dump the XML** so you can see all Elements and their `CssAttributes`. For more information you can check [How to dump XML](xml-dump.md).
1. **Add `CssAttributes`** to the `UiElementSelector` by which the Element will be selected.
  * Note that if there are two or more `UiElement` objects that can be selected by the `UiElementSelector` and we only need one, an error occurs, so you have to be very specific about the attributes values.
  * You can add more than one attribute to the Selector.

Example code for creating a `UiElementSelector`:

```java
UiElementSelector elementSelector = new UiElementSelector();
elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.widget.TextView");
elementSelector.addSelectionAttribute(CssAttribute.TEXT, "Browser");
```

The created Selector will select the browser icon on the home screen of the Device if there is one.

We can also create a `UiElementSelector` directly using the constructor with a `HashMap` with added CSS attributes as Strings to it. Example code:

```java
Map<String, String> nodeAttributeMap = new HashMap<>();
nodeAttributeMap.put("bounds", "[10,15][200,100]");
nodeAttributeMap.put("index", "5");
nodeAttributeMap.put("content-desc", "my-content");
nodeAttributeMap.put("text", "my-text");t
nodeAttributeMap.put("long-clickable", "true");
nodeAttributeMap.put("password", "false");
uiElementSelector = new UiElementSelector(nodeAttributeMap);
```

## Attributes with which you can Select an Element

You can select an Element with the attributes in **NoteDetails** in the Dump XML. Every Element has these attributes and can be selected by one or more of them. Also they contain fields like `Enabled`, `Checked`, `Focused` and others. With them we can check if the interactions are successful or not. For more information you can check [How to dump XML](xml-dump.md).

![XML Dump](images/DumpXmlAttributes.jpg)
