### NSDate

- 数字时间戳转日期

  ```
  NSDateFormatter *formatter = [[NSDateFormatter alloc] init];
  formatter.dateFormat = @"YYYY年MM月dd日";
  // 数字时间戳转化为日期，如果为13位，则需要除以1000，或者去掉后3位
  NSDate *startDate = [NSDate dateWithTimeIntervalSince1970:[[self.model.contractStart substringWithRange:NSMakeRange(0, 10)] doubleValue]];
  NSString *startTime = [formatter stringFromDate:startDate];
  ```

  ​

  ​

