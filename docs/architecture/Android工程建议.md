# Android 工程建议

## 一、推荐技术栈

- Kotlin
- Jetpack Compose
- AndroidX
- Coroutines + Flow
- ViewModel
- Hilt 或 Koin

## 二、为什么这样选

### Kotlin
适合做结构化、多模块项目，类型系统更稳，后期扩展更轻松。

### Compose
适合快速搭建工具型界面，设备页、终端页、日志页、配置页切换效率高。

### Coroutines + Flow
适合处理：

- USB 设备插拔事件
- 终端输出流
- 网络探测结果
- 设备能力状态变化

### ViewModel
适合把页面状态和连接状态隔离开。

## 三、页面组织建议

建议首期页面：

- 首页
- 设备发现页
- 设备详情页
- 终端页
- 配置中心页
- 日志中心页
- 诊断页

## 四、开发节奏建议

- 先把 USB 和 ADB 跑通
- 再把统一终端做通
- 再补配置中心和日志中心
- 最后再做视频与脚本能力
