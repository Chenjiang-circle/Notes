# Linux命令学习

## 0. 重启网络服务

在Ubuntu中使用命令`service network restart`会报错：`Failed to restart network.service: Unit network.service not found.`，可以使用`service network-manager restart`重启网络服务。

## 1. 网络管理

### 1.1 ifconfig

ifconfig命令的英文全称是“*network interfaces configuring*”，即用于配置和显示Linux内核中网络接口的网络参数。用ifconfig命令配置的网卡信息，在网卡重启后机器重启后，配置就不存在。要想将上述的配置信息永远的存在电脑里，那就要修改网卡的配置文件了。

**语法格式：**`ifconfig [参数]`

**常用参数：**

| [参数]    | 含义                     |
| --------- | ------------------------ |
| add<地址> | 设置网络设备IPv6的IP地址 |
| del<地址> | 删除网络设备IPv6的IP地址 |
| down      | 关闭指定的网络设备       |
| up        | 启动指定的网络设备       |
| IP地址    | 指定网络设备的IP地址     |

使用ifconfig修改MAC地址：

```bash
ifconfig eth0 down # 首先禁用网卡
ifconfig eth0 hw ether 00:AA:BB:CC:DD:EE # 修改网卡的MAC地址
ifconfig eth0 up # 启用网卡
```

