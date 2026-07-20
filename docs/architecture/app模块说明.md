# app 模块说明

## 一、职责

app 模块是 Android 应用入口层，负责：

- Application 初始化
- Compose 主题与全局样式
- 页面导航
- 全局依赖注入入口
- 承载统一工作台宿主页面

## 二、建议内容

- `AppApplication`
- `MainActivity`
- `AppNavHost`
- `Theme`
- `AppStartup`

## 三、边界

app 模块尽量不直接写协议逻辑，也不直接处理设备细节。

它主要负责：

- 把不同 feature 页面组织起来
- 组装 connector / profile / use case
- 提供全局错误提示与会话状态管理

## 四、后期扩展

后续如果增加：

- 登录系统
- 云同步
- 团队协作
- 项目导出

都应优先从 app 模块装配，而不是侵入底层模块。
