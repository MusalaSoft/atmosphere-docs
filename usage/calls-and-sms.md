
# Calls and SMS Usage
## Using calls

To receive a call you need the `receiveCall()` method of the `Device` object which requires an object of type `PhoneNumber` as a parameter. To create a `PhoneNumber` object, you need to use its constructor which requires a phone number represented by a `String`. For example:
```java
PhoneNumber phoneNumber = new PhoneNumber("0888826246");
device.receiveCall(phoneNumber);
```

There are several ways to deal with the call:
* You can accept the call using the `acceptCall()` method; It can be used with a phone number parameter (to accept a specific call) or without parameters;
* You can decline the call using the `declineCall()` method;
* You can hold the call using the the `holdCall()` method with a phone number parameter;
* You can cancel the call using the `cancelCall()` method with a phone number parameter; Note that this will leave a missed call notification.

## Using SMS messages

To receive an SMS you need the `receiveSms()` method of the `Device` object which requires an object of type `SmsMessage`. To create a `SmsMessage` object, you need to use its constructor which requires a `PhoneNumber` object representing the phone number and a `String` object representing the text written in the message. For example:
```java
PhoneNumber phoneNumber = new PhoneNumber("0888826246");
SmsMessage smsMessage = new SmsMessage(phoneNumber, "Sample text message");
device.receiveSms(smsMessage);
```

The SMS message will appear in the notification bar.
