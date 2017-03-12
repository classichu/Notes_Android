invalidate()得在UI线程中被调动，在工作者线程中可以通过Handler来通知UI线程进行界面更新。


而postInvalidate()在工作者线程中被调用