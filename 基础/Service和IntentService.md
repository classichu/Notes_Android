Service运行在主线程中，耗时操作会报错,需要在启动的时候new thread 执行  在最后面 紧跟stopself（）

IntentService 自动运行在异步子线程，而且会自动停止，所以常用。