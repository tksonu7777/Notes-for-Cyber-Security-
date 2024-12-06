# 10 Design a location tracking application using GPS






### Prerequisites:
1. **Android Studio** installed.
2. Basic knowledge of Android development (Java or Kotlin).
3. Android device with GPS functionality (or an emulator with GPS capabilities).

### Steps to Develop the Location Tracking Application:

#### 1. **Create a New Android Project**
Create a new Android project in Android Studio with an Empty Activity template. Name it something like `LocationTrackingApp`.

#### 2. **Add Required Permissions**
For location tracking, you need to request permissions in the `AndroidManifest.xml`. You'll need the following permissions:

- **ACCESS_FINE_LOCATION**: To get precise location (GPS).
- **ACCESS_COARSE_LOCATION**: For approximate location (network-based).
- **INTERNET**: If you want to use Google Maps or any other API to display the location.

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.locationtrackingapp">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/Theme.LocationTrackingApp">

        <!-- Permission to access fine location -->
        <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
        <!-- Permission to access coarse location -->
        <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
        <!-- Permission for internet access (if using maps or other network-based services) -->
        <uses-permission android:name="android.permission.INTERNET"/>

        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

#### 3. **Design the Layout in `activity_main.xml`**
Create a layout for displaying the GPS coordinates (latitude, longitude) on the screen.

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp">

    <TextView
        android:id="@+id/tvLatitude"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Latitude: "
        android:textSize="18sp" />

    <TextView
        android:id="@+id/tvLongitude"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Longitude: "
        android:textSize="18sp" />

    <Button
        android:id="@+id/btnStartTracking"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Start Tracking"
        android:layout_gravity="center" />

</LinearLayout>
```

#### 4. **Create the `MainActivity.java` or `MainActivity.kt`**
Use `FusedLocationProviderClient` to get the device's location. This API is recommended because it provides more accurate and power-efficient location data than using the older `LocationManager`.

Here is the Java code for `MainActivity.java`:

```java
import android.Manifest;
import android.content.pm.PackageManager;
import android.location.Location;
import android.os.Bundle;
import android.widget.Button;
import android.widget.TextView;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;
import androidx.core.app.ActivityCompat;

import com.google.android.gms.location.FusedLocationProviderClient;
import com.google.android.gms.location.LocationServices;
import com.google.android.gms.tasks.OnCompleteListener;
import com.google.android.gms.tasks.Task;

public class MainActivity extends AppCompatActivity {

    private FusedLocationProviderClient fusedLocationClient;
    private TextView tvLatitude, tvLongitude;
    private Button btnStartTracking;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize UI elements
        tvLatitude = findViewById(R.id.tvLatitude);
        tvLongitude = findViewById(R.id.tvLongitude);
        btnStartTracking = findViewById(R.id.btnStartTracking);

        // Initialize FusedLocationProviderClient
        fusedLocationClient = LocationServices.getFusedLocationProviderClient(this);

        // Start tracking when the button is clicked
        btnStartTracking.setOnClickListener(v -> {
            if (ActivityCompat.checkSelfPermission(MainActivity.this,
                    Manifest.permission.ACCESS_FINE_LOCATION) != PackageManager.PERMISSION_GRANTED &&
                    ActivityCompat.checkSelfPermission(MainActivity.this,
                            Manifest.permission.ACCESS_COARSE_LOCATION) != PackageManager.PERMISSION_GRANTED) {
                // Request location permissions
                ActivityCompat.requestPermissions(MainActivity.this,
                        new String[]{Manifest.permission.ACCESS_FINE_LOCATION}, 1);
                return;
            }
            getLastKnownLocation();
        });
    }

    // Get the last known location
    private void getLastKnownLocation() {
        fusedLocationClient.getLastLocation()
                .addOnCompleteListener(this, new OnCompleteListener<Location>() {
                    @Override
                    public void onComplete(Task<Location> task) {
                        if (task.isSuccessful() && task.getResult() != null) {
                            Location location = task.getResult();
                            tvLatitude.setText("Latitude: " + location.getLatitude());
                            tvLongitude.setText("Longitude: " + location.getLongitude());
                        } else {
                            Toast.makeText(MainActivity.this, "Failed to get location.", Toast.LENGTH_SHORT).show();
                        }
                    }
                });
    }

    // Handle permission request result
    @Override
    public void onRequestPermissionsResult(int requestCode, String[] permissions, int[] grantResults) {
        super.onRequestPermissionsResult(requestCode, permissions, grantResults);
        if (requestCode == 1) {
            if (grantResults.length > 0 && grantResults[0] == PackageManager.PERMISSION_GRANTED) {
                getLastKnownLocation();
            } else {
                Toast.makeText(this, "Permission denied", Toast.LENGTH_SHORT).show();
            }
        }
    }
}
```

### Explanation:

- **FusedLocationProviderClient**: This class is used to get the device's location. It's part of Google Play services, and it's more power-efficient than the older `LocationManager` API.
- **Permissions**: You need to request location permissions (`ACCESS_FINE_LOCATION`) at runtime for Android 6.0 (API level 23) and higher.
- **`getLastLocation()`**: This method retrieves the most recent location of the device. It's ideal for a basic location tracking app since it doesn't require continuous updates.
- **UI Update**: When the user presses the "Start Tracking" button, the app retrieves the current location and displays the latitude and longitude.

### 5. **Run the Application**

1. **Build and run** the app on an Android device (or emulator with location features).
2. Press the "Start Tracking" button, and the app will retrieve the device's current GPS coordinates and display them on the screen.

#### 6. **Handle Continuous Location Updates (Optional)**

If you want to track the location continuously (e.g., update the coordinates every few seconds), you can use `LocationRequest` and `LocationCallback` with the `FusedLocationProviderClient`.

Here is an example of how to handle continuous location updates:

```java
import com.google.android.gms.location.LocationCallback;
import com.google.android.gms.location.LocationRequest;

private LocationRequest locationRequest;
private LocationCallback locationCallback;

// Initialize location request and callback
private void startLocationUpdates() {
    locationRequest = new LocationRequest();
    locationRequest.setInterval(10000);  // 10 seconds
    locationRequest.setFastestInterval(5000);  // 5 seconds
    locationRequest.setPriority(LocationRequest.PRIORITY_HIGH_ACCURACY);

    locationCallback = new LocationCallback() {
        @Override
        public void onLocationResult(LocationResult locationResult) {
            super.onLocationResult(locationResult);
            if (locationResult != null && locationResult.getLocations().size() > 0) {
                Location location = locationResult.getLastLocation();
                tvLatitude.setText("Latitude: " + location.getLatitude());
                tvLongitude.setText("Longitude: " + location.getLongitude());
            }
        }
    };

    fusedLocationClient.requestLocationUpdates(locationRequest, locationCallback, null);
}

// Stop location updates when not needed
private void stopLocationUpdates() {
    fusedLocationClient.removeLocationUpdates(locationCallback);
}
```

 
