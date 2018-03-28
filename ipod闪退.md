#### ipod闪退

![mage-20180328135707](/var/folders/68/qkffd9n17175z5x2ydxnp6cm0000gn/T/abnerworks.Typora/image-201803281357074.png)



根据崩溃日志，很轻易能找到崩溃原因：usernotification的问题，这个库是ios10之后推出的，所以在ios9.3.5系统的iPod上会闪退。

需要根据系统判断环境，然后分别处理

![mage-20180328141720](/var/folders/68/qkffd9n17175z5x2ydxnp6cm0000gn/T/abnerworks.Typora/image-201803281417200.png)

