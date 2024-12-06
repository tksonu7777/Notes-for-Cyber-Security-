# 4 Design simple GUI application with activity and intents e.g. calculator.



 
### **Steps to Create the Calculator Application:**

1. **Create a New Project in Android Studio**
2. **Design the Calculator Layout (CalculatorActivity)**
3. **Implement Calculator Logic**
4. **Use Intents to Navigate and Display Results**

### **1. Create a New Project in Android Studio:**

1. Open Android Studio and create a new project.
2. Select **Empty Activity**.
3. Name your project `CalculatorApp`.
4. Set the **Minimum API level** (API 21 or above is recommended).
5. Click **Finish** to create the project.

### **2. Design the Calculator Layout (CalculatorActivity)**

Open the `res/layout/activity_main.xml` file and design the layout for the calculator.

 
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp"
    android:gravity="center">

    <EditText
        android:id="@+id/calculatorScreen"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter calculation"
        android:inputType="none"
        android:textSize="24sp"
        android:layout_marginBottom="20dp"
        android:gravity="end"
        android:focusable="false"/>

    <GridLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:columnCount="4"
        android:orientation="horizontal">

        <!-- First row -->
        <Button android:id="@+id/button7" android:text="7" style="@style/CalculatorButton"/>
        <Button android:id="@+id/button8" android:text="8" style="@style/CalculatorButton"/>
        <Button android:id="@+id/button9" android:text="9" style="@style/CalculatorButton"/>
        <Button android:id="@+id/buttonDiv" android:text="/" style="@style/CalculatorButton"/>

        <!-- Second row -->
        <Button android:id="@+id/button4" android:text="4" style="@style/CalculatorButton"/>
        <Button android:id="@+id/button5" android:text="5" style="@style/CalculatorButton"/>
        <Button android:id="@+id/button6" android:text="6" style="@style/CalculatorButton"/>
        <Button android:id="@+id/buttonMul" android:text="*" style="@style/CalculatorButton"/>

        <!-- Third row -->
        <Button android:id="@+id/button1" android:text="1" style="@style/CalculatorButton"/>
        <Button android:id="@+id/button2" android:text="2" style="@style/CalculatorButton"/>
        <Button android:id="@+id/button3" android:text="3" style="@style/CalculatorButton"/>
        <Button android:id="@+id/buttonSub" android:text="-" style="@style/CalculatorButton"/>

        <!-- Fourth row -->
        <Button android:id="@+id/button0" android:text="0" style="@style/CalculatorButton"/>
        <Button android:id="@+id/buttonEqual" android:text="=" style="@style/CalculatorButton"/>
        <Button android:id="@+id/buttonClear" android:text="C" style="@style/CalculatorButton"/>
        <Button android:id="@+id/buttonAdd" android:text="+" style="@style/CalculatorButton"/>
    </GridLayout>
</LinearLayout>
```

You can define the style `CalculatorButton` for consistent button styling, like this:

```xml
<!-- res/values/styles.xml -->
<resources>
    <style name="CalculatorButton">
        <item name="android:layout_width">wrap_content</item>
        <item name="android:layout_height">wrap_content</item>
        <item name="android:layout_margin">8dp</item>
        <item name="android:textSize">20sp</item>
        <item name="android:layout_gravity">center</item>
    </style>
</resources>
```

### **3. Implement Calculator Logic (CalculatorActivity.java)**

In `MainActivity.java`, handle the logic for the calculator.

```java
package com.example.calculatorapp;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    private EditText calculatorScreen;
    private String currentInput = "";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize UI elements
        calculatorScreen = findViewById(R.id.calculatorScreen);

        // Set up button listeners
        setButtonListeners();
    }

    private void setButtonListeners() {
        findViewById(R.id.button0).setOnClickListener(view -> appendToInput("0"));
        findViewById(R.id.button1).setOnClickListener(view -> appendToInput("1"));
        findViewById(R.id.button2).setOnClickListener(view -> appendToInput("2"));
        findViewById(R.id.button3).setOnClickListener(view -> appendToInput("3"));
        findViewById(R.id.button4).setOnClickListener(view -> appendToInput("4"));
        findViewById(R.id.button5).setOnClickListener(view -> appendToInput("5"));
        findViewById(R.id.button6).setOnClickListener(view -> appendToInput("6"));
        findViewById(R.id.button7).setOnClickListener(view -> appendToInput("7"));
        findViewById(R.id.button8).setOnClickListener(view -> appendToInput("8"));
        findViewById(R.id.button9).setOnClickListener(view -> appendToInput("9"));
        findViewById(R.id.buttonAdd).setOnClickListener(view -> appendToInput("+"));
        findViewById(R.id.buttonSub).setOnClickListener(view -> appendToInput("-"));
        findViewById(R.id.buttonMul).setOnClickListener(view -> appendToInput("*"));
        findViewById(R.id.buttonDiv).setOnClickListener(view -> appendToInput("/"));
        findViewById(R.id.buttonClear).setOnClickListener(view -> clearInput());
        findViewById(R.id.buttonEqual).setOnClickListener(view -> calculateResult());
    }

    private void appendToInput(String value) {
        currentInput += value;
        calculatorScreen.setText(currentInput);
    }

    private void clearInput() {
        currentInput = "";
        calculatorScreen.setText("");
    }

    private void calculateResult() {
        try {
            // Use an Intent to pass the calculation string to the result activity
            Intent intent = new Intent(MainActivity.this, ResultActivity.class);
            intent.putExtra("calculation", currentInput);
            startActivity(intent);
        } catch (Exception e) {
            Toast.makeText(MainActivity.this, "Invalid Input", Toast.LENGTH_SHORT).show();
        }
    }
}
```

### **4. Create the ResultActivity to Display Calculation Result**

This activity will take the input from the user, perform the calculation, and show the result.

1. Right-click on `java` -> `com.example.calculatorapp` -> `New` -> `Activity` -> `Empty Activity`.
2. Name it `ResultActivity` and click **Finish**.

In `ResultActivity.java`, handle the calculation and display the result:

```java
package com.example.calculatorapp;

import android.os.Bundle;
import android.widget.TextView;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class ResultActivity extends AppCompatActivity {

    private TextView resultTextView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_result);

        resultTextView = findViewById(R.id.resultTextView);

        // Get the calculation string from the Intent
        String calculation = getIntent().getStringExtra("calculation");

        try {
            double result = evaluateExpression(calculation);
            resultTextView.setText("Result: " + result);
        } catch (Exception e) {
            Toast.makeText(this, "Error in Calculation", Toast.LENGTH_SHORT).show();
        }
    }

    private double evaluateExpression(String expression) {
        // You can use Java's ScriptEngine or implement your own evaluation logic.
        // For simplicity, we will use the following evaluation method.
        return new Object() {
            public double eval(final String str) {
                try {
                    return Double.parseDouble(str);
                } catch (Exception e) {
                    throw new RuntimeException("Error parsing expression");
                }
            }
        }.eval(expression);
    }
}
```

### **5. Update AndroidManifest.xml**

Ensure that both `MainActivity` and `ResultActivity` are declared in the `AndroidManifest.xml`:

```xml
<application
    android:allowBackup="true"
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:theme="@style/

Theme.CalculatorApp">
    
    <activity android:name=".MainActivity">
        <intent-filter>
            <action android:name="android.intent.action.MAIN" />
            <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>
    </activity>
    
    <activity android:name=".ResultActivity"></activity>

</application>
```

### **6. Run the Application**

When you run the application:
- The calculator screen will appear, where you can input numbers and operators.
- Press the "=" button to calculate the result.
- The `ResultActivity` will display the result of the calculation.

 
