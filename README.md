# Ex.No:2a Develop program to create a text field and a button “Navigate”. When you enter “www.gmail.com” and press navigate button it should open google page using Implicit Intents.


## AIM:

To create a navigate button using Implicit Intent to display the gmail page using Android Studio.

## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:



## PROGRAM:
```
/*
Program to print the text “Implicitintent”.
Developed by: JAYANI N
Registeration Number : 212224100025
*/


## activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="24dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Intent Experiment"
        android:textSize="26sp"
        android:textStyle="bold"
        android:layout_marginBottom="24dp" />

    <EditText
        android:id="@+id/urlInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter website URL"
        android:inputType="textUri"
        android:text="https://www.google.com" />

    <Button
        android:id="@+id/openWebButton"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Open Website (Implicit Intent)" />

    <Button
        android:id="@+id/nextButton"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Go to Second Screen (Explicit Intent)"
        android:layout_marginTop="12dp" />
    <WebView
        android:id="@+id/webView"
        android:layout_width="match_parent"
        android:layout_height="300dp" />

</LinearLayout>




## MainActivity.java

package com.example.intents;

import android.content.ActivityNotFoundException;
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.webkit.WebView;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText urlInput;
    Button openWebButton, nextButton;
    WebView webView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        urlInput = findViewById(R.id.urlInput);
        openWebButton = findViewById(R.id.openWebButton);
        nextButton = findViewById(R.id.nextButton);
        webView = findViewById(R.id.webView);

        // Load a website inside the app using WebView
        webView.loadUrl("https://www.google.com");

        // IMPLICIT INTENT: Open a website in an external browser
        openWebButton.setOnClickListener(v -> {

            String url = urlInput.getText().toString().trim();

            if (url.isEmpty()) {
                Toast.makeText(
                        MainActivity.this,
                        "Please enter a website URL",
                        Toast.LENGTH_SHORT
                ).show();
                return;
            }

            if (!url.matches("(?i)^https?://.*")) {
                url = "https://" + url;
            }

            Intent intent = new Intent(
                    Intent.ACTION_VIEW,
                    Uri.parse(url)
            );

            try {
                startActivity(intent);
            } catch (ActivityNotFoundException e) {
                Toast.makeText(
                        MainActivity.this,
                        "No app is available to open this website",
                        Toast.LENGTH_LONG
                ).show();
            }
        });

        // EXPLICIT INTENT: Open SecondActivity directly
        nextButton.setOnClickListener(v -> {

            Intent intent = new Intent(
                    MainActivity.this,
                    SecondActivity.class
            );

            startActivity(intent);
        });
    }
}


```

## OUTPUT

<img width="1471" height="972" alt="image" src="https://github.com/user-attachments/assets/02d22599-89ad-4f47-90c3-eeaf130cb6ba" />
<img width="1638" height="976" alt="image" src="https://github.com/user-attachments/assets/16f810bd-e54b-4a74-aefa-804425796d7e" />



## RESULT
Thus a Simple Android Application create a navigate button using Implicit Intent to display the gmail page using Android Studio is developed and executed successfully.


