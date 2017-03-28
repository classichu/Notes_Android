1. 生命周期 
	
	onCreate —— onStart—— onResume——onPause——onStop——onDestory

	场景1：第一次启动A   A：【onCreate —— onStart—— onResume】
	场景2：在A上启动B    A：【onPause —— （被B覆盖）onStop——（finish或系统回收） onDestory】    					B【onCreate —— onStart—— onResume】（B会等到A的onPause运行后，执行，所有保存瞬时数据应该在onPause里，耗时操作需要开子线程处理）

	场景3：从A返回B      B【onPause —— onStop—— onDestory】
 						A1：【（finish或系统回收）onCreate —— onStart—— onResume】或
						A2：【 onReStart——onStart—— onResume】
	



2.横竖屏幕切换生命周期
	1、不设置Activity的android:configChanges时，切屏会重新调用各个生命周期，切横屏时会执行一次，切竖屏时会执行两次

	2、设置Activity的android:configChanges="orientation"时，切屏还是会重新调用各个生命周期，切横、竖屏时只会执行一次

	3、设置Activity的android:configChanges="orientation|keyboardHidden"时，切屏不会重新调用各个生命周期，只会执行onConfigurationChanged方法









Android生命周期该做的事


onCreate()

声明UI元素，定义成员变量，配置UI等
尽量少做些事，避免程序启动太久而看不见界面
一旦onCreate() 操作完成，系统会迅速调用onStart() 与onResume()方法


onDestoty()

需要将该activity彻底移除的信号时，系统会调用这个方法
大多数app并不需要实现onDestory()这个方法，由于局部类references会随activity的销毁而销毁
我们的activity应该在onPause(), onStop()中执行清除activity资源的操作
如果含有onCreate()中创建的后台线程，或是其他有可能导致内存泄漏的的资源，应在onDestory()中清理资源
在onCreate()中，直接调用finish()方法，系统会直接调用onDestory（）方法，跳过其他的声明周期


onPause()

停止动画或其他运行的的操作，那些都会导致cpu浪费
提交用户离开时期保存的内容(例如邮箱草稿)
释放系统资源，Camera,Broadcast Receiver,sensors(传感器，比如GPS) ，以及任何其他影响电量的资源
不应该保存用户数据到永久存储上 (File或Db中)
尽量减少onPause() 中的工作量避免切换到下一个activity变得缓慢


onResume()

恢复activity时，应该初始化那些onPause() 释放掉的组件
执行那些activity每次进入resume state 都需要进行初始化的动作


onStop()

应该释放那些不再需要的所有资源，避免内存泄漏，onStop() 后系统会在需要内存空间时摧毁它的实例
使用onStop()来执行那些CPU intensive的shut-down操作，例如往数据库写信息
系统会保存布局中视图的当前状态，例如，可以保存EditText中的文本内容


onStart()

在onStop()中里面做了那些清除的操作，就应该做instant中把那些清除掉的资源重新创建出来