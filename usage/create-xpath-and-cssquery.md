# Creating CSS and XPath query

Selecting a `UiElement` by CSS or XPath is much faster than selecting it by a Selector. To create a CSS or XPath query you will need **a String with a specific syntax**. A single String can contain more than one attribute, so you will only need one XPath or CSS query to select a `UiElement`.

#### Example for CSS Query:

```java
final String CSS_QUERY_EXAMPLE = "[bounds=[10,25][34,49]][class=android.widget.ImageView][package=com.example.coolstory]";
```
#### Examples for XPath Query:

```java
final String XPATH_QUERY_EXAMPLE = "//node[@index=1 and @text='' and @className='android.widget.FrameLayout' and @package='com.example.coolstory']";
```

```java
final String XPATH_QUERY_CONTAINS_EXAMPLE = "//node[contains(@text,'CHARTS')][@resourceId='com.android.vending:id/li_title']";
```

*Each attribute can be provided in separate square brackets or in the same square brackets using the `and/or` keywords.*

## CSS and XPath element selection attributes

You can select an element by using the attributes provided in the **NoteDetail** list in the Dump XML. Notice that these attributes are in CSS format and the corresponding XPath ones should use `cammelCase` instead of dashes to differentiate words. Use the table below as an example:

| CSS attribute    | XPath attribute |
|------------------|-----------------|
| `class`          | `className`     |
| `content-desc`   | `contentDesc`   |
| `long-clickable` | `longClickable` |
| `resource-id`    | `resourceId`    |


 For more information about dumping XML you can check [How to dump XML](xml-dump.md).

![XML Dump](images/DumpXmlAttributes.jpg)
