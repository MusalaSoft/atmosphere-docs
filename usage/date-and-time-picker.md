## How to use `DatePicker` and `TimePicker`

`DatePicker` and `TimePicker` give you methods for interacting with Number pickers in Android. Both classes have similar methods - the main difference is the type of the picker we want to interact with. With Date and Time pickers we can set or get the picker values.  
*Information about how to get a Device instance can be found [here](get-device.md).*  
*Information about how to get a Screen instance can be found [here](active-screen.md).*

### Get a `DatePicker`

 1. Create a `Screen` instance.
 2. Use the `screen.getDatePicker()` method to create a `DatePicker` instance.
    * Note that there should be a present `DatePicker` on the active screen for the `getDatePicker()` method to work.

Example code:

```java
DatePicker datePicker = screen.getDatePicker();
```

### Get a `TimePicker`

 1. Create a `Screen` instance.
 2. Use the `screen.getTimePicker()` method to create a `TimePicker` instance.
    *  Note that there should be a present `TimePicker` on the active screen for the `getTimePicker()` method to work.

Example code:

```java
 TimePicker timePicker = screen.getTimePicker();
```

### Get `DatePicker` or `TimePicker` values

 1. Create a picker instance.
 2. There are two methods for getting Date and Time picker values.
   * `picker.getStringValue()` returns a `String` containing the value of the picker.
   * `picker.getValue()` returns a `Calendar` instance containing the fields of the picker as integer values.

Example code for a `TimePicker`:

```java
TimePicker timePicker = screen.getTimePicker();

// Get String Value
String timeText = timePicker.getStringValue();

// Get Calendar instance
Calendar calendarTimeValue = timePicker.getValue();
```

Example code for a `DatePicker`:

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

### Set `DatePicker` or `TimePicker` values

 1. Create a picker instance.
 2. Use the `picker.setValue(calendar)` method to set the fields.
   * For the `DatePicker`, the Calendar instance's `year`, `month` and `day` fields must be filled.
   * For the `TimePicker`, the Calendar instance's `hour` and `minutes` fields must be filled.

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

### How to create a `Calendar` for the `setValue` method

 1. Create a `Calendar` instance.  `Calendar calendar = Calendar.getInstance();`
 2. Set the required fields.
   * For the `DatePicker` use `calendar.set(int year, int month, int date)`. For example `calendar.set(2015, 3, 1)` is the date ''April-1-2015''. Note that the day and month values start from 0 (January is 0).
   * For the `TimePicker` use `calendar.set(int field, int value)` or `calendar.set(int year, int month, int date, int hour, int minutes)`.

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
