# connectors 模块说明

## 一、职责

connectors 负责把“接入协议”封装成可插拔实现。

目标是：

- 上层不关心底层协议差异
- 新增接入方式时，不影响现有 feature
- 不同设备只需切换或组合 connector

## 二、建议子模块

```text
connectors/connector-adb
connectors/connector-serial
connectors/connector-ssh
connectors/connector-rndis
connectors/connector-http
connectors/connector-rawusb
```

## 三、连接器职责边界

每个 connector 负责：

- 探测是否可用
- 建立连接
- 暴露统一会话能力
- 提供连接信息
- 在能力范围内支持 shell / file / diagnostics

不负责：

- 写具体页面
- 写设备型号判断
- 写具体业务字段抽取

## 四、推荐能力输出

- shellAvailable
- fileReadAvailable
- fileWriteAvailable
- logReadAvailable
- networkInfoAvailable
- videoTransportAvailable

## 五、当前优先级

首批优先实现：

1. connector-adb
2. connector-rndis
3. connector-serial

后续补充：

4. connector-ssh
5. connector-http
6. connector-rawusb
