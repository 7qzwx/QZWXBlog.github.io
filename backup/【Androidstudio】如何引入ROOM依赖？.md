# 引入ROOM依赖

> _经错连续四五天的报错，查询各种资料，发现最终解决方法，记下此文章以记录保存。_

**首先，使用KSP而不是KAPT，因为kept跟java8以后版本不兼容（也许）。**

- 在项目级根目录build.gradle.kts代码中添加下面代码：

```kotlin
 id("com.google.devtools.ksp") version "1.9.0-1.0.13" apply false
```

实例：【注意需要修改version版本，请根据你的kotlin版本对应修改】

```kotlin
plugins {
    alias(libs.plugins.android.application) apply false
    alias(libs.plugins.jetbrains.kotlin.android) apply false
    id("com.google.devtools.ksp") version "1.9.0-1.0.13" apply false   //添加此代码，注意version版本需要根据你的kotlin版本号修改，我这个意思是kotlin版本为1.9.0，ksp版本为1.0.13，具体更改的版本号请查询github的ksp仓库：https://github.com/google/ksp/releases?page=4
}
```

- 在模块级build.gradle.kts代码中添加下面代码：

```kotlin
id("com.google.devtools.ksp")
```

实例：

```kotlin
plugins {
    id("com.android.library") // 库模块插件
    kotlin("android")
    id("com.google.devtools.ksp")//添加此代码
}
```

- 引入ROOM依赖：

```kotlin
val room_version = "2.6.1"

implementation("androidx.room:room-runtime:$room_version")
annotationProcessor("androidx.room:room-compiler:$room_version")

// To use Kotlin Symbol Processing (KSP)
ksp("androidx.room:room-compiler:$room_version")

// optional - Kotlin Extensions and Coroutines support for Room
implementation("androidx.room:room-ktx:$room_version")

// optional - RxJava2 support for Room
implementation("androidx.room:room-rxjava2:$room_version")

// optional - RxJava3 support for Room
implementation("androidx.room:room-rxjava3:$room_version")

// optional - Guava support for Room, including Optional and ListenableFuture
implementation("androidx.room:room-guava:$room_version")

// optional - Test helpers
testImplementation("androidx.room:room-testing:$room_version")

// optional - Paging 3 Integration
implementation("androidx.room:room-paging:$room_version")
```

实例：

```kotlin
dependencies {

        val room_version = "2.6.1"

        implementation("androidx.room:room-runtime:$room_version")
        annotationProcessor("androidx.room:room-compiler:$room_version")

        // To use Kotlin Symbol Processing (KSP)
        ksp("androidx.room:room-compiler:$room_version")

        // optional - Kotlin Extensions and Coroutines support for Room
        implementation("androidx.room:room-ktx:$room_version")

        // optional - RxJava2 support for Room
        implementation("androidx.room:room-rxjava2:$room_version")

        // optional - RxJava3 support for Room
        implementation("androidx.room:room-rxjava3:$room_version")

        // optional - Guava support for Room, including Optional and ListenableFuture
        implementation("androidx.room:room-guava:$room_version")

        // optional - Test helpers
        testImplementation("androidx.room:room-testing:$room_version")

        // optional - Paging 3 Integration
        implementation("androidx.room:room-paging:$room_version")



    implementation ("androidx.activity:activity-ktx:1.3.1")
    implementation ("androidx.compose.material:material-icons-extended")
    // Google Material Components
    implementation("com.google.android.material:material:1.9.0")
    }
```

完成！