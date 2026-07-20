# 通用 Linux 设备画像

适用范围：

- 底层为 Linux
- 支持 shell / 文件访问 / 配置导出中的一种或多种

建议探测路径：

- /userdata
- /oem
- /home
- /tmp
- /etc
- /var/log

建议探测文件：

- *.ini
- *.cfg
- *.db
- *.log
- sn.txt
- version 信息文件

建议健康检查：

- 存储是否可读
- 业务进程是否存在
- 网络是否联通
- 配置文件是否完整
