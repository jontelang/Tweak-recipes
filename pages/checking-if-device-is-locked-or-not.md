# iOS compatability

iOS 7 confirmed, 8+ probably as well.

# Checking if device is locked or not

```objective-c
// Interface
@interface SpringBoard : UIApplication
-(_Bool)isLocked;
@end

// Usage example
if ([(SpringBoard *)[UIApplication sharedApplication] isLocked]) {
    return;
}
```

or something like


```objective-c
SBLockScreenManager *lockScreenManager = (SBLockScreenManager *)[%c(SBLockScreenManager) sharedInstance];
if ([lockScreenManager isUILocked]){
    NSLog(@"sup");
}
```