
* 一、打开电池数据的获取以及重置 
  * adb shell dumpsys batterystats --enable full-wake-history
  * adb shell dumpsys batterystats --reset

* 二、导入电量使用详细报告 
  * adb bugreport > bugreport.txt

* 三、关闭电池全量记录唤醒 
  * adb shell dumpsys batterystats --disable full-wake-history
