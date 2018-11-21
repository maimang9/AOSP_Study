# AOSP_Study
Android TV emulator

1.运行在aosp android 7.1.1_r1中；

2.clone 数据后，放在\aosp\device\unisoc；

3.编译执行如下命令：
    source build/envsetup.sh
    lunch atv_arm-eng
    make -j4
    
4.启动模拟器
    emulator -verbose -show-kernel -gpu off -no-boot-anim
    
    
emulator现象：
 server 不停重启。
 
解决方法：
 Z:\Android_Source\aosp\device\generic\goldfish
 中的camera 和 vndk文件夹的Android.mk包含如下语句，可见，针对我们新添加的device，build系统没有执行对应的command。
 
 ifneq ($(filter generic_x86 generic_x86_64 generic generic_arm64 generic_mips generic_mips64, $(TARGET_DEVICE)),)
