#adb
###adb  devices
显示当前模拟器设备列表


###adb -s <sericalNum> <cmd>
指定设备 运行命令

###adb  install d:\00\xx.apk
安装apk

###adb push <local> <remote>
本地文件推送

###adb pull <remote> <local>
文件拉取到本地

###adb shell 
进入Linux Shell




#Android

###android list targets
查询当前可用Android列表


### android create avd -n <name> -t <targetID> 
创建虚拟机（targetID：android 版本 api数字）

### android delete -n <name>
删除虚拟机

#emulator

