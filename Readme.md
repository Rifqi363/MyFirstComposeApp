# Homework 6 — My First Compose App

## Task 3: Colour and Spacing

Colour used: `Color.White`

Padding kept: `48.dp`

What changed / what stayed the same: With 8 dp padding, the texts and image are close to the edge of the screen. With 48 dp padding, there is more empty space around them. The texts, image, order, and colour stay the same. Only the space around the content changes. This is similar to the yellow-striped margin in Module M06, Figure 13.

## Task 4: Build Error

First error message:

`'M' is not a valid file-based resource name character: File-based resource names must contain only lowercase a-z, 0-9, or underscore`

Cause: Android resource file names can only use lowercase letters, numbers, and underscores. The name `My-Picture.png` has capital letters and a hyphen, so the build fails.

Why other errors appear: Android cannot recognize the image resource correctly because of the wrong file name. The code that uses `R.drawable.my_picture` cannot find the resource, so other errors like `Unresolved reference` can appear afterward.

Fix: I renamed the file back to `my_picture.png`, synced Gradle, and ran the app again. Now it builds and runs normally.

## Task 5: Explore the Project

(a) MainActivity: Path `app/src/main/java/com/example/myfirstcomposeapp/MainActivity.kt` — this file contains the `MainActivity` class and my `MyFirstScreen` function.

(b) Gradle file: Path `app/build.gradle.kts` — this file contains the app module settings, including dependencies and SDK configuration.

(c) Launcher image line: `painter = painterResource(id = R.drawable.ic_launcher_foreground)` (line 41 in `MyFirstScreen` in `MainActivity.kt`) — this line displays the default launcher icon.

## Task 6: Preview vs Run

I changed a text in `MyFirstScreen` and refreshed the Preview. The new text appeared in the Preview, but the emulator still showed the old text. This happened because Preview only shows the screen inside Android Studio and does not automatically update the installed app. After I pressed Run, the emulator showed the new text.

## Task 7: Views vs Compose

1. With Views, I change the screen step by step in code, for example, by changing the text of a `TextView`. With Compose, I describe what I want to display on the screen. In my `MyFirstScreen`, I put two `Text` composables and one `Image` inside a `Column`. Compose displays these elements and updates the screen when the relevant data changes.

2. Composable packages and library layers:

| Composable | Package | Library layer |
|---|---|---|
| Column | `androidx.compose.foundation.layout` | Foundation |
| Text | `androidx.compose.material3` | Material 3 |
| Image | `androidx.compose.foundation` | Foundation |