# 5 Write an application that draws basic graphical primitives on the screen


 
### **Steps to Create the Application:**

1. **Create a New Android Project**
2. **Create a Custom View for Drawing**
3. **Draw Basic Graphical Primitives**
4. **Display the View in the Main Activity**

### **1. Create a New Android Project:**

1. Open Android Studio and create a new project.
2. Select **Empty Activity**.
3. Name the project `DrawShapesApp` and choose **Java** (or Kotlin) as the language.
4. Set the **Minimum API level** (API 21 or above is recommended).
5. Click **Finish** to create the project.

### **2. Create a Custom View for Drawing**

We'll create a custom `View` where we will override the `onDraw()` method to draw basic shapes.

#### Create the Custom View Class:

Create a new class `DrawingView.java` inside the `java/com.example.drawshapesapp/` package:

```java
package com.example.drawshapesapp;

import android.content.Context;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;
import android.view.View;

public class DrawingView extends View {

    private Paint paint;

    public DrawingView(Context context) {
        super(context);
        paint = new Paint();
        paint.setStyle(Paint.Style.FILL);
        paint.setColor(Color.BLACK);  // Default color (black)
    }

    @Override
    protected void onDraw(Canvas canvas) {
        super.onDraw(canvas);

        // Draw a line
        paint.setColor(Color.RED);  // Set color to red
        canvas.drawLine(100, 100, 500, 100, paint);

        // Draw a rectangle
        paint.setColor(Color.BLUE);  // Set color to blue
        canvas.drawRect(100, 200, 500, 400, paint);

        // Draw a circle
        paint.setColor(Color.GREEN);  // Set color to green
        canvas.drawCircle(300, 600, 100, paint);

        // Draw a filled oval
        paint.setColor(Color.YELLOW);  // Set color to yellow
        canvas.drawOval(150, 750, 450, 950, paint);

        // Draw a triangle (using Path)
        paint.setColor(Color.MAGENTA);  // Set color to magenta
        android.graphics.Path path = new android.graphics.Path();
        path.moveTo(300, 1100);  // Starting point of the triangle
        path.lineTo(200, 1300);  // Second point
        path.lineTo(400, 1300);  // Third point
        path.close();  // Close the triangle path
        canvas.drawPath(path, paint);
    }
}
```

### **3. Use the Custom View in the Main Activity**

Now that we have created a custom view (`DrawingView`), we will add this view to the `MainActivity` to display it.

In `MainActivity.java`, modify the code to include the custom `DrawingView`:

```java
package com.example.drawshapesapp;

import android.os.Bundle;
import android.widget.LinearLayout;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Create an instance of the DrawingView
        DrawingView drawingView = new DrawingView(this);

        // Set the content view to the DrawingView
        LinearLayout layout = findViewById(R.id.layout);
        layout.addView(drawingView);  // Add the custom view to the layout
    }
}
```

### **4. Update the Layout (activity_main.xml)**

In the `res/layout/activity_main.xml` file, set up a `LinearLayout` or `FrameLayout` where we will add the custom drawing view.

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center">

    <!-- Layout for drawing the shapes -->
    <LinearLayout
        android:id="@+id/layout"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">
    </LinearLayout>

</LinearLayout>
```

### **5. Run the Application**

Once everything is set up, run the application. The `DrawingView` will display the following shapes on the screen:

1. **A Red Line**: Drawn from (100, 100) to (500, 100).
2. **A Blue Rectangle**: Drawn from (100, 200) to (500, 400).
3. **A Green Circle**: Drawn with a center at (300, 600) and a radius of 100.
4. **A Yellow Oval**: Drawn from (150, 750) to (450, 950).
5. **A Magenta Triangle**: Defined using three points.





