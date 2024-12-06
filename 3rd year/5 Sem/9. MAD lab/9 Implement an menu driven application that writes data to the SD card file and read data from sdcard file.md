# 9 Implement an menu driven application that writes data to the SD card file and read data from sdcard file.


 
### Prerequisites:
1. **Android Studio** installed on your computer.
2. Basic knowledge of Android development (Java or Kotlin).
3. An Android device or emulator for testing.

### Steps to Develop the Application:

#### 1. **Create a New Android Project**

Create a new Android project in Android Studio with an Empty Activity template. Name it something like `SensorApp`.

#### 2. **Add Necessary Permissions**

To read sensors, no special permissions are required in the `AndroidManifest.xml` file. However, if you want to use specific sensors (like accelerometer, gyroscope, etc.), you need to handle runtime permissions where applicable.

For this basic app that lists the sensors, you don’t need to add any special permissions to the manifest.

#### 3. **Design the Layout in `activity_main.xml`**

Create a simple UI with a `ListView` or `RecyclerView` to display the sensor names.

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp">

    <TextView
        android:id="@+id/tvTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Available Sensors"
        android:textSize="18sp"
        android:paddingBottom="10dp"
        android:textAlignment="center"/>

    <ListView
        android:id="@+id/lvSensors"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
</LinearLayout>
```

#### 4. **Create the `MainActivity.java` or `MainActivity.kt`**

In `MainActivity.java` (for Java) or `MainActivity.kt` (for Kotlin), you will retrieve the list of sensors using the `SensorManager` and display them in the `ListView`.

Here's the Java code for the activity:

```java
import android.hardware.Sensor;
import android.hardware.SensorManager;
import android.os.Bundle;
import android.widget.ArrayAdapter;
import android.widget.ListView;

import androidx.appcompat.app.AppCompatActivity;

import java.util.List;

public class MainActivity extends AppCompatActivity {

    private ListView lvSensors;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        lvSensors = findViewById(R.id.lvSensors);

        // Get the SensorManager system service
        SensorManager sensorManager = (SensorManager) getSystemService(SENSOR_SERVICE);

        // Get the list of all available sensors
        List<Sensor> sensorList = sensorManager.getSensorList(Sensor.TYPE_ALL);

        // Create an array of sensor names
        String[] sensorNames = new String[sensorList.size()];
        for (int i = 0; i < sensorList.size(); i++) {
            sensorNames[i] = sensorList.get(i).getName();
        }

        // Create an ArrayAdapter to display the sensor names in the ListView
        ArrayAdapter<String> adapter = new ArrayAdapter<>(this, android.R.layout.simple_list_item_1, sensorNames);
        lvSensors.setAdapter(adapter);
    }
}
```

### Explanation:

- **`SensorManager`**: This is a system service that allows access to all sensors on the device. The method `getSensorList(Sensor.TYPE_ALL)` retrieves a list of all available sensors on the device.
- **`Sensor`**: This class represents an individual sensor on the device. The `getName()` method of the `Sensor` object returns the name of the sensor.
- **`ListView`**: This is a simple view to display a list of items. In this case, we are displaying the names of the sensors.

#### 5. **Run the Application**

1. **Build and run the app** on an Android device or emulator.
2. The app will list all the available sensors on the device, such as accelerometer, magnetometer, gyroscope, proximity sensor, etc.

### Kotlin Version of the Code:

If you're using Kotlin, here’s the equivalent `MainActivity.kt`:

```kotlin
import android.hardware.Sensor
import android.hardware.SensorManager
import android.os.Bundle
import android.widget.ArrayAdapter
import android.widget.ListView
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val lvSensors: ListView = findViewById(R.id.lvSensors)

        // Get the SensorManager system service
        val sensorManager = getSystemService(SENSOR_SERVICE) as SensorManager

        // Get the list of all available sensors
        val sensorList: List<Sensor> = sensorManager.getSensorList(Sensor.TYPE_ALL)

        // Create an array of sensor names
        val sensorNames = sensorList.map { it.name }.toTypedArray()

        // Create an ArrayAdapter to display the sensor names in the ListView
        val adapter = ArrayAdapter(this, android.R.layout.simple_list_item_1, sensorNames)
        lvSensors.adapter = adapter
    }
}
```

 
