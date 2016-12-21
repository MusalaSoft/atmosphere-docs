# WebView Usage

## Working with a Single Web View
With Atmosphere Framework you can work easy with web views. Firstly you need to create a [Screen](active-screen.md) object and to know the package name of the web view. An `WebView` object can be created with few lines of code:
```java
Device testDevice = Builder.getInstance().getDevice(testDeviceSelector); // see Active Screen Usage
Screen screen = testDevice.getActiveScreen();
testDevice.startApplication("com.html5test.webview");
WebView webview = screen.getWebView("com.html5test.webview");
```
### UI web element and selectors
The major component of the `WebView` is `UiWebElement`. By selecting the element you can interact with the application or select another element from the DOM tree:
```java
UiWebElement button = webView.findElement(WebElementSelectionCriterion.ID, "button_id");
button.tap(); // tap on the button
String text = button.getText() // returns the button's text as a string
List<UiWebElement> childElements = button.findElements(WebElementSelectionCriterion.LINK, "http://.../home.html");
List<UiWebElement> items = webView.findElements(WebElementSelectionCriterion.CLASS, "item");
```

Once the WebView is created there is various ways to select an element from the UI with `findElement()` method and `WebElementSelectionCriterion`.
```java
UiWebElement buttonElement = view.findElement(WebElementSelectionCriterion.XPATH, "/html/body/div/ul[2]/li[1]");
UiWebElement linkElement = view.findElement(WebElementSelectionCriterion.LINK, "/index.html");
```

## Working with Multiple Web Views
Once the `WebView` object is created it is simple to switch between all the web views available on the screen. There is two basic posibilities to do that:

* switch to another WebView by `WebViewSelectionCriterion` and value using `URL`, `TITLE` or `CHILD_ELEMENT`(with xPath query) criterion:
```java
webView.switchToAnotherWebView(WebViewSelectionCriterion.TITLE, "Multiple Web Views");
webView.switchToAnotherWebView(WebViewSelectionCriterion.URL, "http://.../home.html");
webView.switchToAnotherWebView(WebViewSelectionCriterion.CHILD_ELEMENT, "//*[@id=\"menu\"]/div[1]/a");
```

* swith to another WebView by it's child element selector and `WebElementSelectionCriterion`:
```java
webView.switchToAnotherWebViewByChildWebElement(WebElementSelectionCriterion.XPATH, "//*[@id=\"menu\"]/div[1]/a");
webView.switchToAnotherWebViewByChildWebElement(WebElementSelectionCriterion.LINK, "http://.../home.html");
// selects a web view by child element selector
```
Here you can use all the selection options from the `WebElementSelectionCriterion` that are available for a single `WebView`.
