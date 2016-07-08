
# Calls and SMS Usage
## Using calls

To receive a call you need the functionality **receiveCall()** in **Device** which requires an object of type **PhoneNumber** as parameter. To create a **PhoneNumber** object, you need to use its constructor which requires a phone number represented by a **String**. For example:
```java
PhoneNumber phoneNumber = new PhoneNumber("0888826246");
device.receiveCall(phoneNumber);
```

There are several ways to deal with the call:
* You can accept the call using the **acceptCall()** function; It can be used with a parameter phone number (to accept a specific call) or without;
* You can decline the call using the **declineCall()** function;
* You can hold the call using the the **holdCall()** function with parameter a phone number;
* You can cancel the call using the **cancelCall()** function with parameter a phone number; Note that this will leave a missed call notification.

## Using SMS messages

To receive an SMS you need the functionality **receiveSms()** in **Device** which requires an object of type **SmsMessage**. To create a **SmsMessage** object, you need to use its constructor which requires a **PhoneNumber** object representing the phone number and a **String** object representing the text written in the message. For example:
```java
PhoneNumber phoneNumber = new PhoneNumber("0888826246");
SmsMessage smsMessage = new SmsMessage(phoneNumber, "Sample text message");
device.receiveSms(smsMessage);
```

The SMS message will appear in the notification bar.
