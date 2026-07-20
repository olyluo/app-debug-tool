# settings.gradle.kts 建议

## 一、目标

定义首期多模块工程的 include 结构，并固定仓库源和根项目名。

## 二、建议内容

```kotlin
pluginManagement {
    repositories {
        google()
        mavenCentral()
        gradlePluginPortal()
    }
}

dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        mavenCentral()
    }
}

rootProject.name = "app-debug-tool"

include(":app")

include(":core:common")
include(":core:usb")
include(":core:network")
include(":core:shell")
include(":core:file")
include(":core:terminal")
include(":core:parser")
include(":core:device")

include(":connectors:connector-adb")
include(":connectors:connector-serial")
include(":connectors:connector-rndis")

include(":profiles:profile-generic-linux")
include(":profiles:profile-jt808-ai-recorder")

include(":features:feature-device-discovery")
include(":features:feature-terminal")
include(":features:feature-config-center")
include(":features:feature-log-center")
include(":features:feature-diagnostics")
```

## 三、原则

- 首期只 include 必要模块
- 后续视频与高级协议模块按阶段加入
- 避免一开始引入过多空模块
