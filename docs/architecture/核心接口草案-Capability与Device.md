# 核心接口草案：Capability 与 Device

## 一、目标

把“设备是什么”和“设备能做什么”拆开建模，便于后续支持更多型号。

## 二、Capability 建议

Capability 表示设备当前可用能力，而不是设备宣传能力。

建议枚举：

```kotlin
enum class Capability {
    ADB,
    SERIAL,
    RNDIS,
    SSH,
    HTTP,
    FILE_READ,
    FILE_WRITE,
    SHELL,
    LOG_READ,
    CONFIG_READ,
    CONFIG_WRITE,
    JT808,
    VIDEO_PREVIEW,
    VIDEO_EXPORT,
    DIAGNOSTIC_EXPORT
}
```

## 三、Device 建议

```kotlin
data class Device(
    val id: String,
    val displayName: String,
    val fingerprint: DeviceFingerprint,
    val endpoints: List<DeviceEndpoint>,
    val capabilities: Set<Capability>,
    val matchedProfiles: List<String>
)
```

## 四、DeviceFingerprint 建议

```kotlin
data class DeviceFingerprint(
    val vendorId: Int?,
    val productId: Int?,
    val usbInterfaces: List<UsbInterfaceInfo>,
    val productName: String?,
    val manufacturerName: String?,
    val serialNumber: String?,
    val networkHints: List<String>
)
```

## 五、设计原则

- Device 是运行时对象
- Capability 是动态能力，不写死在型号里
- Profile 负责匹配 fingerprint 并补充解释能力
