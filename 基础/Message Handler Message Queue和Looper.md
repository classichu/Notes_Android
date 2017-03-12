
Handler 先进先出原则。Looper类用来管理特定线程内对象之间的消息交换(Message Exchange)。


一个线程可以产生一个Looper对象，由它来管理此线程里的Message Queue(消息队列)

UI线程：UI thread 通常就是main thread，而Android启动程序时会默认替它建立一个Message Queue。


在非主线程中直接new Handler() 
会报如下的错误: java.lang.RuntimeException: Can't create handler inside thread that has not called Looper.prepare() 

原因是非主线程中默认没有创建Looper对象，需要先调用Looper.prepare()启用Looper。



Looper管理一个Message Queue，Looper.loop() 不断取出Message Queue的Message
