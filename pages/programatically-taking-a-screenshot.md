# iOS compatability

iOS 6/7/8/9

# Programatically taking a screenshot

# iOS 6, 7, 8 and below 9.2

```objective-c
@interface SBScreenShotter
 +(id)sharedInstance;
 -(void)saveScreenshot:(_Bool)arg1;
@end

SBScreenShotter* s = [objc_getClass("SBScreenShotter") sharedInstance];
[s saveScreenshot:YES];
```

# iOS 9.2+

The screenshotter class is gone and now we can do this instead.

```objective-c
@interface SBScreenshotManagerDataSource : NSObject
@end

@interface SBScreenshotManager : NSObject
-(id)initWithDataSource:(id)arg1;
-(void)saveScreenshotsWithCompletion:(/*^block*/id)arg1;
@end

SBScreenshotManagerDataSource *d = [[objc_getClass("SBScreenshotManagerDataSource") alloc] init];
SBScreenshotManager* s = [[objc_getClass("SBScreenshotManager") alloc] initWithDataSource:d];
[s saveScreenshotsWithCompletion:nil];
```