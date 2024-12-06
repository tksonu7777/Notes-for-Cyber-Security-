# 2. Design an application to display IMEI, IMSI, Location, Version, and other basic information of device

 
### **Key Information We Need to Display:**
1. **IMEI** (International Mobile Equipment Identity)
2. **IMSI** (International Mobile Subscriber Identity)
3. **Device Location** (GPS or network-based)
4. **Android Version**
5. **Device Manufacturer**
6. **Model of the device**

### **Important Permissions Needed:**
To access some of the data, we will need to request permissions at runtime and declare them in the manifest:

- `READ_PHONE_STATE` for IMEI and IMSI.
- `ACCESS_FINE_LOCATION` or `ACCESS_COARSE_LOCATION` for location.
- `INTERNET` for getting network-based location (optional).

### **1. Setting Up Permissions**

Open the `AndroidManifest.xml` and add the necessary permissions:

```xml
<uses-permission android:name="android.permission.READ_PHONE_STATE"/>
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
<uses-permission android:name="android.permission.INTERNET"/>
```

### **2. Designing the Layout**

In your `activity_main.xml` file, design a simple layout to display the device information:

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:id="@+id/imeiText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="IMEI: "
        android:textSize="18sp"/>

    <TextView
        android:id="@+id/imsiText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="IMSI: "
        android:textSize="18sp"/>

    <TextView
        android:id="@+id/locationText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Location: "
        android:textSize="18sp"/>

    <TextView
        android:id="@+id/versionText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Version: "
        android:textSize="18sp"/>

    <TextView
        android:id="@+id/manufacturerText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Manufacturer: "
        android:textSize="18sp"/>

    <TextView
        android:id="@+id/modelText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Model: "
        android:textSize="18sp"/>

</LinearLayout>
```

### **3. Java Code to Get Device Information**

Now, in your `MainActivity.java`, you'll retrieve and display the necessary information. Here's the Java code:

```java
package com.example.deviceinfo;

import android.Manifest;
import android.content.pm.PackageManager;
import android.os.Bundle;
import android.os.Build;
import android.provider.Settings;
import android.telephony.TelephonyManager;
import android.location.Location;
import android.location.LocationListener;
import android.location.LocationManager;
import android.widget.TextView;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.app.ActivityCompat;

public class MainActivity extends AppCompatActivity {

    private TextView imeiText, imsiText, locationText, versionText, manufacturerText, modelText;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize TextViews
        imeiText = findViewById(R.id.imeiText);
        imsiText = findViewById(R.id.imsiText);
        locationText = findViewById(R.id.locationText);
        versionText = findViewById(R.id.versionText);
        manufacturerText = findViewById(R.id.manufacturerText);
        modelText = findViewById(R.id.modelText);

        // Display basic device information
        displayDeviceInfo();

        // Request permissions if not granted
        if (ActivityCompat.checkSelfPermission(this, Manifest.permission.READ_PHONE_STATE) != PackageManager.PERMISSION_GRANTED) {
            ActivityCompat.requestPermissions(this, new String[]{Manifest.permission.READ_PHONE_STATE}, 1);
        }
        if (ActivityCompat.checkSelfPermission(this, Manifest.permission.ACCESS_FINE_LOCATION) != PackageManager.PERMISSION_GRANTED) {
            ActivityCompat.requestPermissions(this, new String[]{Manifest.permission.ACCESS_FINE_LOCATION}, 2);
        } else {
            getLocation();
        }
    }

    private void displayDeviceInfo() {
        // Android Version
        versionText.setText("Version: " + Build.VERSION.RELEASE);

        // Device Manufacturer and Model
        manufacturerText.setText("Manufacturer: " + Build.MANUFACTURER);
        modelText.setText("Model: " + Build.MODEL);

        // Telephony Manager for IMEI and IMSI
        TelephonyManager telephonyManager = (TelephonyManager) getSystemService(TELEPHONY_SERVICE);
        if (ActivityCompat.checkSelfPermission(this, Manifest.permission.READ_PHONE_STATE) == PackageManager.PERMISSION_GRANTED) {
            String imei = telephonyManager.getImei();  // IMEI (for devices that support it)
            String imsi = telephonyManager.getSubscriberId();  // IMSI
            imeiText.setText("IMEI: " + (imei != null ? imei : "Not available"));
            imsiText.setText("IMSI: " + (imsi != null ? imsi : "Not available"));
        }
    }

    private void getLocation() {
        LocationManager locationManager = (LocationManager) getSystemService(LOCATION_SERVICE);
        if (locationManager != null) {
            try {
                locationManager.requestLocationUpdates(LocationManager.GPS_PROVIDER, 10000, 10, new LocationListener() {
                    @Override
                    public void onLocationChanged(Location location) {
                        double latitude = location.getLatitude();
                        double longitude = location.getLongitude();
                        locationText.setText("Location: " + latitude + ", " + longitude);
                    }

                    @Override
                    public void onStatusChanged(String provider, int status, Bundle extras) {}

                    @Override
                    public void onProviderEnabled(String provider) {}

                    @Override
                    public void onProviderDisabled(String provider) {}
                });
            } catch (SecurityException e) {
                Toast.makeText(this, "Location permission not granted", Toast.LENGTH_SHORT).show();
            }
        }
    }

    @Override
    public void onRequestPermissionsResult(int requestCode, String[] permissions, int[] grantResults) {
        super.onRequestPermissionsResult(requestCode, permissions, grantResults);
        if (requestCode == 1 && grantResults.length > 0 && grantResults[0] == PackageManager.PERMISSION_GRANTED) {
            displayDeviceInfo();
        }
        if (requestCode == 2 && grantResults.length > 0 && grantResults[0] == PackageManager.PERMISSION_GRANTED) {
            getLocation();
        }
    }
}
```

 
### **4. Run the Application**

- Ensure that you have granted the necessary permissions.
- If you are testing on an emulator, ensure that you have enabled the **Google APIs** for location simulation.
- If testing on a physical device, ensure that the device has mobile network capabilities for IMEI and IMSI retrieval.

 
