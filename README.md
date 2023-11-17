# CONTENT-PROVIDER
## Ex.No : 5 Create Your Own Content Providers to get Contacts details.
### AIM:
To create your own content providers to get contact details using Android Studio.
### ALGORITHM:
```
Step 1: Open Android Studio and then click on File -> New -> New project.
Step 2: Then type the Application name as “contentprovider″ and click Next.
Step 3: Then select the Minimum SDK as shown below and click Next.
Step 4: Then select the Empty Activity and click Next. Finally, click Finish.
Step 5: Design layout in activity_main.xml.
Step 6: Get contact details and Display details give in the MainActivity file.
Step 7: Save and run the application
```
### PROGRAM:
```
DEVELOPED BY:charan
REGISTER NUMBER:212221040067
```
### activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context=".MainActivity">

<Button
    android:id="@+id/button"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginStart="129dp"
    android:layout_marginTop="302dp"
    android:text="GET CONTACTS"
    android:onClick="btnGetContactPressed"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
### MainActivity.java
```
package com.example.contact;

import androidx.appcompat.app.AppCompatActivity;
import androidx.core.app.ActivityCompat;
import androidx.core.content.ContextCompat;

import android.Manifest;
import android.annotation.SuppressLint;
import android.content.ContentResolver;
import android.content.pm.PackageManager;
import android.database.Cursor;
import android.net.Uri;
import android.os.Bundle;
import android.provider.ContactsContract;
import android.util.Log;
import android.view.View;


public class MainActivity extends AppCompatActivity {

@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

}
private void getPhoneContacts(){
    if(ContextCompat.checkSelfPermission(this, Manifest.permission.READ_CONTACTS) != PackageManager.PERMISSION_GRANTED) {
        ActivityCompat.requestPermissions(this,new String[] {Manifest.permission.READ_CONTACTS},0);

    }
    ContentResolver contentResolver = getContentResolver();
    Uri uri = ContactsContract.CommonDataKinds.Phone.CONTENT_URI;
    Cursor cursor = contentResolver.query(uri,null,null,null,null);
    Log.i("CONTACT_PROVIDER_DEMO","TOTAL # COUNTS :::"+cursor.getCount());
    if(cursor.getCount() > 0)
    {
        while(cursor.moveToNext()){
            String contactName = cursor.getString(cursor.getColumnIndex(ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME));
            String contactNumber = cursor.getString(cursor.getColumnIndex(ContactsContract.CommonDataKinds.Phone.NUMBER));
            Log.i("Content_provider_demo","Name: # "+contactName+"Number: # "+contactNumber);
        }

    }
}

public void btnGetContactPressed(View view) {
    getPhoneContacts();
}
}
```
### Android Manifest.java
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:tools="http://schemas.android.com/tools">
<uses-permission android:name="android.permission.READ_CONTACTS"></uses-permission>
<uses-permission android:name="android.permission.WRITE_CONTACTS"></uses-permission>
<application
    android:allowBackup="true"
    android:dataExtractionRules="@xml/data_extraction_rules"
    android:fullBackupContent="@xml/backup_rules"
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:supportsRtl="true"
    android:theme="@style/Theme.Contact"
    tools:targetApi="31">
    <activity
        android:name=".MainActivity"
        android:exported="true">
        <intent-filter>
            <action android:name="android.intent.action.MAIN" />

            <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>
    </activity>
</application>

</manifest>
```
### OUTPUT:

![image](https://github.com/HibaRajarajeswari/CONTENT-PROVIDER/assets/129970809/2b458cc2-e3ef-4455-afe6-48ccb4221abe)

![image](https://github.com/HibaRajarajeswari/CONTENT-PROVIDER/assets/129970809/5930b215-f280-4a93-81c6-1eaf96d4852c)

![image](https://github.com/HibaRajarajeswari/CONTENT-PROVIDER/assets/129970809/9e6c69b9-c092-4375-9418-459a9a893c9a)
### RESULT:
Thus a Simple Android Application create your own content providers to get contacts details using Android Studio is developed and executed successfully.
