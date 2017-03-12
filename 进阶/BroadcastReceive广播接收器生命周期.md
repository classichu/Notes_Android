生命周期只有十秒左右，如果在 onReceive() 内做超过十秒内的事情，就会报ANR(Application No Response) 程序无响应的错误信息

它的生命周期为从回调onReceive()方法开始到该方法返回结果后结束