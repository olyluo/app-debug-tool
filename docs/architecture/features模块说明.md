# features 模块说明

## 一、职责

features 是最终面对用户的功能模块层。

它不关心底层是 ADB、串口、SSH 还是 RNDIS，只关心“用户要完成什么任务”。

## 二、建议 feature 列表

- feature-device-discovery
- feature-terminal
- feature-file-browser
- feature-config-center
- feature-log-center
- feature-jt808-center
- feature-diagnostics
- feature-script-runner
- feature-video-center

## 三、按任务而不是按协议设计

不要做成：

- ADB 页面
- 串口页面
- SSH 页面

而应该做成：

- 设备发现
- 终端
- 配置
- 日志
- JT808
- 视频
- 诊断

这样无论底层接入方式是什么，用户看到的体验都一致。

## 四、首期优先功能

建议先做：

1. 设备发现页
2. 终端页
3. 配置中心
4. 日志中心
5. 诊断中心

然后再做：

- JT808 中心
- 视频中心
- 动作脚本中心
