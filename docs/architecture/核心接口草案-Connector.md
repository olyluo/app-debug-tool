# 核心接口草案：Connector

## 一、目标

Connector 是所有接入方式的统一抽象，屏蔽 ADB、串口、RNDIS、SSH、HTTP、Raw USB 的差异。

## 二、职责

- 探测连接能力
- 建立连接
- 断开连接
- 暴露统一会话能力
- 输出连接信息
- 在能力范围内支持终端、文件、诊断、视频传输

## 三、建议接口

```kotlin
interface Connector {
    val id: String
    val displayName: String
    val type: ConnectorType

    suspend fun probe(target: DeviceTarget): ProbeResult
    suspend fun connect(target: DeviceTarget): ConnectorSession
    suspend fun disconnect(sessionId: String)
}
```

## 四、会话接口建议

```kotlin
interface ConnectorSession {
    val sessionId: String
    val connectionInfo: ConnectionInfo
    val capabilities: Set<Capability>

    suspend fun openTerminal(): TerminalSession?
    suspend fun listFiles(path: String): List<RemoteFile>
    suspend fun readFile(path: String): ByteArray
    suspend fun writeFile(path: String, data: ByteArray): WriteResult
    suspend fun runCommand(command: String): CommandResult
    suspend fun collectDiagnostics(): DiagnosticBundle
}
```

## 五、设计原则

- Connector 只关心接入，不关心设备画像
- Connector 输出统一能力，不向上暴露底层复杂细节
- Feature 层尽量依赖 ConnectorSession 抽象，而不是依赖具体实现
