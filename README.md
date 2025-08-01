# 👁️ PrivScan SDK for Android
**PrivScan** is a lightweight Android SDK for identifying privacy-related GUI components on-screen.  
It provides a floating button to help users analyze the current interface and access relevant privacy policy information in real time.

---

## 🚀 Integration Guide

You can integrate the SDK into your Android project in one of two ways:

### Option 1: Using Git Submodule

```bash
git submodule add https://github.com/Cpp4App/PrivScan.git  sdk/PrivScan
```

Then add the following to your **settings.gradle.kts**:

```bash
include(":PrivScan")
project(":PrivScan").projectDir = file("sdk/PrivScan")
```

And in your app module's **build.gradle.kts**:

```bash
dependencies {
    implementation(project(":PrivScan"))
}
```

### Option 2: Manual Copy
You may also manually copy the **PrivScan/** folder into your project and configure it the same way in **settings.gradle.kts**.

## 🧩 Usage

Initialize the SDK in your Application class:

```bash
import android.app.Application;
import android.graphics.Color;
import com.example.PrivScan.ButtonInjector;

public class MyApplication extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        
        // Initialize the privacy button injector for all activities
        ButtonInjector.init(this, (button, activity) -> {
          
            // Set the initial position of the button on the screen (x, y in pixels)
            button.setPosition(900f, 1950f);  
            
            // Set the size (diameter) of the button in pixels
            button.setSize(100f);  
            
            // Set the button\'s background image (e.g., icon or custom style)
            button.setImage(com.example.SeePrivacyButton.R.drawable.button_bg));  
            
            // Set the background color of the button (used when no image is set)
            button.setColor(Color.parseColor("#8800FF")); 
            
             // Set the official privacy policy URL of your app
            button.setPolicyUrl("https://your-privacy-policy-url.html");  
        });
    }
}
```

Also, register your custom Application class in **AndroidManifest.xml**:

```bash
<application
    android:name=".MyApplication"
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    ... >
</application>
```