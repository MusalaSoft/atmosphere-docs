# How to Create Element Selector

An **ElementSelector** usually contains a **Css Attributes** by which we will **Select an Element from the Active Screen**.

## Create UiElementSelector and add selecting Attributes

1. Create `UiElementSelector`.
2. **Dump the Xml** so you can see all **Elements** and their **CssAttributes** with which an **Element** will be selected.  For more information you can check [How to dump Xml](xml-dump.md).
2. **Add CssAttributes** to the **ElementSelector** by which the **Element** will be selected.
  * Note that if there are two or more **Element** that can be selected by the **ElementSelector** and we want only one **Element** an error occurs, so you have to be very specific about the attributes values.
  * You can add more than one attribute to the Selector.
  * Usually the Element that are on the screen have the same package name but there are many differences like Text, Type, Index etc.

Example code for creating a Selector the created Selector will Select the browser Icon on the home screen of the Device if there is such:

```java
UiElementSelector elementSelector = new UiElementSelector();
elementSelector.addSelectionAttribute(CssAttribute.CLASS_NAME, "android.widget.TextView");
elementSelector.addSelectionAttribute(CssAttribute.TEXT, "Browser");
```

We can also create `ElementSelector` directly with constructor using **HashMap**. They are strings that contains attributes in text like structure. It is recommended to use `UiElementSelector();`.

Example code :

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

You can select an Element with the attributes in **NoteDetails** in the Dump Xml. Every Element has these attributes and can be selected by one or more of them. Also they contained fields like **Enabled**, **Checked**, **Focused** and others. With them we can check if the interactions are successful or not.  For more information you can check [How to dump Xml](xml-dump.md).
