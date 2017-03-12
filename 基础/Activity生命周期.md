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