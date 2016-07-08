## How to use `DatePicker` and `TimePicker`

!DatePicker and !TimePicker give you methods for interacting with Number pickers in Android. Both classes have similar methods the main difference is the type of the picker we want to interact with. With Date and Time pickers we can set or get the picker values.
Information for How to get Device [Here](get-device.md).  
Information for How to get Screen [Here](active-screen.md).

### Get DatePicker

 1. Create Screen instance.
 2. use `screen.getDatePicker()` method for creating a `DatePicker` instance.
    * Note that in order for `getDatePicker()` method to work there should be **present DatePicker** on the active screen.

Example code:

```java
DatePicker datePicker = screen.getDatePicker();
```

### Get `TimePicker`

 1. Create Screen instance.
 2. use `screen.getTimePicker()` method for creating a `TimePicker` instance.
    *  Note that in order for `getTimePicker()` method to work there should be *present `TimePicker`* on the active screen.

Example code:

```java
 TimePicker timePicker = screen.getTimePicker();
```

### Get `DatePicker` and `TimePicker` Value

 1. Create picker instance the way explained above.
 2. There are two main methods for getting Date and Time picker.
    a. `pikcer.getStringValue()` returns string containing the value of the picker.
    b. `picker.getValue()` returns Calendar instance containing the fields of the picker as integer values.
       * TimePicker's `getValue()` return Calendar which only Calendar.MINUTES and Calendar.HOUR fields are filled. If the `TimePicker` type is Meridian(am/pm) then the `Calendar.HOUR` is automatically recalculated in 24 format.
       * DatePikcer's `getValue()` return Calendar which only `Calendar.YEAR`, `Calendar.MONTH` and `Calendar.DAY_OF_MONTH` fields are filled. Additionally there are and get single field methods `getYear()`, `getMonth()` and `getDay()` which return int instances.

Example Code `TimePicker`:

```java
TimePicker timePicker = screen.getTimePicker();

// Get String Value
String timeText = timePicker.getStringValue();

// Get Calendar instance
Calendar calendarTimeValue = timePicker.getValue();
```

Example Code !DatePicker:

```java
DatePicker datePicker = screen.getDatePicker();

// Get String Value
String dateText = datePicker.getStringValue();

// Get Calendar instance
Calendar calendarDateValue = datePicker.getValue();

// Get date fields
int year = datePicker.getYear();
int month = datePicker.getMonth();
int day = datePicker.getDay();
```

### Set `DatePicker` and `TimePicker` Value

 1. Create picker instance explained above.
 2. Use `picker.setValue(calendar);` for setting the fields.
    a. For `DatePicker` we need Calendar instance with year, month and day fields filled.
    b. For `TimePicker` we need Calendar instance with hour and minutes fields filled.

Example code:

```java
Calendar calendar = Calendar.getInstance();

// Date: January 1 2015 3:45 pm
calendar.set(2015, 0, 1, 15, 45);

// Set date
DatePicker datePicker = screen.getDatePicker();
datePicker.setValue(calendar);

// Set TIme
TimePicker timePicker = screen.getTimePicker();
timePikcer.setValue(calendar);
```

### How to create Calendar for `DatePicker` and `TimePicker` `setValue` method

 1. Create Calendar instance.  `Calendar calendar = Calendar.getInstance();`
 2. Now that calendar is created we have to set the fields.
    a. For `DatePicker` use `calendar.set(int year, int month, int date)`. For example `calendar.set(2015, 3, 1)` is the date ''April-1-2015''. Note that date is day of month and month numbers begin from 0 (January is 0).
    b. For `TimePicker` us `calendar.set(int field, int value)` or `calendar.set(int year, int month, int date, int hour, int minutes)`.

Example Code:

```java
Calendar calendar = Calendar.getInstance();

// Set Date and Time: January 1 2015 5:50 pm
calendar.set(2015, 0, 1, 17, 50);

// Set Time: 11:10 am
calendar.set(Calendar.Hour, 11);
calendar.set(Calendar.minutes, 10);

// Set Date: April 1 2010
calendar.set(2010, 3, 1);
```
