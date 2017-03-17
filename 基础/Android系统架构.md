大概分4层  

=》linux内核层（内存管理，进程管理，网络协议和各种驱动等）

=》Android系统库层
==》Android系统自动c/c++的库文件来支持一些组件运行：SQLite、WebKit、MediaFramewok、SSL库等等。
==》Android运行环境（分Dalvik虚拟机(一个应用一个进程，一个虚拟机实例，是基于寄存器的java虚拟机，不是基于栈的java虚拟机，编译生成dex中间吗，而不是生成传统的字节码。)和核心库（提供java语言核心库中的大多数功能），包括：android运行时层：多媒体、数据库和webkit等）。。。。。
每一个Android应用程序都在它自己的进程中运行，都拥有一个独立的Dalvik虚拟机实例。Dalvik被设计成一个设备可以同时高效地运行多个虚拟系统。 Dalvik虚拟机执行(.dex)的Dalvik可执行文件，该格式文件针对小内存使用做了优化。同时虚拟机是基于寄存器的，所有的类都经由JAVA编译器编译，然后通过SDK中 的 "dx" 工具转化成.dex格式由虚拟机执行。

=》android 框架层（提供Api开发框架）：activity manager、window manager、资源、位置管理器、XMPP服务等

=》android应用层：google服务、地图、音乐播放、视频播放等等软件

