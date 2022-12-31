To integrate PhonePe in a Flutter app without using `flutter_upi` package, you can use the 
PhonePe SDK for flutter which provides a simple and easy to use interface for PhonePe Payments in your 
Flutter app.

Here are the steps you can follow to integrate PhonePe in your Flutter app:

1. Add the `phonepe_sdk` dependency to your `pubspec.yaml` file:
```yaml
dependencies:
  flutter:
    sdk: flutter
   phonepe_sdk: <latest_version>
```
2. Import the `phonepe_sdk` library in your Flutter app:

```dart
import 'package:phonepe_sdk/phonepe_sdk.dart';
```
3. Initialize the PhonePe SDK with your merchant ID and merchant key:
PhonePeSdk.init(merchantId:'<your_merchant_id>', merchantKey:'<your_merchant_key>');
4. Use the `startTransaction` method of the `PhonePeSdk` class to initiate a PhonePe payment:
```dart
final PhonePeResponse response = await PhonePeSdk.startTransaction(
                                      transactionId:'<your_transaction_id>',
                                      amount:'1.0',
                                      currency:'INR',
                                      app:PhonePeApps.PhonePe,
                                      deepLink: '<your_deep_link>',
                                      customerPhoneNumber:'<your_customer_phone_number>',
                                      customerEmail:'<your_customer_email>',
                                      customerFirstName:'<your_customer_first_name>',
                                      customerLastName:'<your_customer_last_name>',
                                      paymentType:PaymentType.Payment,
                                      paymentModes: PaymentModes.All,
                                      isTransactionFlow: false,
                                      isBackgroundTransaction: false,
                                    );
```

The `startTransaction` method takes several parameters such as the transaction ID, the amount,
the currency, the customers phone number, email address, first name and last name, the payment type,
the payment modes, and flags for the transaction flow and background transactions

5. Check the response of the  `startTransaction` method to see if the transaction was successful or not:
```dart
if(response.status == PhonePeResponseStatus.Success){
  // Payment was successful
} else if(response.status == PhonePeResponseStatus.Error){
  // Payment failed
} else if (response.status == PhonePeResponseStatus.Cancelled) {
  // Payment was cancelled by the user
}
