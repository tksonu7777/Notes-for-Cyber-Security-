# 3 To understand Activity, Intent, Create sample application with login module.(Check username and password).



### **Steps to Create a Login Module:**

1. **Create a New Android Project in Android Studio**
2. **Design the Login Activity UI**
3. **Create the Login Logic**
4. **Use Intents to Navigate to a New Screen After Successful Login**

### **1. Create a New Project in Android Studio:**

1. Open Android Studio and create a new project.
2. Select **Empty Activity**.
3. Name your project `LoginApp` and choose **Java** (or Kotlin) as the language.
4. Set the **Minimum API level** (API 21 or above is recommended).

### **2. Design the Login Screen (LoginActivity)**

In the `res/layout/activity_main.xml` file, design the layout for the login screen. You’ll need two `EditText` views for the username and password, and a `Button` to submit the login form.

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp"
    android:gravity="center">

    <EditText
        android:id="@+id/username"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Username"
        android:inputType="text"
        android:textSize="16sp"/>

    <EditText
        android:id="@+id/password"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Password"
        android:inputType="textPassword"
        android:textSize="16sp"
        android:layout_marginTop="10dp"/>

    <Button
        android:id="@+id/loginButton"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Login"
        android:layout_marginTop="20dp"/>

</LinearLayout>
```

### **3. Create the Login Logic (LoginActivity.java)**

In `MainActivity.java`, handle the login logic to check if the entered username and password are correct. If the login is successful, navigate to another activity (e.g., `HomeActivity`).

```java
package com.example.loginapp;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    // Declare UI elements
    private EditText usernameEditText, passwordEditText;
    private Button loginButton;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize UI elements
        usernameEditText = findViewById(R.id.username);
        passwordEditText = findViewById(R.id.password);
        loginButton = findViewById(R.id.loginButton);

        // Set up button click listener
        loginButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Get input values from the EditTexts
                String username = usernameEditText.getText().toString();
                String password = passwordEditText.getText().toString();

                // Check the login credentials
                if (username.equals("admin") && password.equals("1234")) {
                    // Login successful, navigate to HomeActivity
                    Intent intent = new Intent(MainActivity.this, HomeActivity.class);
                    startActivity(intent);
                    finish(); // Close login activity after successful login
                } else {
                    // Show error message
                    Toast.makeText(MainActivity.this, "Invalid username or password", Toast.LENGTH_SHORT).show();
                }
            }
        });
    }
}
```

### **4. Create the Home Activity (HomeActivity.java)**

This will be the screen that the user sees after a successful login. It can be a simple `TextView` that shows a "Welcome" message.

Create a new `Activity` called `HomeActivity`:

1. Right-click on `java` -> `com.example.loginapp` -> `New` -> `Activity` -> `Empty Activity`
2. Name it `HomeActivity` and click **Finish**.

Then, in `HomeActivity.java`, add the following code to display a welcome message:

```java
package com.example.loginapp;

import android.os.Bundle;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class HomeActivity extends AppCompatActivity {

    private TextView welcomeText;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_home);

        // Initialize the TextView
        welcomeText = findViewById(R.id.welcomeText);
        
        // Display a welcome message
        welcomeText.setText("Welcome to the Home Screen!");
    }
}
```

In `res/layout/activity_home.xml`, design a simple layout for the home screen:

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="16dp">

    <TextView
        android:id="@+id/welcomeText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="20sp"/>
</LinearLayout>
```

### **5. Update AndroidManifest.xml**

Ensure that both `MainActivity` and `HomeActivity` are declared in the `AndroidManifest.xml` file:

```xml
<application
    android:allowBackup="true"
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:theme="@style/Theme.LoginApp">
    
    <activity android:name=".MainActivity">
        <intent-filter>
            <action android:name="android.intent.action.MAIN" />
            <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>
    </activity>
    
    <activity android:name=".HomeActivity"></activity>

</application>
```

### **6. Run the Application**

- When you run the application, the login screen will appear.
- Enter the username `admin` and the password `1234`.
- After a successful login, the app will navigate to the `HomeActivity`, showing a "Welcome to the Home Screen!" message.
- If the credentials are incorrect, a toast message will show saying "Invalid username or password.













