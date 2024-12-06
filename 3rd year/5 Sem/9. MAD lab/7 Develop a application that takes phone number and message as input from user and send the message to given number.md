# 7 Develop a application that takes phone number and message as input from user and send the message to given number



 
### Prerequisites:
1. **Android Studio** installed on your computer.
2. **Basic knowledge of Android development (Java or Kotlin).**
3. An Android device or emulator for testing.

### Steps to Develop the Application:

#### 1. **Create a New Android Project**

Create a new Android project in Android Studio with an Empty Activity template. Name it something like `SendSMSApp`.

#### 2. **Add Permissions**

Before you can send SMS messages, you need to request the necessary permissions. Open your `AndroidManifest.xml` file and add the following permissions for sending SMS:

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.sendsmsapp">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/Theme.SendSMSApp">
        
        <!-- Permission to send SMS -->
        <uses-permission android:name="android.permission.SEND_SMS"/>
        <!-- Permission to read phone state (optional, for checking SIM status) -->
        <uses-permission android:name="android.permission.READ_PHONE_STATE"/>
        <!-- Permission to read contacts (optional, if needed) -->
        <uses-permission android:name="android.permission.READ_CONTACTS"/>

        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

In this case, `SEND_SMS` is the critical permission that allows your app to send SMS messages.

#### 3. **Design the Layout in `activity_main.xml`**

In your `res/layout/activity_main.xml`, create a simple UI with fields to input the phone number and message, and a button to send the SMS:

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp">

    <EditText
        android:id="@+id/etPhoneNumber"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Phone Number"
        android:inputType="phone" />

    <EditText
        android:id="@+id/etMessage"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Message"
        android:inputType="textMultiLine" />

    <Button
        android:id="@+id/btnSendSMS"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Send SMS" />

</LinearLayout>
```

#### 4. **Handle SMS Sending Logic in `MainActivity.java`**

In `MainActivity.java`, you'll write the logic to send an SMS when the button is clicked. You'll also need to check for the necessary permission at runtime, especially for Android 6.0 (API level 23) and above, since permissions need to be requested dynamically.

Here's how you can handle this:

```java
import android.Manifest;
import android.content.pm.PackageManager;
import android.os.Bundle;
import android.telephony.SmsManager;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;
import androidx.core.app.ActivityCompat;
import androidx.core.content.ContextCompat;

public class MainActivity extends AppCompatActivity {

    private static final int SMS_PERMISSION_CODE = 1;

    private EditText etPhoneNumber, etMessage;
    private Button btnSendSMS;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etPhoneNumber = findViewById(R.id.etPhoneNumber);
        etMessage = findViewById(R.id.etMessage);
        btnSendSMS = findViewById(R.id.btnSendSMS);

        // Check for SMS permission
        if (ContextCompat.checkSelfPermission(this, Manifest.permission.SEND_SMS) != PackageManager.PERMISSION_GRANTED) {
            ActivityCompat.requestPermissions(this, new String[]{Manifest.permission.SEND_SMS}, SMS_PERMISSION_CODE);
        }

        btnSendSMS.setOnClickListener(v -> {
            String phoneNumber = etPhoneNumber.getText().toString();
            String message = etMessage.getText().toString();

            // Send SMS if phone number and message are provided
            if (!phoneNumber.isEmpty() && !message.isEmpty()) {
                sendSMS(phoneNumber, message);
            } else {
                Toast.makeText(MainActivity.this, "Please enter both phone number and message", Toast.LENGTH_SHORT).show();
            }
        });
    }

    // Method to send SMS
    private void sendSMS(String phoneNumber, String message) {
        try {
            SmsManager smsManager = SmsManager.getDefault();
            smsManager.sendTextMessage(phoneNumber, null, message, null, null);
            Toast.makeText(MainActivity.this, "SMS Sent Successfully", Toast.LENGTH_SHORT).show();
        } catch (Exception e) {
            e.printStackTrace();
            Toast.makeText(MainActivity.this, "Failed to send SMS", Toast.LENGTH_SHORT).show();
        }
    }

    // Handle permission request result
    @Override
    public void onRequestPermissionsResult(int requestCode, String[] permissions, int[] grantResults) {
        super.onRequestPermissionsResult(requestCode, permissions, grantResults);
        if (requestCode == SMS_PERMISSION_CODE) {
            if (grantResults.length > 0 && grantResults[0] == PackageManager.PERMISSION_GRANTED) {
                Toast.makeText(this, "SMS Permission Granted", Toast.LENGTH_SHORT).show();
            } else {
                Toast.makeText(this, "SMS Permission Denied", Toast.LENGTH_SHORT).show();
            }
        }
    }
}
```

 
#### 5. **Run the Application**

Run the app on an Android device or emulator. Ensure that the device has SMS functionality (for example, use a real device or an emulator with SMS capabilities). The user can input the phone number and message, and when they click the "Send SMS" button, the app will send the SMS message to the entered number.

 
