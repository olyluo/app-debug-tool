# 根 build.gradle.kts 建议

## 一、目标

统一管理插件版本与全局构建行为，避免模块之间版本漂移。

## 二、建议内容

```kotlin
plugins {
    id("com.android.application") version "8.5.2" apply false
    id("com.android.library") version "8.5.2" apply false
    id("org.jetbrains.kotlin.android") version "2.0.21" apply false
    id("org.jetbrains.kotlin.jvm") version "2.0.21" apply false
    id("com.google.devtools.ksp") version "2.0.21-1.0.28" apply false
    id("com.google.dagger.hilt.android") version "2.52" apply false
}
```

## 三、建议补充

可在 `build-logic` 或 convention plugin 中继续统一：

- compileSdk
- minSdk
- targetSdk
- Kotlin 编译参数
- Compose 开关
- 测试配置

## 四、原则

- 根脚本只做全局版本管理
- 模块具体配置尽量下沉到 convention plugin 或模块脚本
