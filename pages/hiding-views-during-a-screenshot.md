# iOS compatability

iOS 7/8/9 confirmed.

# Hiding views during a screenshot

Sometimes you want to hide something while taking a screenshot. These are some ways to do it. I use them in e.g. Assistive+.

# iOS 7, 8 and below 9.2

```objective-c
%hook SBScreenShotter

-(void)saveScreenshot:(_Bool)arg1{
    your_view.hidden = YES;
    [your_view setNeedsDisplay];

    dispatch_time_t popTime = dispatch_time(DISPATCH_TIME_NOW, (int64_t)(0.005 * NSEC_PER_SEC));
    dispatch_after(popTime, dispatch_get_main_queue(), ^(void) {
        %orig();
    });
}

- (void)finishedWritingScreenshot:(id)arg1 didFinishSavingWithError:(id)arg2 context:(void*)arg3{
    your_view.hidden = NO;
    %orig();
}

%end
```

# iOS 9.2

The screenshotter class is gone and now we can do this instead.

```objective-c
%hook SBScreenshotManager 

-(void)saveScreenshotsWithCompletion:(/*^block*/id)arg1{
    your_view.hidden = YES;
    [your_view setNeedsDisplay];

    dispatch_time_t popTime = dispatch_time(DISPATCH_TIME_NOW, (int64_t)(0.005 * NSEC_PER_SEC));
    dispatch_after(popTime, dispatch_get_main_queue(), ^(void) {
        %orig();

        dispatch_time_t popTime = dispatch_time(DISPATCH_TIME_NOW, (int64_t)(0.005 * NSEC_PER_SEC));
        dispatch_after(popTime, dispatch_get_main_queue(), ^(void) {
            your_view.hidden = NO;
        });
    });
}

%end
```