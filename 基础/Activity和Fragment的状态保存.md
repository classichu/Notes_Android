Activity

非主动销毁会调用onSaveInstanceState：
onSaveInstanceState()只适合用于保存一些临时性的状态，而onPause()适合用于数据的持久化保存。

在恢复时候：能通过onCreate(Bundle)或者onRestoreInstanceState(Bundle)恢复界面的状态。onRestoreInstanceState的bundle参数也会传递到onCreate方法中，你也可以选择在onCreate方法中做数据还原.onRestoreInstanceState()在onStart() 和onPostCreate(Bundle)之间调用。



 onSaveInstanceState()方法的默认实现
　　如果我们没有覆写onSaveInstanceState()方法,此方法的默认实现会自动保存activity中的某些状态数据,比如activity中各种UI控件的状态.。Android应用框架中定义的几乎所有UI控件都恰当的实现了onSaveInstanceState()方法,因此当activity被摧毁和重建时,这些UI控件会自动保存和恢复状态数据.比如EditText控件会自动保存和恢复输入的数据,而CheckBox控件会自动保存和恢复选中状态.开发者只需要为这些控件指定一个唯一的ID(通过设置android:id属性即可),剩余的事情就可以自动完成了.如果没有为控件指定ID, 则这个控件就不会进行自动的数据保存和恢复操作。
 
　　由上所述, 如果我们需要覆写onSaveInstanceState()方法,一般会在第一行代码中调用该方法的默认实现:super.onSaveInstanceState(outState)。



向数据库中插入记录等.保存持久化数据的操作应该放在onPause()中。若是永久性值，则在onPause()中保存；若大量，则另开线程吧，别阻塞UI线程。


onSaveInstanceState()在以下几种情况会被调用： 1，按home键时；2，横竖屏切换时；3，按电源键时；4，从当前activity进入另一个activity时。 系统默认只会保存ui状态--view hierarchy，比如editext里面的text，或者listview的scroll位置， 不会保存别的信息，如果需要保存则复写此方法。


Fragment

