To integrate the Unified Payments Interface (UPI) system in a Flutter app, you can use the Flutter plugin
`flutter_upi` which provides simple and easy to use interface for UPI payments in your flutter app.

Here are the steps you can follow to integrate the UPI system in your flutter app:

1. Add the `flutter_upi` dependancy to your `pubspec.yaml` file:
```yaml
dependencies:
  flutter:
    sdk:flutter
   flutter_upi: <latest_version>
```
2. Import the `flutter_upi` library in your Flutter app:
```dart
import 'package:flutter_upi/flutter_upi.dart';
```
3. Use teh `initiateTransaction` method to the `FlutterUpi` class to initiate a UPI Payment:
```dart
String response = await FlutterUpi.initiateTransaction(
  app: FlutterUpiApps.Paytm,  // or FlutterUpiApps.PhonePe or FlutterUpiApps.GooglePay
  pa: 'paytm@upi',  // or 'phonepe@upi' or 'googlepay@upi'
  pn: 'Paytm',  // or 'PhonePe' or 'Google Pay'
  tr:  '123456789',
  tn:  'Test transaction',
  am:  '1.0',
  cu:  'INR',
  url: 'https://test/com/verify'
);
```
The `initiateTransaction` method takes several parameters such as the UPI app to use, the payee address,
the transaction reference number,the transaction note, the amount, the currency, and the verification URL.

4. Check the response of the `initiateTransaction` method to see if the transaction was successful or not:
 ```dart
 if(response == Flutter UpiResponse.SUCCESS){
  // Payment was successful
 } else if (response == FlutterUpiResponse.ERROR){
  // Payment failed
 } else if(response == FlutterUpiResponse.CANCELLED){
  // Payment was cancelled by the user
 }
 ```
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
