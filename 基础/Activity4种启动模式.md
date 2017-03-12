程序生成一个 回退栈 Back Stack 管理activity返回
AndroidManifest.xml 中aty下配置 android:launchMode属性
或者
(通过addFlags()的方式来设置启动模式有局限性，只能显示的设置“singleTask”和“singleTop”两种启动模式，而并没有对应“standard”和“singleInstance”启动模式的标识)
FLAG_ACTIVITY_NEW_TASK
？？  与"singleTask"启动模式的作用一样。（试验：FLAG_ACTIVITY_NEW_TASK并不像官方文档所说的等同与singleTask） 　　
FLAG_ACTIVITY_SINGLE_TOP
与"singleTop"启动模式的作用一样。
FLAG_ACTIVITY_CLEAR_TOP
？？ 这个标识的意思比较特殊。它不对应于我们上面所说的启动模式中的任何一种 相当于
it.setFlags(Intent.FLAG_ACTIVITY_NEW_TASK|Intent.FLAG_ACTIVITY_CLEAR_TASK);


1. standard  标准模式:默认模式。
2. singleTop  栈顶复用模式：如果已经在Task顶部，复用时onPause, 然后onNewIntent唤起, 走onResume流程. 否则都要创建新的实例。场景：搜索跳结果，结果也同样有搜索框能继续搜索。新闻多条推送打开web内容页。聊天的对话窗口。
3. singleTask  栈内复用模式：如果已经在Task顶部, 如同singleTop的复用模式;
如果不在Task顶部, 则销毁Task中该Activity顶部的所有其他Activity, 通过onNewIntent唤起该Activity, 走onRestart流程。场景：订单支付完成回首页。浏览器主页只打开一次
4. singleInstance  单实例模式：拥有singleTask一致的功能，区别是它让单独一个Task来管理这个活动。场景：闹铃提醒，将闹铃提醒与闹铃设置分离。

参考：

	http://www.cnblogs.com/plokmju/p/android_ActivityLauncherMode.html

	http://www.jianshu.com/p/4c8d6e2117ac

addFlags: 

	http://www.jianshu.com/p/c97688eb5056