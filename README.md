亿连方控介绍：
http://www.carbit.com.cn/
http://z.jd.com/project/details/45183.html

一、蓝牙安装以及配对
1、更新下软件包
sudo apt-get update
2、安装蓝牙程序
sudo apt-get install mpc bluez bluez-firmware bluez-hcidump
3、重启系统
sudo reboot
4、配对蓝牙设备
执行以下命令开始配置蓝牙
sudo bluetoothctl
打开代理
agent on
设置默认代理
default-agent
打开蓝牙扫描
scan on
稍等一会，直到搜索到
XX:XX:XX:XX:XX:XX Ylfk
Ylfk前边的地址即是方控的物理地址，复制该地址以进行配对并替换以下的XX:XX:XX:XX:XX:XX
执行以下命令和方控配对
pair XX:XX:XX:XX:XX:XX
把方控添加到信任设备，这样以后系统会自动连接方控
trust XX:XX:XX:XX:XX:XX
连接方控
connect XX:XX:XX:XX:XX:XX
退出就可以了
quit
这样以后蓝牙就会在开机后自动连接

二、播放控制程序使用教程
git clone https://github.com/fishtest/ylfk --depth=1
cd ylfk
执行
sudo ./ylfk XX:XX:XX:XX:XX:XX（把XX替换为你方控的蓝牙地址）
即可
若想开机自动运行则需
sudo nano /etc/rc.local
在exit 0;之前添加
/home/pi/ylfk/ylfk XX:XX:XX:XX:XX:XX &
请根据实际情况修改yflk程序的地址以及蓝牙设备地址