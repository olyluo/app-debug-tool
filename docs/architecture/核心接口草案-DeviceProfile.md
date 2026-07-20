# 核心接口草案：DeviceProfile

## 一、目标

DeviceProfile 用来描述“某类设备被连接后，应该如何识别、读取、理解和操作”。

## 二、职责

- 匹配设备
- 提供关键路径
- 提供参数提取规则
- 提供健康检查规则
- 提供快捷动作
- 提供推荐连接方式

## 三、建议接口

```kotlin
interface DeviceProfile {
    val profileId: String
    val displayName: String

    fun match(fingerprint: DeviceFingerprint): MatchResult
    fun recommendedConnectors(): List<ConnectorType>
    fun configLocations(): List<String>
    fun logLocations(): List<String>
    fun databaseLocations(): List<String>
    fun extractors(): List<ConfigExtractor>
    fun healthChecks(): List<HealthCheck>
    fun quickActions(): List<DeviceAction>
}
```

## 四、设计原则

- Profile 不直接建立连接
- Profile 不直接依赖 UI
- Profile 负责设备语义，不负责协议实现
- 同一设备可叠加多个 Profile 能力，例如 Linux + JT808 + 厂商定制

## 五、推荐分层

- GenericLinuxProfile
- GenericJt808Profile
- VendorSpecificProfile
