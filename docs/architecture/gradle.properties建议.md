# gradle.properties 建议

## 一、目标

统一 Gradle 构建参数，提高 Android 多模块工程的稳定性和构建体验。

## 二、建议内容

```properties
org.gradle.jvmargs=-Xmx4g -Dfile.encoding=UTF-8
android.useAndroidX=true
kotlin.code.style=official
org.gradle.parallel=true
org.gradle.caching=true
```

## 三、可选项

如果后期模块增多，可以再视情况补充：

- 配置缓存
- 增量编译优化
- Kotlin daemon 参数

## 四、原则

- 先保持简单稳定
- 构建性能优化放在工程可编译之后再逐步加
