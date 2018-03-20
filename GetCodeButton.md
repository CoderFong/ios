#### GetCodeButton

```
// 代码创建self.getCodeBtn
// xib创建的会出现一闪一闪的问题

- (void)startTimer {
    __block int time = 60;
    __block UIButton *verifybutton = self.getCodeBtn;
    verifybutton.enabled = NO;
    dispatch_queue_t queue = dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0);
    dispatch_source_t _timer = dispatch_source_create(DISPATCH_SOURCE_TYPE_TIMER, 0, 0,queue);
    dispatch_source_set_timer(_timer,dispatch_walltime(NULL, 0),1.0*NSEC_PER_SEC, 0); //每秒执行
    dispatch_source_set_event_handler(_timer, ^{
        if(time<=0){ //倒计时结束，关闭
            dispatch_source_cancel(_timer);
            dispatch_async(dispatch_get_main_queue(), ^{
                [verifybutton setTitle:@"获取验证码" forState:UIControlStateNormal];
                verifybutton.enabled = YES;
            });
        }else{
            dispatch_async(dispatch_get_main_queue(), ^{
                NSString *strTime = [NSString stringWithFormat:@"%ds",time];
                [verifybutton setTitle:strTime forState:UIControlStateNormal];
                verifybutton.titleLabel.textColor = [UIColor whiteColor];
            });
            time--;
        }
    });
    dispatch_resume(_timer);
}
```
 
