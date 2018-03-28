#### ipod闪退

![](https://raw.githubusercontent.com/CoderFong/image/master/ipod1.png)



根据崩溃日志，很轻易能找到崩溃原因：usernotification的问题，这个库是ios10之后推出的，所以在ios9.3.5系统的iPod上会闪退。

需要根据系统判断环境，然后分别处理

![](https://raw.githubusercontent.com/CoderFong/image/master/ipod2.png)

