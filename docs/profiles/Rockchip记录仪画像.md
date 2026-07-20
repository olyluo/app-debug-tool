# Rockchip 记录仪画像

结合当前已知设备信息，首批适配建议：

优先连接方式：

1. ADB
2. RNDIS 网络
3. 串口

建议探测路径：

- /userdata/product.ini
- /userdata/product_backup.ini
- /userdata/sn.txt
- /userdata/*.db
- /tmp/*.log
- /oem/home/lib/
- /oem/home/bin/

建议提取字段：

- terminalid
- licenseplateno
- mainserveaddr1/2/3
- mainserveport1/2/3
- registerid1/2/3
- avwhitelist
- tparam*
- serialport.*

已知扩展方向：

- JT808 平台配置
- 白名单
- 视频能力
- AI 报警策略
