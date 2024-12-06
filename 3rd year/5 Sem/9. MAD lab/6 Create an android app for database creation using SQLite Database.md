# 6 Create an android app for database creation using SQLite Database






 
### Prerequisites:
1. **Android Studio** installed on your computer.
2. Basic knowledge of Android development (Java or Kotlin).
3. An Android Emulator or an actual device for testing.

### Steps to Create an Android App with SQLite:

#### 1. Create a New Android Project

Open Android Studio, click on "Start a New Android Studio Project," and select a template (for this tutorial, we will use an empty activity). Name your project (e.g., `SQLiteExample`), choose language (Java or Kotlin), and set the minimum SDK version.

#### 2. Add SQLite Code to Your App

We'll create a helper class for the SQLite database.

##### a) Define a `DatabaseHelper` class:

Create a class named `DatabaseHelper.java` (for Java) or `DatabaseHelper.kt` (for Kotlin) to manage the SQLite database.

```java
import android.content.Context;
import android.database.sqlite.SQLiteDatabase;
import android.database.sqlite.SQLiteOpenHelper;

public class DatabaseHelper extends SQLiteOpenHelper {

    // Database Name and Version
    private static final String DATABASE_NAME = "UserDB";
    private static final int DATABASE_VERSION = 1;

    // Table Name and Column Names
    private static final String TABLE_USER = "user";
    private static final String COLUMN_ID = "id";
    private static final String COLUMN_NAME = "name";
    private static final String COLUMN_EMAIL = "email";

    // SQL Query to Create Table
    private static final String CREATE_TABLE_USER = "CREATE TABLE " + TABLE_USER + "("
            + COLUMN_ID + " INTEGER PRIMARY KEY AUTOINCREMENT,"
            + COLUMN_NAME + " TEXT,"
            + COLUMN_EMAIL + " TEXT"
            + ")";

    public DatabaseHelper(Context context) {
        super(context, DATABASE_NAME, null, DATABASE_VERSION);
    }

    @Override
    public void onCreate(SQLiteDatabase db) {
        // Create the user table
        db.execSQL(CREATE_TABLE_USER);
    }

    @Override
    public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {
        // Drop the existing table and create it again if database version changes
        db.execSQL("DROP TABLE IF EXISTS " + TABLE_USER);
        onCreate(db);
    }
}
```

##### b) Create Methods for CRUD Operations:

Now, you'll add methods to insert, read, update, and delete data from the database.

```java
import android.content.ContentValues;
import android.content.Context;
import android.database.Cursor;
import android.database.SQLException;
import android.database.sqlite.SQLiteDatabase;
import java.util.ArrayList;
import java.util.List;

public class DatabaseManager {

    private SQLiteDatabase database;
    private DatabaseHelper dbHelper;

    public DatabaseManager(Context context) {
        dbHelper = new DatabaseHelper(context);
    }

    // Open the database
    public void open() throws SQLException {
        database = dbHelper.getWritableDatabase();
    }

    // Close the database
    public void close() {
        dbHelper.close();
    }

    // Insert data into the user table
    public long insertUser(String name, String email) {
        ContentValues values = new ContentValues();
        values.put(DatabaseHelper.COLUMN_NAME, name);
        values.put(DatabaseHelper.COLUMN_EMAIL, email);

        return database.insert(DatabaseHelper.TABLE_USER, null, values);
    }

    // Get all users
    public List<String> getAllUsers() {
        List<String> users = new ArrayList<>();
        String selectQuery = "SELECT * FROM " + DatabaseHelper.TABLE_USER;
        Cursor cursor = database.rawQuery(selectQuery, null);

        if (cursor.moveToFirst()) {
            do {
                String name = cursor.getString(cursor.getColumnIndex(DatabaseHelper.COLUMN_NAME));
                String email = cursor.getString(cursor.getColumnIndex(DatabaseHelper.COLUMN_EMAIL));
                users.add("Name: " + name + ", Email: " + email);
            } while (cursor.moveToNext());
        }
        cursor.close();
        return users;
    }

    // Update user email
    public int updateUserEmail(int id, String newEmail) {
        ContentValues values = new ContentValues();
        values.put(DatabaseHelper.COLUMN_EMAIL, newEmail);

        return database.update(DatabaseHelper.TABLE_USER, values,
                DatabaseHelper.COLUMN_ID + " = ?", new String[]{String.valueOf(id)});
    }

    // Delete user by id
    public void deleteUser(int id) {
        database.delete(DatabaseHelper.TABLE_USER,
                DatabaseHelper.COLUMN_ID + " = ?", new String[]{String.valueOf(id)});
    }
}
```

#### 3. Implement SQLite Operations in `MainActivity.java`

Now you will use the `DatabaseManager` class in your `MainActivity.java` to perform database operations such as inserting, updating, reading, and deleting.

```java
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

import java.util.List;

public class MainActivity extends AppCompatActivity {

    private DatabaseManager dbManager;
    private EditText etName, etEmail;
    private Button btnInsert, btnDisplay, btnUpdate, btnDelete;
    private TextView tvUsers;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etName = findViewById(R.id.etName);
        etEmail = findViewById(R.id.etEmail);
        btnInsert = findViewById(R.id.btnInsert);
        btnDisplay = findViewById(R.id.btnDisplay);
        btnUpdate = findViewById(R.id.btnUpdate);
        btnDelete = findViewById(R.id.btnDelete);
        tvUsers = findViewById(R.id.tvUsers);

        dbManager = new DatabaseManager(this);
        dbManager.open();

        btnInsert.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String name = etName.getText().toString();
                String email = etEmail.getText().toString();
                dbManager.insertUser(name, email);
                etName.setText("");
                etEmail.setText("");
            }
        });

        btnDisplay.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                List<String> users = dbManager.getAllUsers();
                StringBuilder stringBuilder = new StringBuilder();
                for (String user : users) {
                    stringBuilder.append(user).append("\n");
                }
                tvUsers.setText(stringBuilder.toString());
            }
        });

        btnUpdate.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Update user email (for demo purpose, just hardcoded ID)
                int userId = 1;  // Example ID
                String newEmail = "newemail@example.com";
                dbManager.updateUserEmail(userId, newEmail);
            }
        });

        btnDelete.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Delete user by ID (for demo purpose, just hardcoded ID)
                int userId = 1;  // Example ID
                dbManager.deleteUser(userId);
            }
        });
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        dbManager.close();
    }
}
```

#### 4. Define the Layout in `activity_main.xml`

In your `res/layout/activity_main.xml`, you can create a simple UI to interact with the database.

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp">

    <EditText
        android:id="@+id/etName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Name"/>

    <EditText
        android:id="@+id/etEmail"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Email"/>

    <Button
        android:id="@+id/btnInsert"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Insert"/>

    <Button
        android:id="@+id/btnDisplay"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Display All Users"/>

    <Button
        android:id="@+id/btnUpdate"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Update"/>

    <Button
        android:id="@+id/btnDelete"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Delete"/>

    <TextView
        android:id="@+id/tvUsers"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="User List Will Appear Here"
        android:paddingTop="16dp"/>

</LinearLayout>
```

### 5. Run the App

 
























