# core 模块说明

## 一、职责

core 是平台能力内核，负责沉淀所有与具体 UI 无关、与具体设备型号弱相关的基础能力。

## 二、建议子模块

```text
core/common
core/usb
core/network
core/shell
core/file
core/terminal
core/parser
core/protocol
core/device
```

## 三、各子模块职责

### core/common
放通用模型、错误定义、结果类型、日志接口、时间工具。

### core/usb
负责：

- USB 设备枚举
- interface/class 解析
- USB 权限管理
- 原始 USB descriptor 抽取

### core/network
负责：

- IP 探测
- 常见端口扫描
- HTTP/TCP 连通性检查
- RNDIS 设备网络识别辅助

### core/shell
定义统一命令执行抽象，屏蔽 ADB / SSH / 本地 shell 差异。

### core/file
定义统一文件访问抽象，支持读、列目录、导出。

### core/terminal
定义统一终端会话模型，供 ADB、串口、SSH 共用。

### core/parser
负责解析：

- ini
- cfg
- sqlite
- log
- jt808 参数映射

### core/protocol
放协议层共性定义，细分：

- adb
- serial
- ssh
- rndis
- jt808
- rawusb

### core/device
负责：

- 设备指纹
- 能力模型
- 画像匹配
- 设备摘要信息

## 四、设计原则

- core 只提供能力，不感知页面
- core 尽量保持可测试
- core 中的能力要可被多个连接器和多个 feature 复用
