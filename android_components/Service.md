## 一、什么是Service？
 * 官方api介绍：
  `Most confusion about the Service class actually revolves around what it is not:

A Service is not a separate process. The Service object itself does not imply it is running in its own process; unless otherwise specified, it runs in the same process as the application it is part of.
A Service is not a thread. It is not a means itself to do work off of the main thread (to avoid Application Not Responding errors).
Thus a Service itself is actually very simple, providing two main features:

A facility for the application to tell the system about something it wants to be doing in the background (even when the user is not directly interacting with the application). This corresponds to calls to Context.startService(), which ask the system to schedule work for the service, to be run until the service or someone else explicitly stop it.
A facility for an application to expose some of its functionality to other applications. This corresponds to calls to Context.bindService(), which allows a long-standing connection to be made to the service in order to interact with it.`<br/>
 * service是可以长期在后台运行的服务组件。service没有运行在单独的线程中，而是运行在UI主线程中的。也就是说，如果用户主动结束应用的进程，相关服务也会被结束掉。<br/>
## 二、Service启动方式
 * （1）context.startService()<br/>
 * （2）绑定方式启动（bindService）<br/>
 * service启动流程图（图片来自网络）：<br/>
  ![service启动流程图](https://github.com/ronindong/Android_InterView_Tips/blob/master/image/service_start_flow.png)<br/>
  
## 三、Service和Thread的区别
 * （1）如果你仅仅需要执行后台任务，并不需要和用户交互，此时你可以使用service。此时依然需要把耗时操作放在工作线程Thread中去执行。<br/>
 * （2）如果你需要在主线程在执行任务，并且当需要和用户交互的时候，此时你可以选择新建一个thread而非service。<br/>
 * （3）在某一个activity中去创建Thread，其他activity很难去控制该线程，无法去对thread进行操作。而Service可以和多个activity进行关联。


### 参考官方指导api:
[Service](https://developer.android.com/reference/android/app/Service.html)<br/>

