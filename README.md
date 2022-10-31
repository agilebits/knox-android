# Knox Android Library

The library package of the Knox design system for Android apps.  After installing the library, Android apps can use tokens from the Knox design system when implementing user interface specifications.

## Introduction

All resources are referred to as tokens in the Knox design system, which include the following types:
- `color`
- `dimen`
- `integer`

Tokens are prefixed with `knox_` to avoid conflicts with other resource names in the app as well as other libraries used by the app.  There are two types of tokens; alias and base.

Alias tokens are named semantically.  The alias token name describes the use in the user interface.  All alias token values are a base token value.

Base tokens are named by value.  The base token name describes the color, size, spacing, weight, etc. of the resource value.  The number suffix of base tokens corresponds to the quantity, opacity, or lightness of the value.  The larger the number suffix of size, spacing, weight, etc. base tokens, the larger the quantity of the value.  The larger the number suffix of black and white color base tokens, the larger the opacity of the color value.  The larger the number suffix of other color base tokens, the smaller the lightness of the color value.

Both alias and base tokens are publicly accessible.  Alias tokens should be used in apps.  Base tokens should only be used when no applicable alias token is available.

## Installation

Follow the steps below to use the library in an Android app.  Steps 1, 2, and 3 are required to build an app using library token references.  Step 4 is required only if Android Studio is used for code autocompletion and to avoid unresolved reference errors.

1. Add the following snippet to the project-level `build.gradle` file in the `allprojects`/`repositories` block.

```groovy
maven {
    url = uri("https://maven.pkg.github.com/agilebits/knox-android")
    credentials {
        password = "PASSWORD"
        username = "agilebits"
    }
}
```

> Replace the `PASSWORD` value with the personal access token of the user.

2. Add the following statement to the app-level `build.gradle` file in the `dependencies` block.

```groovy
implementation libs.onepassword.knox.tokens
```

3. Add the following statement to the `libraries.versions.toml` file in the `libraries` block.

```toml
onepassword-knox-tokens = { group = "com.onepassword.knox", name = "tokens", version = "VERSION" }
```

> Replace the `VERSION` value with the version of the library.

4. Run the ***Sync Project with Gradle Files*** action (e.g. ***File*** > ***Sync Project with Gradle Files*** in Android Studio)

## Implementation

The resources in the Knox Android library can be used in both Kotlin and XML files to reference design system tokens.

### Kotlin

All library token resources can be used in Kotlin files.  As an example, a dimension resource can be referenced with the `com.onepassword.knox.tokens.` prefix as shown in the snippet below.

```kotlin
com.onepassword.knox.tokens.R.dimen.knox_border_radius_medium
```

The fully-qualified prefix can be removed by adding the following import alias statement.

```kotlin
import com.onepassword.knox.tokens.R as knox
```

With the import alias above added to the file, the same dimension resource can be referenced with the snippet below.

```kotlin
knox.dimen.knox_border_radius_medium
```

### XML

All library token resources can be used in XML files.  As an example, a color resource can be referenced as shown in the snippet below.

```xml
app:tint="@color/knox_color_icon_neutral_default"
```

The same color resource can be referenced in `styles.xml` files as shown in the snippet below.

```xml
<item name="tint">@color/knox_color_icon_neutral_default</item>
```
