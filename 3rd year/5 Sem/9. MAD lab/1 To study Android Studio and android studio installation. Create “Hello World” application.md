#  1 To study Android Studio and android studio installation. Create “Hello World” application.

 
### **1. Installing Android Studio**

#### Step 1: Download Android Studio
- Go to the official Android Developer website: [https://developer.android.com/studio](https://developer.android.com/studio)
- Click the **Download Android Studio** button for your operating system (Windows, macOS, or Linux).
- Accept the terms and conditions and wait for the download to finish.

#### Step 2: Install Android Studio
- **Windows**: Run the downloaded `.exe` file and follow the installation wizard. Choose all default settings during installation.
- **macOS**: Open the `.dmg` file and drag the Android Studio icon to the Applications folder.
- **Linux**: Extract the downloaded `.zip` file and run the `studio.sh` script.

#### Step 3: Launch Android Studio
- Open Android Studio after installation.
- The first time you run Android Studio, it may prompt you to download additional components like SDKs. Follow the instructions to install them.

### **2. Set Up a New Android Project in Android Studio**

#### Step 1: Start a New Project
- Open Android Studio.
- Click on **Start a new Android Studio project**.
- Choose **Empty Activity** as the template.
- In the **Name** field, type `HelloWorldApp`.
- Set the **Save location** where you want to save your project.
- For **Language**, select **Java** (or Kotlin if you prefer).
- Set the **Minimum API level** (usually API 21 is fine for most apps).
- Click **Finish**.

#### Step 2: Explore the Project Files
Once the project is created, Android Studio will load it, and you’ll see several files:
- **MainActivity.java (or MainActivity.kt)**: This file contains the code for your main activity (screen) of the app.
- **activity_main.xml**: This is the layout file for your activity, where you can define the UI elements.

### **3. Create the "Hello World" Application**

#### Step 1: Modify the Layout
In the `activity_main.xml` file (found under **res -> layout -> activity_main.xml**), replace the default content with the following XML code to display "Hello, World!" on the screen:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/helloWorldText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello, World!"
        android:textSize="30sp"
        android:layout_centerInParent="true"/>
</RelativeLayout>
```

#### Step 2: Modify the Java Code
Now, open **MainActivity.java** (located in **java -> com.example.helloworldapp -> MainActivity.java**) and ensure it looks like this:

```java
package com.example.helloworldapp;

import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
}
```

This code sets the layout you created (`activity_main.xml`) as the content view for the activity.

### **4. Run the Application**

#### Step 1: Set Up an Emulator or Connect a Device
You can run the application on an emulator or a physical device:
- **Emulator**: Click on the **AVD Manager** (Android Virtual Device) in Android Studio, create a virtual device (choose a phone model), and start it.
- **Physical Device**: Enable **Developer Options** and **USB Debugging** on your Android phone. Connect it via USB to your computer.

#### Step 2: Run the Application
- Click the green **Run** button (triangle icon) in the top toolbar of Android Studio.
- Choose your emulator or connected device to run the app.

Once the app runs, you should see "Hello, World!" displayed in the center of the screen.
