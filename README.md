# NodeMediaDevice


## RasipPublisher
树莓派RTMP直播发布器，使用CSI接口摄像头模组，OMX硬件编码为H.264视频流推送到RTMP服务器。
![img](https://dn-linuxcn.qbox.me/data/attachment/album/201408/21/130426pxvuxrqtnpppxx17.jpg)

### 打开/boot/config.txt,开启mmal摄像头组件.
```
gpu_mem=128
start_file=start_x.elf
fixup_file=fixup_x.dat
```
### 开始推流
```
raspipublisher -w 1280 -h 720 -b 1000000 -t 0 -vf -hf -o rtmp://192.168.0.10/live/s
```
参数设置可参考RaspiVid

