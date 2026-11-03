# Homework 6 — My First Compose App

## Task 3: Colour and Spacing
Colour used: Color.LightGray
Padding kept: [ISI: 8.dp / 24.dp / 48.dp]
What changed / what stayed the same: With 8 dp, the texts and the bicycle picture sit very close to the screen edge, so the content area is wide. With 48 dp, everything moves inward and the content area becomes narrower. The background colour, the order of the elements, and the text size stay the same. This matches the yellow-striped margin in Figure 13: padding is the empty space between the edge of the Column and its content.

## Task 4: Build Error
First error message:
[ISI: salin teks error pertama dari Build Output, kira-kira "Invalid file name: must contain only lowercase a-z, 0-9, or underscore"]

Cause: Android resource file names may contain only lowercase letters, digits, and underscores. "My-Picture.png" has capital letters (M, P) and a hyphen, so the build tool rejects it.
Why other errors appear: Because the file was rejected, Android did not generate the ID R.drawable.my_picture. The code that still uses R.drawable.my_picture then fails with "Unresolved reference", so these errors are only a consequence of the first one.
Fix: I renamed the file back to my_picture.png, reloaded the project from disk, and rebuilt it until the build was successful.

## Task 5: Explore the Project
(a) MainActivity: path app/src/main/java/com/example/myfirstcomposeapp/MainActivity.kt — This file contains the MainActivity class, the entry point of the app, which calls setContent to show the Compose screen.
(b) Gradle file: path app/build.gradle.kts — This file configures the app module, for example the SDK versions, application ID, and the libraries it depends on.
(c) Launcher image line: painter = painterResource(id = R.drawable.ic_launcher_foreground), inside Image in MyFirstScreen (MainActivity.kt) — This line loads the launcher icon from the drawable resources and gives it to Image to display.

## Task 6: Preview vs Run
I changed one text in MyFirstScreen and refreshed the Preview without pressing Run. The Preview showed the new text, but the app on the emulator still showed the old text. Preview only renders the composable inside Android Studio, while the emulator runs the app that was installed earlier. To make the change appear on the device, I have to press Run, so the project is built again and the new version is installed and started on the device.

## Task 7: Views vs Compose
1. In the Views approach (imperative), the layout is written in XML, and in code I give step-by-step commands, such as finding a TextView and calling a function to change its text. In Compose (declarative), I describe what the screen should look like. My MyFirstScreen function says: a Column that contains two Text and one Image, with padding. When the data changes, Compose redraws the screen from this description, and I do not have to find and update each view myself.
2.

| Composable | Package | Library layer |
|---|---|---|
| Column | androidx.compose.foundation.layout | Foundation |
| Text | androidx.compose.material3 | Material |
| Image | androidx.compose.foundation | Foundation |
