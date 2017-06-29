## 一、BroadcastReceiver（广播）定义
 * 首先看下android api对BroadcastReceiver的定义：
  `
  Android apps can send or receive broadcast messages from the Android system and other Android apps, similar to the publish-subscribe design pattern. These broadcasts are sent when an event of interest occurs. For example, the Android system sends broadcasts when various system events occur, such as when the system boots up or the device starts charging. Apps can also send custom broadcasts, for example, to notify other apps of something that they might be interested in (for example, some new data has been downloaded).
  `
 * 从第一句话中可以看出，BroadcastReceiver（广播）是一种可以运用在应用程序之间传递信息。
  
## 二、BroadcastReceiver使用场景
  * （1）应用程序内部不同组件之间的通信，包括APP多进程之间的通信<br/>
  * （2）不同应用程序之间的消息通信<br/>
  
## 三、BroadcastReceiver类型
 * 一般广播（Normal Broadcast）：通过Context.sendBroadcast()发送;<br/>
 * 有序广播（Ordered Broadcast）：通过Context.sendOrderedBroadcast()发送<br/>
  `
  有序广播是用sendOrderedBroadcast来发送。高优先级的接收者会先接收到广播，然后它可以决定是否继续转发，让低优先级的接收者接收到，或者终止广播。高优先级的接收者可以通过setResult把一些信息传给下一个接收者，下一个接收者则通过getResult获取上一个接收者传过来的信息。这个优先级也是用android:priority来设置，范围是-1000到1000。
  `<br/>
 * 粘性广播（Sticky Broadcast）：通过Context.sendStickyBroadcast()发送；<br/>
    `
  即使没有接收者，发送的广播Intent也会一直驻留在系统中，一旦有receiver注册，就会立即收到之前发送的广播。发送这个广播的应用需要权限<uses-permissionandroid:name="android.permission.BROADCAST_STICKY" />
如果sendStickyBroadcast发了多个广播，但暂时没有接收者，系统会保留最后一条广播。当有receiver接收到广播并处理后，系统中驻留的广播Intent仍存在，只有在接收者调用removeStickyBroadcast后系统才会移除该Intent。
`<br/>
 * 本地广播（Local Broadcast）：只在APP内部之间传递的广播;通过support V4包中提供的LocalBroadcastManager来发送广播，其内部是通过Handler的来实现。
  
## 四、BroadcastReceiver注册方式
 * （1）静态注册：在AndroidManifest.xml文件中注册，该注册方式，注册完成后，会一直运行。<br/>
 * （2）动态注册：在Activity中通过调用`registerReceiver()/unregisterReceiver()`进行注册/解注册。跟随activity的生命周期。<br/>
 * 注意：动态注册的广播优先级高于静态注册的优先级，在sendBroadcast()之后，AMS(Activity Manager Service)会接受处理查找对应的广播接收者。在AMS中静态注册的接收者存在一张表中；动态注册的接受者单独存在一张表。AMS会合并两张表，并按照优先级进行排序。如果优先级相同，则把动态注册的广播放在前面。<br/>

## 五、BroadcastReceiver注意点 
 * 广播的OnReceiver()方法是运行在UI线程中的，如果执行耗时超过10s的操作，就会ANR异常，需要把耗时操作放到service或者工作线程中去。<br/>

### 参考博文：
 * [BroadcastReceiver的原理和使用](http://blog.csdn.net/yueqian_scut/article/details/51298996)<br/>
### 参考官方指导api：
 * [BroadcastReceiver类讲解](https://developer.android.com/reference/android/content/BroadcastReceiver.html) <br/>
 * [Broadcasts开发指南介绍](https://developer.android.com/guide/components/broadcasts.html)
