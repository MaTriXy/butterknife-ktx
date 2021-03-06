butterknife-ktx
===============
**ButterKnife using Kotlin extension functions instead of Java Reflection.**

---

*Kotlin extension bridge library for [ButterKnife](https://github.com/JakeWharton/butterknife) (proof-of-concept)*

Read more here: [Kotlin extension function generation 🚀…](https://medium.com/@blipinsk/kotlin-extension-methods-generation-15b5e6499dc8)

Usage
=====
*For a working usage of this library see the `sample/` module.*

 1. Add to your app's `build.gradle`

     ```groovy
     sourceSets {
         main.java.srcDirs += 'src/main/kotlin'
         debug.java.srcDirs += 'src/debug/kotlin'
         release.java.srcDirs += 'src/release/kotlin'
         test.java.srcDirs += 'src/test/kotlin'

         // For kapt stubs
         main.java.srcDirs += [file("$buildDir/generated/source/kapt/main")]
         debug.java.srcDirs += [file("$buildDir/generated/source/kapt/debug")]
         release.java.srcDirs += [file("$buildDir/generated/source/kapt/release")]
         test.java.srcDirs += [file("$buildDir/generated/source/kapt/test")]

         // For kotlin code gen during kapt
         main.java.srcDirs += [file("$buildDir/generated/source/kaptKotlin/main")]
         debug.java.srcDirs += [file("$buildDir/generated/source/kaptKotlin/debug")]
         release.java.srcDirs += [file("$buildDir/generated/source/kaptKotlin/release")]
         test.java.srcDirs += [file("$buildDir/generated/source/kaptKotlin/test")]
     }
     ```

 2. Change:

    ```java
    ButterKnife.bind(target)
    ```

    to (add `Ktx` after `ButterKnife`):

    ```java
    ButterKnifeKtx.bind(target)
    ```

 3. Enjoy **Reflection-free** `ButterKnife`

Including In Your Project
-------------------------
Add in your `build.gradle`:
```xml
repositories {
    maven { url 'https://dl.bintray.com/blipinsk/maven/' }
}

dependencies {
    kapt "com.bartoszlipinski:butterknife-ktx-compiler:0.2.0"
    implementation "com.bartoszlipinski:butterknife-ktx:0.2.0"
}
```

Developed by
============
 * Bartosz Lipiński

License
=======

    Copyright 2018 Bartosz Lipiński
    
    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.