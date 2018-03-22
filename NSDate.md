### NSDate

- 数字时间戳转日期
```
NSDateFormatter *formatter = [[NSDateFormatter alloc] init];
formatter.dateFormat = @"YYYY年MM月dd日";
// 数字时间戳转化为日期，如果为13位，则需要除以1000，或者去掉后3位
NSDate *startDate = [NSDate dateWithTimeIntervalSince1970:[[self.model.contractStart substringWithRange:NSMakeRange(0, 10)] doubleValue]];
NSString *startTime = [formatter stringFromDate:startDate];
```
- 根据NSDate计算星期
```
- (NSString *)getWeakFromDate:(NSDate *)date {
    NSCalendar *calendar = [[NSCalendar alloc] initWithCalendarIdentifier:NSCalendarIdentifierGregorian];
    NSDateComponents *comps = [[NSDateComponents alloc] init];
    NSInteger unitFlags = NSCalendarUnitYear | NSCalendarUnitMonth | NSCalendarUnitDay | NSCalendarUnitWeekday |
    NSCalendarUnitHour | NSCalendarUnitMinute | NSCalendarUnitSecond;
    comps = [calendar components:unitFlags fromDate:date];
    if ([comps weekday] == 1) {
        return @"星期日";
    }else if ([comps weekday] == 2) {
        return @"星期一";
    }else if ([comps weekday] == 3) {
        return @"星期二";
    }else if ([comps weekday] == 4) {
        return @"星期三";
    }else if ([comps weekday] == 5) {
        return @"星期四";
    }else if ([comps weekday] == 6) {
        return @"星期五";
    }else if ([comps weekday] == 7) {
        return @"星期六";
    }
    return @"";
}
```
- 计算两个NSDate之间的天数
```
- (NSInteger)getDaysFromDate:(NSDate *)fromDate toDate:(NSDate *)toDate {
    NSTimeInterval time = [fromDate timeIntervalSinceDate:toDate];
    return (NSInteger)time/(3600*24);
}
```
- 将字符串转成NSDate类型
```
- (NSDate *)dateFromString:(NSString *)dateString {
    NSDateFormatter *dateFormatter = [[NSDateFormatter alloc] init];
    [dateFormatter setDateFormat: @"yyyy-MM-dd"];
    NSDate *destDate= [dateFormatter dateFromString:dateString];
    return destDate;
}
```
- 传入今天的时间，返回明天的时间
```
- (NSString *)GetTomorrowDay:(NSDate *)aDate {
    NSCalendar *gregorian = [[NSCalendar alloc] initWithCalendarIdentifier:NSCalendarIdentifierGregorian];
    NSDateComponents *components = [gregorian components:NSCalendarUnitWeekday | NSCalendarUnitYear | NSCalendarUnitMonth | NSCalendarUnitDay fromDate:aDate];
    [components setDay:([components day]+1)];
    
    NSDate *beginningOfWeek = [gregorian dateFromComponents:components];
    NSDateFormatter *dateday = [[NSDateFormatter alloc] init];
    [dateday setDateFormat:@"yyyy-MM-dd"];
    return [dateday stringFromDate:beginningOfWeek];
}
```
