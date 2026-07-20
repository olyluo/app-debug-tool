# profiles 模块说明

## 一、职责

profiles 用来描述“某类设备连上之后应该怎么理解它”。

这层非常适合当前项目，因为你的设备很多，但本质相近：

- 都是 Linux 底层
- 都有 AI 模块
- 都可能带 JT808
- 都需要查看配置、日志、网络、视频、白名单等信息

## 二、画像主要内容

每个 profile 至少应定义：

- 匹配规则
- 推荐连接方式
- 关键路径
- 参数提取规则
- 健康检查
- 快捷动作
- 视频能力声明

## 三、建议画像层次

### 1. GenericLinuxProfile
适用于所有 Linux 设备。

### 2. GenericJt808Profile
适用于所有带 JT808 的设备。

### 3. Vendor/Family Profile
例如：

- RockchipDashcamProfile
- AiRecorderProfile
- DualSystemLinuxRecorderProfile

## 四、为什么要分层

这样后续新增一款设备时：

- 通用能力继承 GenericLinuxProfile
- JT808 能力继承 GenericJt808Profile
- 特殊路径和特殊字段只在厂商画像里补充

就不用从零开始写适配。
