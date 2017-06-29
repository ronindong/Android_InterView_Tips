## 一、BroadcastReceiver（广播）定义
  * 首先看下android api对BroadcastReceiver的定义：
  ```
  Android apps can send or receive broadcast messages from the Android system and other Android apps, similar to the publish-subscribe design pattern. These broadcasts are sent when an event of interest occurs. For example, the Android system sends broadcasts when various system events occur, such as when the system boots up or the device starts charging. Apps can also send custom broadcasts, for example, to notify other apps of something that they might be interested in (for example, some new data has been downloaded).
  ```
  * 从第一句话中可以看出，BroadcastReceiver（广播）是一种可以运用在应用程序之间传递信息。
  
## 二、BroadcastReceiver使用场景
  * （1）应用程序内部不同组件之间的通信，包括APP多进程之间的通信
  * （2）不同应用程序之间的消息通信
  
## 三、BroadcastReceiver类型
  * 一般广播（Normal Broadcast）：通过Context.sendBroadcast()发送;
  * 系统广播（System Broadcast）：通过Context.sendOrderedBroadcast()发送；
  * 本地广播（Local Broadcast）：只在APP内部之间传递的广播;通过support V4包中提供的LocalBroadcastManager来发送广播，其内部是通过Handler的来实现。
  
## 四、BroadcastReceiver注册方式
  * （1）静态注册：在AndroidManifest.xml文件中注册，该注册方式，注册完成后，会一直运行。
  * （2）动态注册：在Activity中通过调用`registerReceiver()/unregisterReceiver()`进行注册/解注册。跟随activity的生命周期。

## 五、BroadcastReceiver内部实现
  * 
  * 
  * 
  * 

### 参考官方指导api：
![BroadcastReceiver类讲解](https://developer.android.com/reference/android/content/BroadcastReceiver.html)
![Broadcasts开发指南介绍](https://developer.android.com/guide/components/broadcasts.html)
