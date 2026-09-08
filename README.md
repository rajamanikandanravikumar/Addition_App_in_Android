# Addition_App_in_Android

## AIM:
To create a application for addition of two numbers.

## ALGORITHM:
Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as Addition_App and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout using UI components in activity_main.xml.

Step 6: Display the calculator operation in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
### MainActivity.java:
```
package com.example.workshop2;

import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

import java.text.DecimalFormat;

public class MainActivity extends AppCompatActivity {

    private EditText num1, num2;
    private Button addButton, clearButton;
    private TextView resultText;
    private DecimalFormat decimalFormat = new DecimalFormat("#.###");

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        num1 = findViewById(R.id.num1);
        num2 = findViewById(R.id.num2);
        addButton = findViewById(R.id.addButton);
        clearButton = findViewById(R.id.clearButton);
        resultText = findViewById(R.id.result);

        addButton.setOnClickListener(v -> calculateAddition());
        clearButton.setOnClickListener(v -> clearFields());
    }

    private void calculateAddition() {
        String value1 = num1.getText().toString().trim();
        String value2 = num2.getText().toString().trim();

        if (value1.isEmpty() || value2.isEmpty()) {
            Toast.makeText(this, "Please enter both numbers", Toast.LENGTH_SHORT).show();
            resultText.setText("Result: --");
            return;
        }

        try {
            double n1 = Double.parseDouble(value1);
            double n2 = Double.parseDouble(value2);
            double sum = n1 + n2;

            String formattedResult = decimalFormat.format(sum);
            resultText.setText("Result: " + formattedResult);
        } catch (NumberFormatException e) {
            Toast.makeText(this, "Invalid input. Please enter valid numbers.", Toast.LENGTH_SHORT).show();
            resultText.setText("Error");
        }
    }

    private void clearFields() {
        num1.setText("");
        num2.setText("");
        resultText.setText("Result: --");
        num1.requestFocus();
    }
}
```
### activity_main.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.coordinatorlayout.widget.CoordinatorLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="?attr/colorSurfaceContainerLow">

    <com.google.android.material.appbar.AppBarLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="?attr/colorSurface">

        <com.google.android.material.appbar.MaterialToolbar
            android:id="@+id/toolbar"
            android:layout_width="match_parent"
            android:layout_height="?attr/actionBarSize"
            app:title="Addition App"
            app:titleCentered="true" />

    </com.google.android.material.appbar.AppBarLayout>

    <androidx.core.widget.NestedScrollView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:layout_behavior="@string/appbar_scrolling_view_behavior">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical"
            android:padding="24dp">

            <com.google.android.material.card.MaterialCardView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                app:cardCornerRadius="16dp"
                app:cardElevation="2dp"
                app:strokeWidth="0dp">

                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:orientation="vertical"
                    android:padding="20dp">

                    <TextView
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:text="Enter Numbers"
                        android:textAppearance="?attr/textAppearanceTitleMedium"
                        android:layout_marginBottom="16dp"/>

                    <com.google.android.material.textfield.TextInputLayout
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:hint="First Number"
                        app:startIconDrawable="@drawable/ic_calculate"
                        style="@style/Widget.Material3.TextInputLayout.OutlinedBox"
                        android:layout_marginBottom="16dp">

                        <com.google.android.material.textfield.TextInputEditText
                            android:id="@+id/num1"
                            android:layout_width="match_parent"
                            android:layout_height="wrap_content"
                            android:inputType="numberDecimal" />

                    </com.google.android.material.textfield.TextInputLayout>

                    <com.google.android.material.textfield.TextInputLayout
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:hint="Second Number"
                        app:startIconDrawable="@drawable/ic_calculate"
                        style="@style/Widget.Material3.TextInputLayout.OutlinedBox"
                        android:layout_marginBottom="24dp">

                        <com.google.android.material.textfield.TextInputEditText
                            android:id="@+id/num2"
                            android:layout_width="match_parent"
                            android:layout_height="wrap_content"
                            android:inputType="numberDecimal" />

                    </com.google.android.material.textfield.TextInputLayout>

                    <com.google.android.material.button.MaterialButton
                        android:id="@+id/addButton"
                        android:layout_width="match_parent"
                        android:layout_height="64dp"
                        android:text="Calculate Sum"
                        android:textSize="16sp"
                        app:cornerRadius="12dp"
                        android:layout_marginBottom="12dp"/>

                    <com.google.android.material.button.MaterialButton
                        android:id="@+id/clearButton"
                        style="@style/Widget.Material3.Button.OutlinedButton"
                        android:layout_width="match_parent"
                        android:layout_height="64dp"
                        android:text="Clear All"
                        android:textSize="16sp"
                        app:cornerRadius="12dp" />

                </LinearLayout>

            </com.google.android.material.card.MaterialCardView>

            <com.google.android.material.card.MaterialCardView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_marginTop="24dp"
                app:cardCornerRadius="16dp"
                app:cardBackgroundColor="?attr/colorPrimaryContainer"
                app:strokeWidth="0dp">

                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:orientation="vertical"
                    android:gravity="center"
                    android:padding="24dp">

                    <TextView
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:text="RESULT"
                        android:textAppearance="?attr/textAppearanceLabelLarge"
                        android:textColor="?attr/colorOnPrimaryContainer"
                        android:alpha="0.7"/>

                    <TextView
                        android:id="@+id/result"
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:text="--"
                        android:layout_marginTop="8dp"
                        android:textAppearance="?attr/textAppearanceHeadlineLarge"
                        android:textColor="?attr/colorOnPrimaryContainer"
                        android:textStyle="bold"/>

                </LinearLayout>

            </com.google.android.material.card.MaterialCardView>

        </LinearLayout>

    </androidx.core.widget.NestedScrollView>

</androidx.coordinatorlayout.widget.CoordinatorLayout>
```

## OUTPUT:
<img width="1320" height="1012" alt="Screenshot 2026-09-08 105037" src="https://github.com/user-attachments/assets/ba7c8ef5-7f3b-4da3-8c33-eb91561814a6" />

## RESULT:
Thus the simple Addition Application using android studio was successfully created.
















