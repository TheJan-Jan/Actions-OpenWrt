# 云编译OpenWRT

## 自用版本说明：（x86和N1盒子）
### 1.支持ipv6；
### 2.DDNS可以动态绑定域名；
### 3.docker容器，尝试部署docker镜像；
### 4.本固件容量只有200兆。

## N1 OpenWrt如何使用
### 默认自定义防火墙:
`iptables -t nat -I POSTROUTING -o eth0 -j MASQUERADE`
### 用户名和密码
#### * User: root
#### * Password: password
#### * IP: 192.168.0.10
### N1 U盘写入刷emmc
```
cd      /root
./install-to-emmc.sh
```
如果一直卡在fdisk失败那里的解决办法：一是再多试几次，如果还不成功，则需要手动清空分区表然后再重试，具体命令:
```
  dd   if=/dev/zero   of=/dev/mmcblk2  bs=512  count=1  &&  sync
```

#### 升级降级方法统一为：
把 update-amlogic-openwrt.sh 及 img镜像上传至  /mnt/mmcblk2p4
```
cd    /mnt/mmcblk2p4
chmod   755  update-amlogic-openwrt.sh
./update-amlogic-openwrt.sh    xxxxx.img
```
