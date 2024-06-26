# Compose Multiplatform Mobile Extensions (CME)

[![compose-mp-version](https://img.shields.io/badge/compose--multiplatform-1.6.1-blue)](https://github.com/JetBrains/compose-multiplatform)
[![kotlin-version](https://img.shields.io/badge/kotlin-1.9.23-8A2BE2)](https://github.com/JetBrains/compose-jb)

![badge-iOS](https://img.shields.io/badge/Platform-iOS-lightgray)
![badge-Android](https://img.shields.io/badge/Platform-Android-brightgreen)

[![last-version](https://img.shields.io/badge/cme-0.0.1-e26e2b)](https://github.com/aagrishankov/Compose-Multiplatform-Mobile-Extensions)

# Preview
![preview](gitRes/2024-04-21%2011-23-18.gif)

# Gradle

#### Raw
```gradle
// build.gradle.kts
dependencies {
    commonMainApi("io.github.aagrishankov:cme-theme-status-bars:0.0.1")

    // or

    androidMainApi("io.github.aagrishankov:cme-theme-status-bars:0.0.1")
    iosMainApi("io.github.aagrishankov:cme-theme-status-bars:0.0.1")
}
```

#### Version Catalog
```toml
# libs.versions.toml
cme-status-bars = { module = "io.github.aagrishankov:cme-theme-status-bars", version = "0.0.1" }
```
```gradle
// build.gradle.kts
dependencies {
    commonMainApi(libs.cme.status.bars)

    // or

    androidMainApi(libs.cme.status.bars)
    iosMainApi(libs.cme.status.bars)
}
```

# Usage

### Theme System Bars

#### Setup Android

```kotlin
//androidMain
//ComponentActivity

override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)

    //...

    //replace default setContent to setContentThemeWithStatusBars
    setContentThemeWithStatusBars { App() }
}
```

---

#### Setup iOS

```kotlin
//iosMain
//main.kt

fun MainViewController(): UIViewController {

    //replace default ComposeUIViewController to StatusBarsProviderUIViewController
    return StatusBarsProviderUIViewController { App() }
}
```

---

#### How to change theme

commonMain:

```kotlin
//commonMain
//Composable Scope

var theme by LocalThemeStatusBars.current

theme = SystemThemeStatusBars.DARK
//or
theme = SystemThemeStatusBars.LIGHT

```


# Sample
An sample of a project using the library can be viewed here -> [sample](sample)


# License

```
Copyright (c) 2024 CME project and open source contributors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0
    
Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
