# Android Edge-to-Edge UI 🚀

Enable a full-screen immersive experience in **Java** using **AndroidX Activity**, following Google’s modern edge-to-edge UI guidelines.

---

## 📦 Dependencies

# Add these dependencies to your `build.gradle` (app-level):

```gradle
implementation "androidx.activity:activity:1.12.0-alpha09"
implementation "org.jetbrains.kotlin:kotlin-stdlib:2.2.20"
implementation "androidx.core:core:1.17.0" // optional for Material 3 BottomSheet
```

If you get any kind of duplicate library error, uncheck that library. (kotlin-stdlib-2.2.0 or Activity-1.12.0-alpha09)

Error example:
```Markdown
a.a.a.By: Duplicate files from two libraries detected 
File1: /mnt/expand/*/user/0/pro.sketchware/files/libs/libs/kotlin-stdlib-2.2.0/classes.jar 
File2: /storage/emulated/0/.sketchware/libs/local_libs/kotlin-stdlib-v2.2.20/classes.jar 
Archive path: kotlin/kotlin.kotlin_builtins
 at a.a.a.ProjectBuilder.buildApk(ProjectBuilder.java:645)
 at com.besome.sketch.design.DesignActivity$BuildTask.doInBackground(DesignActivity.java:1179)
 at com.besome.sketch.design.DesignActivity$BuildTask.$r8$lambda$0AmVsWQJ9oulgeP8eMAUbl0tGkA(Unknown Source:0)
 at com.besome.sketch.design.DesignActivity$BuildTask$$ExternalSyntheticLambda1.run(D8$$SyntheticClass:0)
 at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1167)
 at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:641)
 at java.lang.Thread.run(Thread.java:919)
```

# 💡 Google recommends:
Use the latest stable androidx.activity and androidx.core versions
Avoid deprecated flags like SYSTEM_UI_FLAG_LAYOUT_FULLSCREEN
Test layouts in both light and dark modes

---

# 📥 How to Enable Edge-to-Edge in Your Project
> Follow these simple steps:
1. Open Activity: Open the activity where you want edge-to-edge UI.

2. Add EdgeToEdge: Call EdgeToEdge.enable(this); immediately after super.onCreate(_savedInstanceState);
3. Set ContentView: Set your layout with setContentView(R.layout.main);
4. Initialize Logic: Run any initialization logic after this.

# Example:
```java
@Override
protected void onCreate(Bundle _savedInstanceState) {
    super.onCreate(_savedInstanceState);
    EdgeToEdge.enable(this);
    setContentView(R.layout.main);
    initialize(_savedInstanceState);
    initializeLogic();
}
```

---

# 🧭 Handling Top App Bar
If your layout uses a Top App Bar, apply insets so the toolbar does not overlap the status bar.

> Steps:
> 1. Call ViewCompat.setOnApplyWindowInsetsListener on your App Bar view.
> 2. Change _app_bar to your actual _app_bar layout ID. For ViewBinding user binding.AppBar
> 3. Get the status bar insets.
> 4. Apply top padding to the App Bar.

Example:
```java
ViewCompat.setOnApplyWindowInsetsListener(_app_bar, (v, insets) -> {
    Insets statusBars = insets.getInsets(WindowInsetsCompat.Type.statusBars());
    v.setPadding(0, statusBars.top, 0, 0);
    return insets;
});
```

# Imports:
```java
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;
import androidx.core.graphics.Insets;
```

---

# 🧱 Without Top App Bar

If you don’t use a Top App Bar, apply insets to your root layout instead.

> 📝 Change _root to your actual root layout ID. For ViewBinding user binding.{Layout binding Id}


```java
ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id._root), (v, insets) -> {
    Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
    v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
    return insets;
});
```

# Imports:
```java
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;
import androidx.core.graphics.Insets;
```

---

# 🎨 Update Theme (Optional)

For full edge-to-edge experience, make status and navigation bars transparent:
```xml
<item name="android:statusBarColor">@android:color/transparent</item>
<item name="android:navigationBarColor">@android:color/transparent</item>
<item name="android:windowLightStatusBar">true</item>
<item name="android:windowLightNavigationBar">true</item>
```

---

# 🧠 Google Recommended Best Practices
Use EdgeToEdge API (API 21+)
Handle WindowInsetsCompat for consistent padding
Test with gesture navigation enabled
Combine with Material 3 components for dynamic colors
Check light and dark themes for contrast

---

# ✅ Result
Your app now:
Draws content behind the status and navigation bars
Adapts automatically to gestures and themes
Looks modern and clean with Edge-to-Edge UI.
Check video: https://t.me/fastersoftwaredeveloper/465

---
