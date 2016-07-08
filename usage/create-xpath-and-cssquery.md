# Creating Css amd Xpath query

Selecting an **Element** by **Css and Xpath** is much faster than by Selector. For them you should just create an String with the required **syntax**. The given string can contain more that one attribute so you just need one Xpath or Css query to select wanted **Element**.

Example for Css Query:

```java
final String CSS_QUERY_EXAMPLE = "[bounds=[10,25][34,49]][class=android.widget.ImageView][package=com.example.coolstory]";
```
Example for Xpath Query:

```java
final String XPATH_QUERY_EXAMPLE = "//node[@index=1 and @text='' and @class='android.widget.FrameLayout' and @package='com.example.coolstory']";
```

## Attributes with which you can Select an Element

You can select an Element with the attributes in **NoteDetails** in the Dump Xml. Every Element has these attributes and can be selected by one or more of them. Also they contained fields like **Enabled**, **Checked**, **Focused** and others. With them we can check if the interactions are successful or not.  For more information you can check [How to dump Xml](xml-dump.md).
